---
title: 'OpenStack, Logstash and Elasticsearch: living on the edge'
date: '18-09-2014 11:25'
taxonomy:
    category:
        - Eurecom
---

As part of my work for [Bigfoot](http://bigfootproject.eu), I deployed a system to gather application logs and metering data coming from an [OpenStack](http://openstack.org)installation into [Elasticsearch](http://elasticsearch.org), for data analysis and processing. This post is based on OpenStack Icehouse.

## Ceilometer to Elasticsearch

Ceilometer promises to gather metering data from the OpenStack cloud and aggregate it into a database, where it can be accessed by monitoring and billing software. In reality getting some data is very easy, but getting all the data is very hard, and in some cases, impossible.

Some OpenStack projects integrate the metering functionality and send their samples (VM CPU usage, disk, network, etc.) via RabbitMQ to a central agent. Other do not integrate Ceilometer (why? I don't know) and the administrator has to run periodically a separate script/daemon to gather the information and send it out. The lack of documentation in this area is almost complete, I found out about "neutron-metering-agent" and "cinder-volume-usage-audit" by chance and doing Google searches for them, right now, results in nothing that explains what they are and how
to use them.

Once the data is gathered, Ceilometer wants to store it into a database. MongoDB is highly suggested, but it does not work together with Sahara, another OpenStack project. The [issue ticket](https://bugs.launchpad.net/ceilometer/+bug/1246264) has been opened almost a year ago, and it is still open.

Mysql is not up to the task, a week of data causes the database to grow to a few tens of gigabytes. The script provided by Ceilometer to delete old data then tries to load everything in memory, hits swap and all hope is lost. I let it run for a week trying to delete one day of data, then I decided to try something else.

Ceilometer can send the data in [msgpack](http://msgpack.org/)format via UDP to an external collector. I removed the central agent and the database and pointed Ceilometer to [Logstash](http://logstash.net/).
Connecting Logstash to Elasticsearch is very easy and now I can do something useful with the data. It works quite well, and here is how I did it:

First, the Ceilometer pipeline.yaml:

```yaml
    sources:
      - name: bigfoot_source
        interval: 60
        meters:
            - "*"
        sinks:
            - bigfoot_sink
    sinks:
      - name: bigfoot_sink
        transformers:
        publishers:
          - udp://<logstash ip>:<logstash port>
```

This file has to be copied to all OpenStack hosts running Ceilometer agents (even on the Swift Proxy that does not have a standalone agent).

Logstash needs an input:

```
    input {
      udp {
        port => <some port>
        codec => msgpack
        type => ceilometer
      }
    }
```

and some filters:

```
    filter {
      if [type] == "ceilometer" and [counter_name] == "bandwidth" {
        date {
          match => [ "timestamp", "YYY-MM-dd HH:mm:ss.SSSSSS" ]
          remove_field => "timestamp"
          timezone => "UTC"
        }
      }
      if [type] == "ceilometer" and [counter_name] == "volume" {
        date {
          match => [ "timestamp", "YYY-MM-dd HH:mm:ss.SSSSSS" ]
          remove_field => "timestamp"
          timezone => "UTC"
        }
        date {
          match =>["[resource_metadata][created_at]","YYY-MM-dd HH:mm:ss"]
          remove_field => "[resource_metadata][created_at]"
          target => "[resource_metadata][created_at_parsed]"
          timezone => "UTC"
        }
      }
      if [type] == "ceilometer" and [counter_name] == "volume.size" {
        date {
          match => [ "timestamp", "YYY-MM-dd HH:mm:ss.SSSSSS" ]
          remove_field => "timestamp"
          timezone => "UTC"
        }
        date {
          match =>["[resource_metadata][created_at]","YYY-MM-dd HH:mm:ss"]
          remove_field => "[resource_metadata][created_at]"
          target => "[resource_metadata][created_at_parsed]"
          timezone => "UTC"
        }
      }
    }
```
These filters are needed because date formats in Ceilometer messages are inconsistent. Without these filters Elasticsearch will try to parse them and fail, discarding the messages. Perhaps there are other messages with this problem, but the only way to find them is wait for a parser exception in Elasticsearch logs.

I think this configuration is much more scalable, flexible and useful to the end user than the standard Ceilometer way, with its database and custom API for which there are no consumers.

## Application logs

Managing an OpenStack deployment is hard. It is a complex distributed system, composed of many processes running on different physical machines. Each process logs to a different file, on the machine it is running on. A general lack of documentation and inconsistent use of log levels across OpenStack projects means that trying to investigate an issue is a tedious and time consuming job. Processes need to be restarted with debugging enabled, and a few important lines get lost
among tons of other stuff.

To try to simplify this situation I used again Logstash+Elasticsearch to gather all the application logs coming from OpenStack. To work at its best and provide meaningful searches (all messages from a certain Python module, all messages with exception traces), I decided to use a Python logging module that would translate the Python log objects into Logstash (json) dictionaries. This way the structure is conserved and not lost in syslog-like text translation.

Doing that is fairly simple, with a few caveats. First you will need to install [python-logstash](https://github.com/bigfootproject/python-logstash) (my version reduces the number of fields that get discarded).

Then add this file to the configuration directory of the project you want to get the logs from (for example /etc/neutron/logging.conf):

```ini
    [loggers]
    keys=root

    [handlers]
    keys=stream

    [formatters]
    keys=

    [logger_root]
    level=INFO
    handlers=stream

    [handler_stream]
    class=logstash.UDPLogstashHandler
    args=(<logstash server>, <logstash port>, 'pythonlog', None, False, 1)
```

And finally add this option to Neutron's config file (it is the same for the other OpenStack projects):

```
    log_config_append=/etc/neutron/logging.conf
```

Configuring logstash is easy, just add this:

```
    input {
      udp {
        codec => "json"
        port => <some port>
        type => "pythonlog"
        buffer_size => 16384
      }
    }
```

Now, the caveats:

* this will disable completely any other logging option you set in the configuration files (debug, verbose, log\_dir, ...). Disregard what the documentation says about the fact the logging conguration will be appended, it does not, it overrides anything else and because of how the python logging system is made, there is nothing that can be done. If you use that option, all logging configuration has to reside in the logging.conf file.
* The configuration above discards all logs with a level lower than INFO. DEBUG level is needed to investigate issues, but the volume of logs coming from a full OpenStack install at DEBUG level is just too big and imposes useless load.
* Depending on the size and the load of your deployment, you may need to scale up both logstash and elasticsearch.

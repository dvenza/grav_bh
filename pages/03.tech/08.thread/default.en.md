---
title: Thread
date: '24-12-2002 12:31'
---

This sample code shows how to execution a function (`my_thread`) in a different thread.

```c
#include <stdio.h>
#include <pthread.h>

void *my_thread();

int a, b, c, x=1, y=4, z=9, w;

int main()
{
        pthread_t my_thr;
        int err;

        err = pthread_create(&my_thr, NULL, &my_thread, NULL);
        a = x + y;
        pthread_join(my_thr, NULL);
        c = a - b;
        w = c + 1;
        printf("a=%d b=%d c=%d x=%d y=%d z=%d w=%d\n", a, b, c, x, y, z, w);
        exit(0);
}

void *my_thread()
{
        b = z + 1;
        pthread_exit(NULL);
}
```

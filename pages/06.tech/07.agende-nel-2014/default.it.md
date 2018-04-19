---
title: 'Agende nel 2014'
date: '23-03-2014 13:19'
---

Sono sempre alla ricerca di modi per organizzarmi meglio e periodicamente parto per delle quest, alla ricerca della soluzione definitiva ai miei problemi. Oggi riassumo i risultati delle mie ricerche sui modi migliori per organizzare una agenda di cose da fare.

I miei requisiti sono semplici, almeno all'apparenza:

1.  Client offline Android e PC (windows), sincronizzazione automatica
2.  I dati devono risiedere sul mio server
3.  Integrazione con la rubrica (compleanni, liste di persone presenti alle riunioni)
4.  Integrazione con un gestore di "attività/task". Mi riferisco ai task inclusi nella specifica del protocollo caldav (i VTODO nella definizione dell'[RFC 2445](http://www.ietf.org/rfc/rfc2445.txt)).

Sinceramente, non penso di chiedere la Luna. Il punto 1 dovrebbe essere piuttosto diffuso vista la quantità di telefoni Android e PC Windows in circolazione.Il punto 2 dovrebbe interessare a chiunque abbia o un minimo di riguardo per la propria privacy, o voglia tenere i dati della propria attività lavorativa sotto il proprio controllo e non cederlo a terzi.
Il punto 3 è questione di integrazione tra servizi esistenti, niente di nuovo da inventare. Outlook con Exchange lo fa già molto bene da tanto tempo, ad esempio.
Il punto 4, i task: mi piacerebbe poter tenere una lista delle cose che ho in mente di fare. Alcune hanno delle scadenze e altre no. Quelle che hanno scadenza dovrebbero apparire nell'agenda. Di nuovo, integrazione tra servizi, niente di nuovo.

Dopo innumerevoli ricerche, ripensamenti, installazioni e software in prova sono giunto alla conclusione che c'è parecchia strada da fare. Vediamo un po'.
## Server

Per fare sincronizzazione facile ed affidabile ci vuole un server. La soluzione più promettente in quanto standardizzata e aperta sembra è [caldav](http://en.wikipedia.org/wiki/CalDAV). Ci sono vari server, uno che ho provato è [baïkal](http://baikal-server.com/), che mi sembra faccia il suo lavoro egregiamente ed è facile da installare. Un altro è [radicale](http://radicale.org/documentation/), ma è implementato in Python e quindi non è facile da installare su un web server in hosting. Il mio provider di posta offre anche un server suo, basato su [SabreDAV](http://sabre.io/), a cui hanno aggiunto un'interfaccia web.

Il lato server è il più facile, ci sono varie soluzioni, tutte buone.

## Client Android

Qui inizia il calvario. Android non supporta caldav. Ci sono app [a pagamento](https://play.google.com/store/apps/details?id=org.dmfs.caldav.lib) o [gratuite](https://play.google.com/store/apps/details?id=at.bitfire.davdroid) (beta) che fanno la sincronizzazione (ma non la fanno dei task per qualche motivo a me ignoto).

Questo già mi sembra un po' tanto grave in un sistema operativo che fa di un punto di forza il suo essere aperto e libero.

Una volta che l'agenda è sincronizzata (ma non i task/attività, ripeto) ci sono varie app, alcune anche molto carine e ben fatte. Uso [Business Calendar Pro](https://play.google.com/store/apps/details?id=mikado.bizcalpro), che ha dei bei widget, ma c'è anche [SolCalendar](https://play.google.com/store/apps/details?id=net.daum.android.solcalendar).

Businness Calendar ha un supporto parziale per gli inviti ai meeting che arrivano da un calendario Google. Dico parziale perché appare la domanda "vuoi partecipare a questo meeting?", ma poi non mi sembra che accada alcunché, qualunque sia la riposta.

Esiste una app, chiamata [Birthday Adapter](https://play.google.com/store/apps/details?id=org.birthdayadapter.free), che riempie un calendario a scelta coi compleanni presi dalla rubrica di Android. È utile, ma è un tapullo. Gli eventi sono visibili solo sul cellulare ed è ancora un altro servizio che deve girare su un dispositivo a batteria quando invece potrebbe essere fatto lato server ed essere condiviso su tutti i dispositivi.

Per i task c'è [Mirakel](https://play.google.com/store/apps/details?id=de.azapps.mirakelandroid). Che vuole una versione con patch della app per sincronizzare caldav. È tutto molto beta. Oppure c'è [una app](https://play.google.com/store/apps/details?id=org.dmfs.tasks) della stessa persona che fa caldav-sync, la app a pagamento per la sincronizzazione, ma è limitata e non fa cose fondamentali come i task ricorrenti (tipo qualcosa che si ripete una volta a settimana).

## Client Windows

C'è [Thunderbird](http://www.mozilla.org/it/thunderbird/)con l'addon [lightning](http://www.mozilla.org/en-US/projects/calendar/). Poverino, fa il suo dovere e ha qualche bachetto. Zero sincronizzazione con la rubrica, che comunque in Thunderbird non si sincronizza. Non trova da solo tutti i calendari in un account e bisogna aggiungerli uno alla volta manualmente.
In alternativa c'è [eM client](http://www.emclient.com/). Che è un client di posta più moderno, ma che non solo vuole una licenza, ma aggiunge veramente pochissimo (una rubrica che si sincronizza) a quello che fa Thunderbird. Non sono a conoscenza di altri software, forse ci sono dei port di software Linux, come Evolution, ma nella mia esperienza è raro che tali progetti di porting funzionino decentemente e siano supportati bene.

## Personalizzazioni

Ho sviluppato uno script che scarica un calendario condiviso e lo ripubblica all'interno di un calendario privato. Serve ad accentrare in un punto unico (il mio server) tutti i calendari di cui ho bisogno. Ad esempio uso un calendario pubblico di festività francesi e lo importo sul mio server, a questo modo ho quegli eventi su tutti i miei dispositivi automaticamente. Ho intenzione di estendere la cosa anche per i compleanni, basta leggere dalla rubrica condivisa e creare degli eventi in un calendario apposta.

## Conclusioni

Manca del tutto un sistema di organizzazione personale, per singoli individui. Un sistema che racchiuda rubrica, calendario, posta e task manager, usando tecnologie e software esistenti e già diffusi, senza reinventare la ruota. La maggior parte delle componenti esiste già, mancano un po' di pezzetti qui e là ed un po' di colla per tenere insieme il tutto e dargli un aspetto decoroso. Ad averci il tempo potrebbe essere anche un progetto interessante, ma per ora purtroppo, si va avanti a script o si fa senza.

## Curiosità

Durante la mia quest ho incontrato siti interessanti:

* [Guida per creare un client caldav](http://sabre.io/dav/building-a-caldav-client/)
* [Package Python](http://icalendar.readthedocs.org/en/latest/index.html) per leggere e scrivere in formato iCalendar
* Calendari pubblici di [festività nazionali](http://www.mozilla.org/en-US/projects/calendar/holidays/) e di [altre cose a caso](http://icalshare.com/) (tipo i compleanni dei personaggi dei fumetti)

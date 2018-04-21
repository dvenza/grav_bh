---
title: 'Storia del sito'
---

## Che bello il blog di initd (2004-10-06)

Era da un po' che pensavo di mettere insieme un mio blog, solo che non ho mai avuto il tempo di installarne uno sul mio server di casa. Avevo guardato un po' i vari software esistenti, ma mi sono sembrati tutti abbastanza complicati da richiedere un certo tempo per l'installazione (e soprattutto per il mantenimento).
Ora, visto che qualcun altro ha fatto il lavoro per me (grazie fog), come rinunciarvi ?

## Traslochi (2005-02-08)

Dopo aver spostato il blog da *initd* (uno spazio web offerto da associazioni LUG di Torino ed Alessandria) a qui, sul mio server, per poterci giocare più facilmente, senza dover rompere tutte le volte a fog per chiedergli di installarmi qualche nuovo plugin, ho buttato via pyblosxom, passando a drupal.

Il cambio non è stato del tutto indolore perché non ho potuto importare i vecchi post mantenendo la data originale.

Li ho ripostati lo stesso, aggiungendo in fondo la data, sono solo un paio e li trovate subito dopo di questo.

Mi trovo bene con drupal, è senz'altro esagerato per le mie esigenze, ma funziona bene, in particolare il post via xmlrpc e non ha problemi con le immagini.

## Novità (2005-02-18)

Tante novità, per cominciare sono molto soddisfatto dell'acquisto del Mac Mini. Ho avuto la sfortunata idea di installare windows media player 9 per Os X per vedere i filmati i wmv e da quel momento Safari ha iniziato a piantarsi ogni volta che vede un file di quel tipo. Eliminare windows media player non ha eliminato il problema... Al suo posto ho messo [mplayer per Os X](http://mplayerosx.sourceforge.net/), che vede un sacco di formati e pare funzionare bene.
Infine ho appena comperato un dominio e dello spazio web, appena tutte le pratiche saranno concluse inizierò a spostare il sito, purtroppo questo blog è destinato ancora a qualche travaglio. Aggiornamenti a seguire.

## Altri traslochi (2005-02-21)

Ho spostato tutto il sito e il blog su un nuovo server, con un dominio nuovo di zecca. Il mio povero server a casa non ce la faceva più, ma soprattutto non mi fidavo a tenerci sopra così tanta roba senza avere il tempo di stare dietro a tutti gli aggiornamenti di sicurezza.

Per far andare Drupal su Debian woody sono necessari diversi backport, che non è detto siano sempre aggiornatissimi in fatto di sicurezza.
Questa volta sono anche riuscito a importare i post mantenendo la data originale, o meglio prima ho ripostato tutti gli articoli, poi ho modificato il database a mano. Le date sono memorizzate in secondi dall'epoca UNIX, quindi è bastato usare `date "01 gen 2005 12:10" +%s` per ottenere la data da incollare in mysql.

## La giornata del sistemista (2005-03-24)

Oggi ho passato la giornata a giocare al piccolo sistemista. Tenendo iTunes in background con una radio online di sola musica anni '80 e lavorando via ssh sul server casalingo ho giocato un po' con tethereal e [subversion](http://subversion.tigris.org/), ottenendo delle cose abbastanza utili.

Stamattina tethereal. Fino ad oggi usavo tcpdump e uno scriptino bash per recuperare le informazioni su certi pacchetti che mi interessano, però la soluzione non era ottimale perché catturava poche informazioni su troppi pacchetti, dato che tcpdump non ha filtri per protocolli ad alto livello.
Con tethereal posso catturare solo i pacchetti che mi interessano in un certo periodo di tempo e metterne il dump in un file (in formato pcap). Uno script chiamato da cron, ad intervalli regolari, uccide il processo di cattura, esegue di nuovo tethereal sul file di cattura con parametri differenti (per fargli risolvere gli indirizzi IP) passando l'output ad un programmino in [Python](http://www.python.org/) per estrarre solo le informazioni interessanti. Alla fine mi manda il tutto via mail e rimette in esecuzione il processo di cattura su un file vuoto. Quei simpaticoni di Echelon a confronto sono dei pivellini.

Il pomeriggio, invece, l'ho passato a litigarmi con subversion, apache2, mod_ssl e mod_auth_pam, però alla fine ne ho avuto ragione...
La configurazione che mi ero posto come obiettivo era:

1.  area pubblica in sola lettura
2.  autenticazione per poter modificare il repository

Avevo già l'autenticazione grazie a svn+ssh, ma dove sto facendo la tesi escono su Internet solo con un proxy (anche se ogni tanto si esce tranquilli con un NAT, dipende dalle maree e da certi riti sull'altare che hanno in terrazzo, credo) e volevo anche poter fornire accesso al 'grande pubblico', in particolare per il driver sis900.

L'unico tipo di autenticazione su http che funziona con mod_auth_pam (non volevo avere ancora un'altra password diversa) è 'Basic', con la password che viaggia in chiaro per mezzo mondo. La soluzione è stata usare mod_ssl. Non ci sono alternative se non criptare l'intera connessione, anche se l'unica cosa che vuoi tenere segreta è la password. Bah.

Mi sono creato la mia CA fasulla e l'ho usata per firmare il mio certificato fasullo anche lui e ora ho la mia brava connessione su https, alla faccia di tutti quelli che dicono che non si può avere SSL insieme ai virtual host di Apache (certo, non si può se si fanno le cose sul serio, con dei certificati veri, ma se uno fa finta di non vedere un paio di warning all'avvio di apache, problemi non ce ne sono...). Ora su https magari ci metto pure su un webmail, così posso leggermi la posta anche quando il sistemista in ditta si dimentica di fare i sacrifici agli dei.

Alla fine pure mod_auth_pam ha iniziato a funzionare senza particolari problemi (occhio che su Debian bisogna attivarlo con `AuthPAM_Enabled on`, anche se nella [documentazione sul sito](http://pam.sourceforge.net/mod_auth_pam/configure.html) dice che quello è il valore di default).

Ora devo solo attivare un po' di controllo di accesso sui singoli repository, attraverso un altro modulo dav_svn_<qualcosa>.

Appena c'è qualche cosa di significativo visibile all'esterno posto un link.

## Galleria fotografica (2005-04-13)

Ho appena finito di fare l'upload la [nuova galleria fotografica](http://www.brownhat.org/photos/index.php), l'ho scritta in questi ultimi giorni, dopo essermi stufato di quella vecchia. Ho speso parecchio tempo a costruire un buon formato sul disco per l'organizzazione delle foto e alla fine sono arrivato ad una doppia struttura. Le foto sono organizzate in directory per anno e mese, così se decido di cambiare la grafica o la categoria non perdo i bookmark e i motori di ricerca. L'organizzazione sta in un albero di directory separato, con una serie di file di testo che elencano le fotografie appartenenti a ciascuna suddivisione.

Ho usato solo XHTML e CSS, ma non ho ancora verificato se valida sul sito del w3c. Devo anche rifare tutte le thumbnail, in modo che abbiano le stesse dimensioni.

## Galleria fotografica 2 (2005-04-17)

Ho aggiornato la galleria fotografica con tutte le foto che valeva la pena pubblicare, ho aggiunto e tolto parecchia roba, quindi ci saranno sicuramente degli errori, segnalatemeli! Tutte le foto che ho mantenuto le ho ripassate allo scanner per essere sicuro sulla qualità e sulle dimensioni. Anche le date dei copyright ora sono giuste.
Insomma, un lavoraccio, ma dovrebbe essere per il meglio.

Qualunque commento è benvenuto.

## Antichi ricordi (2006-02-25)

Ho appena (ri)scoperto per puro caso [questo sito](http://users.libero.it/venza/), da lungo tempo dimenticato. In effetti ho dimenticato la password e quindi non ci posso fare più nulla, così è e così rimarrà fino alla fine dei suoi giorni. Sono piuttosto sorpreso che sia ancora lì, era lo spazio web fornito con il contratto Internet via modem 33.6K.
Quell'immagine con la pianta e la scritta l'avevo fatta con un qualche software di rendering 3D, mi ricordo che il mio povero macinino ci aveva messo anni a generare l'immagine a partire dalla scena. Il vaso e la pianta erano nella libreria di esempi, non ricordo neppure se avevo cambiato i colori.
Il contatore sembra ibernato su 2150 contatti.
Nella pagina proj.html c'è anche un blog, come ero avanti nei tempi !
I link erano abbastanza generici che sono ancora tutti funzionanti, tranne quelli che puntano a iol, dove c'è scritto 'Manutenzione straordinaria'. Sì, sì, certo.
Il numero ICQ è ancora buono, mentre l'indirizzo mail, crazy_ivan@unforgettable.com, non esiste più da un pezzo ;-)

Ah, non sono più un fan di Red Hat.

## Insoddisfazioni (2006-12-28)

Vorrei lamentarmi un po' dello stato attuale dei sistemi di *web publishing* esistenti. Una persona che abbia del contenuto da pubblicare su Internet ha varie possibilità.

Il blog è adatto ad un tipo di contenuto breve e cronologico. Ci si possono anche scrivere degli articoli, ma le cose diventano macchinose. Per cominciare è difficile scrivere offline: i software di blogging tipo Ecto o [MarsEdit](http://ranchero.com/marsedit/) sono all'inseguimento, ma stanno rimanendo indietro. [Ecto](http://ecto.kung-foo.tv/) è pieno di bachi, poco gravi, nella formattazione del testo, ma che danno parecchio fastidio. L'autore promette cose da fantascienza in ecto3 che non si sa quando arriverà. [Marsedit non funziona più con Blogger](http://www.newsgator.com/FORUM/Topic21478-11-1.aspx#bm23620), quindi l'ho buttato via dopo la prima prova. Entrambi vogliono anche dei soldi (24.95$ per MerdEdit e 17.95$ per Ecto). La situazione su Windows è ancora peggiore. Non ho provato il [client della Microsoft](https://support.microsoft.com/en-us/help/18614/windows-essentials) perché sono prevenuto, [Contribute della Adobe](http://www.adobe.com/products/contribute/) (149$) va bene per editare delle pagine web esistenti, ma quando ho provato a postare su un blog ha fatto casino e ha inquinato l'albero FTP con le sue directory. Altri client erano troppo immaturi e avevano problemi vari. Utilizzabili, ma insoddisfacenti.

Se uno rinuncia a scrivere offline, può usare le interfacce web offerte dai vari servizi online di blogging. Però il browser non è un editor di testo e non ci si riesce a scrivere niente di lungo o formattato in maniera un po' più complessa.

Programmi tipo iBlog (produced by Lifli, now discontinued) (19.95$) generano in locale una pagina web ad ogni aggiornamento e poi si offrono di farne l'upload su FTP. Possono andare bene, ma sono chiusi. Se uno si stufa e vuole cambiare programma, non gli rimane altro che editarsi a manina l'HTML, difficilmente potrà importarsi tutta la struttura (date, tag, categorie, commenti) in un altro programma simile.
Una soluzione simile, ma molto più interessante, se non altro dal punto di vista tecnico, è [TiddlyWiki](http://www.tiddlywiki.com/). È una pagina web in grado di autoeditarsi tramite una quantità di Javascript. È un po' lenta da caricare, non offre grandi possibilità come editor, ma è estremamente comoda per appunti personali o per un blog "da combattimento".

Poi ci sono i wiki. Vanno benissimo per scrivere qualcosa in maniera collaborativa. I sistemi di editing come [Textile](http://www.textism.com/tools/textile/) o
[Wikitext](http://meta.wikimedia.org/wiki/Help:Wikitext_examples) alleviano un po' le limitazioni del browser come editor e sono molto intuitivi. Rimane il problema dell'editing offline. Certo, uno può sempre scrivere su un file di testo e poi a mano fare il copia e incolla, sperando che nel mentre nessun'altro abbia modificato la pagina.
Per definizione i wiki sono sistemi aperti. Per un uso come sistema di publishing personale (un blog più strutturato o un sito web meno statico) sono sovradimensionati. Ho provato [moinmoin](http://moinmoin.wikiwikiweb.de/), ma è qualcosa di estremo come quantità di file da uploadare, decisamente esagerato. Per gli altri programmi è difficile scegliere, ce ne sono troppi e [WikiMatrix](http://www.wikimatrix.org/) non aiuta.

Ci sono i CMS, ma sono giusto un pelino troppo pesanti per un uso personale.

Infine uno può sempre scriversi direttamente le pagine html e tanti saluti. Per scrivere l'html può aiutarsi con programmi tipo [Dreamweaver](http://www.adobe.com/it/products/dreamweaver/) (574,80€ tanto per indicare il capo della categoria), ma deve comunque farsi al minimo un sistema di ricerca, uno di tagging ed uno di commenti, se li vuole. Ma qui dovrei iniziare un'altra filippica contro i linguaggi lato server (javascript è un bersaglio troppo banale), che mi tengo per la prossima volta.

Ah, ho messo su le foto della Svezia, abbiamo superato il totale di 500 foto !

## Aggiornamenti del sito (2007-04-25)

Oggi, giorno di festa nazionale, malgrado la mia iniziale intenzione di starmene in terrazzo a prendere il sole (ma ieri non avevano previsto pioggia, fulmini e tempeste ?), son finito a fare qualche modifica al sito. E quindi tra una partitella a Super Bubble Bobble e la lettura di un post del Dread che mi ha fatto ricordare che quando ero piccolo, guardando [Labirynth](http://www.imdb.com/title/tt0091369/?fr=c2l0ZT1kZnx0dD0xfGZiPXV8cG49MHxrdz0xfHE9bGFieXJpbnRofGZ0PTF8bXg9MjB8bG09NTAwfGNvPTF8c2M9MXxodG1sPTF8bm09MQ__;fc=1;ft=76;fm=1), mi ero innamorato di [Jennifer Connelly](http://www.imdb.com/name/nm0000124/), ho fatto un aggiornamento del CSS della galleria fotografica e ho aggiunto il feed di Google Reader qui di lato. Quest'ultimo purtroppo rallenta un po' il caricamento della pagina.
Per la galleria fotografica, un giorno magari mi deciderò a implementare un qualche sistema di feed per facilitare l'accesso agli aggiornamenti che faccio di tanto in tanto, il problema è che tecnicamente non è banale per come è fatto il sistema di galleria...
Intanto ho portato tutto ad uno sfondo grigio scuro, con le foto con una cornice nera. L'idea è che il nero aiuta a concentrare l'attenzione dell'occhio sulla foto. In più il colore di sfondo che c'era prima è stato definito da alcune parti "cacca molla" e quindi dovevo cambiarlo.
Il resto del sito per ora rimane così, più che altro perché mi mancano le idee su come cambiarlo.

Per modificare il CSS è stato di enorme aiuto [CSSEdit](http://macrabbit.com/cssedit/) (per MAC) che consente di giocare col CSS in diretta su una qualsiasi pagina web direttamente prendendola dalla rete, l'interfaccia è fatta bene e rende tutto il programma veloce da usare. Se lo usassi un po' più spesso potrei addirittura comprarlo (29,95$), che tanto ora c'è anche il dollaro basso.

## Photoblogging (2007-10-07)

Controllando le statistiche di accesso ho notato che le gallerie fotografiche, che sono la parte più vasta del sito (e anche quella più importante per me), sono visitate pochissimo.

Visto che aggiungo foto regolarmente, ho pensato bene di mettere in piedi anche un photoblog per dare la possibilità di iscriversi al feed rss e tenersi aggiornati sulle nuove foto che metto nella galleria.

Dopo un po' di ricerca (e di litigio con [MovableType](http://www.movabletype.org/ "MovableType")) ho deciso di utilizzare [PixelPost](http://www.pixelpost.org/ "PixelPost"), molto semplice ed elegante. Fa una sola cosa e la fa bene, i template sono facili da modificare, le foto facili da uploadare. C'è anche il plugin per postare via mail, anche se non l'ho ancora provato.

L'idea è di mettere su almeno una foto alla settimana, dovrebbe essere fattibile...

Quanto al lavoro, sono diventato "Responsabile Tecnico Del Settore Software", detto anche "CTO - Software Division". Peccato che, come al solito, lo stipendio sia rimasto lo stesso...

## Passaggio a Wordpress (2008-01-03)

Per unificare i due blog e semplificarmi la vita sono passato a [Wordpress](http://wordpress.org/ "Wordpress english site"). Ho trovato plugin per fare quasi tutto quello che mi interessava e l'installazione in sé è durata davvero [meno di 5 minuti](http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install "Istruzioni per i 5 minuti di installazione") come pubblicizzano sul sito ufficiale.

Il problema è stato trovare un tema decente: non l'ho trovato. Quello che vedete è uno che ho trovato dopo parecchie ricerche, che mi soddisfa fino ad un certo punto e che ho modificato per supportare [YAPB](http://johannes.jarolim.com/blog/wordpress/yet-another-photoblog/ "YAPB homepage") e per togliere un po' di grafica inutile. Se avessi una qualche abilità grafica me lo farei, il mio tema.

Ho trasportato tutti i post sia del vecchio blog che del fotoblog e i commenti più recenti, l'operazione è stata molto indolore grazie alle funzioni di import. Ho anche messo un po' di redirect per i feed e gli index.php (evvai di [RewriteRule](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteRule "ModRewrite documentation") di Apache!).

## Ferie forzate (2008-08-08)

Visto che [la mia Azienda](http://www.telereggio.it/2008/07/15/la-calda-estate-di-fantuzzi/) si è avvalsa del diritto di decidere per me il 50% delle ferie annuali, ho avuto modo di fare un po' di ordine sul sito. Per cominciare ho usato Greybox per ottenere una galleria navigabile senza troppo dispendio di energie. Per vederlo in azione basta cliccare su qualsiasi foto, se non c'è Javascript a disposizione dovrebbe funzionare come prima, aprendo direttamente il file jpeg.

Ho pubblicato anche un po' di foto, visto ero rimasto indietro ormai di quasi un anno.

Ho anche sostituito una foto al portfolio, mettendone una con le capre che mi guardano mentre fotografo.

## Aggiornamento di tutto il sito (2010-02-21)

Programmo tutto il tempo, al lavoro, ma sfortunatamente non posso condividere il software che scrivo. Sarebbe interessante, attualmente sto scrivendo un'applicazione embedded che genera al volo controlli [QT](https://www.qt.io/download/), rispettando allo stesso tempo regole di programmazione di sicurezza (EN 13849 e IEC 61508-3) per i percorsi critici e usando qua e la concetti di programmazione in tempo reale.

Per il sito ho iniziato a fare un po' di aggiornamenti. Ho spostato tutti i metadati delle fotografie direttamente nei file, usando i campi EXIF e IPTC. Poi ho cambiato il codice PHP per leggere i dati direttamente, senza usare database esterni. A questo modo riesco a mantenere una sola copia di titoli, descrizioni, posizioni geografiche, direttamente nelle fotografie. Potete vedere il risultato di questo lavoro in una [fotografia a caso](https://www.brownhat.org/photos/show_photo.php?pid=2455&year=2005&month=November "Sample photo page with metadata"). Mi sono anche liberato di tutto il Javascript di greybox, aggiungendo però il codice di [Google Maps](http://code.google.com/apis/maps/ "GMaps APIs") al suo posto.

Subito dopo voglio rivedere la disposizione delle pagine, è troppo fisso e si vede male in parecchie dimensioni di finestra. Sono particolarmente orgoglioso del CSS nella pagina di cui sopra, si ridimensiona bene, con differenti font e risoluzioni.

Prima di cominciare questo lavoro ho messo in questione la motivazione di tenere una galleria nel mio sito (perché non usare [Flickr](http://www.flickr.com/ "Flickr social photography")?) e dello sviluppare del software apposta (invece di usare [Gallery](http://gallery.menalto.com/ "Gallery php app") o [Coppermine](http://coppermine-gallery.net/ "Coppermine PHP app") ?).

Non voglio usare servizio come [Flikr](http://www.flickr.com/ "Flickr social photography") o [Picasa](http://picasaweb.google.it/home "Picasa web albums") perché non mi fido delle grandi corporazioni a cui questi siti fanno capo. Specialmente perché questi servizi sono gratuiti e possono cambiare radicalmente da un giorno all'altro. Odio i cambiamenti forzati di termini di servizio scarsamente pubblicizzati e poco chiari.

Avere un sito personale potrebbe voler dire affrontare un problema di visibilità. In realtà le foto gettate nel grande mare di fotografie che si trova in questi siti non sono per nulla più facili da trovare. Un sito dedicato, invece, può permettersi di aggiungere un tocco personale, spiegazioni e organizzare i contenuti in maniera migliore.

Quanto ai software esistenti, hanno un sacco di caratteristiche che non mi servono, ma solo circa il 60% di quelle che voglio. Per coprire quello che manca dovrei sviluppare dei plug-in e modificare dei temi grafici. Poi dovrei tenere il tutto aggiornato per via dei problemi di sicurezza che vengono trovati in questo genere di sistemi.

Il sistema di gallerie fotografiche che ho sviluppato non ha una sola form HTML e non usa un database, quindi posso ignorare intere classi di problemi di sicurezza e usare il mio tempo in modi più interessanti.

Sto già tenendo aggiornato [Wordpress](http://wordpress.org/) e mi irrita.

## Photo map (2010-03-20)

After struggling a bit with KML I finally managed to get a working [map with all the geo-referenced photos linked to
it](http://www.brownhat.org/photos/map.php "Brownhat photo map"). The biggest problem is that [Google Maps](http://maps.google.se) servers will cache the KML overlay for an indefinite time and this behaviour is **not** documented anywhere.
Testing a KML generator is impossible until the trick is discovered. Just add a fake argument to the Maps XML API url, like this:

`GeoXml("http://www.brownhat.org/photos/brownhat_photos.kml?100");`

and then change it every time the KML changes. This way I discovered that Google Maps overlays are just bitmap tiles generated server-side and positioned over the map tiles.

## Gallery usability (2010-08-14)

Finally, after several years of irritated users and embarrassing questions I got around implementing an "What's new" feature in the [photo gallery](http://www.brownhat.org/photos/). Each category and subcategory that contains at least one photo uploaded more recently than thirty days ago has a small "<span style="color: #ff0000;">Updated</span>" red tag. The new photos have a "<span style="color: #ff0000;">New</span>" tag.

I'm slowly uploading some photos from the end of 2009 and 2010. I have decided to concentrate more on quality than on quantity, so I'm selecting, writing titles, descriptions, tags and setting/checking GPS position for each photo I upload. It requires a lot of time, but in the end there is a better website for the visitors and a better Google indexing as well.

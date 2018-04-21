---
title: 'Diario di laurea'
media_order: '20050608 Tesi (0012).jpg,20050711 Tesi (0026).jpg,20050608 Tesi (0023).jpg,20050704 Tesi (0025).jpg,slides.pdf,thesis.pdf,thesis_en.pdf'
published: true
---

## Esamoni (2005-02-18)

Lunedì ho superato uno degli esami considerati tra i peggiori di tutto il corso di laurea in Informatica. Trattasi del famigerato [Algoritmi e strutture dati: algoritmi, calcolabilità e complessità](http://www.disi.unige.it/person/MoggiE/ASD02/).
Con la riforma della nuova laurea il corso che avevo frequentato due anni fa è stato sostituito da altri due. Il passaggio è avvenuto con delle modalità molto strane. Tanto per cominciare prima era un corso annuale con un esame in tre parti:

* scritto primo semestre
* scritto secondo semestre
* orale su entrambe le parti

Ora ASD:DCC è equivalente ai seguenti corsi:

* [CASD](https://web.archive.org/web/20050214064345/http://www.disi.unige.it/person/SobreroD/compalgo04/): scritto, orale e laboratorio
* [CC](http://www.disi.unige.it/person/MoggiE/ASD02/): scritto e orale

All'orale di CASD ha partecipato il Prof. Moggi, che non era elencato in commissione, ma che era il titolare del vecchio ASD. La Prof. De Floriani, titolare, non si è vista. Moggi tentava di chiedere cose fuori dal programma del corso, ma di solito veniva imbrigliato dalla tuttofare Prof. Magillo. In generale CASD non è difficile, anzi è sicuramente più semplice della prima parte di ASD.

Invece CC è oggettivamente difficile, bisogna aver compreso a fondo (leggi: studiato a memoria) tutto il programma per riuscire a passare.
Per lo scritto sembra che la teoria non serva a nulla, si tratta soltanto di provare a rifare gli scritti passati risolti da precedenti generazioni di studenti e sperare che capitino esercizi già fatti negli anni passati. Dopo parecchio studio si capisce che è possibile fare uno scritto decente arrivandoci col ragionamento (ma l'ho capito dopo aver passato lo scritto, mente preparavo l'orale).

All'orale di CC c'è lui, Moggi, da solo. È estremamente preciso, un parser umano di formule logiche. Finché ripeti quello che c'è sulle dispense, tutto ok. Se sbagli qualcosa ti aspetta una fine lenta e dolorosa.
Si inizia con un 'no !' e si prosegue con un 'perché ?'. Difficilmente Moggi ti aiuta a trovare l'errore in quello che affermi, sta lì e aspetta, paziente.
In ogni caso (che uno si corregga o meno) ti aspetta la dimostrazione. Giustamente se affermi qualcosa di poco convincente vuol dire che sai dimostrarlo, altrimenti non ti verrebbe neanche in mente.

Peccato che la mente dello studente medio non funzioni così. Lui è abituato a presentarsi ad un esame con un certo bagaglio di conoscenze appiccicate con lo sputo ed a usare l'intuito e un buona dose di fortuna per tutto quello che manca. In generale l'obiettivo è superare l'esame con il minor sforzo possibile e il massimo rendimento. Ovviamente questo non vale per tutti gli studenti, né per tutti gli esami, però...
Quindi se lo studente è veramente bravo (o la sa raccontare molto bene) riesce a dimostrare la sua affermazione, altrimenti, beh, c'è sempre la prossima volta...

[Qui](http://www.disi.unige.it/person/MoggiE/ESAMI/VOTI.html) ci sono i voti di tutti gli studenti che hanno incontrato Moggi almeno una volta nella loro vita, è un club esclusivo, ma l'elenco dei partecipanti è pubblicamente consumabile per la gioia di grandi, piccini e del garante della Privacy.

## Tesi 2, la vendetta (2005-03-10)

Dopo aver abbandonato una tesi sulla bioinformatica a favore di un argomento più promettente, in particolare quanto a prospettive lavorative, sembra che finalmente lunedì potrò iniziare.
Dovrò lavorare allo sviluppo di un sistema di comunicazioni wireless con routing dinamico e idealmente senza infrastruttura fissa da utilizzare in ambiente portuale.
Il tutto dovrebbe offrire un'interfaccia generica per permettere a qualunque tipo di applicazione di lavorare in modo trasparente, si va dal semplice scambio di dati sulle merci spostate al VoIP. Ovviamente ci sono anche degli studi di affidabilità e velocità da fare sugli algoritmi attualmente esistenti.
Il tutto si baserà su Linux, che è il sistema che già usano nella [ditta presso cui vado](http://www.motronica.com/) a fare il tirocinio.
La mia intenzione è di tenere qui un diario degli avanzamenti, vedremo se ciò mi sarà possibile...

## Primo giorno (2005-03-14)

Primo giorno di tirocinio in azienda. Dopo un po' di scenette comiche nel parcheggio (prima ho messo la macchina nel parcheggio per i disabili, poi nel posto di un'altra ditta, solo alla terza ho beccato il posto giusto), ho scoperto di essere arrivato troppo presto, gli uffici erano semivuoti.

Dato che non mi era ancora stato assegnato un tavolo, mi sono sistemato in sala riunioni, un bel posto con un'ottima vista, annotandomi di arrivare almeno un'ora dopo in futuro.
Verso mezzogiorno ho esaurito il materiale che avevo scaricato sul portatile, così mi hanno dato il tavolo e un allaccio a internet, coi soliti problemi di cavi, borchie inattive, script che smettono di funzionare sul più bello e sistemisti che hanno troppo da fare.

All'ora di pranzo l'ufficio si è improvvisamente svuotato, io mi ero portato (da furbo) un panino, ma devo comunque aver mosso l'istinto materno di una delle dipendenti che è venuta a chiedermi se ero a posto per mangiare.

Il resto della giornata è passato tranquillo, ho iniziato a scrivere un rapporto su tutta la tecnologia esistente. Per ora vedo tantissimi articoli accademici, poche implementazioni con codice sorgente alla mano e un solo software (olsrd) testato su rete di dimensioni realistiche (di più di una decina di nodi).

## La tesi procede... (2005-03-23)

Ho completato la prima fase di ricerca dello stato dell'arte attuale sul routing dinamico su reti wireless. Ho scritto qualche pagina con i risultati ottenuti, che farà parte della mia tesi. In più ho compilato un elenco di link utili, da cui ho preso tutte le informazioni necessarie. La trovate [qui](/ad-hoc-links), casomai interessasse.

## Penultimo esame! (2005-04-14)

Sul fronte tesi ho dovuto fare una pausa per dare un esame, ora ne manca uno solo che conto di dare verso giugno.
Negli ultimi giorni prima di iniziare a studiare, ho cercato delle schede wireless PCMCIA con due connettori per le antenne, ben supportate da Linux e in grado di funzionare in modalità Access Point. Il risultato della ricerca è che solo i driver [hostap](http://hostap.epitest.fi/) possono fare da AP e le uniche schede supportate da quel driver sono quelle basate su chipset Prism. Alla fine ci siamo diretti verso delle schede della Senao, trovate tramite il sito di [SeattleWireless](https://en.wikipedia.org/wiki/Seattle_Wireless) che dovrebbero avere tutto quello che ci serve. Ne abbiamo ordinata una come campione, appena arriva la proviamo.
La modalità AP ci serve per due motivi, come rete di sicurezza nel caso il routing dinamico non abbia prestazioni sufficienti e come come esperimenti per vedere se è possibile usare dei mini pc linux come access point invece di hardware apposito, più costoso e delicato.

## Router hackerabile (2005-04-19)

Oggi pomeriggio è arrivato il router wireless [Linksys WRT54g](https://en.wikipedia.org/wiki/Linksys_WRT54G_series), l'abbiamo pagato 72 € IVA inclusa ed è a tutti gli effetti un mini PC con Linux, scheda WiFi e scheda Ethernet. È possibile cambiargli il firmware con uno che comprende un sistema di pacchetti alla apt, creato dai tizi di [Freifunk](https://freifunk.net/en/) (il resto del sito è in tedesco).
Appena aperta la scatola, l'abbiamo subito smontato per vedere come è fatta la scheda interna, nelle nostre mani la garanzia non è durata 5 minuti. Poi abbiamo riscritto il firmware con [OpenWRT](https://openwrt.org/).
Ora ho una rete [OLSR](http://www.olsr.org/) di 3 nodi, il linksys, il mio portatile e un blue box che mi hanno dato per i test.

![Test sul terrazzo](20050608%20Tesi%20%280012%29.jpg)

## Wardriving (2005-04-23)

Ieri pomeriggio siamo montati in macchina facendo il giro dell'isolato dotati di portatile, access point, inverter, ciabatta e antenna Cisco bianca lunga un metro e mezzo tenuta a mano fuori dal finestrino.
Avremmo dovuto vedere i dati trasmessi dall'antenna sul tetto, ma dopo due giri e un cambio di antenna senza ricevere neanche un bit, siamo andati direttamente sul tetto scoprendo che la portata era di circa 30 centimetri. Forse c'è un problema sulla potenza di trasmissione della nuova scheda PCMCIA della Senao o qualche dispersione di troppo lungo il cavo che arriva fino al tetto. Martedì cercherò di capire.
In compenso abbiamo scoperto quante reti ci sono in quella zona: vi consiglio il parcheggio dell'IKEA, se volete avere una visione quasi completa (ero troppo occupato a guidare con il portatile sulle gambe per vedere se erano in chiaro e quanto traffico ci passava, però ne ho viste almeno tre).

![Wardriving](20050711%20Tesi%20%280026%29.jpg)

## Altro wardriving (2005-06-17)

Ieri pomeriggio, in mezzo ai miraggi e alle onde di calore che si sprigionavano dall'asfalto, si potevano osservare due tizi che camminavano con fare intento per la strada, uno con un portatile aperto tra le braccia e l'altro con un'antenna in una mano e un cavetto nell'altra. Entrambi guardavano alternativamente lo schermo del portatile (completamente illeggibile a causa del sole) e una piccola sporgenza sul tetto di un palazzo, sei piani più in alto, come se potessero vedere le onde elettromagnetiche.

Ecco qualche dato utile: per cominciare, se ancora c'erano dei dubbi, le piccole antenne integrate nelle schede PCMCIA fanno abbastanza pena e sono adatte solo a distanze sotto i 50m. Ma non appena si entra nel [magico mondo delle antenne esterne](http://www.cisco.com/en/US/products/hw/wireless/ps469/products_data_sheet09186a008008883b.html), si può facilmente quadruplicare quella distanza.
Su collegamenti punto a punto con il WiFi si possono fare anche dei chilometri, ma qui sto parlando di un access point che irradia a 360° con una potenza di 84mW (ben al di sotto dei 100mW di legge in Italia).

![Antenna](20050608%20Tesi%20%280023%29.jpg)

Altra informazione utile è che al di sopra dei 120-150m la copertura arborea della strada ha fatto cadere la connessione, che però si è subito ripresa a livelli accettabili a 200m, dove non c'erano più alberi nella linea d'aria tra noi e l'antenna sul tetto. Infine abbiamo osservato che le informazioni fornite da /proc/net/wireless su Linux sono in ritardo di circa 20 secondi rispetto alla realtà perché, probabilmente, il driver fa una qualche media sui dati che riceve dalla
scheda.

I prossimi passi sono: provare ancora un'altra antenna, misurare l'ampiezza di banda ([netperf](http://www.netperf.org/netperf/NetperfPage.html)?) e provare un multihop un po' più complesso.

## Una di quelle giornate... (2005-07-04)

Oggi non ha funzionato nulla. Ma veramente niente. Anzi per la maggior parte del tempo le cose sono funzionate un po', ma non abbastanza. L'idea è di fare un collegamento tra un nodo sul tetto ed uno due piani più sotto. Farlo wireless è risultato impossibile, con le apparecchiature che vogliamo usare quello sotto vede quello sopra, ma non viceversa. Abbiamo provato con quasi tutte le combinazioni di antenne e cavi possibili (e domani ne proviamo altre!), ma non c'è stato niente da fare.
A coronamento della giornata, verso le 18.30 abbiamo deciso di tirare un cavo Ethernet dal tetto, il cavo l'abbiamo fatto, ma è venuto male, o meglio: il tester dice che i fili sono tutti collegati giusti, ma il portatile dice 'no link', e gli switch lampeggiano, come se volessero indicare un problema. Ma quale ?
Vabbè, come si suol dire: "Domani è un altro giorno..."

## Antenne, antenne, antenne! (2005-07-11)

Stamattina altro giro di prove, questa volta in macchina. Con una nuova antenna ho potuto ottenere risultati migliori rispetto all'altro giorno (250m con degli alberi frapposti senza problemi) e in più ho giocherellato con VNC. Ho provato ad usare un desktop remoto attraverso un hop di rete mesh, riuscendoci abbastanza bene.
Il problema maggiore è stato il server VNC (TightVNC su Windows) che era un po' rapido a far cadere la connessione al primo accenno di problemi, però bastava ricollegarsi per ottenere un servizio decentemente fluido a 640x480 e 32bit di colore. Per l'applicazione della mia tesi la risoluzione ed i colori dovrebbero essere inferiori, quindi sono abbastanza tranquillo che il sistema (se c'è abbastanza copertura radio!) possa funzionare.

![Test antenne](20050704%20Tesi%20%280025%29.jpg)

## La discussione della tesi (2005-11-10)

Alla fine ci siamo arrivati. Tutti questi anni di studio, di fatiche, di gioie e di amicizie per arrivare alla fine dell'università e al titolo di Dottore in Informatica. Abito spezzato, pantaloni color panna e giacca scura, tutto comprato nuovo apposta per la presentazione davanti alla commissione. Il pomeriggio è intenso, le sessioni di laurea si susseguono senza sosta, con parenti e amici venuti a dare supporto ai candidati che si mescolano e vagano dispersi per la facoltà.
Infatti quando è il mio turno, il mio gruppo, distratto, non se ne rende conto ed entra a presentazione già iniziata.

La tesi e le slide della presentazione sono qua:

* [Testo in italiano (PDF)](thesis.pdf)
* [Testo in inglese (PDF)](thesis_en.pdf)
* [Slide (PDF)](slides.pdf)

## Aggiornamenti (2006-12-03)

Un aggiornamento: il terminal di Nola (NA), dove avrei dovuto installare la rete mesh implementata nella mia tesi di Laurea, mi dicono, è fallito. Ecco un link alla [foto da satellite](https://www.google.it/maps/place/Interporto+Campano+Spa/@40.964345,14.48041,5275m/data=!3m1!1e3!4m5!3m4!1s0x0:0x9fa92a5035ded3a6!8m2!3d40.9633323!4d14.4825232?hl=it) di Google Earth.
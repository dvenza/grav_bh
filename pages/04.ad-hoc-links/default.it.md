---
title: 'Ricerca in letteratura di protocolli per reti mesh senza fili'
date: '25-03-2005 11:03'
---

### Protocolli con implementazione open source per 802.11

-   **AODV**
    -   [AODV](http://moment.cs.ucsb.edu): Informazioni generali e link a materiale specifico, c'è anche un elenco delle implementazioni
    -   [AODV-UU](http://web.archive.org/web/20060916171558/http://core.it.uu.se/AdHoc/AodvUUImpl): Implementazione dell'Uppsala University
    -   www.tml.hut.fi/~ajtuomin/manet/aodv/: Implementazione solo IPv6 (HUT AODV for IPv6) *broken link*
    -   [AODV Kernel](http://web.archive.org/web/20160409173711/http://w3.antd.nist.gov/wctg/aodv_kernel/):
        Implementazione del NIST
-   **OLSR**
    -   [Optimized Link State Routing](http://web.archive.org/web/20110926230841/http://menetou.inria.fr/olsr/): Informazioni generali e link a materiale specifico
    -   [UnikOLSR](http://www.olsr.org/): implementazione molto avanzata e attiva, per Windows e Linux
    -   [qolyester (OLSR)](http://qolsr.lri.fr/): implementazione C++
    -   [Lille sans fil](http://www.lillesansfil.org/): rete cittadina su OLSR
-   [Monarch DSR](http://www.monarch.cs.rice.edu/dsr-impl.html): implementazione Dynamic Source Routing, ultimo aggiornamento del 2000
-   [UC Boulder DSR](http://pecolab.colorado.edu/): implementazione università del Colorado, vedi anche link successivo
-   [The Grid](https://pdos.csail.mit.edu/archive/grid/): rooftop system al MIT, basato su DSR
-   [Ad-hoc Support Library](http://aslib.sourceforge.net/): libreria per lo sviluppo di algoritmi routing dinamico
-   [ZRP](http://web.archive.org/web/20090107150742/http://people.ece.cornell.edu/haas/wnl/wnlprojects.html): implementazione Zoned Routing Protocol
-   [MMRP for Linux](http://www.mitre.org/work/tech_transfer/mobilemesh/): implementazione Linux di un algoritmo proattivo
-   MMRP for Windows: come sopra, ma per windows *era un progetto chiamato ipmesh su sourceforge, che non esiste più*
-   [LUNAR](http://web.archive.org/web/20060430035722/http://core.it.uu.se/AdHoc/LunarImpl): algoritmo e implementazione, adatto a reti di piccole dimensioni
-   [Champaign-Urbana Community Wireless Network](https://en.wikipedia.org/wiki/Champaign-Urbana_Community_Wireless_Network): rete cittadina basata su un protocollo sviluppato appositamente
-   [Locust World](http://www.locustworld.com/): usa NIST AODV su 802.11, bluetooth e ethernet, sono disponibili delle ISO da scaricare, vendono anche hardware predisposto

### Studi teorici, documentazione accademica e non

-   [picoNet](http://piconet.sourceforge.net/): Tesi di laurea su un algoritmo DSR
-   DAWN: Progetto di ricerca della DARPA per reti dense ed asimmetriche *il sito web non esiste più*
-   [IRTF RRG](https://irtf.org/concluded/rrg): IETF Internet draft su vari aspetti delle reti wireless ad hoc
-   [Mobile Agents](http://alumni.media.mit.edu/~nelson/research/routes/): Studio tecnico e simulazioni
-   tf2_beyer.pdf: presentazione su reti mesh per uso cittadino *il file è citato anche da parecchi articoli accademici, ma non è più disponibile*
-   [Random Trip mobility model](http://icawww1.epfl.ch/RandomTrip/): modello teorico per lo studio dei movimenti in una rete ad hoc
-   [TBRPF](http://web.archive.org/web/20060615044204/http://www.sri.com/esd/projects/tbrpf/): Topology Broadcast Reverse-Path Forwarding
-   [WINGS](http://www.cse.ucsc.edu/research/ccrg/projects/wings.html): accesso a Internet multihop, elenco documentazione e link, sembra non aggiornato da tempo

### Soluzioni Commerciali su 802.11

-   [Green Packet](http://www.greenpacket.com/): per windows XP, rete mesh per piccole comunità
-   [Kiyon](http://www.kiyon.com/): hardware per costruire reti mesh fornendo un accesso con 802.11 (sembra solo per sistemi fissi)
-   [MobileRoute](http://www.scires.com/products/cne/mr.htm): scarse informazioni tecniche
-   [RoamAD](http://web.archive.org/web/20070810210416/http://www.roamad.com/roamad/): hardware per costruire reti mesh, scarse informazioni tecniche (anche sistemi mobili)
-   [Strix Systems](http://www.strixsystems.com/): hardware per costruire reti mesh (sembra solo per sistemi fissi)
-   [Tropos Networks](http://www.tropos.com/technology/index.shtml): hardware per costruire reti mesh (sembra solo per sistemi fissi)
-   [MeshDynamics](http://www.meshdynamics.com/index.html): usato dall'aeronautica militare USA, sembrano degli access point con gli steroidi
-   [PacketHop](http://archiv.iwi.uni-hannover.de/lv/seminar_ss04/www/Jan_Gacnik/bibliography/PACKETHOP-GGSN.pdf): scarse informazioni tecniche, usato nella zona del Golden Gate, San Francisco per i servizi di emergenza

### Soluzioni commerciali non 802.11 o con scarse informazioni tecniche

-   [NovaRoam](http://www.nova-eng.com/novaroam.html): Usa TORA e AODV per reti con nodi mobili
-   BelAir: offriva una tecnologia brevettata, sembra scarsamente mobile, ora sembra essere stata acquisita da Ericsson
-   Dust Networks: reti di sensori, piccoli dispositivi alimentati a batteria da installare su sensori *il sito web non esiste più*
-   [Firetide](http://www.firetide.com/): poche informazioni tecniche
-   [Mesh Networks](http://www.meshnetworks.com/): Motorola, tecnologie varie
-   [Millenial Net](http://www.millennialnet.com/): reti di sensori
-   [OrderOne Networks](http://www.orderonenetworks.com/): reti enormi, nell'ordine di 10.000+ nodi, algoritmi brevettati
-   [Richochet](http://www.ricochet.com/): software Windows e Mac OS X, vendono i loro modem, poche informazioni tecniche

Nota: la dicitura "poche/scarse informazioni tecniche" significa che una ricerca veloce, ma abbastanza completa nel sito non dato risultati su quali algoritmi di routing dinamico vengano usati in quella particolare implementazione.

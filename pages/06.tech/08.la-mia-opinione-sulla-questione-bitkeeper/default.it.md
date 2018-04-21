---
title: 'La mia opinione sulla questione BitKeeper'
date: '10-02-2005 17:33'
---

Qualche giorno fa si è scatenato l'ennesimo thread infinito su linux-kernel@vger.kernel.org sul problema che BitMover (la ditta dietro al prodotto BitKeeper) non fornisce abbastanza informazioni per ricostruire completamente la storia dei sorgenti del kernel di Linux. Io non credo che questo sia un problema reale, le patch su [ftp.kernel.org](ftp://ftp.kernel.org/pub/linux/kernel) hanno una granularità sufficiente per la maggior parte degli usi che mi vengono in mente.

Il problema che vedo io riguarda i piccoli sviluppatori, come me. Per noi è diventato estremamente difficile seguire lo sviluppo del piccolo pezzetto di kernel di cui ci vogliamo occupare senza utilizzare [BitKeeper](http://www.bitkeeper.com/).

Qualche mese fa mi sono trovato delle modifiche (perfettamente giuste e legittime) al driver che mantengo, già incluse nella release stabile, mentre le mie povere patch faticavano a passare i molti filtri. Ho dovuto rifare le mie patch perché non si applicavano più...  In pratica sono stato aggirato da qualcuno con BitKeeper.

Non ha alcun senso che per mantenere un driver di 50KB io debba mantenere un albero cvs (o svn o bk) di diverse centinaia di megabyte contenente tutta la storia possibile. Attualmente uso una soluzione fatta in casa, quasi totalmente automatizzata che mi permette di fornire patch che si applicano all'ultimo snapshot di Torvalds. Internamente uso [Subversion](http://subversion.tigris.org/) per mantenere la storia delle modifiche ai sorgenti. E' un buon prodotto, decisamente migliore di cvs e più intuitivo di [arch](http://www.gnu.org/software/gnu-arch/) (e forse anche più avanti nello sviluppo).

Quindi il mio problema non è che la gente usi [BitKeeper](http://www.bitkeeper.com/), a loro fa comodo, a me no. Il problema è che [BitKeeper](http://www.bitkeeper.com/) consente a chi lo usa una via rapida e veloce per includere modifiche senza che ci sia un reale controllo da parte della comunità. Si sono formate due categorie, quelli che usano [BitKeeper](http://www.bitkeeper.com/) e tutti gli altri, con questi ultimi che si sbattono con scriptini e casini vari perché non possono (o non vogliono) usare un programma che ha una licenza alquanto discutibile.
Dato che la maggior parte dei piccoli sviluppatori lo fa per hobby, più gli rendi le cose difficili e meno avranno voglia di continuare il lavoro.

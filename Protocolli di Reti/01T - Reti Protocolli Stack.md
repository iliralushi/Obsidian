PW PER ACCEDERE AL MOODLE
- dieMiephie3b

**Rete**
La rete ha due definizioni:
- **Base:** Sono due o più nodi connessi tramite collegamenti.
- **Ricorsiva:** Due o più reti connesse tramite nodi.

**Nodi**
I nodi sono di due tipi:
- **Host**: Sono i nodi terminali, ovvero quei nodi che si trovano al capo della comunicazione (mittente, destinatario).
- **Switch/Bridge/Router**: Sono i nodi intermediari, ovvero i nodi che collegano gli host. Sono tre termini differenti e per ognuno assumono un significato diverso.

**Link**
Un collegamento (link) è la connessione che avviene tra due nodi per formare una rete. Può avvenire in due modi:
- **Wired**: Ethernet, fibra ottica...
- **Wireless**: Wifi, bluetooth...

**Astrazione di Reti**
La definizione ricorsiva delle reti permette di usare paradigmi di astrazione che possono essere applicati più volte **(ricorsione xd)**. Possiamo nascondere dettagli non essenziali per focalizzarsi sulle funzionalità di interesse.

**Comunicazione Logica**
Presa una rete con varie LAN (host) e WAN (reti intermediarie) logicamente comunicano solo gli host terminali, ovvero i due host coinvolti nello scambio di informazioni.

**Comunicazione Reale**
Nella realtà le informazioni attraversano tutti i nodi ed i collegamenti.
- Possiamo avere problemi di instradamento e di condivisione delle risorse.

**Caratteristiche Fondamentali delle Reti**
1) Host, nodi e collegamenti sono **eterogenei**.
2) La rete può cambiare nel tempo (nelle tecnologie, negli scopi...)
3) La rete è **condivisa**.

**Protocollo**
Tutte le comunicazioni sono regolate da protocolli.
- Insieme di regole e convenzioni seguite da entità, dislocate su nodi distinti che intendono comunicare per svolgere un compito comune.

I protocolli hanno lo scopo di assicurare una cooperazione efficiente tra entità per la realizzazione dei servizi di rete.

**Elementi di un Protocollo di Comunicazione**
- **Sintassi**: Insieme e struttura dei comandi e delle risposte. Il formato in cui i messaggi vengono inviati.
- **Semantica**: Significato dei comandi e delle risposte da effettuare al momento della ricezione/trasmissione dei messaggi.
- **Temporizzazione**: Gestione del tempo su come i vari comandi, messaggi, risposte verranno effettuati.

**Obiettivo Reale delle Reti**
È lo trasferimento di un messaggio (insieme di bit) da un host all'altro, garantendo anche:
- Massima velocità possibile (**prestazioni**)
- Il superamento di guasti/malfunzionamenti (**affidabilità**)
- **Sicurezza** della trasmissione.

Questi obiettivi in un contesto eterogeneo sono meno banali da garantire.

**Metodologia**
Quando la complessità del problema è elevata possiamo seguire questo schema (astrazione per mascherare la complessità del problema. approccio **layering**);
1) Dividere il problema in sottoproblemi
2) Risolvere i sottoproblemi
3) "Collegare" le soluzioni parziali.

**Stack di Protocolli**
Nelle architetture di rete ci sono diversi tipi di funzionalità associate a ruoli diversi. Uno stack (semplificato) di esempio può essere:

| Implementazione di logiche applicative specializzate (Web, real time...) |
| ------------------------------------------------------------------------ |
| **Comunicazione fra applicazioni in esecuzione su host**                 |
| **Comunicazione fra nodi di reti differenti**                            |
| **Comunicazione fra nodi di una stessa rete**                            |

Ogni layer può offrire delle alternative a seconda delle necessità.

| Logica applicativa                                            |
| ------------------------------------------------------------- |
| **Comunicazione fra applicazioni** (affidabili ma più lente)  |
| **Comunicazione fra reti**                                    |
| **Comunicazione fra nodi** (per reti wireless/per reti wired) |

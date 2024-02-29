***dato = informazione grezza di cui si è già a conoscenza, sono il risultato di codifica delle informazioni.***
Una **base di dati** è un insieme di dati utilizzato per lo svolgimento di varie attività (di un ente, di un azienda, ufficio, persona...).

Il **sistema informativo** è un insieme di componenti che gestiscono dati per fornire informazioni ad un organizzazione. Ogni organizzazione contiene un sistema informativo. E' di supporto ad altri sotto-sistemi, quindi va studiato nel contesto in cui si trova.

Il **sistema informatico** è la parte automatizzata del sistema informativo. Nel sistema informativo, le informazioni vengono rappresentate in modo essenziale attraverso i dati.

Le basi di dati sono:
- Grandi.
- Persistenti. Hanno un tempo di vita indipendente dalle applicazioni che le usano.
- Condivise. Ogni organizzazione è divisa in settori e ciascun organizzazione ha un sistema informativo. Sono condivise perchè altrimenti si rischierebbe ridondanza e incoerenza nei dati.
  
 Un **DBMS** (Database Management System) è un sistema che gestisce basi di dati.
 Garantisce:
- Privatezza. Si possono definire meccanismi di autorizzazione.
- Affidabilità. E' resistente a malfunzionamenti di hardware/software.
- Efficienti.
- Efficaci. Cercano di rendere produttive le attività per gli utilizzatori.

Una base di dati è una risorsa pregiata quindi deve essere conservata per tanto tempo. Viene usata una "tecnica" fondamentale, la gestione di transazioni.

Una **transazione** è un insieme di operazioni da considerare:
- Atomiche. Questo vuol dire che sono indivisibili. 
  ESEMPIO: In un trasferimento tra due conti bisogna prima prelevare i soldi dal conto A e depositarli nel conto B. La transazione deve essere atomica, altrimenti si potrebbe svolgere solo una delle due operazioni.
- Coerente. Se due persone prenotano un biglietto del treno bisogna evitare di dare lo stesso posto.
- Permanente. Se la transizione è andata a buon fine si ha un "commit" che terrà traccia del risultato della transazione in qualsiasi evenienza.

In ogni Base di Dati esiste:
- Uno schema che ne descrive la struttura, invariato nel tempo.
- Un istanza che sono i valori attuali (e possono cambiare molto rapidamente).

Un **modello di dati** è un insieme di costrutti utilizzati per organizzare i dati e descrivere il loro comportamento. E' prevista una componente fondamentale, il **costruttore di tipo**.
ESEMPIO: Il modello relazionale contiene il costruttore relazione che permette di definire insiemi di record. Le tipologie sono:
- Modelli logici. Usati nel DBMS per l'organizzazione di dati.
- Modelli concettuali. Rappresentano i dati in modo indipendente da ogni sistema (Entity-Relationship).

Architettura DBMS semplice -> ( utente -> schema logico -> schema interno -> bd )
- Schema logico. Descrizione della base di dati nel modello logico.
- Schema interno. Rappresentazione dello schema logico per mezzo di strutture di memorizzazione.

Architettura ANSI è leggermente diversa. In questo caso lo schema logico comprende tutta la base di dati e c'è uno schema esterno che descrive parte della base di dati con un modello logico. L'accesso viene con la parte esterna. Il livello esterno è indipendente da quello logico. Il livello logico ed esterno sono indipendenti dal livello fisico.

![[Schema Architettura ANSI.png]]







**SISTEMA INFORMATIVO**
Insieme degli strumenti, delle risorse e delle procedure che consentono la gestione delle informazioni aziendali. Include software, hardware, risorse umane...
- Applicazioni gestionali
- Applicazioni finanziarie
- Sistemi di prenotazione

**SISTEMA INFORMATICO**
Sotto-sistema del sistema informativo, comprende i sistemi di hardware e software del sistema informativo. Serve per gestire le informazioni attraverso supporti informatici.

**DATO E INFORMAZIONE**
- DATO: Unità elementare di informazione
- INFORMAZIONE: Elaborazione di un dato che ci permette di estrarre informazioni

**BASE DI DATI**
Un insieme di dati utilizzati per il supporto delle attività aziendali. Essi saranno gestiti da un DBMS.

**CARATTERISTICHE BASE DI DATI**
- Grandi, possono arrivare a pesare anche molti TB
- Persistenti, il loro tempo di vita non dipende dalle applicazioni che le usano
- Condivise, altrimenti si rischierebbe ridondanza ed incoerenza nei dati

**DBMS**
Il sistema che usiamo per gestire le basi di dati. L'architettura DBMS ci permette di gestire i dati in maniera unitaria e ad alto livello.

**CARATTERISTICHE DBMS**
Essi garantiscono:
- Privatezza, si possono definire dei meccanismi di autorizzazione
  (L'utente A è in grado di leggere di dati dell'utente B)
- Affidabilità, sono resistenti a malfunzionamenti hardware e software (transazioni)
- Efficienti
- Efficaci

**TRANSAZIONE**
Insieme di operazioni che vengono considerate atomiche, corrette anche in presenza di concorrenza e permanenti.
- ATOMICHE: Sono operazioni indivisibili
- COERENTI: Sono operazioni che funzionano anche in caso di conflitto
- PERMANENTI: Sono operazioni irreversibili una volta effettuate

**SCHEMA ED ISTANZA**
- SCHEMA: Descrive la struttura della base di dati, invariato nel tempo
- ISTANZA: I valori attuali, possono cambiare rapidamente nel tempo

**MODELLO DI DATI**
Rappresentazioni astratta e semplificata di dati. Viene utilizzato per organizzare e descrivere i dati e il loro comportamento. I modelli di dati principali sono DUE:
- MODELLO LOGICO: Usati nel DBMS per organizzare i dati
- MODELLO CONCETTUALE: Rappresenta i dati in modo indipendente da ogni sistema (Modello Entity-Relationship)

**ARCHITETTURA DBMS (UTENTE -> SCHEMA LOGICO -> SCHEMA INTERNO -> BD)**
- SCHEMA LOGICO: Descrizione della base di dati nel modello logico
- SCHEMA INTERNO: Rappresentazione dello schema logico per mezzo di strutture di memorizzazione.
- Il livello logico è indipendente da quello interno

**ARCHITETTURA ANSI**
Leggermente diversa da quella DBMS.
- SCHEMA LOGICO: Descrizione dell'intera base di dati nel modello logico del DBMS
- SCHEMA INTERNO: Descrizione dello schema logico via mezzi di memorizzazione
- SCHEMA ESTERNO: Descrizione parziale della base di dati nel modello logico
- Il livello esterno è indipendente da quello logico
- Il livello esterno e logico sono entrambi indipendenti da quello interno

![[Schema Architettura ANSI.png]]
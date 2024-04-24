**MODELLO E/R**
Il modello E/R è il modello utilizzato per esprimere una base di dati in uno schema concettuale.
Usa simboli per facilitarne la lettura. Sono schemi grafici con l'aggiunta di frasi di specifica e vincoli.

**ISTANZA DI ENTITÀ**
L'istanza di entità è UNA occorrenza di un qualcosa di cui vogliamo registrare fatti specifici e che può essere chiaramente identificata in modo da poter distinguerla dalle altre.
- ESEMPIO: Il docente Martoglia, lo studente 176180.

**ISTANZA DI RELAZIONE**
L'istanza di relazione è UN fatto che descrive un'azione o una situazione e stabilisce legami fra istanze di entità. Per le relazioni usiamo il termine ASSOCIAZIONE.
- ES: Martoglia **INSEGNA** DB, la ditta Rossi **ORDINA** computer.

**ATTRIBUTI**
Gli attributi sono fatti che descrivono le caratteristiche delle istanze di entità e delle istanze di associazione. Essi assumono valori.
- ES: Martoglia **HA NOME** Riccardo, Martoglia insegna DB **A INFORMATICA**,

**CLASSIFICAZIONE**
È un meccanismo che permette di astrarre le differenze fra le singole istanze per poter unificare le istanze di entità/di associazione in un unica classe. Diventeranno semplicemente entità e relazioni.
La classe è un insieme di istanze di entità/associazione che son considerate dello stesso tipo.
- ES: Ceri, Martoglia, Tiberio vengono considerati in un unica entità chiamata **DOCENTI**.

**AGGREGAZIONE**
È un meccanismo che definisce il tipo delle istanze di classi attraverso aggregazione di attributi.
- ES: Corsi **(CODICE, NOME, ANNO, ORE)**, Docenti (**CODICE, NOME, COGNOME, QUALIFICA)**.

**SCHEMA SCHELETRO**
È uno schema molto riduttivo che definisce solo le entità con le varie associazioni. Ci permette di dare un primo schema molto semplice, senza informazioni aggiuntive.

![[Schema Scheletro.png]]
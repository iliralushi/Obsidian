**MODELLO E-R**
Il modello Entity-Relationship è il modello utilizzato per lo schema concettuale della base di dati.
Esso usa simboli grafici per una comprensione più facile.

**ISTANZA DI ENTITÀ**
L'istanza di entità è una cosa con esistenza autonoma di cui vogliamo descrivere fatti specifici. Deve essere chiaramente identificata in modo di distinguerla.
- ES: Il docente Riccardo Martoglia, il numero di matricola di uno studente.

**ISTANZA DI RELAZIONE**
L'istanza di relazione è un fatto che descrive un'azione e stabilisce un legame tra istanze di entità.
- ES: Martoglia **insegna** Basi di Dati, Bianchi **lavora** al magazzino 4.

**ATTRIBUTI**
Gli attributi sono fatti che descrivono le caratteristiche delle istanze di entità e le caratteristiche delle istanze di associazione. Gli attributi assumono valori. 
- ES ENTITÀ: Martoglia ha **nome** Riccardo, Bianchi ha **matricola** 01783.
- ES ASSOCIAZIONE: Martoglia insegna Basi di Dati **a informatica**, Bianchi ha lavorato **3 ore** al magazzino 4.

**CLASSIFICAZIONE**
Astrarre le differenze tra le varie istanze per evidenziare ciò che le rende omogenee in un certo contesto. La classificazione permette di ragruppare le varie istanze di entità o relazioni in un unica classe, diventeranno quindi entità e relazioni.
- ES: Istanze di entità diverse come Ceri, Martoglia, Tiberio vengono classificate come "docenti" per mettere in evidenza il fatto che a tutti interessano vari attributi come un codice, nome, cognome, data di nascita etc...

**CLASSE**
Insieme di istanze considerate dello stesso tipo in un certo contesto.
- ES: Docenti, medici, operai, cittadini, dirigenti etc...

**AGGREGAZIONE DEL TIPO**
Meccanismo che definisce il tipo delle istanze delle varie classi come insieme di vari attributi.
- ES: DOCENTI (**codice, nome, cognome, qualifica...**) CORSI (**codice, nome, anno, ore...**)

**SCHEMA SCHELETRO**
Lo schema scheletro è uno schema molto riduttivo. Definisce le associazioni tra entità e relazioni. Ci permette di dare una prima struttura dello schema, senza indicazioni sul tipo delle entità e delle relazioni.

**SCHEMA SCHELETRO ES 1**
Errore che ho fatto:
- Città di partenza e arrivo non sono due entità separate perchè sono sempre città, possiamo quindi usarle per associare viaggio e città ricorsivamente.

![[Schema Scheletro Agenzia di Viaggi.png]]




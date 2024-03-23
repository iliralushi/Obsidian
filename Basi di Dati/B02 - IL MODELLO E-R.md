**MODELLO E-R**
Il modello Entity-Relationship è il modello utilizzato per lo schema concettuale della base di dati.
Esso usa simboli grafici per una comprensione più facile. Essenzialmente è uno schema grafico con aggiunte di frasi di specifica e di vincoli.

**ISTANZA DI ENTITÀ**
E' un oggetto con esistenza autonoma che deve essere chiaramente specificato e di cui vogliamo descrivere fatti specifici.
- ES: Il docente Riccardo Martoglia, il num di matricola di uno studente

**ISTANZA DI RELAZIONE**
E' un fatto che descrive un'azione e stabilisce un legame tra istanze di entità.
(Si usa il termine associazione per indicare una relazione).
- ES: Martoglia **insegna** Basi di Dati, Bianchi **lavora** al magazzino 4

**ATTRIBUTI**
Sono fatti che descrivono le caratteristiche delle istanze di entità/di relazione. Gli attributi assumono valori.
- ES PER ISTANZA DI ENTITÀ: Martoglia ha **nome Riccardo**, Bianchi ha **matricola 01783**
- ES PER ISTANZA DI ASSOCIAZIONE: Martoglia insegna Basi di Dati **a informatica**, Bianchi ha lavorato **3 ore** al magazzino 4

**CLASSIFICAZIONE**
Astrarre le differenze tra le varie istanze per evidenziare ciò che le rende omogenee e congrue in un certo contesto.
- ES: Istanze diverse di entità come Ceri, Martoglia, Tiberio vengono classificate come docenti per mettere in evidenza il fatto che pur essendo persone diverse li accomuna il fatto che tutti condividono un codice, nome, cognome, data di nascita etc...

**CLASSE**
Insieme di istanze considerate dello stesso **TIPO** in un certo contesto.
- ES TIPO: Docenti, medici, operai etc...

**AGGREGAZIONE**
Meccanismo che definisce il **TIPO** (la struttura) delle istanzi delle varie classi come aggregazione di vari attributi che accomunano il tipo.
- ES: DOCENTI (**codice, nome, cognome, qualifica...**) CORSI (**codice, nome, anno, ore...**)

**CLASSIFICAZIONE (cont...)**
La classificazione permette di raggruppare le varie istanze di entità o relazioni in un unica classe. Un insieme di istanze di entità come **ENTITÀ** e un insieme di istanze di relazioni come **RELAZIONI**.

**SIMBOLI**
- ENTITÀ: Rettangolo
- RELAZIONE: Rombo
- ATTRIBUTI (di entità o di relazione): "Spilla"

**SCHEMA SCHELETRO**
E' uno schema molto riduttivo. Definisce le associazioni tra entità e relazioni. Ci permette di dare una prima struttura dello schema, senza indicazioni sul tipo delle entità e delle relazioni.

**RIDONDANZE**
Bisogna fare attenzioni alle ridondanze. Dipende molto da caso a caso, bisogna percorrere attentamente il percorso della mappa e riflettere se un associazione è necessaria o meno.

**INCERTEZZE**
![[Incertezze.png]]

**Supponiamo che i guidatori possano guidare più tir e i tir sono assegnati a più percorsi**

Nel primo caso abbiamo che i guidatori sono associati ai tir e i tir sono associati ai percorsi.
- Il guidatore guida il tir N1 e N2
- Il tir N1 è associato ai percorsi X, Y. 
Non possiamo sapere che percorso sceglie il guidatore perchè essendo le associazioni "separate" non possiamo direttamente assegnare al guidatore il percorso scelto, rendendo lo schema invalido per questo tipo di problema.

Nel secondo caso abbiamo una tripla dove guidatori, tir e percorsi sono associati assieme.
In questo caso possiamo assegnare direttamente al guidatore il percorso su cui si sta guidando siccome le entità guidatori, tir e percorsi sono tutte associate tra di loro. Lo schema è valido e non sono equivalenti tra di loro.

**SCHEMA SCHELETRO ES 1**
Non definiamo città di partenza e città di arrivo come entità separate perchè sono sempre città. Nella sua relazione con il viaggio può assumere un ruolo di città di partenza e città di arrivo. Modelliamo ciò con due associazioni.

![[Schema Scheletro Agenzia di Viaggi.png]]




**IL PROGETTO DELLA BASE DI DATI**
Si inserisce nel ciclo di vita di un sistema informativo. Comprende in generale le seguenti attività:
- Raccolta ed analisi dei requisiti
- Progettazione
- Implementazione
- Validazione e collaudo
- Funzionamento

**ANALISI DEI REQUISITI**
Comprende attività su:
- Unità organizzative omogenee che utilizzeranno la nostra base di dati.
- Individuazione delle attività che devono essere supportate dal sistema.
- Produzione di una descrizione informale, quanto possibile completa sulle due fasi sopra.

**PROGETTAZIONE CONCETTUALE**
La progettazione concettuale traduce ciò che abbiamo scritto nell'analisi dei requisiti in uno schema implementabile senza DBMS. Fa riferimento al modello concettuale (E/R). 

**SCHEMA CONCETTUALE**
Lo schema concettuale è una rappresentazione semplificata di una BD che contiene solo le informazioni essenziali.

**STEP DELLA PROGETTAZIONE CONCETTUALE**
- Si analizza il sistema informativo esistente.
- Si produce una prima versione dei requisiti in linguaggio naturale, leggendo ciò che si è scritto, questa è la creazione dell'analisi dei requisiti.
- Si costruisce a partire dalle frasi un glossario dei termini che comprende entità, associazioni, sinonimi e attributi. 
- Si crea uno schema scheletro per ogni vista.
- Si crea un dizionario dei dati a partire dal glossario dei termini. Comprende specifiche sugli attributi, chiave interne/esterne, gerarchie...
- Si svolge lo schema E/R, prima per ogni vista, poi unificando lo schema in uno unico.

**QUALI COSTRUTTI E/R USARE**
- Entità: Se ha proprietà significative ed esprime oggetti in maniera autonoma.
- Attributo: Se è semplice e non ha proprietà.
- Relationship: Se correla due o più concetti.
- Gerarchia: Se è caso particolare di un altro.

**REIFICAZIONE**
La reificazione è una complicanza dello schema E/R. Consiste nell'aggiungere un entità e due associazioni binarie aggiuntive per poter esprimere in dettaglio certi fatti.

**DESIGN PATTERNS**

![[Reificazione di attributo di entità.png]]
![[Part-of.png]]![[Instance-of.png]]![[Reificazione di relazione binaria.png]]
![[Reificazione di relazione ricorsiva.png]]
![[Reificazione di relazione ternaria.png]]
![[Reificazione di attributo di relazione.png]]
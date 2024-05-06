**REGOLA 20/80**
Il carico di lavoro sul DB è rappresentato
- Dalla dimensione dei dati.
- Dalle operazioni più significative che si stima vengano eseguite sul DB.
- Regola 20-80: Il 20% delle operazioni produce l'80% del carico.

**CARICO DI LAVORO I**
Il carico di lavoro per i volumi è espresso dalla tabella dei volumi.
Essa comprende il concetto, che sarà il nome dell'entità/associazione, il tipo che esprime il tipo dell'entità/associazione/attributo e del volume dei dati.

**VOLUME DEI DATI**
Il volume dei dati comprende:
- Numero medio di istanze di ogni entità e associazione.
- Cardinalità e dimensioni di ciascun attributo.
- Percentuale di copertura delle gerarchie.

![[Schema tabella volumi.png]]

**CARICO DI LAVORO II**
Il carico di lavoro per le operazioni è espresso dalla tabella delle operazioni.
Essa comprende il tipo di operazione che sarà interattiva/batch, la frequenza, quindi il numero medio di esecuzioni di una certa operazione in un certo periodo di tempo e lo schema di operazione.

**SCHEMA DI OPERAZIONE**
Lo schema di operazione comprende un frammento di E/R che avrà cammino logico ed interessa le entità e le associazioni che verrano attraversate per compiere l'operazione.

![[Schema tabella dati.png]]

**CARICO DI LAVORO III**
Con la tabella dei volumi e delle operazioni possiamo esprimere una stima del costo degli accessi di un operazione contando il numero di accessi alle istanze e associazioni necessarie per eseguire l'operazione. I dati saranno espressi nella tabella degli accessi.

**TABELLA DEGLI ACCESSI**
La tabella degli accessi comprende il concetto, quindi il nome dell'entità/associazione coinvolta, gli accessi che saranno il numero effettivo di accessi in quell'entità/associazione necessari per svolgere l'operazione e il tipo dell'accesso che sarà di scrittura o lettura.
- Il peso degli accessi in **SCRITTURA** è doppio rispetto agli accessi in **LETTURA**.
 
![[Schema tabella accessi.png]]

**DATO DERIVATO**
Il dato derivato è un dato che può essere ricavato attraverso una serie di operazioni su altri dati. Esso è un dato ridonante, quindi ripetuto che però in certi casi può tornare utile e ne vale la pena valutare ciò.
- VANTAGGIO: A tempo di accesso non serve nessuna operazione per ricavare il valore del dato derivato.
- SVANTAGGIO: Essendo un attributo ridondante, quindi un attributo in più, vanno effettuate operazioni di aggiornamento per mantenere la consistenza dei dati.

**ESERCIZIO SU DATO DERIVATO**

![[Esercizio dato derivato.png]]

Per prima cosa identifichiamo quando il dato derivato facilita l'operazione e quando no.
In questo caso abbiamo con il dato derivato abbiamo:
- OP1: Immediata, basta accedere all'entità cliente.
- OP2: Siccome abbiamo il dato derivato dobbiamo aggiornare sia il bilancio che il bilancio netto. Facciamo il deposito sul conto corrente e aggiorniamo il bilancio netto.

Mentre senza dato derivato abbiamo:
- OP1: Siccome non abbiamo il dato derivato per leggere il bilancio netto dobbiamo accedere in conto corrente, quindi accediamo da cliente e andiamo in conto corrente.
- OP2: Immediata, basta accedere al conto corrente.

**FASE 2 - MANTENERE O MENO IL DATO DERIVATO**
![[Tabella dei Volumi.png]]

- IN CASO DI LETTURA: Ci sarà una operazione di lettura.
- IN CASO DI INSERIMENTO/CANCELLAZIONE: Ci sarà una operazione di scrittura.
- IN CASO DI AGGIORNAMENTO: Ci sarà una operazione di lettura ed una di scrittura.

Per spostarsi da un entità A ad un entità B è necessario calcolare gli accessi che si hanno con l'associazione X. Per farlo dobbiamo guardare la cardinalità dell'associazione dal lato dell'entità A.

- **CASO 1:** Se la cardinalità minima coincide con la cardinalità massima allora coincide con la cardinalità degli accessi a X e B. Ci bastano quindi due accessi per spostarci da A a B.
- **CASO 2:** In tutti gli altri casi dobbiamo fare il calcolo sfruttando la tabella dei **VOLUMI**, ci servono quindi il volume dati di X e A (se dobbiamo passare da A a B). Per trovare il numero di accessi ci basta fare vol.dati(X)/vol.dati(B) quindi 30000/15000=2.

![[Cardinalità uguale.png]]
![[Cardinalità diversa.png]]

**ATTENZIONE!**
> Il numero di accessi all'entità "destinazione" B **coincide** col numero di accessi minimi per passare dall'associazione X. Il numero di accessi all'entità "destinazione" B **non coincide** assolutamente con il suo volume dei dati. 
> Questa informazione è utile se dobbiamo attraversare X partendo da B, quindi facendo B->A.




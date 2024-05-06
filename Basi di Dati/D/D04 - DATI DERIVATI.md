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
![[Tabelle.png]]

**COSA CAMBIA CON O SENZA DATO DERIVATO NELLE OPERAZIONI?**
Per prima cosa identifichiamo quando il dato derivato facilita l'operazione e quando no.
In questo caso abbiamo con il dato derivato abbiamo:
- OP1: Immediata, basta accedere all'entità cliente.
- OP2: Siccome abbiamo il dato derivato dobbiamo aggiornare sia il bilancio che il bilancio netto. Facciamo il deposito sul conto corrente e aggiorniamo il bilancio netto.

Senza dato derivato abbiamo:
- OP1: Siccome non abbiamo il dato derivato per leggere il bilancio netto dobbiamo accedere in conto corrente, quindi accediamo da cliente e andiamo in conto corrente.
- OP2: Immediata, basta accedere al conto corrente.

**TIPI DI OPERAZIONI: LETTURA E SCRITTURA**
- In caso di lettura di un istanza contiamo una operazione di lettura.
- In caso di aggiornamento di un istanza contiamo una di lettura e una di scrittura.
- In caso di inserimento/cancellamento è necessaria una scrittura.

**CALCOLARE IL NUMERO DI ACCESSI PER SPOSTARSI DA UN ENTITA ALL'ALTRA**
ENTITA A = A.
ENTITA B = B.
ASSOCIAZIONE X = X.

Per spostarsi da A a B è necessario calcolare la cardinalità di accessi per X. Se troviamo il numero di accessi per X troviamo anche il numero di accessi per B. Abbiamo due casi possibili:
- CARDINALITA MINIMA = MASSIMA: In questo caso allora avremo che questa coincide con la cardinalità degli accessi di X e B, quindi per ogni istanza di A abbiamo 2 istanze di X e 2 di B.
- QUALSIASI ALTRO CASO: Dobbiamo fare il calcolo sfruttando la tabella dei volumi. Per trovare la cardinalità dell'associazione facciamo VolX/VolA. Quindi facciamo 30000/10000 = 3 istanze di X e B collegate.

![[Calcolo di cardinalità.png]]
![[Cardinalità diversa.png]]

ATTENZIONE!
- Il numero di accessi all'entità "destinazione" coincide col numero di accessi dell'associazione X attraversata.
- Il numero di accessi all'entità "destinazione" B **NON DIPENDE** dal volume dei dati di B, questi serviranno solo se ci dobbiamo spostare da B ad A e la nostra cardinalità minima =/= massima!

**COMPLETARE LA TABELLA DEI VOLUMI**
A volte la tabella dei volumi non contiene esplicitamente tutti i dati, questo perchè è facile dedurli.
In questo esempio possiamo dedurre che se A ha 10000 dati possiamo fare 10000 * 3 e trovare il volume dei dati dell'associazione.

![[Completare tabella volumi.png]]

**RISOLUZIONE PROBLEMA**
![[Con dato derivato.png]]![[Senza dato derivato.png]]
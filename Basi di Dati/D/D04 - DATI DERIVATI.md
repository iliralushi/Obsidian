**REGOLA 20/80**
Il carico di lavoro sul DB è rappresentato dal volume dei dati e dalle operazioni che si stimano essere le più eseguite nel DB. Il 20% delle operazioni produce l'80% del carico.

**TABELLA DEI VOLUMI**
La tabella dei volumi comprende il concetto, il tipo e il volume dei dati che dipende da:
- Numero medio di istanze di ogni entità ed associazione.
- Cardinalità e dimensioni di ciascun attributo.
- Percentuali di copertura delle gerarchie.

**TABELLA DELLE OPERAZIONI**
La tabella delle operazioni comprende l'operazione, il suo tipo e la frequenza.
- TIPO DI OPERAZIONE: Interattiva o batch.
- FREQUENZA: Numero medio di esecuzioni in un certo periodo di tempo.
- SCHEMA DI OPERAZIONE: Frammento di E/R interessato dall'operazione con cammino logico da percorrere per accedere alle nostre informazioni di interesse.

**TABELLA DEGLI ACCESSI**
La tabella degli accessi comprende il concetto, gli accessi ed il tipo. Viene ricavata dalla tabella 
dei volumi e delle operazioni. Si può stimare il costo un operazione contando il numero di accessi alle istanze e alle associazioni necessarie per eseguire l'operazione.
- **IL PESO DEGLI ACCESSI IN SCRITTURA È DOPPIO RISPETTO A QUELLI IN LETTURA.**

**DATO DERIVATO**
Un dato derivato è un dato che può essere ottenuto attraverso una serie di operazioni eseguita su altri dati. In questo tipo di esercizi il nostro scopo è valutare se conviene il dato derivato.
- VANTAGGIO: quando accediamo al dato non è richiesta alcuna operazione per ricavare il valore dall'attributo dato che già risiede su un entità.
- SVANTAGGIO: è comunque un attributo ridondante, quindi quando si modificano i dati dobbiamo eseguire operazioni di aggiornamento.

**ESEMPIO ESERCIZIO DATO DERIVATO**
![[Esercizio DD.png]]

**FASE 1 - VANTAGGI/SVANTAGGI DATO DERIVATO**
Con dato derivato:
- Operazione 1: È immediata. Basta accedere all'entità cliente.
- Operazione 2: Dobbiamo percorrere il nostro schema per poter svolgere la seconda operazione.

Senza dato derivato:
- Operazione 1: Dobbiamo percorrere il nostro schema per poter svolgere la prima operazione.
- Operazione 2: È immediata. Non dobbiamo accedere al cliente per poter effettuare un deposito.

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




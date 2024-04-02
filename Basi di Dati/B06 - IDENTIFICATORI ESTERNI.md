**ENTITA DEBOLE**
Un entità debole sono quelle entità che contengono istanze la cui presenza è accettata dal sistema solo se son presenti altre istanze di entità da cui le entità deboli dipendono.
- In caso di eliminazione dell'entità forte allora anche l'entità debole verrà eliminata.
- L'identificatore dell'entità debole deve contenere l'identificatore dell'entità a cui appartiene, quindi un identificatore esterno.

**ESEMPIO IDENTIFICATORE ESTERNO**
Un dipendente può o non può (fare ciò che c'è scritto nell'associazione) delle auto, una sola auto viene (ciò che c'è scritto nell'associazione) da uno e un solo indipendente. 
La chiave di auto sarà l'unione della chiave dell'entità forte e dell'attributo a cui associamo l'identificatore, quindi la coppia (matr, n_a).

![[Identificatore Esterno.png]]

**CARATTERISTICHE IDENTIFICATORI ESTERNI**
- Le identificazioni esterne avvengono SEMPRE con un associazione binaria.
- Una identificazione esterna può coinvolgere un altra identificazione esterna a patto che non si creino cicli di identificazione.
- Una identificazione esterna può coinvolgere più entità purchè ci sia un associazione binaria e che la cardinalità sia (1,1).

**ESEMPIO CUSTODE**

![[Esempio Custode.png]]

In questo esempio abbiamo due vincoli da gestire:
- Ogni area è assegnata ad un unico custode
- Ogni custode sorveglia una sola area per notte

**SOLUZIONE SEMPLICE**:
Una semplice associazione tra la custode e l'area. L'associazione sarà il turno con l'attributo notte.
Questa soluzione non funziona perchè è troppo semplice. Addirittura non possiamo nemmeno modellare il fatto che un custode sorvegli un area per due giorni consecutivi perchè violiamo la chiave (area, custode).

**SOLUZIONE TERNARIA**:
Una associazione tra custode, area e notte che diventa un entità. L'associazione sarà il turno.
Questa soluzione non funziona perchè non c'è alcun vincolo, possiamo aggiungere ciò che vogliamo, per esempio possiamo aggiungere due custodi per una notte unica, oppure un custode in due aree diverse nello stesso giorno.

**SOLUZIONE**:

![[Soluzione Custode.png]]

Entrambi i vincoli vengono rispettati. Turno (riportato sbagliatamente come notte) avrà due chiavi, la chiave (mat, notte) e la chaive (num_area, notte) che non verranno mai violate.
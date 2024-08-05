**Cos'è R**
R è un linguaggio di programmazione funzionale, quindi un paradigma di programmazione dove i programmi vengono creati maggiormente attraverso l'uso di funzioni.

**Operazioni Aritmetiche**
- Addizione, sottrazione, moltiplicazione, divisione, potenza.

**Costanti**
Le costanti in R sono variabili che possono essere modificate. Per ripristinare il valore di default possiamo chiudere l'applicazione, usare la funzione `rm(variable)` o l'icona scopa.
- Pi, numero di Nepero, true, false...

**Funzione Esponenziale**
La funzione `exp(n)` è la funzione esponenziale. In input prende un numero ed in output restituisce la costante di Nepero elevata al numero dato in input.

**Funzione Logaritmica**
La funzione `log(num, base)` è la funzione logaritmica. In input prende il numero e la base ed in output restituisce il logaritmo del numero dato in input. Se si omette la base abbiamo
il logaritmo naturale del numero inserito.

**Variabili**
Per poter immagazinare un valore in una variabile usiamo la sintassi del punto 1.
Per poter vedere le caratteristiche della nostra variabile usiamo la sintassi del punto 2.

``` R
1) height <- 170 # in centimeters
2) str(height) # num 170
```

**Documentazione**
Per vedere come funziona una determinata funzione si può usare il carattere `?`

**Vettori**
Un vettore contiene una serie di numeri dello stesso tipo. Possiamo crearlo in due modi:

``` R
1) primes <- c(2, 3, 5, 7, 9, 11) # funzione c raggruppa i valori
2) one_to_ten <- 1:10 # crea vettore 1:10
```

**Funzione Rep**
La funzione Rep permette di creare i vettori in modi differenti attraverso varie keywords.
Il vettore può essere di qualunque tipo di dato.

- **Times**: Indica quante volte ripetere un vettore. Dando un vettore come input possiamo ripetere i nostri elementi e l'ordine sarà quello del vettore originale.
- **Length.out**: Ripete il pattern del vettore per un numero. Tronca gli elementi rimasti una volta arrivato al numero desiderato.
- **Each**: Ha la stessa funzionalità di times nel momento in cui viene usato un vettore di dimensione uguale per ogni elemento.

``` R
1) rep(c(2, 3), times = 2) # 2 3 2 3
2) rep(c(2, 3), times = c(2, 2)) # 2 2 3 3
3) rep(c(2, 3), times = c(2, 3)) # 2 2 3 3 3
4) rep(c(2, 3), length.out = 3) # 2 3 2
5) rep(c(2, 3), each = 2) # 2 2 3 3
```

**Funzione Seq**
La funzione Seq è un altro metodo per creare vettori. Generalizza l'operatore `:`
Il vettore può essere di qualunque tipo di dato.

- **From**: Indica il numero iniziale del vettore.
- **To**: Indica il numero finale del vettore.
- **By**: Indica quanti salti fare come mostrato nel primo esempio.
- **Length.out**: Permette di creare un vettore con quel numero esatto di elementi.

``` R
1) seq(from = 1, to = 11, by = 2) # 1 3 5 7 9 11
2) seq(from = 1, to = 11, length.out = 21) # 1.0 1.5 2.0 2.5 ...
```

**Operatori Aritmetici Vettori**
- Tutti gli operatori/funzioni aritmetiche viste in precedenza.
- **Sum**: Somma il valore del vettore.
- **Max**: Trova il massimo valore del vettore.

**Comando Plot**
Il comando Plot serve per creare grafici con dei valori già creati.

**Brackets**
I brackets sono usati per tante operazioni come;
- Selezionare un elemento singolo del vettore.
- Selezionare una porzione di vettore.
- Rimuovere l'elemento del vettore in posizione num.

``` R
1) values[1] # considera il primo elemento del vettore
2) half_vector <- values[1:3] # half_vector contiene gli elem. 1-3
3) values[-1] # rimuove il primo elemento dal vettore
```

**Vettore di Bool**
Si possono creare dei vettori di booleani. Se mettiamo un vettore di bool come indice di un vettore esso restituirà gli elementi che sono TRUE. Il modo più utile di usare un booleano è
usare una condizione, tipo `primes > 6.`

**Operazioni Booleane**
- Uguaglianza, diverso da, maggiore/minore, maggiore/minore uguale.

**Operatore %in%**
L'operatore %in% ritorna TRUE se l'elemento è presente nel vettore.

``` R
primes <- c(1, 3, 5, 7, 11)
primes[primes %in% odds] # 3 5 7 11
```

**Funzione Head**
La funzione Head prende come input un numero e in output ritorna i primi N numeri di un vettore/dataset. Il valore di default è 6.

``` R
head(rivers) # i primi 6 elementi di rivers
head(discoveries, n = 10) # i primi 10 elementi di discoveries
```

**Altre Operazioni coi Vettori/Dataset**
- **Sort**: Ordina in modo crescente/decrescente gli elementi di un vettore (col parametro decreasing).
- **Table**: Crea una tabella con le occorrenze degli elementi di un vettore.
- **Which**: Restituisce l'indice dell'elemento se TRUE.

**Tipi di Dato**
- Numeric, integer, character, logical, complex, raw.
- **Factor**: Il tipo di dato che categorizza i dati in un dataset e li distribuisce per livelli.

**N/A**
Non è un tipo di dato, ma un valore che può assumere qualsiasi tipo di dato.
- **Mean**: Funzione che restituisce la mediana di un vettore/dataset. Se ci sono tipi di dati N/A non funziona, vanno rimossi con la funzione rm `(na.rm) = TRUE.`

**Data Frame**
Un data frame è un insieme di variabili organizzati su una tabella, quindi abbiamo le righe che contengono i valori e le colonne che contengono l'informazione del campo. Per trovare
un campo possiamo usare i brackets `[riga, colonna].`

**Operatore $**
L'operatore $ serve per selezionare una singola colonna da un data frame.

**Comando data.frame**
Il comando data.frame crea un data frame che prende come righe la parte a destra dell'uguale e come colonne la parte a sinistra.

``` R
great_lakes <- data.frame
(
	Name = c("A", "B", "C")
	Volume = c("1000", "2000", "3000")
	...
)
```

**Caricare Data Frames da File**
Per poter caricare i CSV ed usarli su RStudio esistono varie funzioni utili:
- **file.choose()**: Permette di trovare il path del file CSV tramite menù interattivo.
- **read.csv()**: Prende in input un path e legge il CSV. Per poter usarlo basta metterlo in una variabile.

**Packages**
RStudio è estendibile attraverso i packages. Per installare un pacchetto bisogna usare 
la funzione `install.packages()` mentre per metterlo in atto bisogna usare la funzione `library().`

**Espressioni Comuni in RStudio**
- `sum(vec == n)`: Il numero di volte che il valore n appare nel vettore.
- `mean(vec == n)`: La percentuale di quante volte n appare nel vettore.
- `table(vec)`: Quante volte ogni valore appare nel vettore.
- `max(table(vec))`: Il valore apparso più volte nel vettore.
- `length(unique(vec))`: Il numero di valori distinti che appaiono nel vettore.
- `vec[vec > 0]`: Un nuovo vettore che contiene gli elementi > 0.
- `vec[!is.na(vec)]`: Un nuovo vettore che include i valori non mancanti in vec.





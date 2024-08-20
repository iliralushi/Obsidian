**Operazioni Aritmetiche**
- Addizione, sottrazione, moltiplicazione, divisione, potenza.

**Funzione Esponenziale**
La funzione `exp(n)` è la funzione esponenziale. In input prende un numero ed in output restituisce la costante di Nepero elevata al numero dato in input.
- `e^n`

**Funzione Logaritmica**
La funzione `log(num, base)` è la funzione logaritmica. In input prende il numero e la base ed in output restituisce il logaritmo del numero dato in input. Se si omette la base abbiamo
il logaritmo naturale del numero inserito.
- `logb(x)`

**Variabili**
Per poter immagazinare un valore in una variabile usiamo la sintassi del punto 1.
Per poter vedere le caratteristiche della nostra variabile usiamo la sintassi del punto 2 o 3.

``` R
1) height <- 62 # height <- height + 2
2) height # 62
3) str(height) # num 64
```

**Costanti**
Le costanti in R sono variabili che possono essere modificate. Per ripristinare il valore di default possiamo chiudere l'applicazione, usare la funzione `rm(variable)` o l'icona scopa.
- Pi, numero di Nepero, T, F...

**Help**
Per usare la documentazione di R usiamo il carattere `?`
- Il comando `?log` fornisce una pagina dettagliata di informazioni su come funziona.

**Vettori**
Un vettore è una serie di valori dello stesso tipo (e di qualunque tipo).
Per poter creare un vettore in R nel modo più semplice usiamo la funzione c, che prende in input una serie di valori e restituisce il vettore.

``` R
primes <- c(2, 3, 5, 7, 9, 11)
```

**Operatore :**
L'operatore `:` è un altro modo semplice per creare un vettore.

``` R
vector_1_to_10 <- 1:10
```

**Funzione Rep**
La funzione Rep è un modo più flessibile per creare vettori. Prende come argomenti un vettore di elementi e degli argomenti opzionali spiegati sotto (se ne sceglie uno):

- **Times**: Ripete gli elementi in ordine del vettore dato. Il valore di Times può anche essere un vettore lungo quanto ogni elemento. Ogni valore esprime quante volte verrà ripetuto il singolo elemento come visto negli esempi 2,3.
- **Length.out**: Ripete il pattern del vettore per un numero. Tronca gli elementi rimasti una volta arrivato al numero desiderato.
- **Each**: Funziona come Times quando prende un vettore come valore, quindi segue l'ordine del vettore e ripete gli elementi x volte.

``` R
1) rep(c(2, 3), times = 2) # 2 3 2 3
2) rep(c(2, 3), times = c(2, 2)) # 2 2 3 3
3) rep(c(2, 3), times = c(2, 3)) # 2 2 3 3 3
4) rep(c(2, 3), length.out = 3) # 2 3 2
5) rep(c(2, 3), each = 2) # 2 2 3 3
```

**Funzione Seq**
La funzione Seq è un modo più specifico di creare vettori. Si rifà all'operatore `:`

- **From**: Numero iniziale vettore.
- **To**: Numero finale vettore.
- **By**: Salti dei numeri del vettore.
- **Length.out**: Funzionamento uguale a Rep.
  
``` R
1) seq(from = 1, to = 11, by = 2) # 1 3 5 7 9 11
2) seq(from = 1, to = 11, length.out = 21) # 1.0 1.5 2.0 2.5 ...
```

**Operazioni Aritmetiche su Vettori**
Trattiamo un vettore come una variabile. Possiamo usare il nome del vettore per poter svolgere una operazione/funzione su tutti gli elementi del vettore.
- Oltre alle operazioni precedenti abbiamo `sum(vector)` che somma tutti gli elementi di un vettore e `max(vector)` che ne ricava il massimo.

**Funzione Plot**
La funzione Plot è una funzione che prende come argomenti due vettori numerici `(x,y)` e come risultato restituisce il grafico associato ai due punti.

**Brackets**
I brackets in un vettore servono principalmente per:
1) Selezionare un elemento singolo del vettore
2) Selezionare una porzione di vettore tramite operatore `:`
3) Rimuovere elementi dal vettore in posizione x

``` R
1) values[1] # prende il primo elemento di un vettore
2) vector <- values[1:3] # vector prende i primi 3 elementi di values
3) values[-1] # rimuove il primo elemento dal vettore
```

**Vettore Booleano**
I vettori possono essere di qualsiasi tipo, anche booleano.

``` R
1) primes[c(TRUE, FALSE, TRUE, FALSE, TRUE)] # 2 5 11
2) primes[primes > 6] # 7 11
```

**Operazioni Booleane**
- Uguaglianza, diverso da, maggiore/minore, maggiore/minore uguale.

**Operatore In**
L'operatore `%in%` ritorna TRUE se l'elemento è presente nel vettore.

``` R
odds <- seq(from = 1, to = 11, by = 2) 
primes[primes %in% odds] # 3 5 7 11
```

**Funzione Head**
La funzione Head prende come input un vettore ed un numero e in output ritorna i primi N elementi del vettore/dataset. Il valore di default è 6.

``` R
head(rivers) # i primi 6 elementi di rivers
head(discoveries, n = 10) # i primi 10 elementi di discoveries
```

**Other**
- **Sort**: Funzione che prende in input un vettore/dataset e un parametro decreasing (settato a FALSE di default) che determina l'ordine crescente/decrescente.
- **Table**: Funzione che prende in input un vettore/dataset e ritorna il numero di occorrenze per ogni elemento.
- **Which**: Funzione che prende in input un vettore di booleani e restituisce TRUE se l'indice del valore è vero.
  
``` R
which(discoveries > 5) + 1859 # anni con più di 5 scoperte
```
  
**Tipi di Dato**
- Numeric, integer, character, logical, complex, raw.
- **Factor**: Il tipo di dato che categorizza i dati in un dataset e li distribuisce per livelli.

**N/A**
Non è un tipo di dato, ma un valore che può assumere qualsiasi tipo di dato.
- **Mean**: Funzione che restituisce la mediana di un vettore/dataset. Non funziona se abbiamo elementi N/A come nel caso del dataset `airquality$Ozone.` Per poter trovar la media quindi usiamo il parametro `na.rm` che rimuove gli elementi NA.

``` R
mean(airquality$Ozone, na.rm = TRUE)
```

**Data Frame**
Un data frame è un insieme di variabili organizzati su una tabella. Le righe contengono i dati
mentre le colonne cosa rappresenta il dato. Possiamo selezionare un valore usando brackets
`[riga, colonna].`

``` R
mtcars[3, 6] # 2.32 - valore della terza riga, sesta colonna
mtcars[3,  ] # tutta la terza riga

mtcars[1:10, ] # le prime 10 righe
```

**Operatore $**
L'operatore $ serve per selezionare una singola colonna da un data frame.

``` R
mtcars$wt # tutti i valori della colonna wt
mtcars$wt[3] # il terzo valore della colonna wt (sesta colonna)
```

**Comando Data.Frame**
Il comando data.frame crea un data frame che prende come righe i valori a destra dell'uguale e come colonne la parte a sinistra.

``` R
great_lakes <- data.frame
(
	Name = c("A", "B", "C")
	Volume = c("1000", "2000", "3000")
	...
)
```

**Caricare Data Frames da File**
RStudio usa principalmente i file CSV, che posson essere caricati come data frame esterni. Ci sono diverse funzioni che permettono di caricare da file, principalmente abbiamo:
- **read.csv():** Prende in input un path e legge il file CSV. Per comodità, si può usare la funzione `getwd()` che trova il path della cartella di RStudio. A quel punto, basta scrivere il nome del file se è all'interno di quella cartella. Per poter usare quel data frame basta inserirlo all'interno di una variabile.
- **file.choose()**: Apre direttamente una finestra che ti fa selezionare il data frame.
- **write.csv():** Permette di scrivere direttamente su data frame.
  
**Packages**
I package sono comandi extra che si possono installare. Per installare un package si usa il comando `install.packages("Package")` mentre per metterlo in atto dobbiamo, ogni volta che si apre RStudio, usare il comando `library(Package)`

**Espressioni Comuni in RStudio**

``` R
sum(vec == 3) # occorrenze del numero 3
table(vec) # occorrenze per ogni valore
max(table(vec)) # occorrenze del numero che appare più spesso

mean(vec == 3) # percentuale delle occorenze del numero 3
length(unique(vec)) # numero di valori distinti

vec[vec > 0] # nuovo vettore che contiene solo valori positivi
vec[!is.na(vec)] # vettore che comprende i valori di vec, escludendo NA
``` 




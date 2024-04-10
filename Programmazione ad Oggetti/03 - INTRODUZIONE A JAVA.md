**CARATTERISTICHE JAVA**
- Linguaggio imperativo, ad oggetti ed interpretato.
- L'utente può allocare memoria dinamica usando la keyword new. La deallocazione è svolta dal garbage collector.
- Ambiente di sviluppo JDK, compilatore javac, interprete JVM, debugger jdb. Contiene numerose librerie quali per I/O, GUI, database...
- JRE è il Java Runtime Enviroment, serve SOLO per eseguire il software.
- Le versioni di Java e JDK sono diverse tra loro.

**TIPI PRIMITIVI**

```                                                                 Java
byte, short, int, long, float, double, char (16 bit), boolean
```

**TIPI RIFERIMENTO**
Un riferimento è un oggetto istanza di una classe, referenziato da una variabile.
Si usa null per indicare nessun riferimento.

**ASSEGNAMENTO**

```                                                                 Java
// Assegnamento fatto tramite operatore uguale.
// L-value (variabile) = R-value (espressione).

a = 5;
a = (b = 3); // valido
``` 

**CAST**

```                                                                 Java
// Si può forzare un valore ad essere un tipo diverso.
// La sintassi del cast è (nuovo_tipo) valore;

int i;
float f = 5.15F;
i = int(f); // casting
``` 

**OPERATORI ARITMETICI**

```                                                                 Java
somma (+), sottrazione (-), moltiplicazione (*), divisione (/), 
modulo (%), incremento (++), decremento (--).
``` 

**OPERATORI BOOLEANI**

```                                                                 Java
or logico (||), and logico (&&), negazione (!).

// funzionano in cortocircuito; se il primo operando dell'or è vero non verrà valutato il secondo, se il primo operando dell'and è falso non verrà valutato il secondo
``` 

**OPERATORI BIT A BIT**

```                                                                 Java
or bitwise (|), and bitwise (&), 
n shift a dx (>>), n shift a sx (<<)
``` 

**OPERATORI DI CONFRONTO**

```                                                                 Java
uguaglianza (==), disuguaglianza (!=), maggiore (>), minore (<), 
maggiore-uguale (>=), minore-uguale (<=).
``` 

**COSTRUTTI CONDIZIONALI - IF**

```                                                                 Java
// Esegue uno statement se la condizione è vera.

if (a > 10)
	b = 1;
else
	b = -1;
```

**COSTRUTTI CONDIZIONALI - SWITCH**

```                                                                 Java
// Viene eseguito il blocco corrispondente alla variabile.

// Se non viene messo il break vengono eseguiti tutti i blocchi dal valore della variabile fino al prossimo break o alla fine.

String day = "Monday";
int dayOfWeek = switch(day)
{
	case "Monday" -> 1;
	case "Tuesday" -> 2;
	...
	...
	default -> -1;
} ;
```


**COSTRUTTI ITERATIVI - FOR**

```                                                                 Java
// 1) Esegue il blocco di istruzioni iniziale.
// 2) Lo ripete affinchè la condizione è vera.
// 3) Ad ogni iterazione incrementa i numeri.

for (int i = 0; i<10; i++)
	a = a*2;
```

**COSTRUTTI ITERATIVI - WHILE**

```                                                                            Java
// Esegue il blocco di istruzioni affinchè la condizione è vera.

while (i < 10)
	i++;
```

**COSTRUTTI ITERATIVI - DO-WHILE**

```                                                                            Java
// Uguale al while di funzionamento.
// Il blocco viene eseguito sempre una volta, la condizione viene testata dopo.

do
	i++;
while (i < 10)

```

**FUNZIONI**

```                                                                 Java
// In Java si chiamano metodi.
// Possono essere definiti solo dentro una classe.
// Possono esistere metodi con lo stesso nome ma parametri diversi.

int somma (int a, int b)
{ return a+b; }
```

**CLASSE**

```                                                                 Java
// Insieme di stato e metodi.
// È un Abstract Data Type.
// Definisce lo stato e i metodi di un oggetto di una classe.
// Si creano oggetti usando la keyword new.
// Esistono classi Wrapper che permettono di usare tipi primitivi come oggetti.

class Contatore
{
	// stato, composto da variabili
	private int val;

	// interfaccia, composta da metodi
	public Contatore() { val = 0; } // COSTRUTTORE
	public void setVal(int newVal) { val = newVal; }
	public void inc() { val++; }
	public int getVal() { return val; }
}
```

**COSTRUTTORE**

```                                                                          Java
// È un metodo speciale che viene chiamato quando si crea un oggetto
// di una classe specifica. Inizializza l'oggetto stesso.
// Ha lo stesso nome della classe e non ha valore di ritorno.
// Possono essere più di uno se differenziati dal numero/tipo di parametri.

public Contatore() { val = 0; }
```

**CREAZIONE DELL'OGGETTO IN MEMORIA**

```                                                                          Java
// cont in questo esempio contiene un riferimento ad un area di memoria
// in cui è contenuto il nostro oggetto.

Contatore cont;
cont = new Contatore();
```

**ESECUZIONE DI UN PROGRAMMA**

```                                                                          Java
// Parte dal metodo citato qui sotto. Il metoodo in questione può
// creare oggetti ed invocare i metodi.

public static void main(String args[])

// Viene creato un sorgente .class in bytecode attraverso il compilatore.
javac nomefile.java

// L'interprete esegue il sorgente con la classe che contiene il main.
java nomeclasse
```

**COMPILATORE VS INTERPRETE IN JAVA**

```                                                                          Java
// Java li usa entrambi.
// Usa il compilatore javac per creare il sorgente in formato bytecode.
// Usa l'interprete JVM per eseguire il sorgente.
// In questo modo si ha velocità nell'eseguire il programma e una
// buona portabilità.
```

**STRINGHE**

```                                                                          Java
// Le stringhe in Java sono oggetti, istanze della classe String.
// Non sono un buffer modificabile, per questo bisogna usare il tipo
// Stringbuffer.

String s = "ciao"; // viene creato un oggetto di tipo string con valore ciao.
String s = "ciao" + " " + "pippo"; // concatenare stringhe con operatore +.

String s = "Nel mezzo del cammin";
char ch = charAt(4) // valore di ch è "m".
```

**METODI STRINGHE**

```                                                                          Java
char charAt(int index) // restituisce il carattere in quella posizione.
boolean endsWith(String suffix) // vero se finisce con quella stringa.
boolean beginsWith(String prefix) // vero se inizia con quella stringa.
boolean equals(Object other) // vero se la stringa è uguale a other.
String substring(int beginidx) // restituisce una stringa che parte dall'indice beginidx fino alla fine.
String substring(int beginidx, int endidx) // restituisce una stringa che parte dall'indice beginidx e finisce ad endidx.
int length() // restituisce la lunghezza della stringa.
String toLowerCase() // rende la stringa tutta minuscola.
String toUpperCase() // rende la stringa tutta maiuscola.
```

**ARRAY**

```                                                                         Java 
// Gli array in Java sono oggetti. Sono identificati dall'operatore [].
// Definire un array definisce un riferimento. Per crearlo usare new.

int[] v1 = {8, 12, 3, 4}; // array statico, già definito

int[] v2;
v2 = new int[5] // crea 5 celle di tipo int, inizializzate a zero

String v1[];
v1 = new String[2]; // crea 2 riferimenti ad oggetto, inizializzati a null
v1[0] = "Hello World!"; // stringa statica
v1[1] = new String("Ciao n." + 2) // stringa dinamica

Contatore cont[]
cont = new Contatore[3]; // 3 riferimenti a Contatore, inizializzati a null

cont[0] = new Contatore(0); // valore 0
cont[1] = new Contatore(100); // valore 100
cont[2] = null; // non inizializzato
```

**DOCUMENTAZIONE**

```                                                                         Java 
// È possibile creare commenti con /**, verranno interpretati come
// informazioni da inserire in documentazione.
// Javadoc crea pagine HTML di documentazione.
```
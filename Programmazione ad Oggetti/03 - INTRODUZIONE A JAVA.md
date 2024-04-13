**CARATTERISTICHE JAVA**
- Linguaggio imperativo, tipizzato, ad oggetti, interpretato ed indipendente dalla piattaforma.
- L'utente alloca spazio in memoria dinamica usando la keyword new. Il sistema gestisce la deallocazione autonomamente grazie al garbage collector.
- L'ambiente di sviluppo è il JDK e funziona da linea di comando. Il compilatore è javac che produce codice intermedio (in bytecode), l'interprete è il JVM, il debugger è il jdb.
- Esistono molte librerie, quali per I/O, GUI, networking, threads, database...
- Il JRE è il Java Runtime Enviroment, è un tool che serve per l'esecuzione del software.
- Le versioni di Java e JDK sono diverse tra loro.

**TIPI PRIMITIVI**
 
```                                                                          Java
byte, short, int, long, float, double, char (16 bit), boolean
```

**TIPI RIFERIMENTO**

```                                                                            Java
// Un riferimento è un oggetto istanza di una classe, referenziato da
// una variabile.

Contatore cont; // tipo riferimento, usare null per indicare nessun riferimento
```

**ASSEGNAMENTO**

```                                                                 Java
// Assegnamento fatto tramite operatore uguale.
// L-value (variabile) = R-value (espressione).

a = 5;
a = (b = 3); // valido
``` 

**CAST**

```                                                                            Java
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

```                                                                            Java
// Esegue uno statement se la condizione è vera.

if (a > 10)
	b = 1;
else
	b = -1;
```

**COSTRUTTI CONDIZIONALI - SWITCH**

```                                                                            Java
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

```                                                                            Java
// 1) Esegue il blocco di istruzioni iniziale.
// 2) Lo ripete affinchè la condizione è vera.
// 3) Ad ogni iterazione incrementa la variabile di controllo.

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

```                                                                            Java
// In Java si chiamano metodi.
// Possono essere definiti solo dentro una classe.
// Possono esistere metodi con lo stesso nome ma parametri diversi.

int somma (int a, int b)
{ return a+b; }
```

**COMMENTI**

```                                                                            Java
// Esistono 3 tipi di commenti:
// C-styled /* e terminano con */
// C++ styled //
// Documentazione Java /** e terminano con */ - non considerati dal compiler
```

**CLASSE**

```                                                                            Java
// Insieme di stato e metodi, definiscono l'oggetto.
// È un Abstract Data Type.
// Si creano oggetti usando la keyword new.
// Esistono classi Wrapper che permettono di usare tipi primitivi come oggetti.

class Contatore
{
	// stato, composto da variabili
	private int val;

	// interfaccia, composta da metodi
	public Contatore() { val = 0; } // costruttore
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

public Contatore() { val = 0; } // costruttore
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
// creare oggetti ed invocare i metodi. Solitamente si crea la classe
// Main.

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
v2 = new int[5]; // crea 5 celle di tipo int, inizializzate a zero

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

```                                                                           Java 
// Javadoc crea pagine HTML di documentazione.
// Per creare il file HTML di documentazione si può usare il comando
// javadoc -author -version -d doc file.java
```

**PACKAGES**

```                                                                         Java 
// Sono contenitori logici di classi. Corrispondono a contenitori fisici
// dei file delle classi .class. Sono anche contenitori ricorsivi, quindi
// esistono package e sottopackage.

// Supponiamo di inserire la classe Contatore e Data all'interno del package
// utilità

package utilità -> // creazione del package
utilità.Contatore o utilità.Data // nome completo della classe senza importare
utilità.Contatore c1 = new utilità.Contatore() // creazione oggetto

$ java utilità.Contatore // esegue main della classe Contatore, package utilità

import utilità.Contatore // importa la classe del package su un altro file
Contatore c1 = new Contatore(); // non c'è bisogno del package.classe se si importa il package

import utilità.*; // importa tutte le classi della directory (* non è ricorsivo)

package utilità // per inserire una classe in un package
public class Contatore // basta specificare la direttiva package nomePackage
{
	...
}

package utilità.file // per inserire una classe in un sottopackage
public class Contatore // package nomePackage nomeSottoPackage
{
	...
}

// Questi sono package di default, vengono inseriti nella directory corrente.
// Tutte le entità definite senza modificatori (public, private) sono visibili
// solo nel package.
```

**VARIABILI DI CLASSE**

```                                                                         Java 
// Variabili definite attraverso la keyword static. Esistono
// indipendentemente dall'esistenza di oggetti di quella classe.

class Esempio
{
	private static int x = 0;
	...
}
```

**METODI DI CLASSE**

```                                                                           Java 
// Metodi definiti attraverso la keyword static. 
// Esistono indipendentemente dall'esistenza di oggetti di quella classe.
// Possono essere invocati anche senza la creazione di un oggetto della classe.
// Possono accedere solo a variabili di classe.

class Esempio
{
	public static void prova() { System.out.print("ciao"); }
}

Esempio.prova(); // valido invocare dall'esterno
```

**COSTANTI**

```                                                                         Java 
// Sono etichettate con la keyword final.
// Tipicamente variabili statiche di classe, ma anche locali.

class EsempioCostanti
{
	private static final int max = 8; // costante di classe
	void metodo() { final float radiceDi2 = 1.4142F } // costante locale
}
```

**RIFERIMENTI AD OGGETTI**

```                                                                         Java 
// Le variabili di tipo riferimento contengono un riferimento ad
// un oggetto.

Contatore p1 = new Contatore();
Contatore p2 = p1; // non duplica p1 ma copia il suo riferimento
p2.inc(); // vale anche per p1, puntano allo stesso oggetto
System.out.print(p1.getVal()); // stampa 1
```

**CLONAZIONE DI OGGETTI**

```                                                                         Java 
// Per copiare un oggetto bisogna usare il metodo clone()

Contatore p1 = new Contatore();
Contatore p2 = (Contatore)p1.clone(); // copiato
p2.inc();
System.out.println(p1.getVal()) // stampa 0, non ha copiato il riferimento
```

**PASSAGGIO DEI PARAMETRI**

```                                                                         Java 
// Tutti i parametri sono passati per riferimento.
// Se di tipo primitivo viene passato per valore vero e proprio.
// Se di tipo riferimento viene pasasato per indirizzo.
```

**CONFRONTO TRA OGGETTI**

```                                                                         Java 
// Bisogna usare il metodo equals(). Non possiamo paragonare due
// riferimenti, in quel caso restituisce true se entrambi i riferimenti
// puntano allo stesso oggetto.
```

**GARBAGE COLLECTOR**

```                                                                         Java 
// È un componente dell'interprete, si occupa di liberare automaticamente
// memoria dinamica una volta che non è più accessibile.
```

**KEYWORD THIS**

```                                                                         Java 
// Parola chiave che serve per indicare l'oggetto stesso che sta eseguendo
// il codice. Riferimento ad istanza di oggetto.
// Serve per specificare variabili/metodi di istanza.
// Serve per chiamare costruttori della stessa classe.

class Contatore
{
	private int val;
	public Contatore(int val) { this.val = val; }
	public Contatore() { this(0); }
}
```

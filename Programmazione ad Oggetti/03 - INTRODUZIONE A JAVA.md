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
// In Java si chiamano METODI.
// Possono essere definiti SOLO dentro una classe.
// Possono esistere metodi con lo stesso nome ma parametri diversi.

int somma (int a, int b)
{ return a+b; }
```

**CLASSE**

```                                                                 Java
// Insieme di variabili (stato) e di metodi (interfaccia).
// ADT, definisce tutti i metodi e le variabili comuni a tutti gli oggetti di un certo tipo.
// Si creano oggetti usando la keyword "new".

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

```                                                                 Java
// Il costruttore è un metodo speciale che viene chiamato quando
// si crea un oggetto della classe.
// Esso serve per inizializzare l'oggetto.

	public Contatore() { val = 0; }

// Ha lo stesso nome della classe, non ritorna niente, più di uno se differenziati dal numero/tipo di parametri.
```

**CREAZIONE DELL'OGGETTO IN MEMORIA**

```                                                                 Java
// cont è una variabile che contiene un riferimento in memoria 
// in cui è contenuto il nostro oggetto.

Contatore cont;
cont = new Contatore();
```

**ESECUZIONE DI UN PROGRAMMA**

```                                                                 Java
// L'esecuzione di un programma parte da un metodo main.
// Questo metodo può creare oggetti ed invocare i metodi.

public static void main(String args[])

// Un sorgente java viene compilato con javac. Produce un file
// Che contiene il bytecode della classe con estensione .class
javac nomefile.java

// Per eseguire bisogna invocare l'interprete java con il nome della CLASSE che contiene il metodo main.
java nomeclasse
```


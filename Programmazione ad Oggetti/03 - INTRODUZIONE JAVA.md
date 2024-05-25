**CARATTERISTICHE BASE DI JAVA**
- È un linguaggio imperativo, fortemente tipizzato, ad oggetti, interpretato, portabile.
- Filosofia Smalltalk per quanto riguarda la memoria; allocazione gestita dal developer (new), deallocazione gestita dal garbage collector.
- Ambiente di sviluppo JDK, compilatore javac, interprete JVM, debugger jdb.
- Il linguaggio Java ha un numero di versione, l'interprete JVM un altra.

**TIPI PRIMITIVI**
I tipi primitivi disponibili in Java sono:
- Byte, short, int, long, float, double, boolean, char.

**TIPI RIFERIMENTO**
È un oggetto, istanza di una classe referenziato da una variabile. Si usa null per indicare nessun riferimento.

**ASSEGNAMENTO**
L'assegnamento viene fatto tramite l'operatore uguale.
- L-value = R-value.
- L-value è una variabile, R-value è una espressione.
- a = (b = 3);

**CAST (FORZATURA)**
Si può forzare un valore ad essere di un tipo diverso tramite un cast esplicito.
- (nuovo_tipo) valore.

``` Java
int i;
float f = 5.15F;
i = (int)f;
```

**OPERATORI ARITMETICI**
Sono disponibili vari operatori aritmetici come:
- Somma, sottrazione, moltiplicazione, divisione, resto, incremento, decremento.

**OPERATORI BOOLEANI**
Cortocircuito; se il primo operatore è falso in un and allora il secondo operando non viene valutato, viceversa se il primo operatore è vero in un or non viene valutato il secondo.
Sono disponibili i seguenti operatori booleani:
- Or, and, not.

**OPERATORI SU BIT**
Sono disponibili operatori che operano sui singoli bit di un numero.
- Or, and bitwise, shift a destra, shift a sinistra.

**OPERATORI DI CONFRONTO**
Sono disponibili questi operatori di confronto che restituiscono un boolean:
- Uguaglianza, disuguaglianza, maggiore, minore e uguale.

**BLOCCHI DI ISTRUZIONE**
Un blocco è un insieme di istruzione rinchiuso tra due graffe, rappresenta una singola istruzione logica composta da più istruzioni, può essere vuoto.

**COSTRUTTO CONDIZIONALE - IF**
Esegue uno statement se la condizione è vera.

``` Java
if (a > 10)
{
	b = 1;
}
else
{
	b = -1;
}
```

**COSTRUTTO SELETTIVO - SWITCH**
Viene eseguito il blocco corrispondente al valore della variabile. Se non c'è un break allora verranno eseguite tutte le istruzioni che vanno dal valore della variabile fino al prossimo break.

``` Java
String day;
int dayOfWeek = switch (day)
{
	case "Monday" -> 1;
	case "Tuesday" -> 2;
	...
	default -> -1;
} ;
```

**COSTRUTTO ITERATIVO - FOR**
Esegue:
- L'assegnamento iniziale.
- Ripete un blocco di istruzioni finchè la condizione è vera.
- Esegue l'incremento alla fine del blocco.

``` Java
for (int i = 0; i<10; i++)
	a *= 2;
```

**COSTRUTTO ITERATIVO - WHILE**
Esegue il blocco di istruzioni finchè la condizione è vera.

``` Java
while (i < 10)
	i = i + 1;
```

**COSTRUTTO ITERATIVO - DO-WHILE**
Funziona come il while però il controllo viene eseguito dopo, quindi il blocco di istruzioni verrà eseguito minimo una volta.

**FUNZIONI**
In Java si chiamano metodi, possono essere definiti solo dentro una classe e possono esistere metodi di nome uguale con numero o tipo di parametri diverso.

**CLASSE**
Insieme di attributi e metodi. È un tipo di dato astratto, template che definisce gli attributi e i metodi di tutte le istanze della classe. Essendo un tipo quindi si possono dichiarare variabili. Si creano oggetti usando la keyword new.

**METODO COSTRUTTORE**
Ogni classe ha uno o più metodi costruttore che vengono chiamati automaticamente quando viene creato l'oggetto e serve per inizializzare tutti gli attributi di una classe specifica. Se il programmatore non scrive niente viene sostituito da un costruttore vuoto con 0 parametri.
- Ha lo stesso nome della classe.
- Non ha valore di ritorno.
- Più di uno se differenziati dal numero/tipo dei parametri.

``` Java
class Contatore
{
	private int val;

	public Contatore() {val = 0;} // costruttore

	public void setVal(int newVal) {val = newVal;}
	public void inc() {val++;}
	public int getVal() {return val;}
}
```

**CREAZIONE DELL'OGGETTO IN MEMORIA**
Cont è una variabile che contiene un riferimento ad un area di memoria del nostro oggetto.

``` Java
Contatore cont;
cont = new Contatore();
```

**ESECUZIONE DI UN PROGRAMMA JAVA**
È definita da un metodo che può invocare altri metodi e creare oggetti.

``` Java
public static void main(String args[])
```

Per quanto riguarda la linea di comando bisogna fare due passaggi per eseguire il programma;
- Invocare il compilatore javac tramite la dicitura javac nomefile.java che crea un file bytecode (file intermedio) della classe con estensione .class.
- Invocare l'interprete JVM tramite la dicitura java nomeclasse con nomeclasse il nome della classe che contiene il metodo main.

**PRIMO PROGRAMMA JAVA**

``` Java
public class PrimoEsempio
{
	public static void main(String args[])
	{
		Contatore c;
		c = new Contatore();

		c = setVal(0);
		c.inc();

		System.out.print("Numero = ");
		System.out.println(c.getVal());
		System.out.println("Ciao Mondo!");
	}
}

// Compilazione
$ javac PrimoEsempio.java
$ java PrimoEsempio
```

**ARGOMENTI DEL MAIN**
È possibile passare degli argomenti al programma via linea di comando e si possono recuperare attraverso il parametro args del metodo main.

``` Java
$ java PrimoEsempio pippo pluto

public static void main(String args[])
{
	for (int i = 0; i<args.length; i++)
		System.out.println("arg" + (i+1) + ": " + args[i]);
}
```

**STRINGHE**
In Java le stringhe sono oggetti, istanze della classe String. Non sono dei buffer modificabili e per memorizzare stringhe modificabili si usa StringBuffer. Quando si scrivono costanti stringhe fra virgolette allora l'oggetto String verrà inizializzato a quel valore.

``` Java
String s = "ciao"; // s già inizializzata al valore di ciao
String s = "ciao" + "pippo"; // concatenazione di stringhe con +
```

La selezione di un carattere non si fa accedendo alla stringa ma con il metodo charAt().

``` Java
String s = "Nel mezzo del cammin";
char ch = charAt(4); // ch contiene m
```

**METODI STRINGHE**

``` Java
char charAt(int index)
// Restituisce char in pos index
boolean endsWith(String suffix)
// Vero se la stringa finisce con suffix
boolean beginsWith(String prefix)
// Vero se la stringa inizia con prefix
boolean equals(Object other)
// Vero se la stringa è uguale ad other
String substring(int beginindex)
String substring(int beginindex, int endindex)
// Restituisce sottostringa che parte da beginindex
// Restituisce sottostringa che parte da beginindex e finisce a endindex
int length()
// Restituisce la lunghezza della stringa
String toLowerCase()
// Restituisce la stringa minuscola
String toUpperCase()
// Restituisce la stringa maiuscola
```

**ARRAYS**
In Java anche gli array sono oggetti; non esiste il nome della classe perchè sono identificati dall'operatore [] . Definire un array vuol dire definire un riferimento ad oggetto che verrà creato con l'operatore new almeno che non sia specificato con una costante, inoltre la loro lunghezza è definita dal campo length.

``` Java
class EsempioArray
{
	public static void main(String args[])
	{
		int[] v1 = {8, 12, 3, 4}; // array definito

		int[] v2; // riferimento ad array di int
		v2 = new int[5]; // array di int di 5 elementi iniz. a 0
	}
}
```

Creare un array con new vuol dire creare:
- N celle di un tipo primitivo oppure
- N riferimenti ad oggetti (tutti null) se l'array è di oggetti.

``` Java
class EsempioArray2
{
	public static void main(String args[])
	{
		String v1[]; // riferimento a String
		v1 = new String[2]; // 2 riferimenti null a String

		v1[0] = "Ciao mondo";
		v1[1] = new String("Ciao n. " + 2); // stringa dinamica
	}
}
```

**DOCUMENTAZIONE**
Nel codice è possibile inserire dei commenti che iniziano con /** . Questi commenti poi verranno interpretati come informazioni inseribili su Javadoc, che sono pagine HTML di documentazione.
Per creare i file HTML di documentazione si usa:

``` Java
$ javadoc -author -version -d doc ContatoreDoc.java
```

**PACKAGE**
I package sono contenitori logici di classi, quindi dei contenitori fisici di file .class;
- Directory nel file system.
- Corrispondenza anche nel nome.
- Un package può contenere classi e sottopackage.

Il package non è solo un contenitore di classi, ma determina anche un ambito di visibilità; tutte le entità definite senza modificatori sono visibili solo all'interno del package.

**USO PACKAGE**
Supponiamo di inserire una classe Contatore ed una classe Data all'interno del package utilità.
Il nome completo delle classi diventerà utilità.Contatore e utilità.Data. I file Contatore.class e Data.class quindi saranno contenuti in utilità.

Quando si vuole usare una classe inserita in un package basta specificare il percorso completo, quindi la classe contatore contenuto nel package utilità diventa:

``` Java
utilità.Contatore c1 = new utilità.Contatore();

$ java esempio.Esempio2

// Esegue il main della classe Esempio2 contenuta nel package esempio.
// Va specificato il path completo per poter eseguire il main delle classi
// all'interno di un package.
```

**IMPORT PACKAGE**
Non è comodo dover specificare il percorso della classe, quindi possiamo importare i package nei nostri file, in questo modo possiamo semplicemente usare il nome della classe.

``` Java
import utilità.Contatore;
...
Contatore c1 = new Contatore();
```

È possibile usare la wildcard * che include tutte le classi di un package. **NON** è ricorsivo, quindi importerà soltanto le classi contenute nel package stesso.

``` Java
import utilità.*;
```

**INSERIRE CLASSI IN PACKAGE**

``` Java
package utilità; // inserisco la classe Contatore nel package utilità
public class Contatore
{
	...
}
```

``` Java
package utilità.file // inserisco la classe nel sottopackage file
public class FileComparator
{
	...
}
```

**VARIABILI DI CLASSE**
Sono le variabili definite attraverso la keyword static. Esistono indipendentemente dall'esistenza di oggetti in quella classe e sono condivise tra tutti gli oggetti.

**VARIABILI DI METODI**
Sono i metodi definiti attraverso la keyword static. Esistono indipendentemente dall'esistenza di oggetti in quella classe, possono accedere solo a variabili di classe e possono essere invocati anche senza creare un oggetto di quella classe.
- Classe.metodo();

**COSTANTI**
Le costanti vengono definite attraverso la keyword final.

**RIFERIMENTI AD OGGETTI**
Le variabili di tipo riferimento contengono un riferimento ad oggetto. Un assegnamento come
p2 = p1; non duplica p2 in p1 ma bensì p2 prenderà come riferimento il riferimento di p1.

``` Java
Contatore p1 = new Contatore();
Contatore p2 = p1;

p2.inc();
System.out.println(p1.getVal());
// Stampa 1, entrambi valgono 1.
```

``` Java
Contatore p1 = new Contatore();
Contatore p2 = (Contatore)p1.clone();
// Possiamo clonare un oggetto usando il metodo clone()
// Se si incrementa p1 allora p2 vale ancora 0.
```

``` Java
p1.equals(p2);
// Possiamo usare il metodo equals per confrontare oggetti
// Se usiamo l'operatore di confronto ci paragona i riferimenti
// che restituisce true se entrambi puntano allo stesso oggetto
```

**PASSAGGIO PARAMETRI**
Tutti i parametri in Java sono passati per copia.
- Se di tipo primitivo si effettua il passaggio per valore.
- Se di tipo oggetto si effettua il passaggio per indirizzo.

**GARBAGE COLLECTOR**
Il garbage collector è un componente dell'interprete di Java che si occupa di liberare memoria non più accessibile. Un esempio è il seguente:

``` Java
Contatore p1 = new Contatore();
c = null;
// Il garbage collector agirà liberando automaticamente la memoria
```

**THIS**
La keyword this serve per indicare l'oggetto stesso che sta eseguendo il codice. Si usa per:
- Specificare variabili e metodi di istanza, utile in caso di ambiguità.
- Chiamare costruttori della stessa classe.

``` Java
class Contatore
{
	private int val;
	public Contatore(int val) {this.val = val;}
	public Contatore() {this(0);}
}
```

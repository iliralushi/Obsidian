**INCAPSULAMENTO**
L'incapsulamento dice che la classe "incapsula" queste caratteristiche:
- Variabili che siano primitive o riferimenti
- Metodi (funzioni), devono essere definiti all'interno della classe che li dichiara.
- Altre classi (nested class)

**VISIBILITÀ**
Le variabili e i metodi possono avere uno dei seguenti attributi di visibilità:
- Private: non visibile all'esterno.
- Public: visibile da tutti.
- Protected: visibile solo dalle classi figlie e dalle classi dello stesso package.

**ESEMPIO INCAPSULAMENTO

```                                                                          Java
public class Veicolo
{
	// variabili private
	private int velocitaMassima;
	private int numeroPosti;

	// costruttore
	public Veicolo(int VM, int NP)
	{
		velocitaMassima = VM;
		numeroPosti = NP;	
	}

	// metodi pubblici
	public int getVelocitaMassima() { return velocitaMassima; }
	public int getNumeroPosti() { return numeroPosti; }
}

public class Main
{
	public static void main(String args[])
	{
		Veicolo miaMacchina;
		miaMacchina = new Veicolo(150, 5);
		System.out.print("La mia macchina ha ");
		System.out.print(miaMacchina.getNumeroPosti() + "posti" );
		System.out.print("e raggiunge la velocità di ");
		System.out.print(miaMacchina.getVelocitaMassima() + "km/h");
	}
}

// Questo programma stamperà "La mia macchina ha 5 posti e raggiunge la velocità massima di 150 km/h"
```

**EREDITARIETÀ**
L'ereditarietà serve per definire una classe partendo da classi esistenti. Può capitare di dover definire una classe che sia simile ma non identica. Viene creata una nuova classe che eredita tutti i metodi e gli attributi della classe padre. Può aggiungere attrbuti e metodi, inoltre può modificare i metodi ereditati. 

```                                                                            Java
// esempio
class Contatore2 extends Contatore
{
	// aggiungo un nuovo metodo mantenendo i metodi della classe Contatore
	public void decremento() { setVal(getVal()-1); }
	// se val non fosse private si poteva fare val-- direttamente;
}
```

**EREDITARIETÀ IN JAVA**
Si usa la keyword extends.
L'ereditarietà singola fa ereditare alla classe figlia gli attributi ed i metodi della classe padre. Può gestire direttamente solo gli attributi visibili (non private). L'ereditarietà monotòna è quando si possono solo aggiungere metodi/attributi.

**RELAZIONI TRA CLASSI CON EREDITARIETÀ**
Con l'ereditarietà si avrà una relazione tra classi. Come per il fatto che l'oggetto singolare è un istanza della classe si ha una classe padre (classe base, superclasse) che fa ereditare e la classe figlio (classe derivata, sottoclasse) che eredita.

**COSTRUTTORI EREDITARIETÀ**
La classe figlio non eredita i costruttori perchè non svolgono funzioni bensì inizializzano un'istanza della classe. Se non ci sono costruttori si avrà che verrà chiamato il costruttore padre senza parametri.

**KEYWORD SUPER**
Serve per specificare che si sta facendo riferimento di un attributo o metodo della classe padre oppure per chiamare un costruttore della classe padre. Non esiste la definizione super.super per indicare la classe nonno.

```                                                                          Java
class ContatorePreciso extends Contatore
{
	private double val; // indica il campo val di ContatorePreciso
	// super.val indica il val della classe Contatore
	@Override

	public void inc() {super.inc(); val++;}
	// inc incrementa val di ContatorePreciso, super.inc() incrementa val di
	// Contatore.

	// Ridefinire le variabili con lo stesso nome non è tanto utile, mentre
	// mentre ridefinire i metodi serve per avere un comportamento polimorfico.
	// Super permette di riusare codice della classe padre.
}
```

**GERARCHIA JAVA**
Viene definita una classe radice che raggruppa le definizioni comuni ad ogni oggetto e dalla quale originano tutte le classi, ovvero la classe Object.

**ESEMPIO EREDITARIETÀ**

```                                                                          Java
public class Veicolo // extends Object
{
	private int numeroPosti;

	public Veicolo(int NP) { numeroPosti = NP; }
	public int getNumeroPosti() { return numeroPosti; }
}

public class VeicoloTerrestre extends Veicolo
{
	private int numeroRuote;

	public VeicoloTerrestre(int NP, int NR) { super(NP); numeroRuote = NR; }
	public int getNumeroRuote() { return numeroRuote; }
}

public class VeicoloAcquatico extends Veicolo
{
	private long stazza;

	public VeicoloAcquatico(int NP, long S) {super(NP); stazza = S; }
	public long getStazza() { return stazza; }
}

public class Main
{
	public static void main(String args[])
	{
		VeicoloTerrestre miaMacchina;
		VeicoloAcquatico miaNave;

		miaMacchina = new VeicoloTerrestre(5, 4);
		System.out.print("La mia macchina ha ");
		System.out.print(miaMacchina.getNumeroPosti() + " " + "posti e ");
		System.out.println(miaMacchina.getNumeroRuote() + " " + "ruote");

		miaNave = new VeicoloAcquatico(10, 10);
		System.out.print("La mia nave ha ");
		System.out.print(miaNave.getNumeroPosti() + " " + "posti e ");
		System.out.println("una stazza di " + miaNave.getStazza());
	}
}

$ java Main
// La mia macchina ha 5 posti e 4 ruote
// La mia nave ha 10 posti e una stazza di 10
```

**PROTECTED**
Le sottoclassi devono accedere in un qualche modo agli attributi delle superclassi. Siccome di default le classi hanno gli attributi privati (inaccessibili da tutto tranne che la classe stessa) serve un nuovo tipo di visibilità.
- Protected: Le classi figlie possono accedere, così come una classe dello stesso package, il resto no.

![[Visibilità.png]]

**COMPATIBILITÀ TRA CLASSI**
L'ereditarietà non serve solo per riutilizzare codice ma anche per definire una relazione tipo-sottotipo (classificazione).
Contatore2 ha tutte le caratteristiche di Contatore, eredita l'entità con l'aggiunta di altri metodi. 
Contatore2 è sottotipo di Contatore.

```                                                                          Java
public static void main(String args[])
{
	Contatore c1 = new Contatore(3);
	Contatore c2 = new Contatore2();
	c2.dec(); // esiste in contatore2, va bene
	c1.dec(); // errato, non esiste in contatore anche se c1 fa riferimento a c2
	c1 = c2; // giusto, contatore2 è anche contatore
	c2 = c1; // errato, non vale il viceversa, dec non esiste in c1
}
```

```                                                                          Java
// Possiamo usare il concetto di ereditarietà per creare entità legate
// tra di loro. Per esempio entità Persona (generica) e Studente (specifica).

public class Persona
{
	private String nome;

	public Persona() { nome = ""; }
	public Persona(String n) { nome = n; }
	public void print() { System.out.print("Il mio nome è " + nome); }
}

public class Studente extends Persona
{
	private int matricola;

	public Studente() { super(); matricola = 0; }
	public Studente(String n) { super(n); matricola = 0; }
	public Studente(String n, int m) { super(n); matricola = m; }
	@Override

	public void print()
	{
		super.print();
		System.out.println("Matricola = " + matricola);
	}
}
```

**POLIMORFISMO**


**INCAPSULAMENTO**
L'incapsulamento dice che la classe conterrà:
- Variabili di qualsiasi tipo (primitivo o riferimento).
- Metodi che devono essere definiti all'interno della classe.
- Altre classi, dette nested class.

**VISIBILITÀ**
- **PRIVATE**: non visibile dall'esterno.
- **PUBLIC**: visibile ovunque.
- **PROTECTED**: visibile solo dalle classi figlie e dalle classi dello stesso package.

**ESEMPIO INCAPSULAMENTO**

``` Java
public class Veicolo
{
	private int velocitaMassima;
	private int numeroPosti;

	public Veicolo(int velocitaMassima, int numeroPosti)
	{this.velocitaMassima = velocitaMassima;
	 this.numeroPosti = numeroPosti;}

	public int getVelocitaMassima() {return velocitaMassima;}
	public int getNumeroPosti() {return numeroPosti;}
}

public class Esempio2
{
	public static void main(String args[])
	{
		Veicolo miaMacchina;
		miaMacchina = new Veicolo(150, 5);

		System.out.print("La mia macchina ha ");
		System.out.print(miaMacchina.getNumeroPosti() + "posti");
		System.out.print(" e raggiunge la velocita' di ");
		System.out.println(miaMacchina.getVelocitaMassima() + " km/h.");
	}
}

// Stampa:
// "La mia macchina ha 5 posti e raggiunge la velocita' di 150 km/h." 

// Se avessi scritto
int intero = miaMacchina.numeroPosti;
// Il compilatore mi avrebbe dato errore.
```

**EREDITARIETÀ**
È una caratteristica della OOP che permette di creare una nuova classe figlio che eredita le caratteristiche della classe padre, permettendo di aggiungere nuovi attributi/metodi per estendere la classe oppure modificare i metodi già esistenti.
- **ES:** possiamo estendere la classe contatore aggiungendo il decremento.

``` Java
class Contatore2 extends Contatore
{
	public void dec() {setVal(getVal()-1)}
}

// Contatore2 estende Contatore
// Contatore2 aggiunge il metodo dec()
// setVal e getVal vengono chiamati sull'oggetto stesso dato che eredita.
```

**EREDITARIETÀ IN JAVA**
- **SINGOLA**: Una classe può derivare da altre classi; la classe figlia eredita tutti gli attributi ed i metodi ma può gestire solo quelli visibili che non vengono ridefiniti (Override).
- **MONOTONA**: Una classe può solo aggiungere membri.
- **SUPER**: Keyword usata per accedere ai membri ridefiniti.

L'ereditarietà si può vedere come una relazione tra classi;
- **CLASSE PADRE**: Classe base o superclasse.
- **CLASSE FIGLIA**: Classe derivata o sottoclasse.

**COSTRUTTORE EREDITARIETÀ**
La classe figlia eredita tutto tranne i costruttori della superclasse siccome il costruttore inizializza gli attributi della classe specifica, quindi è unico per classe. Se non viene messo un costruttore ne viene creato uno senza parametri che chiamerà il costruttore senza parametri della superclasse.
- Se il costruttore senza parametri della superclasse non esiste allora si verifica un errore.

**SUPER**
La keyword super viene usata per due motivi principalmente;
- Per specificare che si sta facendo riferimento ad un attributo/metodo della superclasse.
- Per chiamare un costruttore della superclasse.
- **NON** esiste la notazione super.super per chiamare la classe nonno.

``` Java
class ContatorePreciso extends Contatore
{
	private double val;
	// val = val di ContatorePreciso
	// super.val = val di Contatore
	@Override

	public void inc() {super.inc(); val++;}
	// inc() = metodo di ContatorePreciso
	// super.inc() = metodo di Contatore
}
```

**OVERRIDE**
- Usare @Override per specificare che un attributo/metodo è stato ridefinito.
- Ridefinire un nuovo attributo non è molto utile, può creare solo confusione.
- Ridefinire un nuovo metodo invece è essenziale per avere un comportamento polimorfico.

**CLASSE OBJECT**
La classe Object è una classe che raggruppa tutte le definizioni necessarie ad ogni oggetto. Tutte le classi derivano da Object.

**ESEMPIO EREDITARIETÀ**

``` Java
public class Veicolo // extends Object
{
	private int numeroPosti;
	public Veicolo(int NP) {numeroPosti = NP;}
	public int getNumeroPosti() {return numeroPosti;}
}

public class VeicoloTerrestre extends Veicolo
{
	private int numeroRuote;
	public VeicoloTerrestre(int NP, int NR)
	{super(NP); numeroRuote = NR;}
	public int getNumeroRuote() {return numeroRuote;}
}

public class VeicoloAcquatico extends Veicolo
{
	private long stazza;
	public VeicoloAcquatico(int NP, long S)
	{super(NP), stazza = S;}
	public long getStazza() {return stazza;}
}

public class Esempio3
{
	public static void main(String args[])
	{
		VeicoloTerrestre miaMacchina;
		VeicoloAcquatico miaNave;

		miaMacchina = new VeicoloTerrestre(5, 4);
		System.out.print("La mia macchina ha ");
		System.out.print(miaMacchina.getNumeroPosti() + " posti e ");
		System.out.println(miaMacchina.getNumeroRuote() + " ruote");

		miaNave = new VeicoloAcquatico(10, 10);
		System.out.print("La mia nave ha ");
		System.out.print(miaNave.getNumeroPosti() + " posti e ");
		System.out.println("una stazza di " + miaNave.getStazza());
	}
}

$ java Esempio3
// Stampa:
// La mia macchina ha 5 posti e 4 ruote
// La mia nave ha 10 posti e una stazza di 10
```

**COMPATIBILITÀ TRA CLASSI**
Prendendo esempio la classe del Contatore, un Contatore2 ha tutte le caratteristiche di Contatore
- Contatore2 è un sottotipo di Contatore.
- Se ho bisogno di un Contatore posso usare anche Contatore2 usando solo le caratteristiche di Contatore.

L'ereditarietà serve non solo per riutilizzare codice ma anche per definire una classificazione tra entità e per definire una gerarchia padre-figlio tra le varie classi.

``` Java
public static void main(String args[])
{
	Contatore c1 = new Contatore(3);
	Contatore c2 = new Contatore2();

	c2.dec(); // Si, metodo di Contatore2.
	c1.dec(); // No, non presente nella classe padre.
	c1=c2; // Si, contatore2 è anche contatore.
	c2=c1; // No, c1 è un semplice contatore.
}
```

**POLIMORFISMO**
Il polimorfismo di Java si basa su:
- **BINDING DINAMICO**: Associazione dinamica variabile-oggetto, come tra V e l'oggetto.
- **OPERATION DISPATCHING DINAMICO**: Ricerca dinamica dei metodi tipo il metodo toString().
- **OVERRIDING**: Sovrascrittura dei metodi ereditati, come per il caso del metodo toString().
- **REGOLA DI CONFORMITÀ**: Ad una variabile della classe padre è possibile assegnare un istanza di una qualsiasi classe discendente, come in V = A1/A2.

A tempo di esecuzione verranno eseguiti i metodi della classe di cui l'oggetto è effettiva istanza e a differenza di uno switch-case non dobbiamo sapere in anticipo i tipi da gestire.

**POLIMORFISMO ESEMPIO**

``` Java
public class Veicolo // extends Object
{
	private int numeroPosti;
	public Veicolo(int NP) {numeroPosti = NP;}
	public int getNumeroPosti() {return numeroPosti;}
	public String toString() {return "Veicolo con " + numeroPosti + " posti";}
}

public class Topolino extends Veicolo
{
	public Topolino(int NP) {super(NP);}
	@Override
	public string toString() 
	{return "Sono una Topolino e ho " + getnumeroPosti() + " posti";}
}

public class SeicentoFamiliare extends Veicolo
{
	public SeicentoFamiliare(int NP) {super(NP);}
	@Override
	public string toString()
	{return "Sono una SeicentoFamiliare e ho " + getnumeroPosti() + " posti";}
}

public class Esempio4
{
	public static void main(String args[])
	{
		Veicolo V;
		Topolino A1 = new Topolino(4);
		SeicentoFamiliare A2 = new SeicentoFamiliare(6);

		V = A1;
		System.out.println(V.toString());
		V = A2;
		System.out.println(V.toString());
	}
}

$ java Esempio4
// Stampa:
// Sono una Topolino e ho 4 posti
// Sono una SeicentoFamiliare e ho 6 posti
```

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
	{ this.velocitaMassima = velocitaMassima;
	  this.numeroPosti = numeroPosti;       }

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
- Ridefinire un nuovo attributo non è molto utile, può creare solo confusione.
- Ridefinire un nuovo metodo invece è essenziale per avere un comportamento polimorfico
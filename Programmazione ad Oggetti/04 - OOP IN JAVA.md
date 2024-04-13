**INCAPSULAMENTO**
L'incapsulamento dice che la classe "incapsula" queste caratteristiche:
- Variabili che siano primitive o riferimenti
- Metodi (funzioni)
- Altre classi, creando classi innestate

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
L'ereditarietà serve per definire una classe partendo da classi esistenti.
Per esempio possiamo sfruttare l'ereditarietà in una classe Contatore per aggiungere il decremento. Viene creata una nuova classe che eredita tutti i metodi e gli attributi della classe padre. Può aggiungere attrbuti e metodi, inoltre può modificare i metodi della classe padre.

```                                                                          Java
class Contatore2 extends Contatore
{
	// aggiungo un nuovo metodo mantenendo i metodi della classe Contatore
	public void decremento() { setVal(getVal()-1); }
	// se val non fosse private si poteva fare val--;
}
```

**EREDITARIETÀ IN JAVA**
Esistono due tipi di ereditarietà:
- Ereditarietà singola, si usa la keyword extends. Eredita tutti i metodi e gli attributi e gestisce i metodi non-private che non vengono ridefiniti. Questo si chiama overriding, banalmente vuol dire che si riscrive un metodo/attributo ereditato.
- Ereditarietà monotòna, si possono solo aggiungere membri e non rimuovere. Per i membri ridefiniti, quindi per variabili e metodi della classe padre, si usa la keyword super.

**RELAZIONI TRA CLASSI CON EREDITARIETÀ**
Con l'ereditarietà si avrà una relazione tra classi. Come per il fatto che l'oggetto singolare è un istanza della classe si ha una classe padre (classe base, superclasse) che fa ereditare e la classe figlio (classe derivata, sottoclasse) che eredita.

**COSTRUTTORI EREDITARIETÀ**
La classe figlio NON eredita i costruttori perchè non svolgono funzioni bensì inizializzano attributi. Se non ci sono costruttori si avrà che la classe figlio si limita a chiamare i costruttori della classe padre. Se si vogliono creare degli attributi nella classe figlio occorre inizializzarli con un altro costruttore.

**KEYWORD SUPER**
Serve per specificare che si sta facendo riferimento di un attributo o metodo della classe padre oppure per chiamare un costruttore della classe padre. Non esiste la definizione super.super per indicare la classe nonno.

```                                                                          Java
class ContatorePreciso extends Contatore
{
	private double val; // indica il campo val di ContatorePreciso
	super.val // indica il campo val di Contatore
	@Override

	public void inc() {super.inc(); val++;}
	// inc incrementa val di ContatorePreciso, super.inc() incrementa val di
	// Contatore.

	// Ridefinire le variabili non è tanto utile, mentre ridefinire i
	// metodi serve per avere un comportamento polimorfico.
	// Super permette di riusare codice della classe padre.
}
```

**GERARCHIA JAVA**
Tutte le classi derivano da Object. È una classe radice che raggruppa le definizioni comuni per ogni oggetto.

**ESEMPIO EREDITARIETÀ**

```                                                                          Java
public class Veicolo
{
	private int numeroPosti;

	public Veicolo(int NP) { numeroPosti = NP; } // costruttore
	public int getNumeroPosti() { return numeroPosti; }
}

public class VeicoloTerrestre extends Veicolo
{
	private int numeroRuote;

	public VeicoloTerrestre(int NP, int NR) 
	{ 
		super(NP);
		numeroRuote = NR; 
	}
	
	public int getNumeroRuote() { return numeroRuote; }
}

public class VeicoloAcquatico extends Veicolo
{
	private long stazza;

	public VeicoloAcquatico (int NP, long S)
	{
		super(NP);
		stazza = S;
	}
}
```
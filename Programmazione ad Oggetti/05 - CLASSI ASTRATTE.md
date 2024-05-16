**CLASSI ASTRATTE**
Sono delle classi che contengono solo la definizione dei metodi, quindi **NO** implementazioni. Per creare una classe/metodo astratto va usata la keyword abstract.
- Non servono a creare istanze.
- Definiscono un comportamento comune per le sottoclassi.

**ESEMPIO I**
Prendiamo una classe Automobile ed una Motocicletta. Essendo entrambi di tipo Veicolo hanno caratteristiche comuni (cilindrata, trasporta, si muove...) e ci è utile fattorizzare questi concetti in una superclasse comune.
- Utile sia dal punto di vista progettuale che per l'implementazione.
- Le caratteristiche vengono fattorizzate in una classe astratta Veicolo che **NON** esisterà come istanza nella realtà ma solo come categoria concettuale.

**CARATTERISTICHE CLASSE ASTRATTA**
- Una classe avente anche un singolo metodo abstract è una classe astratta.
- Una classe astratta può anche non avere alcun metodo abstract dichiarato.
- Una sottoclasse di classe astratta sarà anch'essa astratta almeno che non ridefinisce tutti i metodi astratti della classe padre.

**ESEMPIO CLASSE ASTRATTA**

``` Java
public abstract class Veicolo
{
	private String nome;
	private String targa;
	private int cilindrata;
	...

	public abstract String si_muove();
	public abstract String trasporta();
	...
}
```

**COSTRUTTORE**
Anche se non istanziamo una classe astratta può essere utile per istanziare lo stato all'interno della classe attraverso una chiamata di un costruttore della sottoclasse.
- Il costruttore può essere chiamato solo dalle sottoclassi.
  
**CLASSE VEICOLO**
Ogni veicolo ha le seguenti classi:
- si_muove(); definisce l'ambiente in cui il veicolo si muove - abstract.
- trasporta(); definisce cosa trasporta un tipo di veicolo - abstract.
- chi_sei(); definisce il tipo del veicolo - abstract.
- toString(); restituisce una descrizione del veicolo - non-abstract.

``` Java
public abstract class Veicolo
{
	private String nome;
	
	public Veicolo(String s) {nome = s;}
	
	public abstract si_muove();
	public abstract trasporta();
	public abstract chi_sei();
	
	public String toString() 
	{ return nome + ", " + chi_sei() + ", " + "si muove" + si_muove() +
	"e trasporta " + trasporta() };
}
```

Veicolo è una classe astratta, dobbiamo definire delle sottoclassi concrete affinchè ogni metodo abstract sia implementato. Per definire una gerarchia dobbiamo decidere da quale criterio partire per definire le sottoclassi di primo livello. Le nostre scelte sono:
- L'ambiente in cui il nostro veicolo si muove.
- Il tipo di cose trasportate dal nostro veicolo.

Possiamo partire da entrambi i criteri ma scegliamo l'ambiente.
- Abbiamo **veicoli terrestri** e **veicoli acquatici.**
- Non abbiamo finito, avremo ancora classi astratte dato che non abbiamo definito ciò che trasportano.

``` Java
public abstract class VeicoloTerrestre extends Veicolo
{
	public VeicoloTerrestre(String s) {super(s);}

	@Override
	public String si_muove() {return "sulla terraferma";}
	@Override
	public String chi_sei() {return "un veicolo terrestre";}

	// trasporta() rimane astratto
}
```

``` Java
public abstract class VeicoloAcquatico extends Veicolo
{
	public VeicoloAcquatico(String s) {super(s);}
	
	@Override
	public String si_muove() {return "nell'acqua";}
	@Override
	public String chi_sei() {return "un veicolo acquatico";}
	
	// trasporta() rimane astratto
}
```

Dopo aver definito il primo criterio (ambiente) possiamo procedere a definire il secondo. Abbiamo che i veicoli terrestri si distinguono in Automobili e Camion.
- Avremo delle classi concrete dato che abbiamo definito tutti i metodi abstract.

``` Java
public class Automobile extends VeicoloTerrestre
{
	public Automobile(String s) {super(s);}
	
	@Override
	public String trasporta() {return "persone";}
	@Override
	public String chi_sei() {return "una auto";}
}
```

``` Java
public class Camion extends VeicoloTerrestre
{
	public Camion(String s) {super(s);}
	
	@Override
	public String trasporta() {return "merci";}
	@Override
	public String chi_sei() {return "un camion";}
}
```

``` Java
public class MondoVeicoli
{
	public static void main(String args[])
	{
		Automobile a = new Automobile("Volo AA111BB");
		Camion c = new Camion("Fiat ZZ999XX");
		System.out.println(c.toString());
		System.out.println(a.toString()); 
		
		// VeicoloTerrestre v = new VeicoloTerrestre()
		// NO! Non possiamo istanziare classi astratte
	}
}

// Stampa:
// Fiat ZZ999XX, un camion, si muove sulla terraferma e trasporta merci
// Volvo AA111BB, una auto, si muove sulla terraferma e trasporta persone
```

**ARRAY DI VEICOLI**
Non possiamo istanziare classi astratte però possiamo creare array di tipo classe astratta. Ad ogni cella possiamo assegnare un oggetto della sottoclasse.
- In questo esempio il polimorfismo agisce nel for; ad ogni elemento dell'array toString() ritornerà i dati dell'oggetto dato che abbiamo ridefinito il metodo per ogni istanza di classe.

``` Java
public class Città
{
	public static void main(String args[])
	{
		Veicolo v[] = new Veicolo[4];
		
		v[0] = new Camion("Fiat ZZ999XX");
		v[1] = new Automobile("Volvo AA111BB");
		v[2] = new Camion ("Mercedes MM123NN");
		v[3] = new Automobile ("Volkswagen GG777CC");

		for (int i = 0; i<4; i++)
			System.out.println(v[i].toString());
	}
}
```

**EREDITARIETÀ MULTIPLA**
Ci serve per poter unire i concetti di ambiente e trasporto. È uno strumento molto potente ma molto difficile da gestire. Inesistente in Java, le interfacce svolgono un ruolo simile.
- Se partiamo da ambiente allora dividiamo il concetto di trasporto tra le varie classi.
- Se partiamo da trasporto allora dividiamo il concetto di ambiente tra le varie classi.

**INTERFACCIA**
Sono un insieme di **DICHIARAZIONI** di metodi. Per creare un interfaccia usiamo keyword interface.
- Una classe implementa un interfaccia se definisce un corpo per ogni metodo dell'interfaccia. Si usa la keyword implements.
- Ereditarietà multipla per le interfacce, quindi non ci sono conflitti.
- Una classe può implementare zero o più interfacce.

``` Java
// Definizione interfaccia
public interface VeicoloPersone
{
	public void viaggia();
	...
}

// Ereditarietà multipla
public interface AutoDiplomatica extends VeicoloPersone, AccessoDiplomatico
{
	...
}

// Esempio di uso
public class Automobile extends VeicoloTerrestre implements VeicoloPersone
{
	@Override
	public void viaggia()
	// {corpo del metodo}
}
```

**ARRAY DI INTERFACCE**
Possiamo creare delle variabili di tipo interfaccia. Ad una variabile di tipo interfaccia possiamo assegnare un oggetto di una classe che implementa un interfaccia.

``` Java
public class Esempio5
{
	public static void main(String args[])
	{
		VeicoloPersone a[] = new VeicoloPersone[20];
		a[1] = new Automobile();
		a[1].viaggia;
		...
	}
}
```

**INTERFACCE E METODOLOGIA**
Usando le interfacce è possibile definire quali criteri implementare attraverso l'uso di interfacce e quali attraverso l'uso delle classi.
- **INTERFACCE**: Aspetto progettuale.
- **CLASSI**: Aspetto implementativo.
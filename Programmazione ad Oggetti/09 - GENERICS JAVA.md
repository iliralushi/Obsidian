**TYPE-SAFETY**
Il type-safety è un problema. Dobbiamo garantire la coerenza dei dati a runtime di una collezione o struttura dati.

**CONFORMITÀ**
Possiamo usare la conformità per usare sottoclassi come fossero classi base. Abbiamo dei vantaggi, come poter usare gli stessi algoritmi per ogni sottoclasse, però potrebbe creare problemi di type-safety.

**ESEMPIO CONCRETO DI PROBLEMA TYPE-SAFETY**
Dobbiamo implementare un archivio di studenti e professori, essi non si devono mischiare.
Dato che sono entrambe persone possiamo creare una gerarchia.

``` Java
import java.util.Vector;

public class Persona
{
	private String nome, cognome;
	private int età;

	public Persona(String nome, String cognome, int età)
	{
		this.nome = nome;
		this.cognome = cognome;
		this.età = età;
	}

	public String toString()
	{
		return nome + " " + cognome + " " + età;
	}
}

public class Professore extends Persona
{
	private String materia;

	public Professore(String materia)
	{
		super(nome, cognome, età);
		this.materia = materia;
	}

	public String getMateria()
	{
		return materia;
	}
}

public class Studente extends Persona
{
	private int matricola;

	public Studente(int matricola)
	{
		super(nome, cognome, età);
		this.matricola = matricola;
	}

	return matricola;
}

public class Archivio1
{
	private Vector persone;

	public Archivio1()
	{
		persone = new Vector(10);
	}

	public void aggiungi(Persona p)
	{
		persone.add(p);
	}

	public void rimuovi(Persona p)
	{
		persone.remove(p);
	}

	public Persona get(int index)
	{
		return (Persona)persone.get(index);
	}

	public int size()
	{
		return persone.size();
	}
}
```

La classe Archivio1 gestisce con **UNA** sola logica tutti i tipi di persona, quindi non abbiamo modo di sapere se stiamo aggiungendo uno studente oppure un professore, rendendo il codice type-unsafety.

**GENERICS**
I generics sono i tipi parametrizzati. Una classe che sfrutta i generics non ha un tipo definito, lo riceve a tempo di istanziazione, quindi possiamo sfruttare le gerarchie usando gli stessi algoritmi per ogni sottoclasse mantenendo una coerenza dei tipi di dati.

I generics non impediscono di usare le gerarchie, limitano soltanto potenziali errori di 
type-unsafety.

``` Java
// Riprendendo l'esempio precedente:

public class Archivio2<E>
{
	private Vector persone;

	public Archivio2
	{
		persone = new Vector(10);
	}

	public void aggiungi(E p)
	{
		persone.add(p);
	}

	public void rimuovi(E p)
	{
		persone.remove(p);
	}

	public E get(int index)
	{
		return (E)persone.get(index);
	}

	public int size()
	{
		return persone.size();
	}
}

public class Main
{
	public static void main(String args[])
	{
		Archivio2<Professore> archivio_prof = new Archivio2<Professore>();
		Archivio2<Studente> archivio_stud = new Archivio2<Studente>();
		Archivio2<Persona> archivio_per = new Archivio2<Persona>();

		archivio_prof.aggiungi(prof1);
		archivio_prof.aggiungi(prof2);
		archivio_prof.aggiung(stud1); // ERRORE!
		...
	}
}
```

**WILDCARDS**
I generics ammette l'uso "?" come wildcard speciale. 
- Per esempio, la dicitura < ? extends type > indica tutti i tipi che ereditano da type.
- Non è possibile usare classi diverse rispetto alla classe Persona.

**EREDITARE CLASSE CON GENERICS**

**CLASSI WRAPPER**
Le classi wrapper servono per istanziare oggetti di tipo primitivo, dato che nativamente non sono oggetti.

**AUTOBOXING/OUTBOXING**
Invece di usare le classi wrapper possiamo usare direttamente uno scalare in un contesto di oggetto, lasciando il compilatore a gestire il wrapping del tipo.

``` Java
Vector v = new Vector(10);

for(int i = 0; i<5; i++)
{
	v.add(i);
	v.add(((float)i) * 2.5);
}

for(int i = 0; i<v.size(); i++)
	System.out.println(i + "=" + v.elementAt(i));


/* Output
0 = 0
1 = 0.0
2 = 1
3 = 2.5
4 = 2
5 = 5.0
6 = 3
7 = 7.5
8 = 4
9 = 10.0
*/
```

**FOREACH**
Un ciclo foreach è diverso dal for perchè permette di scorrere tutti gli elementi di una struttura dati gestendo automaticamente:
- Incremento di eventuali indici.
- Assegnamento della variabile di ciclo all'elemento successivo.

Il foreach non può essere usato come ciclo di assegnamento, ma solo come ciclo di estrazione, quindi per stampare.
- Non si è a conoscenza della posizione dell'elemento corrente.
- Riduce il rischio di errori banali come ArrayOutOfBounds.
- Il foreach funziona su strutture dati che implementano l'interfaccia Iterable.

``` Java
// SINTASSI:
// for (variable_type variable_name : list)

import java.util.Vector;

public class foreach2
{
	public static void main(String argv[])
	{
		Vector v = new Vector(10);

		for (int i = 0; i<10; i++)
			v.add("String n." + i);

		for (Object s: v)
			System.out.println(s);

		// Per i vector si usa il tipo Object perchè il vector
		// memorizza e restituisce Object. Il foreach non svolge
		// cast automatici, si possono usare generics per quello.
	}
}
```

**VARARGS**
Possiamo definire metodi che accettano un numero variabile di argomenti.
- Gli argomenti devono avere tutti lo stesso tipo (al limite Object).
- La sintassi prevede l'uso dell'operatore . . 

``` Java
public class varargs
{
	public void mvar(String...pars)
	{
		for(String s : pars)
			System.out.println(s);
	}

	public static void main(String argv[])
	{
		varargs v = new varargs();
		v.mvar("ALFA", "BETA", "GAMMA");
	}
}
```

**OVERLOAD**
Possiamo sovraccaricare un metodo varargs con una lista di argomenti dello stesso tipo. Verrà eseguito il primo metodo che richiama perfettamente i parametri del prototipo.

**ENUM**
La keyword enum permette di definire enumerazioni. Un utilizzo classico è la lista static di valori. Le enumerazioni sono trattate come oggetti.

``` Java
public class EventType
{
	public static enum type
	{
		OPEN,
		CLOSE,
		EXIT,
	} ;
}

public class Main1
{
	public void fireEvent(EventType.type event)
	{
		System.out.println("L'evento ricevuto è");

		if (event == EventType.type.OPEN)
			System.out.println("APERTURA");
		else
			if (event == EventType.type.CLOSE)
				System.out.println("CHIUSURA");
		else
			if (event == EventType.type.EXIT)
				System.out.println("USCITA");
	}

	public static void main(String args[])
	{
		Main1 m = new Main1();
		m.fireEvent(EventType.type.OPEN);
		m.fireEvent(EventType.type.CLOSE);
		m.fireEvent(EventType.type.USCITA);
	}
}
```

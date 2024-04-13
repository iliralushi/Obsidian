**PROGRAMMAZIONE AD OGGETTI**
Per i programmi di medie/grandi dimensioni abbiamo visto che è la soluzione migliore.
Come paradigma ha nativamente un alto livello di astrazione, una maggior protezione dei dati e un facile riutilizzo del codice già scritto grazie al concetto di entità in OOP.

```                                                                            Java
ADTDef Contatore 
{
	// definizione attributi
	int val;

	// definizione operazioni
	void setVal(int newVal) { val = newVal; }
	void inc() { val++; }
	int getVal() { return val; }
}

int main()
{
	Contatore cont; // oggetto 1
	Contatore cont2; // oggetto 2
	cont.setVal(0); cont2.setVal(1);
	cont.inc(); // cont = 1
	cont2.inc(); // cont2 = 2, posso invocare la stessa operazione senza
	// intaccare l'altro contatore

	cont++; // non possibile, non è un intero cont, è possibile solo citando
	// il campo cont.val
}
```

**PROTEZIONE DEI DATI**
Il controllo è incluso nell'entità. La protezione dei dati impone alle operazioni di accedere ai nostri dati solo attraverso i metodi dell'astrazione di dato.

**OGGETTI**
Sono entità che incapsulano dati e codice. È composto da uno stato e dall'interfaccia, unisce i dati e le operazioni contenute sull'astrazione di dato. È un tipo di dato astratto (ADT).

```                                                                          Java
Contatore cont; // questo è un oggetto
```

**STATO**
È ciò che compone la parte dei dati. Può essere composto da variabili oppure oggetti ed è nascosto dall'esterno.

**INTERFACCIA**
È ciò che compone la parte delle operazioni. Possono agire dall'esterno sullo stato. Le operazioni vengono chiamate anche metodi.

**CLASSI**
Oggetti diversi possono avere la stessa struttura (incapsulamento).
Una classe descrive la struttura comune per ogni istanza di oggetto di quella classe. I valori possono essere diversi. 

**CLASSI E OGGETTI**
Le classi vengono definite staticamente dal programmatore, gli oggetti vengono creati dinamicamente. Il client richiede il servizio e conosce il server (class), il server mette a disposizione il servizio ma non conosce il client (oggetto).

**FUNZIONAMENTO DI OGGETTI**
Non viene chiamata una funzione che agisce su un entità ma chiede all'entità di svolgere un servizio.

![[Differenza Funzioni tra OOP e Procedurale.png]]

**CLASSE**
- Classificazione: Insiemi di oggetti che possono condividere lo stesso comportamento.
- Classe: Entità che raggruppa lo stato e l'interfaccia. Essa determina il comportamento dell'oggetto che deriva da una classe.
- Oggetto: Istanza di una classe. Forte dipendenza tra l'oggetto e la classe.

**COMPOSIZIONE OGGETTO**
- Variabili di istanza: Variabili di quell'oggetto in particolare.
- Variabili di classe: Variabili condivise da tutte le istanze di una particolare classe.
- Metodi di classe/istanza.


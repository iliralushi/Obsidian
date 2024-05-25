**QUAL È UNA SOLUZIONE POSSIBILE?**
Usare un paradigma di programmazione che mette a disposizione costrutti che permettono di:
- Astrarre maggiormente il software.
- Riesce a proteggere gli attributi meglio.
- Permette di far riutilizzare codice in modo intelligente.
- Avere un entità unica dove raggruppare attributi ed operazioni.

**ESEMPIO: CONTATORE**
Questo paradigma di programmazione ci permette di fare tutto ciò che abbiamo chiesto con i limiti necessari come:
- Non poter fare operazioni al di fuori di quelle dichiarate.
- Non poter accedere ai dati dall'esterno tranne dalle operazioni dell'entità.

``` C++
ADTdef Contatore // contatore definito tramite un costrutto
{
	int val; // attributi non accessibili

	void setVal(int newVal) {val = newVal;} // operazioni
	void inc() {val++;}
	int getVal() {return val;}
}

main()
{ 
	Contatore cont, cont2; // istanzio due oggetti contatori
	cont.setVal(0); cont2.setVal(1);
	cont.inc(); // invoco operazioni
	cont2.inc(); // non intacco il contatore prima, sono separati

	if(cont.getVal() > MAX) 
	{
		// istruzioni
	}
}

cont++; // errore, cont è di tipo Contatore, non int
cont.val = cont*345; cont.val++; // errore, non possiamo accederci
```

**ESEMPIO: PERSONA**
``` C++
ADTdef Persona 
{

	int età; // attributi

	void setEtà(int nuovaEtà)
	{
		if (nuovaEtà >=0)
			età = nuovaEtà;
		else
			ERRORE;
	}
}

main()
{
	Persona p;
	p.setEtà(2); // corretto
	p.setEtà(-2); // errore, non rispetta la condizione dell'if
}
```

**PROTEZIONE DEI DATI**
In questo paradigma di programmazione il controllo è incluso nell'entità, viene codificato li una volta per tutte. La protezione dei dati impone di accedere agli attributi dell'entità solo attraverso le varie funzioni.

**OGGETTI**
Nell'esempio del contatore cont1 e cont2 sono oggetti che incapsulano le proprietà dell'entità, quindi gli attributi e le operazioni. È un entità software che:
- Rappresenta un concetto reale.
- È composto da stato ed interfaccia.
- È un entità che lega attributi ed operazioni.
- È un astrazione di dato, quindi istanza di un tipo di dato astratto.

**STATO**
È nascosto all'esterno ed è composto da una serie di attributi (variabili).
Può anche essere composto da oggetti.

**INTERFACCIA**
È costituita dalle operazioni (metodi) che possono essere invocate dall'esterno.
I metodi servono per agire sullo stato e sono gli unici che possono accederci.

**CLASSI**
È una sorta di stampino per creare oggetti. 
Le classi descrivono la struttura che è comune per più oggetti in:
- Termini di attributi ed operazioni.
- I valori dei singoli oggetti possono essere diversi.

**RELAZIONE TRA CLASSI ED OGGETTI**
Le classi sono definite staticamente dal programmatore, mentre gli oggetti sono definiti dinamicamente dal programma. Si ha una specie di modello client-server dove l'oggetto è il server che mette a disposizione il servizio e la classe è il client, ovvero richiede il servizio.
- Si ha uno spostamento del fuoco; **NON** viene invocata una funzione che agisce su un entità **MA** si chiede all'entità di svolgere un servizio.

**CLASSI II**
- **CLASSIFICAZIONE**: Insieme di oggetti che possono condividere lo stesso comportamento.
- **CLASSE**: Entità che raggruppa attributi ed operazioni, caratterizzano l'oggetto.
- **OGGETTO**: Istanza di una classe.
- Forte dipendenza tra oggetto e classe, perdura per tutta la durata dell'istanza.

**OGGETTI II**
- **VARIABILI DI ISTANZA**: Ogni istanza ne possiede una copia ed è legata all'esistenza dell'oggetto stesso.
- **VARIABILI DI CLASSE**: Sono condivise da tutte le istanze di classe ed esistono indipendentemente dall'esistenza di istanze.







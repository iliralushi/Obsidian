**OOP**
Per software di complessità elevata è la soluzione migliore. Offre un livello alto di astrazione, una maggiore protezione dei dati e un facile riutilizzo del codice già scritto. Usa entità che lega dati e operazioni assieme. Gli esempi riportati sotto non permettono di fare operazioni illegali.

```                                                                          Java
ADTDef Contatore {
	// attributi non accessibili
	int val;
	// operazioni ammesse
	void setVal(int newVal) {val = newVal;}
	void inc() {val++;}
	int getVal() {return val;}
}
```

```                                                                          Java
ADTDef Persona {
	// attributi non accessibili
	int età; // deve essere >= 0
	// operazioni ammesse
	void setEtà(int nuovaEtà)
	{
		if (nuovaEtà >= 0)
			età = nuovaEtà;
		else
			ERRORE;
	}
}

Persona p;
p.setEtà(21); // OK!
p.setEtà(-2); // Errore, l'età di p rimane invariata.
```

**PROTEZIONE DEI DATI**
Il controllo delle variabili è incluso nelle entità e viene codificato li, altrimenti si dovrebbe fare il controllo per ogni istanza di entità. Inoltre il controllo può essere modificato senza dover cambiare il resto del software.

**OGGETTI**
È un entità software che modella oggetti reali, incapsula dati e codice. È composto da stato ed interfaccia, unisce dati assieme ed è un istanza di ADT.

```                                                                          Java
Contatore cont; // oggetto
```

**STATO**
Contiene informazioni sullo stato dell'oggetto, è nascosto dall'esterno ed è composto da un insieme di attributi (variabili). Può anche essere composto da oggetti.

**INTERFACCIA**
L'interfaccia è composta dalle operazioni che possono accedere agli attributi dall'esterno. Queste operazioni si chiamano metodi (funzioni). Solo i metodi di una certa classe possono agire sullo stato.

**CLASSI**
Gli oggetti possono avere struttura uguale.
Una classe descrive la struttura comune a più oggetti in termini di attributi e metodi, i valori dei singoli oggetti possono essere diversi. È un ADT e i suoi dati e le operazioni disponibili derivano dalla classe.

**CLASSI E OGGETTI**
Le classi vengono definite staticamente dal programmatore, gli oggetti sono dinamicamente creati a tempo di runtime. Gli oggetti possono essere considerati come server che mettono a disposizione servizi. Ogni operazione invocabile dall'esterno è considerato come un servizio messo in atto dall'oggetto.

**COME UN OGGETTO VIENE MODIFICATO**
NON viene chiamata una funzione che agisce su una determinata entità MA viene chiesto all'entità di svolgere un servizio.

![[Differenza Funzioni tra OOP e Procedurale.png]]

**IN BREVE...**
- Classificazione: Insiemi di oggetti che possono condividere lo stesso comportamento.
- Classe: Entità che raggruppa lo stato e le definizioni. Essa determina cosa può fare un oggetto.
- Oggetto: Istanza di una classe.

**CLASSE - OGGETTO**
C'è una forte dipendenza tra classe ed oggetto, la relazione tra di loro dura per tutta la vita del programma, l'istanza ritrova nella classe il codice da eseguire se richiesto.
- Variabili di istanza: Ogni istanza ne possiede una copia, l'esistenza è legata all'esistenza dell'istanza.
- Variabili di classe: Sono condivise da tutte le istanze, esistono indipendentemente dall'esistenza di un oggetto.
- Metodi di classe/istanza.

**NOTA SU COME FUNZIONA LA OOP**
- Gli oggetti vengono creati quando servono dinamicamente, non si ha una dichiarazione generale di tutte le variabili come in C.
- Gli oggetti devono conoscersi in qualche modo. il client deve conoscere il server siccome richiede il servizio. Lo si fa attraverso dei riferimenti.
- Un oggetto che crea un altro oggetto conosce il suo indirizzo.
- Un oggetto che non ha creato un altro oggetto deve conoscere il suo indirizzo per interagire.


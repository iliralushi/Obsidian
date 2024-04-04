**OOP**
Per programmi di complessità elevata è la soluzione migliore. Offre un livello alto di astrazione, una maggiore protezione dei dati e un facile riutilizzo del codice già scritto. Usa entità che lega dati e operazioni assieme. Gli esempi riportati sotto non permettono di fare operazioni illegali.

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
```

Se provo a fare un operazione illegale del tipo setEtà(-2) mi ritorna errore, non rendendolo possibile, se ho definito la mia età prima essa rimane quella.

**PROTEZIONE DEI DATI**
Il controllo delle variabili è incluso nelle entità, non farà il controllo ogni volta che si modifica il valore della variabile. Inoltre il controllo può essere modificato senza dover cambiare il resto del software.

**OGGETTI**
```                                                                          Java
	Contatore cont;
```
"cont" è un oggetto, quindi un entità che incapsula dati e operazioni. È un entità software che modella oggetti reali, è composto da stato ed interfaccia, unisce dati assieme ed è un ADT.

**STATO**
Contiene informazioni sullo stato dell'oggetto, è nascosto dall'esterno ed è composto da un insieme di attributi (variabili). Può anche essere composto da oggetti.

**INTERFACCIA**
L'interfaccia è composta dalle operazioni che possono accedere agli attributi dall'esterno. Queste operazioni si chiamano metodi (funzioni). Solo i metodi di una certa classe possono agire sullo stato.

**CLASSI**
Gli oggetti possono avere struttura uguale.
Una classe descrive la struttura comune a più oggetti in termini di attributi e metodi, i valori dei singoli oggetti possono essere diversi. È un ADT e "serve per creare oggetti".

**CLASSI E OGGETTI**
Le classi vengono definite staticamente dal programmatore, gli oggetti sono dinamicamente creati a tempo di runtime. Gli oggetti possono essere considerati come server che mettono a disposizione servizi.

**MODELLO CLIENT-SERVER**
NON chiama una funzione che agisce su una determinata entità MA chiedi all'entità di svolgere un servizio. 
- Client: Richiede il servizio, conosce il server, NON possono accedere direttamente ai vari metodi.
- Server: Fornisce il servizio, NON conosce il client.
- 
![[Differenza Funzioni tra OOP e Procedurale.png]]

**CLASSE**
- Classificazione: Insiemi di oggetti che possono condividere lo stesso comportamento.
- Classe: Entità descrittiva che raggruppa tutti gli attributi e i metodi che caratterizzano un insieme di oggetti.
- Oggetto: Istanza di una classe.

**OGGETTO DI UNA CLASSE**
C'è una forte dipendenza tra classe ed oggetto, la relazione tra di loro perdura per tutta la vita del programma, l'istanza ritrova nella classe il codice da eseguire se richiesto.
- Variabili di istanza: Ogni istanza ne possiede una copia, l'esistenza è legata all'esistenza dell'istanza.
- Variabili di classe: Sono condivise da tutte le istanze, esistono indipendentemente dall'esistenza di un oggetto.
- Metodi di classe/istanza.

**INTRODUZIONE CONCETTI BASE OOP**
- Incapsulamento: Ogni oggetto incapsula dati ed operazioni, ogni oggetto protegge i suoi dati dall'esterno. Solo l'oggetto può manipolare i dati che contiene.
- Ereditarietà: Una classe può derivare da un altra classe, estendendola e specializzandola. La classe figlia eredita gli attributi e i metodi dalla classe padre. La classe figlia aggiunge i propri attributi ed istanze. È molto utile per riscrivere codice in modo efficiente.
- Polimorfismo: Alla stessa richiesta di operazione è possibile che possano corrispondere a comportamenti diversi.


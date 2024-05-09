**COME DEV'ESSERE UN SOFTWARE**
- **PROTETTO**: Per evitare che parti di programma errate influiscano su parti corrette.
- **RIUSABILE**: Per evitare di dover riscrivere codice ogni volta.
- **DOCUMENTATO**: Per far capire a chi deve vedere il codice sorgente cosa fa il programma.
- **MODULARE**: Per poter dividere le funzionalità del programma e gestirle separatamente.
- **ESTENDIBILE**: Per aggiungere solo ciò che manca al software scritto.

**PROGRAMMAZIONE TRADIZIONALE**
La programmazione tradizionale è limitata e non riesce a rispettare i punti descritti sopra. Diventa quasi impossibile mantenere un programma di grandi dimensioni proprio per come funziona la programmazione tradizionale.

**PROGRAMMAZIONE OOP**
Dato che la programmazione tradizionale è limitata abbiamo bisogno di un paradigma che:
- **PROGETTO**: Permetta di pensare al software come entità ben definite e complesse.
- **IMPLEMENTAZIONE**: Permetta di identificare le funzioni che agiscono su determinati dati e di proteggerle dalle altre funzioni.

**ASTRAZIONE DI DATO**
Una astrazione di dato è un entità astratta che è definita da:
- **ATTRIBUTI**: Che caratterizzano l'entità. Non sono accessibili dall'esterno.
- **OPERAZIONI**: Che specificano il funzionamento dell'entità. Sono accessibili dall'esterno ed accedono agli attributi della stessa entità.

I vantaggi dell'astrazione di dato sono:
- Agevolano la modularità del programma unendo attributi ed operazioni.
- Favorisce il controllo sull'integrità dei dati.
- Favorisce la creazione di componenti autonomi e validati.

**TIPO DI DATO ASTRATTO (ADT)**
È simile all'astrazione di dato però non lo è esattamente. È un tipo di dato da cui si possono derivare entità con la stessa struttura in termini di attributi ed operazioni.

**ESEMPIO: CONTATORE**
Un contatore è un entità che conta, quindi come attributo avrà un valore che memorizza il numero e come operazioni avrà la sua definizione, l'incremento e la lettura. Il C non permette di creare un astrazione di dato in modo semplice, quindi è possibile fare operazioni illegali come l'ultima.

``` C++
// Definizione
int cont = 0;

// Incremento
cont++;

// Lettura
if (cont == 10) { cout << cont; }

// Però, possiamo fare anche:
cont--;
```

**ESEMPIO: STUDENTE**
Uno studente è un entità che rappresenta i dati di uno studente e dell'esame che sostiene. In C se dichiariamo l'entità in questo modo possiamo accedere ai dati interni di studente, inoltre possiamo modificare il voto senza che il compilatore ci dia errore, cosa ovviamente sbagliata.

``` C++
// Astrazione di dato
typedef struct Studente 
{
	char nome[20];
	char cognome[20];
	int matricola;
	int esami_dati;
	
	struct esami[29] 
	{
		char nome[20];
		int voto;
	}
}

// Operazioni
void nuovo_esame_dato(Studente s, char* nome_esame, int voto_preso)
{
	strcpy(s.esami[s.esami_dati].nome,nome_esame);
	s.esami[s.esami_dati++].voto = voto_preso;
}

// Main
int main()
{
	Studente s1, s2;
	s1.nome = "Mario"; s1.cognome = "Rossi";
	nuovo_esame_dato(s1, "Sistemi Operativi", 18);
	s1.esami[4].voto++;
}
```

**SCOMPOSIZIONE DI UN PROGRAMMA C IN FILE**
È possibile farlo usando i moduli di C, ogni file può rappresentare un entità oppure un modulo del nostro software. Questo porta solo vantaggi, ci permette di dividere il software in più parti.

**PROTEZIONE DEI DATI IN C**
Per proteggere i dati in C possiamo sfruttare le classi di memorizzazione che specificano il tempo di vita e di visibilità di un entità, quindi attributo o operazione. Sfruttiamo il fatto che le variabili statiche sono visibili solo nel file in cui stiamo operando. Le classi di memorizzazione sono 4:
- Auto, register, static, extern.

**ESEMPIO: CONTATORE II**
Usando un astrazione di dato:
- **PRO**: Siamo riusciti a creare un entità contatore protetta, quindi gli attributi non sono accessibili dall'esterno e le operazioni accedono solo agli attributi della loro entità.
- **CONTRO**: Riusciamo a creare un solo tipo di dato astratto contatore.

Usando un tipo di dato astratto:
- **PRO**: Possiamo creare più istanze della nostra entità contatore.
- **CONTRO**: Possiamo tranquillamente modificare i nostri attributi perchè abbiamo libero accesso. Inoltre c'è il rischio di usare oggetti non inizializzati.

Oltre a questi problemi, se noi volessimo estendere il nostro codice aggiungendo il decremento le nostre opzioni sono tutte sub-ottimali:
- Modificare il codice porta il rischio di fare errori, inoltre introduce problemi per le applicazioni che usano contatore senza decremento.
- Riscrivere il codice è una perdita di tempo.
- Scrivere una nuova entità ci permette di poter accedere a dati a cui non dovremmo.
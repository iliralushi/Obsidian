**PERCHÈ USARE LA PROGRAMMAZIONE AD OGGETTI**
La programmazione ad oggetti supera i limiti della programmazione tradizionale, offrendo un paradigma di programmazione che permette di proteggere i dati, riusare codice in modo più intelligente, essere molto più mantenibile rispetto ad un paradigma non-OOP e astrarre ad ad altissimo livello.
- A livello di progetto possiamo pensare al nostro software come una serie di entità.
- A livello di implementazione possiamo identificare le funzioni che agiscono sulle entità e proteggerle dalle altre funzioni.

![[OOP.png]]

**ASTRAZIONE DI DATO**
Una astrazione di dato è un entità astratta che modella un entità del mondo reale. È definita da attributi (dati) e operazioni (funzioni). Tipicamente gli attributi non sono accessibili dall'esterno mentre le operazioni si e possono accedere agli attributi dell'entità stessa (in modo controllato).
- Agevola la modularità accoppiando dati e funzioni.
- Favorisce il controllo sull'integrità dei dati.
- Favorisce la creazione di componenti "autonomi" e validati.

**ABSTRACT DATA TYPE**
Un abstract data type è simile all'astrazione di dato però non è un entità, bensì un tipo da cui puoi derivare entità concrete che hanno tutte la stessa struttura in termini di attributi e operazioni.

```                                                                     c++ 
// esempio
typedef struct Studente {
char nome[20];
char cognome[20];
int matricola;
int esami_dati;
}

Studente s1; // ADT
```

**ASTRAZIONI DI DATO IN C**
Prendiamo C, un linguaggio tradizionale. Possiamo scomporre il nostro software in vari file utilizzando i moduli, ogni file rappresenta un entità. Per proteggere i dati invece possiamo sfruttare le classi di memorizzazioni che indicano il tipo di area di memoria in cui un entità viene memorizzata. Esse sono auto, register, static, extern.

**LIMITI DELLA PROGRAMMAZIONE TRADIZIONALE**
Un linguaggio tradizionale non è ottimale perchè per poter proteggere i dati in modo completo dobbiamo fare uso di casting e puntatori, inoltre se vogliamo riusare il codice dobbiamo per forza riscriverlo, perdendo efficienza e semplicità.

Prendendo l'esempio di un contatore:
- Usando un astrazione di dato abbiamo che il nostro contatore è protetto e svolge le operazioni che abbiamo definito, però possiamo definire una sola istanza di contatore per tutto il nostro programma.
- Usando un ADT abbiamo che possiamo definire più istanze di contatore però non sono protette, inoltre usiamo puntatori che sono pesanti.
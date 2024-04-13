**COSA DEVE FARE UN LINGUAGGIO DI PROGRAMMAZIONE**
Siccome le esigenze e le aspettative del software crescono di giorno in giorno, serve un paradigma di programmazione che permette di gestire con facilità programmi di medie e grandi dimensioni, inoltre il nostro software dev'essere protetto, riusabile, documentato, modulare ed estendibile.
Questo è ciò che offre la OOP a differenza della programmazione tradizionale.

![[OOP.png]]

**PARADIGMA OOP**
- A livello di progetto deve pensare il progetto come una serie di entità ben definite e complesse.
- A livello di implementazione deve identificare le funzioni che agiscono sui dati e proteggerli da altre funzioni.

**ASTRAZIONE DI DATO**
È un entità astratta che modella i dati del mondo reale. È definita da attributi e metodi.
Gli attributi tipicamente non sono accessibili dall'esterno mentre i metodi si, e accedono agli attributi dell'entità stessa.
- Questa aiuta a modulare il programma e proteggere i dati che vogliamo proteggere.

**ABSTRACT DATA TYPE**
Un ADT è simile ad un astrazione di dato. Non è un entità ma è un tipo di dato da cui possiamo derivare entità concrete che avranno la struttura della nostra astrazione di dato.

```                                                                            C++ 
// esempio
typedef struct Studente { // astrazione di dato
char nome[20];
char cognome[20];
int matricola;
int esami_dati;
}

Studente s1; // ADT
```

**PROBLEMA PROGRAMMAZIONE TRADIZIONALE**
Nella programmazione tradizionale non agiamo sulle entità, ma agiamo sui tipi di dato.
Questo non ci permette di proteggere i nostri dati dall'esterno.
- In C possiamo prendere un contatore e decrementarlo anche se non è pianificato.

**ASTRAZIONI DI DATO IN LINGUAGGI TRADIZIONALI**
Per poter fare ciò dobbiamo fare due cose; scomporre il software in entità e proteggere i dati.
- Per scomporre il software possiamo dividere il nostro programma in moduli.
- Per proteggere i nostri dati possiamo sfruttare le classi di memorizzazioni, che indicano l'area di memoria in cui un entità viene memorizzata e definiscono tempo di vita e visibiltà. Questo vale sia per le variabili che le funzioni e sono 4; auto, register, static, extern.

**LIMITI DELLA PROGRAMMAZIONE TRADIZIONALE**
- Usando un astrazione di dato abbiamo che i nostri dati sono protetti, però è possibile avere una sola istanza di oggetto.
- Usando un ADT abbiamo che possiamo creare infinite istanze di oggetto, però possiamo accedere ai dati all'esterno.
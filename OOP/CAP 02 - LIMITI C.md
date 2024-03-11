Al passare del tempo un software è diventato sempre più complesso. Deve essere **protetto, riusabile, documentato, modulare, estendibile.** 

La programmazione funzionale non è adatta per creare questo tipo di software perchè è difficile proteggere tutti i dati, è difficile da mantenere e non è estendibile. Inoltre per i programmi di grande dimensione non è per niente ottimale per due grossi motivi:
- Un dato è usabile globalmente quando in realtà dovrebbe essere utilizzabile solo da un entità e le sue funzioni.
- Trovare errori nel codice diventa praticamente impossibile.
  
Nasce così un nuovo approccio che:
- A livello di **progetto** permette di pensare al software in termini di **entità**.
- A livello di **implementazione** permette solo alle funzioni che abbiamo scelto di impattare su certi dati, proteggendo i dati da altre funzioni.

Un **astrazione di dato** è un entità astratta che è definita da:
- **Attributi**, sono i nostri dati.
- **Operazioni**, esprimono cosa possiamo fare con gli attributi.

I vantaggi sono:
- Agevola la modularità del programma. Si ha un programma meno complesso.
- Protegge i dati. In questo modo un operazione accede solo ai dati con cui dovrebbe.
- Minimizza la distanza concettuale tra problema e risoluzione.

Il **tipo di dato astratto** è un concetto simile. Non è un entità di per sè ma è un tipo che deriva entità in modo tale che l'ADT ha le stesse funzionalità dell'entità derivata.

Supponiamo di avere un entità studente.
- Attributi: Nome, cognome, indirizzo, numero di matricola...
- Operazioni: Leggere informazioni, aggiornare l'anno scolastico.
Certe operazioni **NON** dovrebbero essere ammesse, come la modifica di un voto.
Se proviamo a creare questa entità in C abbiamo:

``` C++
typedef struct Studente
{
char nome[20];
char cognome[20];
int matricola;
int num_esami_dati;
struct esami[29]; char nome[20]; int voto;
}
```

Definiamo una funzione nuovo_esame_dato(Studente s, char nome_esame, int voto_preso).
Essa serve per definire un nuovo esame. Così abbiamo la possibilità di fare un operazione che aumenta il nostro voto, s1.esami[num_esame].voto++
Ovviamente questo non è permesso.

Possiamo risolvere il problema in due modi:
- Creare un astrazione di dato in C. Questo vorrebbe dire separare il programma in file, per ogni file associare dati a varie funzioni e limitare per ogni dato l'accesso da parte di altre funzioni che potrebbero non usare in modo corretto il dato.
- Usare un programma dove per definizione il dato è legato alla funzione in modo che automaticamente viene creato un astrazione di dato. Essi si chiamano **OGGETTI.**

Proviamo il primo metodo in C. I nostri obiettivi sono scomporre il software in entità e proteggere i dati. Per scomporre il software possiamo usare i moduli, possiamo vedere ogni file/modulo come un entità.

Per proteggere i dati invece possiamo sfruttare le **classi di memorizzazione**. Esse sono quattro e valgono sia per i dati sia per le funzioni.
- Auto. Tempo di vita limitato al blocco dove viene definita, visibilità locale al blocco, allocazione sullo stack, valore indefinito.
- Register. Uguale ad Auto, allocazione su registro CPU solo se possibile.
- Extern. Tempo di vita è di tutto il programma, visibilità locale (solo nel blocco in cui è dichiarata) o globale (in tutto il file, ma NON in altri file), allocazione su segmento dati, valore 0.
- Static. Tempo di vita è di tutto il programma, visibilità nel file in cui è dichiarata, allocazione su segmento dati, valore 0.

Adesso possiamo creare la nostra entità studente in due modi:
- Astrazione di dato. Ha uno svantaggio molto grande, non si può dichiarare più di un oggetto.
- Tipo di dato astratto. Ha tre svantaggi; uso di puntatori, rischio di passare variabili non inizializzate, permette l'uso di operazioni illegali.

Inoltre c'è un altro problema, se noi volessimo aggiungere in un oggetto contatore il decremento possiamo farlo in tre modi, tutti non perfetti:
- Modificare la funzione. C'è rischio di introdurre errori.
- Riscrivere il codice da zero. Perdita di tempo.
- Scrivere una nuova identità che riprende quella già definita. Problemi di protezione di dato.







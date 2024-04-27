**CASO STUDIO: BASE DI DATI ERRATA**
Questa sarà la base di dati usata per reintrodurre il concetto di dipendenza funzionale e introdurre il concetto di normalizzazione. Si ha:
- **RIDONDANZA**: Si ripete più volte il fatto che un impiegato ha un certo stipendio, come si ripete più volte che un progetto ha un certo budget. I valori di progetto e impiegato non possono essere presi singolarmente come chiavi che sarà (progetto, impiegato).
- **AGGIORNAMENTO**: Poichè si ripete più volte il fatto che un certo impiegato prende un certo stipendio l'aggiornamento dei valori avrà un efficienza scarsa dato che dobbiamo operare su ogni tupla di impiegato X per cambiare il valore. Vale anche per progetto-budget.
- **CANCELLAZIONE**: Supponendo che un impiegato lasci l'azienda e sia l'ultima persona rimasta sul progetto possiamo perdere i dati su di esso, analogamente anche se un progetto viene eliminato possiamo perdere i dati dell'impiegato. Essendo la chiave (progetto, impiegato) potremmo avere valori invalidi (NULL).
- **INSERIMENTO**: Essendo la chiave (progetto, impiegato) non possiamo aggiungere impiegati che non partecipano ad un progetto, quindi nemmeno progetti che non hanno impiegati all'interno.

![[Tabella.png]]

**DIPENDENZA FUNZIONALE**
La dipendenza funzionale è un vincolo di integrità per il modello relazionale. Osservando la relazione ricaviamo che:
- Ogni volta che in una tupla appare un impiegato abbiamo uno stipendio che è uguale.
- Possiamo dire che il valore dell'impiegato determina lo stipendio, quindi che possiamo associare ad un impiegato nel dominio degli impiegati **UN SOLO VALORE** dal dominio degli stipendi.
- Analogamente per progetto e budget.

**DEFINIZIONE FORMALE DI DIPENDENZA FUNZIONALE**
La dipendenza funzionale si può definire formalmente come:
Data una relazione R definita su uno schema S(X) e due sottoinsiemi di attributi Y e Z appartenenti ad X non vuoti esiste una dipendenza funzionale Y->Z se per ogni copia di tuple (T1, T2) aventi lo stesso valore di Y risulta che hanno lo stesso valore di Z.
- impiegato->stipendio, progetto->budget.

**DIPENDENZE FUNZIONALI NELLA BASE DI DATI**
Dato un impiegato lo stipendio sarà lo stesso, dato un progetto il budget sarà lo stesso. Se prendiamo la chiave K della relazione R si verifica che, essendo il valore di chiave unico si avrà una dipendenza funzionale tra la chiave e tutti i suoi attributi. Questo va in conflitto con ciò scritto nell'immagine, perchè possiamo determinare le dipendenze (3) e (4) che sono sbagliate.
- (impiegato, progetto)->funzione è una dipendenza completa.
- (impiegato, progetto)->stipendio/budget sono dipendenze parziali che causano le anomalie nella base di dati.

![[Obsidian/Basi di Dati/PNG/D/D03/Esempio.png]]

**FORMA NORMALE**
Le ridondanze ed anomalie nascono quando la X nella dipendenza X->Y non contiene la chiave della relazione. Possiamo quindi introdurre il concetto di forma normale (Boyce&Codd) che si ha per ogni dipendenza X->Y dove X è superchiave della relazione.

**NORMALIZZAZIONE**
Per sistemare le relazioni in forma non normale è necessario normalizzarle. Esse possono essere scomposte in due o più relazioni normali. La scomposizione avviene tramite proiezioni in modo tale da ottenere che ciascuna proiezione simboleggi una singola dipendenza funzionale. Essa è corretta se il join riunisce tutte le proiezioni senza la perdita di dati.
- PER FUNZIONI: (impiegato, progetto)->funzioni.
- PER IMPIEGEATI: impiegato->stipendio.
- PER PROGETTO: progetto->budget.

![[Soluzione.png]]

**ERRORI CHE SI POSSONO INCONTRARE NELLA SCOMPOSIZIONE**
Le scomposizioni sono errate se quando si effettua un join si ha una perdita di informazioni.
Consideriamo una relazione SEDI (impiegato, progetto, sede) con un vincolo che dice che gli impiegati hanno come sede la sede dei loro progetti e le dipendenze:
- (impiegato, progetto)->sede.
- impiegato->sede e progetto->sede.

Scomponendo secondo le due dipendenze riportate dalla tabella sotto avremo una tabella (impiegato, sede) e una tabella (progetto, sede). Se uniamo le tabelle usando l'attributo sede abbiamo che un impiegato sarà associato ad ogni progetto di una sede, crea quindi tuple che
prima non esistevano, inoltre non rispettano nemmeno il vincolo. Una buona scomposizione quindi deve prevedere la ricostruzione di join su chiavi.

Scomponendo partendo dallo schema E/R abbiamo una tabella (progetto, sede), una (impiegato, sede) e una (impiegato, progetto). Questa soluzione è parzialmente corretta. Va bene ma non abbiamo modo di esprimere il vincolo che verrà gestito con strumenti più avanti.

![[Tabella II.png]]

**ANOMALIE DI UNA BASE DI DATI**
1) **Ridondanza**; ogni volta che inseriamo un impiegato dobbiamo specificare lo stipendio, così come ogni volta che inseriamo un progetto dobbiamo specificare il budget. Non possiamo avere una chiave (progetto, impiegato) perchè non c'è unicità nei valori.
2) **Aggiornamento**; essendo che i dati vengono ripetuti spesso allora l'efficienza nell'aggiornare il database non sarà buona. Prendendo come esempio il budget, se il progetto "biella" cambia budget allora dobbiamo operare su ogni tupla e cambiare il valore del campo.
3) **Cancellazione**; se un impiegato lascia il progetto ed è l'ultimo rimasto rischiamo di perdere dati sul progetto, se la chiave è (progetto, impiegato) allora abbiamo valori nulli, quindi incompatibili di chiave.
4) **Inserimento**; se la chiave è (progetto, impiegato) non abbiamo modo di inserire un impiegato che non partecipa ad alcun progetto, stessa cosa vale per un progetto che non ha impiegati.

![[Tabella.png]]

**DIPENDENZA FUNZIONALE**
La dipendenza funzionale è un vincolo di integrità per il modello relazionale.
Supponiamo di avere una relazione R definita su uno schema S(X) e due sottoinsiemi di attributi Y e Z appartenenti ad X non vuoti. Esiste una dipendenza funzionale tra Y e Z se per ogni coppia di tuple T1 e T2 che hanno il valore di Y si ha che hanno il valore anche di Z.
Dall'osservazione della relazione ricaviamo che:
- Ogni volta che in una tupla compare un certo impiegato lo stipendio è sempre lo stesso.
- Esiste una funzione che associa ad ogni valore nel dominio impiegato UN SOLO valore nel dominio stipendio. Questo vale anche per il progetto.

**DIPENDENZE FUNZIONALI DELLA TABELLA**
Impiegato, progetto -> funzione è una dipendenza completa.
Impiegato, progetto -> stipendio e impiegato, progetto -> budget sono in realtà;
Impiegato -> stipendio e progetto -> budget. Dalla nostra dipendenza finale possiamo dedurre le dipendenze (3) e (4). Queste sono quindi dipendenze parziali che causano anomalie.

![[Obsidian/Basi di Dati/PNG/D/D03/Esempio.png]]

**RELAZIONE IN FORMA NORMALE**
Le anomalie nascono dalle dipendenze X->Y dove X non contiene la chiave della funzione.
Una relazione R è in forma normale (Boyce e Codd) quando per ogni dipendenza X->Y in R, X è superchiave, quindi contiene una chiave K di R.

**COME SISTEMARE LE RELAZIONI IN FORMA NON NORMALE**
Una relazione in forma non normale è possibile che venga scomposta in due o più relazioni in forma normale. Possiamo scomporre la relazione in modo tale che ogni dipendenza funzionale corrisponda ad una relazione separata:
- FUNZIONI: impiegato, progetto -> funzione.
- IMPIEGATI: impiegato -> stipendio.
- PROGETTO: progetto -> budget.

![[Soluzione parziale.png]]
![[Join.png]]

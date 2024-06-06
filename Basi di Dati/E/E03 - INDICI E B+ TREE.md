**INDICE**
**TIPO DI ACCESSO SECONDARIO!**
Associa ad un file una tabella nella quale l'entrata i-esima memorizza una coppia del tipo (Ki, Pi).
- Ki è un valore di chiave.
- Pi è un riferimento al record della tupla con valore di chiave Ki.
- L'indice è **ordinato**: Le coppie (Ki, Pi) sono ordinate in base ai valori di k.

![[Tabella Indice.png]]

Nell'esempio abbiamo mostrato solo la colonna della chiave e la posizione della tupla. Un indice è costituito da mini-tuple ed occupa uno spazio di memoria di circa 5/20%
- Ordinare il file indice è più veloce.
- L'indice può essere costruito per qualsiasi attributo anche non-chiave.
- L'indice fornisce una visione ordinata della relazione anche su colonne non di ordinamento.

**ORGANIZZAZIONE CON INDICE**
I riferimenti (4-8 byte) vengono chiamati indirizzi, puntatori oppure **TID** (tuple identifier).
I TID sono costituiti da una coppia (ID Blocco, Indirizzo Blocco).

**METODO DI ACCESSO**
Per accedere ad una chiave K eseguiamo i seguenti passaggi:
1) Accediamo all'indice.
2) Ricerchiamo la coppia desiderata (K,B).
3) Accediamo al blocco dati B.
4) Accediamo alla tupla che contiene K passando per il riferimento P.

Le coppie (K,B) vengono collezionate in blocchi ed ordinate. 
Questi blocchi sono **FOGLIE** dell'indice e sono collegati tra di loro con puntatori.

**RAPPRESENTAZIONE AD ALBERO**
Viene quindi costruito un albero a più livelli di indirizzamento:
- Ogni foglia è rappresentata da una coppia (K,B).
- I blocchi a livello sopra sono rappresentati a loro volta da livelli superiori fino ad arrivare alla radice.

![[B+ Tree.png]]

**TIPI DI INDICI**
- **CLUSTERED/UNCLUSTERED**: L'indice si dice clustered se è costruito su attributo di ordinamento, altrimenti si dice unclustered.
- L'indice può essere costruito su attributi con valori ripetuti. La coppia K diventa quindi la coppia (K, p1, p2..., pN).

**INDICI B+ TREE**
- **B+ TREE**: Struttura dati DINAMICA. Albero associato ad un SW di gestione che lo mantiene sempre equilibrato. Ogni percorso dalla radice ad una foglia ha sempre lunghezza h, chiamata altezza del B+ tree.
- **O**: Ordine del B+ tree.
- `La radice può avere da 2 a non più di 2 * O+1 figli, contiene da 1 a non più di 2 * O valori.`
- `Ogni blocco intermedio ha sempre almeno O+1 e non più di 2 * O+1 figli, contiene almeno O e non più di 2 * O valori dell'attributo.``
- Le foglie sono riempite dal 50 al 100% (media 69%).

**PRESTAZIONI DEL B+ TREE**
Per calcolare le prestazioni del B+ tree prendiamo come input:
- **D**: Dimensione del blocco, in questo caso 4096.
- **L(p)**: Dimensione del puntatore ai nodi intermedi, in questo caso 4 per entrambi i nodi.
- **L(k)**: Dimensione del valore K.

E dobbiamo calcolare:
- **O**: L'ordine del B+ tree.
- **NF**: Il numero di foglie.
- **H**: L'altezza.

1) **TROVARE L'ORDINE O:**
   Per trovare l'ordine O sfruttiamo la disequazione:
   `2 * O * L(k) + (2 * O + 1) * L(p) <= D`
   A questo punto troviamo la formula inversa `O = (D - L(p)) / (2 * (L(k)) + L(p))`
   Con una dimensione di L(k) = 10 si ha `O = 146 + 4 byte inutilizzati per ogni nodo.`

2) **TROVARE IL NUMERO DI FOGLIE:**
   NF dipende dal numero di tuple NT e dal fattore di riempimento medio di circa 69%.
   Nelle foglie abbiamo un numero NT ed un numero di valori NK per cui:
   `NF = (NK * L(k) + NT * L(p) / D * (ln(2)))`
   Con una dimensione `L(k) = 10, NT = 10^6, NK = 10^4 si ha NF = 5776`

3) **TROVARE L'ALTEZZA DEL B+ TREE:**
   Hmin si può ottenere quando tutti i nodi sono pieni. Poichè abbiamo bisogno di NF puntatori al penultimo livello allora:
   `NF <= (2 * O + 1) ^Hmin-1 e quindi Hmin = 1 + Log2*0+1(NF)`
   Per hmax invece abbiamo:
   `NF <= 2 * (O+1)^Hmax-2  e quindi Hmax = 2 + Log0+1 (NF/2)`
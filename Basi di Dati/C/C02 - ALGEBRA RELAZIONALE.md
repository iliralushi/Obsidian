**ESEMPIO TRATTATO**
![[Tabella studenti.png]]

**SELEZIONE (σ)**
SELECT [PredicatoSel] TABELLA. È una tabella priva di nome con:
- SCHEMA: Lo stesso schema di "TABELLA".
- ISTANZA: Le tuple che soddisfano PredicatoSel.

SELECT [NOME='PAOLA'] STUDENTE.
L'espressione restituisce lo schema di studente con le tuple che contengono il nome Paola.

**PREDICATO DI SELEZIONE**
All'interno del predicato di selezione possiamo inserire:
- OPERAZIONI BOOLEANE: And, or, not.
- COMPARATORI: =, !=, <, <=, >, >=.
- PREDICATI SEMPLICI: True, false.
- TERMINE: Costante, attributo, espressioni aritmetiche.

SELECT [(CITTA='Torino') OR ((CITTA='Roma') AND NOT (C-DIP='log'))] STUDENTE
L'espressione restituisce le tuple degli studenti di Torino (senza vincoli) e di Roma che però non devono far parte del dipartimento di Logistica. Quindi verrà restituita solo la tupla di Paola.

**PROIEZIONE (π)**
PROJECT [attributiProiez] TABELLA. È una tabella priva di nome con:
- SCHEMA: Gli attributi "attributiProiez".
- ATTRIBUTI: La restrizione delle tuple sugli attributi "attributiProiez".

PROJECT [NOME, C-DIP] STUDENTE
L'espressione restituisce lo schema degli attributi di NOME e C-DIP e come istanza restituisce la restrizione delle tuple degli attributi di NOME e C-DIP, quindi tutti i nomi e i codici dipartimento.

**PROIEZIONE E DUPLICATI**
- Nel modello formale la proiezione elimina i duplicati.
- Nel modello informale la eliminazione dei duplicati va richiesta esplicitamente.
- PROJECT [C-DIP] STUDENTE elimina i duplicati di Inf, restituendo solo "Inf e Log" senza aggiungere un altro attributo.

**ASSEGNAMENTO (=)**
Serve per dare un nome al risultato di un espressione algebrica.
- **INFORMATICI =** SELECT[C-DIP='Inf'] STUDENTI.
- **TORINESI** = SELECT[CITTA='Torino'] STUDENTI.

**UNIONE (U)**
TABELLA1 UNION TABELLA2, si può fare se TABELLA1 e TABELLA2 sono compatibili, ovvero hanno domini ordinatamente dello stesso tipo. È commutativa ed associativa.
È una tabella priva di nome con:
- SCHEMA: Lo schema di TABELLA1.
- ISTANZA: L'unione delle tuple di entrambe le tabelle.

INFORMATICI UNION TORINESI
È un espressione possibile perchè sia gli informatici che i torinesi hanno lo stesso schema. 
Essa restituisce lo schema di Informatici e l'unione delle tuple di Informatici e Torinesi, quindi restituisce tutti gli Informatici e tutti i Torinesi, quindi le tuple di Paola e Carlo.

**DIFFERENZA (-)**
TABELLA1 MINUS TABELLA2, si può fare se TABELLA1 e TABELLA2 sono compatibili, ovvero hanno domini ordinatamente dello stesso tipo. Non è commutativa ed associativa.
È una tabella priva di nome con:
- SCHEMA: Lo schema di TABELLA1.
- ISTANZA: La differenza delle tuple di entrambe le tabelle.

INFORMATICI MINUS TORINESI
È un espressione che restituisce come schema lo schema di Informatici, come istanze gli Informatici che non sono di Torino. Quindi restituirà solo Carlo.

**JOIN (⋈)**
TABELLA1 JOIN [PredicatoJoin] TABELLA2. È commutativo ed associativo. È una tabella priva di nome con:
- SCHEMA: La concatenazione di entrambe le tabelle.
- ISTANZA: Le tuple ottenute concatenando le tuple di TABELLA1 e TABELLA2 che soddisfano il predicato 'PredicatoJoin'.

STUDENTE JOIN [MATR=MATR] ESAME
È un espressione che restituisce come schema lo schema di Studente ed Esame, come istanze le tuple che si ottengono concatenando studente ed esame che soddisfano il predicato.
[MATR=MATR] è un predicato che dice che il campo matricola dello studente è uguale al campo matricola dell'esame. Con questa condizione possiamo dire quale studente ha dato un esame, per quello Paola è esclusa dalla tabella.

![[Risultato Join.png]]

**SINTASSI DEL PREDICATO DI JOIN**
ATTR1 comp ATTR2 dove:
- ATTR1 appartiene a TABELLA1.
- ATRT2 appartiene a TABELLA2.
- Comp è un espressione di comparazione.
- Attributi omonimi sono resi non ambigui usando la notazione puntata (ESAME.MATR, STUDENTE.MATR).

**EQUI-JOIN E JOIN NATURALE**
- EQUI-JOIN: Esso è un join dove i confronti sono solo di uguaglianza.
- JOIN NATURALE: Equi-join di tutti gli attributi omonimi. Lo si ha quando non si esprime il predicato del join.
- JOIN NATURALE SENZA ATTRIBUTI OMONIMI: Sarà composto dal prodotto cartesiano di tutte le tuple.

**PRIORITY DEGLI OPERATORI**
In assenza delle parentesi valgono le regole di priorità:
- SELEZIONE, PROIEZIONE.
- JOIN.
- UNIONE, DIFFERENZA.




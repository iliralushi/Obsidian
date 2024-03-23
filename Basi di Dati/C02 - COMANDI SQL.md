**SELECT** (SELECT [PredSel] TABELLA)
E' una tabella priva di nome con
- SCHEMA: Lo stesso di tabella
- ISTANZA: Le tuple di TABELLA che soddisfano il predicato di selezione PredSel

**SINTASSI PREDICATO**
- OPERAZIONI BOOLEANE: AND, OR, NOT
- COMPARATORI: =, !=, <, <=, >, >=
- TERMINE: Attributi
- PREDICATI: TRUE, FALSE, termine comparatore termine

**PROJECT** (PROJECT [attributiProiez] TABELLA)
E' una tabella priva di nome con
- SCHEMA: Gli attributi attributiProiez
- ISTANZA: La restrizione di tuple sugli attributi attributiProiez
- Nel modello formale PROJECT elimina i duplicati, nel modello informale va richiesto

**ASSEGNAMENTO** (=)
Serve per dare un nome al risultato di un espressione algebrica, non è inclusa nelle operazioni algebriche.

**UNIONE** (TABELLA 1 UNION TABELLA 2)
Si può fare solo se entrambe le tabelle sono compatibili, ovvero hanno domini ordinatamente dello stesso tipo.
E' una tabella priva di nome con
- SCHEMA: Lo schema di TABELLA 1
- ISTANZA: L'unione delle tuple di TABELLA 1 e TABELLA 2
- E' commutativa e associativa

**DIFFERENZA** (TABELLA 1 MINUS TABELLA 2)
Si può fare solo se entrambe le tabelle sono compatibili, ovvero hanno domini ordinatamente dello stesso tipo.
E' una tabella priva di nome con
- SCHEMA: Lo schema di TABELLA 1
- ISTANZA: La differenza delle tuple di TABELLA 1 e TABELLA 2
- NON è commutativa e associativa

**JOIN** (TABELLA1 JOIN [PredJoin] TABELLA2)
E' una tabella priva di nome con
- SCHEMA: La concatenazione degli schemi di TABELLA 1 e TABELLA 2
- ISTANZA: Le tuple concatenate ottenute da TABELLA 1 e TABELLA 2 che soddisfano la condizione imposta dal predicato PredJoin
- EQUI-JOIN: Confronti di uguaglianza
- JOIN NATURALE: Equi-join di tutti gli attributi
  JOIN NATURALE SENZA ATTRIBUTI: Se le due relazioni non hanno attributi con lo stesso nome allora il join si riduce ad essere un semplice prodotto cartesiano delle varie tuple
- E' commutativo e associativo

**PREDICATO JOIN** (ATTR1 comparatore ATTR2)
- ATTR1 appartiene a TAB1
- ATTR2 appartiene a TAB2
- Attributi uguali sono resi non ambigui usando la notazione puntata
  ES: ESAME.MATR e STUDENTE.MATR

**PRIORITA DEGLI OPERATORI**
E' buona abitudine usare le parentesi per specificare la priorità specifica degli operatori.
Senza parentesi è
- 1) SELECT, PROJECT
- 2) JOIN
- 3) UNION, MINUS
SELECT

OPERATORI LOGICI

PROJECT

ASSEGNAMENTO
- Serve per dare un nome ad un risultato di un espressione algebrica.
- Non fa parte delle operazioni algebriche.

UNIONE (TABELLA 1 UNION TABELLA 2)
- Si può fare se entrambe le tabelle sono compatibili (con domini dello stesso tipo).
- In output restituisce come schema lo schema della tabella 1 e come istanze l'unione di tuple tra tabella 1 e 2.
- L'unione è commutativa e associativa.

DIFFERENZA (TABELLA 1 MINUS TABELLA 2)
- È il contrario dell'unione, si può fare se entrambe le tabelle sono compatibili.
- In output restituisce come schema lo schema della tabella 1 e come istanze la differenza di tuple tra tabella 1 e 2.
- La differenza NON è commutativa e associativa.

JOIN (TABELLA1 JOIN [PredJoin] TABELLA2)
- In output restituisce come schema la concatenazione degli schemi di tabella 1 e 2 e come istanza le tuple ottenute concatenando le tuple di tabella 1 e 2 che soddisfano il predicato PredJoin.
- EQUI-JOIN = solo confronti di uguaglianza.
- JOIN NATURALE = equi-join applicato a tutti gli attributi omonimi.
- Il join è commutativo e associativo.

PREDICATO JOIN (ATTR1 comp ATTR2)
- Dove ATTR1 appartiene alla tabella 1, ATTR2 appartiene alla tabella 2, comp invece è un operatore logico.

PRIORITÀ DEGLI OPERATORI
- sfdsaf

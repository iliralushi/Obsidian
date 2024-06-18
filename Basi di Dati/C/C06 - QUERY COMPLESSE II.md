**QUERY BINARIE**
Si eliminano i duplicati. Questi comandi sono equivalenti all'algebra relazionale.
- **UNION**: Unione di due tabelle.
- **INTERSECT**: Intersezione di due tabelle.
- **EXCEPT**: Differenza di due tabelle.

**QUERY 1**: Selezionare i codici degli ordini i cui importi superano 500 euro oppure presenti in qualche dettaglio con quantità superiore a 1000.
**QUERY 2**: Selezionare i codici degli ordini i cui importi superano 500 euro ma non presenti in qualche dettaglio con quantità superiore a 1000.
**QUERY 3**: Selezionare i codici degli ordini i cui importi superano 500 euro e che sono presenti in qualche dettaglio con quantità superiore a 1000.

``` SQL
QUERY1:
SELECT COD-ORD
FROM ORDINE
WHERE IMPORTO > 500
UNION
SELECT COD-ORD
FROM DETTAGLIO
WHERE QTA > 1000

QUERY2:
SELECT COD-ORD
FROM ORDINE
WHERE IMPORTO > 500
EXCEPT
SELECT COD-ORD
FROM DETTAGLIO
WHERE QTA > 1000

QUERY3:
SELECT COD-ORD
FROM ORDINE
WHERE IMPORTO > 500
INTERSECT
SELECT COD-ORD
FROM DETTAGLIO
```

**COMANDI QUERY ANNIDATE**
Sono costruite concatenando due query SQL nel predicato WHERE:
- **[NOT] IN**: appartenenza.
- **ANY, ALL**: quantificatori.
- **[NOT] EXISTS**: esistenza.

**QUERY CON IN E NOT IN**
- Il predicato IN (subquery) ha valore true se e solo se almeno uno dei valori restituiti da subquery è **UGUALE AL VALORE DELL'ATTRIBUTO SPECIFICATO.**
- Il predicato NOT IN invece è l'opposto.

**QUERY 1**: Selezionare nome e indirizzo dei clienti che hanno emesso qualche ordine di importo superiore a 10.000 euro.
**QUERY 2**: Selezionare nome e indirizzo dei clienti che **NON** hanno emesso qualche ordine di importo superiore a 10.000 euro.
**QUERY 3**: Selezionare nome e indirizzo dei clienti che hanno emesso qualche ordine i cui dettagli comprendono il prodotto Pneumatico.
**QUERY 4**: Aumentare di 5 euro l'importo di tutti gli ordini che comprendono il prodotto 456.

``` SQL
QUERY1:
SELECT NOME, INDIRIZZO
FROM CLIENTE
WHERE COD-CLI IN
(
	SELECT COD-CLI
	FROM ORDINE
	WHERE IMPORTO > 10.000
)

QUERY2:
SELECT NOME, INDIRIZZO
FROM CLIENTE
WHERE COD-CLI NOT IN
(
	SELECT COD-CLI
	FROM ORDINE
	WHERE IMPORTO > 10.000
)

QUERY3:
SELECT NOME, INDIRIZZO
FROM CLIENTE
WHERE COD-CLI IN
(
	SELECT COD-CLI
	FROM ORDINE O, DETTAGLO D, PRODOTTO P
	WHERE O.COD-ORD = D.COD-ORD
	AND D.COD-PROD = P.COD-PROD
	AND P.NOME = 'PNEUMATICO'
)

QUERY4:
UPDATE ORDINE
SET IMPORTO = IMPORTO + 5
WHERE COD-ORD IN
(
	SELECT COD-ORD
	FROM ORDINE
	WHERE COD-PROD = 456
)
```

**QUERY CON ANY E ALL**
- Il predicato ANY ha valore true se e solo se almeno uno dei valori restituiti da subquery **SODDISFA LA CONDIZIONE IN CUI COMPARE**.
- Il predicato ALL è analogo ad ANY con l'eccezione che deve essere vera per **TUTTI I VALORI**.

**QUERY 1**: Trova il codice dell'ordine con importi maggiori dell'importo più piccolo inserito nella tabella.
**QUERY 2**: Trova il codice dell'ordine con l'importo più grande.

``` SQL
QUERY1:
SELECT COD-ORD
FROM ORDINE
WHERE IMPORTO > ANY
(
	SELECT IMPORTO
	FROM ORDINE
)

QUERY2:
SELECT COD-ORD
FROM ORDINE
WHERE IMPORTO >= ALL
(
	SELECT IMPORTO
	FROM ORDINE
)
```

**QUERY CON EXISTS**
Dobbiamo avere un legame tra sottoquery e query di sopra attraverso un join.
- Il predicato EXISTS ha valore true se e solo se l'insieme dei valori restituiti dalla subquery è **NON VUOTO**.
- Il predicato NOT EXISTS è invece l'opposto.

**QUERY 1**: Selezionare nome e indirizzo dei clienti che hanno emesso qualche ordine di importo superiore a 10.000 euro.
**QUERY 2**: Selezionare i codici degli ordini i cui importi superano 500 euro ma non presenti in qualche dettaglio con quantità superiore a 1000.

``` SQL
QUERY1:
SELECT NOME, INDIRIZZO
FROM CLIENTE C
WHERE EXISTS
(
	SELECT *
	FROM ORDINE O
	WHERE C.CODCLI = O.CODCLI
	AND IMPORTO > 10.000
)

QUERY2:
SELECT COD-ORD
FROM ORDINE O
WHERE IMPORTO > 500
AND NOT EXISTS
(
	SELECT *
	FROM DETTAGLIO D
	WHERE O.COD-ORD = D.COD-ORD
	AND D.QTY > 1000
)
```

**NESTED QUERY CON OPERATORI DI CONFRONTO**
Possiamo fare query annidate con operatori di confronto a patto che la subquery restituisca solo una singola tupla.

**QUERY 1**: Selezionare il nome degli impiegati il cui il salario è maggiore di quello del proprio manager.
**QUERY 2**: In quali tipi di progetto lavora Giovanni?
**QUERY 3**: Chi è il manager di Piero?

``` SQL
QUERY1:
SELECT NOME
FROM IMPIEGATI
WHERE SALARIO >
(
	SELECT SALARIO
	FROM IMPIEGATI Y
	WHERE MATR = Y.MATR-MGR
)

QUERY2:
SELECT TIPO
FROM PROGETTO
WHERE NUM-PROG IN
(
	SELECT NUM-PROG
	FROM ASSEGNAMENTO
	WHERE MATR IN
	(
		SELECT MATR
		FROM IMPIEGATO
		WHERE NOME = 'GIOVANNI'
	)
)

QUERY3:
SELECT NOME
FROM IMPIEGATO
WHERE MATR IN
(
	SELECT MATR-MGR
	FROM IMPIEGATO 
	WHERE NOME = 'PIERO'
)
```

**RIDUZIONI DI QUERY ANNIDATE**
Le query annidate formulate con i seguenti operatori si possono ridurre a query semplici.
- **IN, ANY, EXISTS**.

Le query annidate formulate con i seguenti operatori **NON** si possono ridurre a query semplici.
- **NOT IN, ALL, NOT EXISTS**.


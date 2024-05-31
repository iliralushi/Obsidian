**QUERY CON ORDINAMENTO**
- **ORDER**: Essenziale per poter risolvere le query con ordinamento.
- **QUERY1**: Ordina la data degli ordini con importo inferiore a 100.000EUR.
- **QUERY2**: Ordina la data in ordine decrescente e i codici clienti in ordine crescente degli ordini incon importo inferiore a 100.000EUR.

``` SQL
QUERY1
SELECT * FROM ORDINE 
WHERE IMPORTO < 100.000
ORDER BY DATA

QUERY2
SELECT * FROM COD-ORD, DATA
WHERE IMPORTO < 100.000
ORDER BY COD-ORD ASC, DATA DESC
```

**QUERY CON AGGREGAZIONI**
**FUNZIONI AGGREGATE**: Le usiamo per risolvere le query con aggregazioni. Usabili soltanto con SELECT ed HAVING:
- **SUM**: Sommatoria.
- **AVG**: Media.
- **MIN**: Minimo.
- **MAX**: Massimo.
- **COUNT**: Cardinalità.

- **QUERY 1**: Valore massimo di un ordine.
- **QUERY 2**: Somma degli importi degli ordini del cliente 1.

``` SQL
QUERY1
SELECT MAX(IMPORTO) AS MAX-IMP FROM ORDINE

QUERY2
SELECT SUM(IMPORTO) FROM ORDINE
WHERE COD-CLIENTE = 1
```

**QUERY CON RAGGRUPPAMENTO**
Oltre agli operatori SELECT, FROM, WHERE aggiungiamo:
- **GROUP-BY**: Raggruppamento.
- **HAVING**: Selezione dei gruppi.

Usando GROUP BY il risultato della SELECT è un unico record per ciascun gruppo. Quindi, in SELECT ed HAVING possono comparire solo:
- Uno o più attributi del raggruppamento (i campi specificati nella GROUP BY)
- Funzioni aggregate.
- Possiamo ordinare il risultato delle query con raggruppamento.

- **QUERY 1:** Selezionare la somma degli importi degli ordini successivi al 10-6-14 per quei clienti che hanno emesso almeno 2 ordini.
- **QUERY 2**: Selezionare la somma delle quantità dei dettagli degli ordini emessi da ciascun cliente per ciascun prodotto, purchè la somma superi 50.
- **QUERY 3**: Selezionare la somma degli importi degli ordini successivi al 10-6-14 per quei clienti che hanno emesso almeno 2 ordini dopo quella data, in ordine di cliente.

``` SQL
QUERY1
SELECT COD-CLI, SUM(IMPORTO) FROM ORDINE
WHERE DATA > 2014-06-10
GROUP BY COD-CLI
HAVING COUNT(IMPORTO) >= 2

QUERY2
SELECT COD-ORD, COD-CLI, SUM(QTA)
FROM ORDINE AS O, DETTAGLIO AS D
WHERE O.COD-ORD = D.COD-ORD
GROUP BY COD-ORD, COD-CLI
HAVING SUM(QTA) > 50

QUERY3
SELECT COD-CLI, SUM(IMPORTO) FROM ORDINE
WHERE DATA > 2014-06-10
GROUP BY COD-CLI
HAVING COUNT(IMPORTO) >= 2
ORDER BY COD-CLI
```


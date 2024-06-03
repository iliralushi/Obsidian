**DIVISIONE IN SQL**
L'operazione di divisione in AR non è definita in SQL. Quindi le interrogazioni che richiedono tale operatore, come ad esempio:
- Selezionare i dati degli ordini che contengono **tutti** i prodotti di prezzo maggiore di 100.

Devono essere formulate con una doppia negazione nel seguente modo:
- Selezionare i dati degli ordini per i quali non esiste alcun prodotto di prezzo maggiore di 100 che non sia contenuto in essi.

``` SQL
SELECT *
FROM ORDINE O
WHERE NOT EXISTS
	(
		SELECT *
		FROM PRODOTTO P
		WHERE P.PREZZO > 100
		AND NOT EXISTS
		(
			SELECT *
			FROM DETTAGLIO D
			WHERE D.COD-PROD = P.COD-PROD
			AND D.COD-ORD = O.COD-ORD
		)
	)
```

**CREAZIONE DI INDICI**
- Meccanismi di accesso efficiente ai dati. Concetto approfondito nella parte E del corso.
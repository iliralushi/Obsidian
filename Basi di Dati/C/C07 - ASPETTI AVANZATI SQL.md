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
- Meccanismi di accesso efficiente ai dati. Concetto approfondito nella parte di progettazione fisica del corso.

``` SQL
CREATE INDEX
CREATE INDEX DATA-IX
ON ORDINI (DATA)

CREATE UNIQUE INDEX
CREATE UNIQUE INDEX ORD-KEY
ON ORDINI (ORD-COD)
```

**COMANDI DI MODIFICA DEGLI SCHEMI**
- **CREATE:** Crea oggetti.
- **ALTER**: Modifica oggetti.
- **DROP**: Elimina oggetti.
- Per il DROP Possiamo usare le opzioni **RESTRICT** che impedisce DROP se gli oggetti comprendono istanze e **CASCADE** che applica drop agli oggetti applicati.

``` SQL
DROP:
DROP TABLE ORDINI
DROP INDEX DATA-IX

ALTER TABLE ORDINI ADD COLUMN NUM-FATT CHAR(6)
ALTER TABLE ORDINI ALTER COLUM IMPORTO ADD DEFAULT 0
ALTER TABLE ORDINI DROP COLUMN DATA
```

**VISTE RELAZIONALI**
Offrono la visione di tabelle virtuali (schemi esterni). Sono classificate in:
- **SEMPLICI** (selezione e proiezione su una sola tabella)
- **COMPLESSE**

Le query possono includere al loro interno viste già create in precedenza, inoltre una volta creata una view possiamo anche interrogarla e nella maggior parte dei casi modificarla.

**VIEW1**: La vista restituirà tutti gli ordini con importo superiore a 10.000. Si chiamerà "ordini-principali"
**VIEW2**: Vista complessa.

``` SQL
VIEW1:
CREATE VIEW ORDINI-PRINCIPALI AS
SELECT * FROM ORDINI
WHERE IMPORTO > 10.000

VIEW2:
CREATE VIEW CLI-PRO (CLIENTE, PRODOTTO) AS
SELECT COD-CLI, COD-PROD
FROM ORDINE JOIN DETTAGLIO
	ON ORDINE.COD-ORD = DETTAGLIO.COD-ORD
```
**INTEGRITA REFERENZIALE**
Esprime un legame gerarchico fra tabelle. Alcuni attributi della tabella figlio sono definiti Foreign Key. I valori contenuti nella Foreign Key devono essere sempre presenti nella tabella padre.
- **VINCOLO DI TABELLA**: FOREIGN KEY (MATR) REFERENCES STUDENTI (MATR).
- **VINCOLO DI COLONNA**: MATR CHAR(6) REFERENCES STUDENTI (MATR).

Se omettiamo la lista delle colonne riferite viene utilizzata la **CHIAVE PRIMARIA** della tabella riferita. Ad esempio, questo comando è equivalente al primo.
- FOREIGN KEY (MATR) REFERENCES STUDENTI.

**IL PROBLEMA DEGLI ORFANI**
Gli orfani sono tuple che restano prive di padre data una cancellazione/modifica nella tabella del padre. Usiamo le keyword:
- **ON DELETE** - **ON UPDATE**.

**GESTIONE DEGLI ORFANI**
- **CASCADE**: Aggiornamenti su colonne riferite aggiornano tutte le colonne delle tuple in Foreign Key. Se invece viene cancellata una tupla verranno cancellate anche nelle colonne in FK.
- **SET NULL**: Aggiornamenti e cancellazioni su colonne riferite causano la modifica delle colonne in Foreign Key a NULL.
- **SET DEFAULT**: Aggiornamenti e cancellazioni su colonne riferite causano la modifica delle colonne in Foreign Key a DEFAULT.
- **NO ACTION**: Aggiornamenti e cancellazioni su colonne riferite sono proibiti se c'è una colonna in Foreign Key.

**ESEMPIO I**

``` SQL
CREATE TABLE ESAME
(
	...
	FOREIGN KEY (MATR) REFERENCES STUDENTI
		ON DELETE CASCADE ON UPDATE CASCADE
)

CREATE TABLE ESAME
(
	...
	PRIMARY KEY(MATR, COD-CORSO),
	FOREIGN KEY (MATR) REFERENCES STUDENTI
		ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD-CORSO) REFERENCES CORSO
		ON DELETE NO ACTION ON UPDATE NO ACTION
)
```

**ESEMPIO II**

``` SQL
CREATE TABLE CLIENTE
(
	COD-CLI CHAR(6) PRIMARY KEY,
	INDIRIZZO CHAR(50),
	P-IVA CHAR(12) NOT NULL UNIQUE
)

CREATE TABLE ORDINE
(
	COD-ORD CHAR(6) PRIMARY KEY,
	COD-CLI CHAR(6) NOT NULL DEFAULT='999999',
	DATA DATE,
	IMPORTO INTEGER,
	FOREIGN KEY (COD-CLI) REFERENCES CLIENTE
		ON DELETE SET DEFAULT ON UPDATE SET DEFAULT
)

CREATE TABLE DETTAGLIO
(
	COD-ORD CHAR(6),
	COD-PROD CHAR(6),
	QTA SMALLINT,
	PRIMARY KEY (COD-ORD, COD-PROD),
	FOREIGN KEY (COD-ORD) REFERENCES ORDINE
		ON DELETE CASCADE ON UPDATE CASCADE
	FOREIGN KEY (COD-PROD) REFERENCES PRODOTTO
		ON DELETE NO ACTION ON UPDATE NO ACTION
)

CREATE TABLE PRODOTTO
(
	COD-PROD CHAR(6) PRIMARY KEY,
	NOME CHAR(20),
	PREZZO SMALLINT,
)
```

**SELECT IN SQL**
- **SELECT STAR**: Seleziona tutta la tabella.
- **SELECT NOME, CITTÀ**: Seleziona gli attributi scelti.
- **SELECT DISTINCT CITTÀ**: Seleziona l'attributo città senza contare i duplicati.
- **SELECT CITTA AS LUOGO-DI-RESIDENZA**: Seleziona la colonna città e restituisce una colonna di nome Luogo-di-residenza (alias).
- **SELECT SUM (SALARIO)** : Restituisce la sommatoria di tutti i valori inclusi in salario.

**FROM IN SQL**
- **FROM STUDENTE**: Seleziona l'attributo studente e serve per dire su quale tabella dobbiamo estrarre i dati.
- **FROM STUDENTE AS X**: Seleziona l'attributo studente e lo restituisce con alias X. Possiamo anche omettere l'AS.
- **FROM STUDENTE JOIN ESAME ON STUDENTE.MATR=ESAME.MATR**: Join diretto nel FROM.

**WHERE IN SQL**
Il where serve per esprimere le condizioni che devono essere raggiunte dalle tuple per poter essere incluse nel risultato della query. Inoltre abbiamo:
- **BETWEEN**: Per indicare un campo che è nel mezzo tra un numero ed un altro.
- **LIKE**: Pattern matching.
  - C-DIP LIKE 'log%' - STRINGA ARBITRARIA.
  - TARGA LIKE 'E_777CX' - CARATTERE ARBITRARIO.

**VALORI NULLI**
La query sotto non va bene. Se città ha valore NULL il risultato per CITTA=MILANO avrà valore "UNKNOWN".

``` SQL
SELECT *
FROM STUDENTE
WHERE CITTA IS [NOT] NULL
```

**JOIN IN SQL**
Dato che non esiste il join naturale in SQL abbiamo due metodi per farlo:
- Join nel WHERE.
- Join nel FROM.

``` SQL
JOIN1
SELECT NOME
FROM STUDENTE, ESAME
WHERE STUDENTE.MATR = ESAME.MATR 
AND C-DIP LIKE 'IN%' AND VOTO = 30

JOIN2
SELECT NOME
FROM STUDENTE JOIN ESAME 
	ON STUDENTE.MATR = ESAME.MATR
WHERE C-DIP LIKE 'IN%' AND VOTO = 30
```

**QUERY CON VARIABILI RELAZIONALI**
- **QUERY 1**: Chi sono i dipendenti non-pendolari?
- **QUERY 2**: (Self-join) Chi sono i dipendenti di Giorgio?
- **QUERY 3**: In quali tipi di progetti lavora Giovanni?
- **QUERY 4**: Chi è il manager di Piero?

``` SQL
QUERY1
SELECT NOME
FROM IMPIEGATO AS I, DIPARTIMENTO AS D, ASSEGNAMENTO AS A
WHERE I.CITTA = D.CITTA
AND I.MATR = A.MATR
AND D.DNO = A.DNO

QUERY2
SELECT NOME
FROM IMPIEGATO AS I1, IMPIEGATO AS I2
WHERE I1.MATR-MGR = I2.MATR
AND I2.NOME = GIORGIO

QUERY3
SELECT TITOLO
FROM IMPIEGATO AS I, ASSEGNAMENTO AS A, PROGETTO AS P
WHERE I.MATR = A.MATR
AND A.NUM-PROG = P.NUM-PROG
AND NOME = 'GIOVANNI'

QUERY4
SELECT NOME
FROM IMPIEGATO AS I1, IMPIEGATO AS I2
WHERE I1.MATR-MGR = I2.MATR
AND I1.NOME = 'PIERO'
```


**TIPI DI DATI SQL**
- **STRINGHE**: CHAR (N), VARCHAR (N).
- **STRINGHE DI BIT 0/1**: BIT(N), VARBIT(N).
- **NUMERICI**: NUMERIC (Precision, Scale), INTEGER, SMALLINT.
- **NUMERICI APPROSSIMATI**: REAL, DOUBLE.
- **DOMINI SPECIALI**: DATE, TIME(N), TIMESTAMP, INTERVAL.

**PRECISION E SCALE**
- **PRECISION**: Numero di cifre significative per tutto il numero.
- **SCALE**: Numero di cifre decimali.
- Il numero 23.5141 avrà 6 cifre di precision e 4 di scale.

**IL VALORE NULL**
Null è un valore polimorfo (appartiene a tutti i domini) col significato di valore non noto.
I casi sono i seguenti:
- Il valore esiste ma è ignoto al database (data di nascita).
- Il valore è inapplicabile (numero patente per minorenni).

**DEFINIZIONE DELLE TABELLE**
Una tabella è costituita da:
- Una lista di uno o più attributi (colonne).
- Un insieme di zero o più vincoli.

``` SQL
CREATE TABLE <nome-tabella> 
(
	<nome-col> <dominio> [<vincoli-col>]
	...
	<nome-col> <dominio> [<vincoli-col>]
	[<vincoli-tab>]
)
```

**VINCOLI DI COLONNA**
- **NOT NULL**: L'attributo non può assumere null.
- **UNIQUE**: L'attributo sarà unico.
- **PRIMARY KEY**: L'attributo sarà la chiave primaria.
- **CHECK**: Esprime un vincolo sulla colonna tramite espressione logico-relazionale.
- **REFERENCES**: Esprime il vincolo della Foreign Key.

**VINCOLI DI TABELLA**
Sono gli stessi dei vincoli di colonna, però agiranno su tutta la tabella.
Possiamo specificare le colonne su cui agire. I costrutti sono i seguenti:
- **UNIQUE (lista-colonne)**: La combinazione dei valori delle colonne è unica per tutte le tuple della tabella.
- **PRIMARY KEY (lista-colonne)**: Chiave primaria della tabella.
- **FOREIGN KEY (lista-colonne) REFERENCES TAB (lista-colonne):** Foreign key.
- **CHECK (condizione)**: Predicato che deve essere soddisfatto per tutte le tuple della tabella.

**ESEMPIO I**

``` SQL
CREATE TABLE STUDENTE
(
	MATR CHAR(6) PRIMARY KEY,
	NOME VARCHAR(30) NOT NULL,
	CITTA VARCHAR(20),
	C-DIP CHAR(3)
)

CREATE TABLE CORSO
(
	COD-CORSO CHAR(6) PRIMARY KEY,
	TITOLO VARCHAR(30) NOT NULL,
	DOCENTE VARCHAR(20)
)

CREATE TABLE ESAME
(
	MATR CHAR(6),
	COD-CORSO CHAR(6),
	DATA DATE NOT NULL,
	VOTO SMALLINT NOT NULL,
	PRIMARY KEY(MATR, COD-CORSO),
	FOREIGN KEY (MATR) REFERENCES STUDENTI,
	FOREIGN KEY (COD-CORSO) REFERENCES CORSO
)
```

**ALTERNATIVE KEYS**
In SQL non esiste il costrutto ALTERNATIVE KEY.
Usiamo i costrutti già presenti NOT NULL & UNIQUE.

``` SQL
CREATE TABLE STUDENTE
(
	MATR CHAR(6) PRIMARY KEY,
	CF CHAR(16) NOT NULL UNIQUE, 
	NOME VARCHAR(30) NOT NULL,
	CITTA VARCHAR(20),
	C-DIP CHAR(3)
)
```

**DICHIARATIVITA DI SQL**
In SQL l'utente specifica quale informazione è di suo interesse ma non specifica come estrarla dai dati. Il sistema costruisce una strategia di accesso. (Per quello usiamo SELECT e FROM assieme).

**STRUTTURA BASE DI SQL**
- **SELECT**
- **FROM**
- **WHERE**

``` SQL
SELECT *
FROM STUDENTE
WHERE C-DIP = 'Log'
```

**BLOCCHI SQL PER LA MODIFICA**
- **DELETE (FROM)**
- **INSERT (INTO)**
- **UPDATE (SET)**

``` SQL
CANCELLAZIONE:
DELETE FROM STUDENTE WHERE MATR = '678678'

INSERIMENTO:
INSERT INTO STUDENTE 
VALUES
('456878', 'GIORGIO ROSSI', 'BOLOGNA', 'LOGISTICA E PRODUZIONE')

INSERT INTO BOLOGNESI
(
	SELECT *
	FROM STUDENTE
	WHERE CITTA = 'BOLOGNA'
)

MODIFICA:
UPDATE ESAME
SET VOTO = 30
WHERE DATA = 2014-04-01

UPDATE ESAME
SET VOTO = VOTO+1
WHERE MATR = '787989'
```
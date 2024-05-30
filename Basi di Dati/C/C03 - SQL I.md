**TIPI DI DATI SQL-2**
- **STRINGHE**: CHAR (N), VARCHAR (N).
- **STRINGHE DI BIT**: BIT(N), VARBIT(N).
- **NUMERICI**: NUMERIC (Prec, Scale), INTEGER, SMALLINT.
- **NUMERICI APPROSSIMATI**: REAL, DOUBLE.
- **DOMINI SPECIALI**: DATE, TIME(N), TIMESTAMP, INTERVAL.

**PRECISION E SCALE (TIPO NUMERIC)**
- **PRECISION**: Numero di cifre significative per tutto il numero.
- **SCALE**: Numero di cifre decimali.
- Il numero 23.5141 avrà 6 cifre di precision e 4 di scale.

**IL VALORE NULL**
Null è un valore polimorfo (appartiene a tutti i domini) col significato di valore non noto.
- Il valore esiste ma è ignoto al database, come per la data di nascita.
- Il valore è inapplicabile, come per il numero patente per minorenni.

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
- **NOT NULL**: L'attributo non può assumere il valore null.
- **UNIQUE**: Unicità dell'attributo.
- **PRIMARY KEY**: L'attributo è la chiave primaria.
- **CHECK**: Esprime un generico vincolo sulla colonna tramite un espressione logico-relazionale
- **REFERENCES**: Esprime il vincolo della FK.

**VINCOLI DI TABELLA**
Funzionano in modo simile ai vincoli di colonna, però agiranno su tutta la tabella. Possiamo specificare le colonne su cui devono agire. Viene aggiunto un nuovo costrutto:
- **FOREIGN KEY (lista-colonne) REFERENCES tab [(lista-colonne)]

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
	PRIMARY KEY(MATR, COD-CORSO)
	FOREIGN KEY (MATR) REFERENCES STUDENTI,
	FOREIGN KEY (COD-CORSO) REFERENCES CORSO
)
```

**CHIAVI ALTERNATIVE**
Per esprimere le chiavi alternative usiamo i vincoli di colonna NOT NULL e UNIQUE.

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
In SQL l'utente specifica **QUALE** informazione è di suo interesse ma **NO** come estrarla dai dati.
Il sistema costruisce una strategia di accesso (**QUERY OPTIMIZATION**).

**STRUTTURA DI SQL**
- **SELECT**: Selezione.
- **FROM**: Proiezione.
- **WHERE**: Usato per estrarre solo i campi che rispettano una certa condizione.

``` SQL
SELECT *
FROM STUDENTE
WHERE C-DIP = 'Log'
```

**BLOCCHI SQL PER LA MODIFICA**
- **DELETE**: Cancellazione.
- **INSERT**: Inserimento.
- **UPDATE**: Modifica.

``` SQL
CANCELLAZIONE:
DELETE FROM STUDENTE WHERE MATR = '678678'

INSERIMENTO:
INSERT INTO STUDENTE VALUES
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
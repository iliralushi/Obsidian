Quali studenti (nome) sono iscritti al diploma di Informatica?
PROJECT [NOME]
	SELECT [C-DIP='INF'] STUDENTE

Quali studenti (nome) di Logistica non sono di Milano?
PROJECT [NOME]
	SELECT [C-DIP='LOG' AND CITTA!='MILANO'] STUDENTE

Quali studenti (nome) hanno preso 30 in matematica?
PROJECT [NOME]
	(STUDENTE JOIN
		(SELECT [VOTO='30'] ESAME JOIN
			SELECT [TITOLO='MATEMATICA'] CORSO))

Quali professori hanno esaminato Antonio?
PROJECT [DOCENTE]
	(ESAME JOIN
		(CORSO JOIN
			SELECT [NOME='ANTONIO'] STUDENTE))

Estrarre la matricola degli studenti romani oppure gli studenti che hanno sostenuto un esame il giorno 8-1-15 (Caso tipico di union; estrarre x che ha fatto azione oppure azione y).

(PROJECT [MATR]
	SELECT [CITTA='ROMA'] STUDENTE)
UNION
(PROJECT [MATR]
	SELECT [DATA='8-1-15'] ESAME)

Estrarre la matricola degli studenti che hanno preso almeno un voto superiore a 28 e non sono mai scesi sotto il 25 (Caso tipico di minus, la negazione; non sono/non hanno...).

(PROJECT [MATR]
	SELECT [VOTO>'28'] ESAME)
MINUS
(PROJECT [MATR]
	SELECT [VOTO<'25'] ESAME)

![[Gestione ordini.png]]

Quali ordini (codice) ha emesso Paolo?
PROJECT [COD-ORD]
	SELECT [NOME='PAOLO']
		(CLIENTE JOIN ORDINE)

Quali prodotti (nomi) sono ordinati da un cliente di Milano?
PROJECT [PRODOTTO.NOME]
	SELECT [CITTA='MILANO']
		(CLIENTE JOIN ORDINE JOIN DETTAGLIO JOIN [COD-PROD=COD-PROD] PRODOTTO)

COD-PROD=COD-PROD è giusto metterlo perchè il join naturale unirebbe tutte le colonne con lo stesso nome e non vogliamo questo dato che indicano due cose diverse.

Quali prodotti (nomi) hanno prezzo inferiore a 10eur e non sono presenti in nessun ordine?
(PROJECT [PRODOTTO.NOME]
	SELECT [PREZZO<'10EUR'] PRODOTTO)
MINUS
(PROJECT [PRODOTTO.NOME]
	(DETTAGLIO JOIN PRODOTTO))

Tipico problema che usa il minus.

![[Gestione personale.png]]

In quali tipi di progetti lavora Giovanni?
PROJECT [TIPO]
	SELECT [NOME='GIOVANNI']
		(IMPIEGATO JOIN ASSEGNAMENTO JOIN PROGETTO)

Chi è il manager di Piero?
PROJECT [NOME]
	(PROJECT [MATR-MGR]
		(SELECT [NOME='PIERO'] IMPIEGATO))
			JOIN [MATR-MGR=MATR] IMPIEGATO
	
Bisogna fare un self-join, quindi un join applicato sulla stessa tabella. Estraiamo la matricola del manager con le righe in mezzo della nostra query e uniamo quindi la tabella che avrà il manager di Piero con la tabella impiegato dove la matricola del manager equivale alla matricola. Questo ci restituisce la tupla di Giorgio e da li basta fare un project sul nome.

Quale impiegato è stato assunto per primo?
PROJECT [MATR] IMPIEGATO
MINUS
PROJECT [MATR]
	IMPIEGATO JOIN [DATA-ASS>DATA-ASS]
		PROJECT [DATA-ASS] IMPIEGATO

Questo è un problema di minimo/massimo. Si usa quindi un self-join che a sinistra contiene i dati degli impiegati e a destra la data di assunzione di ogni impiegato. La condizione per il join sarà quindi che ogni impiegato incluso nella tabella avrà una data di assunzione più recente rispetto al membro di destra, quindi verranno presi tutti gli impiegati tranne il più anziano. Da questo punto si fa un minus tra tutti gli impiegati e tutti gli impiegati tranne il più anziano, in questo modo otteniamo l'impiegato assunto per primo.

Quale impiegato è assegnato a tutti i progetti?
PROJECT [MATR, NUM-PROG] ASSEGNAMENTO
/
PROJECT [NUM-PROG] PROGETTO

**DIVISIONE**
Il risultato dell'operazione di divisione tra due relazioni r ed s con schemi R(X) ed S(Y) con Y sottoinsieme di X, è una relazione d con schema D(X MINUS Y) contenente le tuple di r associate a tutte le tuple di s.

![[CD.png]]

(PROJECT [NTESS, NOME, INDIRIZZO]
	(CD JOIN CLIENTE JOIN ACQUISTO))
MINUS
(PROJECT [NTESS, NOME, INDIRIZZO]
	(SELECT [DATA>1/1/1997 AND CASADISCO='MUTE']
		(CD JOIN CLIENTE JOIN ACQUISTO)))

PROJECT [NTESS, CODCD] 
	(CLIENTE JOIN CD)
/
PROJECT [CODCD]
	SELECT [AUTORE='DEPECHE MODE] CD
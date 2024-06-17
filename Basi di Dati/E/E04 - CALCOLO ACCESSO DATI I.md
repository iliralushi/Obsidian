**OTTIMIZZATORI**
Lo scopo dei query-optimizer è valutare qual'è la miglior strategia di accesso per le query di SQL. Gli ottimizzatori non prendono decisioni sull'ordinamento delle relazioni e su che indici costruire.

**UTILIZZO INDICI**
Un indice può essere utilizzato per eseguire una interrogazione di SQL se:
- Compare nella clausola **WHERE**.
- Viene contenuto in un **FATTORE BOOLEANO**.
- Il fattore booleano è **ARGOMENTO DI RICERCA** attraverso indice.
- Compare in un **ORDER BY** o **GROUP BY**.

**FATTORE BOOLEANO**
Un predicato si dice fattore booleano se:
- Collegato nel WHERE-Tree tramite un AND.
- Se falso allora determina il risultato falso per la query.

**ESEMPIO**
- Nella prima query tutti i fattori booleani possono essere indicizzati.
- Nella seconda query il secondo fattore booleano è un espressione algebrica, mentre la terza opera su due attributi diverse, quindi non è indicizzabile.

``` SQL
TABELLA:
IMPIEGATI (Matr, cognome, nome, lavoro, qualifica, salario, straordinario, dno)

QUERY1:
SELECT Cognome, Salario
FROM Impiegati
WHERE DNO = 51 AND Salario > 2000 
AND (Lavoro = 'Fattorino' OR Lavoro = 'Guardiano')

QUERY2:
SELECT Cognome, Salario
FROM Impiegati
WHERE DNO = 51 AND Salario + Straordinario > 3000
AND (Lavoro = 'Fattorino' OR Qualifica = '7')
```

**RIPASSO NOTAZIONI**
- NT: Numero di Tuple.
- NB: Numero di Blocchi.
- NF: Numero di Foglie.
- NK. Max. Min: Cardinalità

**MODELLO DI COSTO**
Un indice è utile per una query solo se il costo di accesso con l'indice è minore del costo di accesso sequenziale, ovvero NB (NB/2 se indice Unique).

**FATTORE DI SELETTIVITA**
Un predicato è selettivo se non tutte le tuple lo soddisfano. Il fattore di selettività quindi sarà il numero delle tuple che soddisfa il predicato.
- **FORMULA**: `F = SK/NK` (VALORI SELEZIONATI / VALORI SELEZIONABILI).
- **ATTRIBUTI DIVERSI**: `F = Fpred1 + Fpred2  + FpredN - Fpred1 - Fpred2 - FpredN.`
- **ATTRIBUTO A = ATTRIBUTO B**: `F = 1/max(NKa, NKb).`
- **NUM. TUPLE**: `E = NT * Fpred`
- **NUM. TUPLE PER + PREDICATI**: `E = NT * ∏ Fpred.`

**CALCOLO COSTO DI ACCESSO**
Bisogna considerare vari fattori come:
- Indice clustered/unclustered.
- Attributo unique/con ripetizione di valori.
- Predicato di uguaglianza/di range/OR.
- **Uso di un solo indice/più indici**.

**IPOTESI DI BUFFER**
Ipotizziamo il fatto che ogni relazione/indice ha una sola pagina di buffer in memoria centrale, quindi prendiamo i dati direttamente da disco. Supposizione pessimistica, per calcolare upper bound.

**COSTO DI ACCESSO**
Il costo di C è dato dal Costo di Indice + Costo di Relazione. Nel caso in cui abbiamo un OR allora dobbiamo moltiplicare per due, indipendentemente da clustered/unclustered.
- **CLUSTERED**: `COSTO = ⌈F * NF⌉ + ⌈F + NB⌉.`
- **UNCLUSTERED**: `COSTO = ⌈F * NF⌉ + ⌈F + NT⌉.`
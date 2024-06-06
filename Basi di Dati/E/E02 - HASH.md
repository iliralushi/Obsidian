**HASH**
Associare ad un file con NB blocchi una funzione HASH che si occupa di trasformare un valore di chiave `Ki` in un numero di blocco `Bi` compreso tra 1 e NB. Il blocco prende il nome di **bucket**.
- Una tupla viene memorizzata in un blocco `Bi`.
- Ad ogni blocco è associato un indirizzo nel disco.
- Un blocco può contenere una o più tuple.

**ORGANIZZAZIONE HASH**
La regola con cui un valore di chiave K viene associato ad un numero di blocco B si chiama funzione HASH o algoritmo di hashing. `HASH (chiave) = b`

Il file è ben utilizzato se:
- **M**: Numero massimo di record per blocco.
- **m**: Numero medio di record per blocco.
- Ci sono pochi spazi vuoti, cioè se il fattore di packing è elevato: `FattPacking = m/M < 1`
- Fp basso sta ad indicare che il file è vuoto, Fp vicino ad 1 indica che molti blocchi sono pieni. Con i blocchi pieni abbiamo un problema di **OVERFLOW**.

**OVERFLOW**
Quando un blocco è pieno ed una nuova tupla dev'essere inserita poichè la funzione di HASH gli ha assegnato quel blocco, allora verrà creata una lista di overflow.

L'overflow avviene per due motivi:
- Ci sono più tuple con lo stesso valore di chiave per cui FH (funzione HASH) le manda nello stesso blocco.
- FH non è perfetta e assegna a due o più valori di chiavi diverse lo stesso blocco del file.

**METODI PER LA FUNZIONE HASH**
1) **MID-SQUARE**: La chiave K (convertita in numero) è moltiplicata per se stessa ed i numeri centrali del quadrato vengono presi e **NORMALIZZATI** per rientrare nel range NB del numero blocchi del file.

**ES1**: Record key = 6 cifre, file NB = 7000. Se il numero è 172148 allora facciamo 172148^2 (029634933904) e prendiamo le cifre centrali (3493). Se le cifre > 7000 allora lo **NORMALIZZIAMO**.

2) **DIVISIONE**: La chiave K viene divisa per il numero primo più vicino ad NB ed il **RESTO** viene preso come numero del blocco.

**ES2**: Record key = 172148, file NB = 7000. Facciamo 172148/6997 = resto 4220. 
Non è un randomizzatore ma assegna valori successivi di K a blocchi successivi.

3) **SHIFTING**: Le cifre della chiave K vengono divise a gruppi grandi quanto le cifre del nostro NB.  I frammenti di K vengono poi sovrapposti, sommati ed il risultato viene normalizzato se > NB.

**ES3**: Record key = 17207329, cifre NB = 4. 1720 | 7329 = 1720+7329 = 9049.

4) **FOLDING**: I frammenti di K vengono ripiegati su se stessi e poi sommati. Le cifre in eccesso vengono eliminate. Invertiamo un frammento si ed un frammento no.

**ES4**: Record key = 17207329, cifre NB = 3. 17 | 207 | 329 = 710+207+923 = 1840 = 840.

**FUNZIONE HASH MIGLIORE**
Il metodo migliore è quello che distribuisce le tuple in modo più uniforme possibile.
- Mid-square è quello che si avvicina di più ad un randomizer.
- La divisione generalmente è il metodo migliore.

**DIMENSIONAMENTO E PRESTAZIONI**
Per un file HASH dobbiamo definire:
- Un numero NB di blocchi che definiscono la prima area.
- Un numero NO di blocchi per la overflow area.
- `Costo di accesso = Chash = 1 se standard, >= 2 se overflow.`


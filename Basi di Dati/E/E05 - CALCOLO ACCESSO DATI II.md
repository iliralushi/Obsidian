**USO DEGLI INDICI**
Non usiamo gli indici su tutti gli attributi perchè non è ottimale. Gli indici devono essere mantenuti, quindi è possibile che abbiano un costo maggiore rispetto all'accesso sequenziale.

**CASO DEL JOIN**
Un predicato di join è utilizzabile come argomento di ricerca solo se è possibile sostituire un valore al posto di uno dei due attributi.

**NESTED LOOP METHOD**
``` SQL
QUERY:
SELECT Cognome, Salario
FROM Impiegati as IMP, Dipartimenti as DIP
WHERE Lavoro = ‘Fattorino’
AND Sede = ‘Milano’
AND Imp.dno = Dip.dno
```

Possiamo considerare il nested loop method che va applicato due volte in caso di due relazioni e che consiste nel:
- **LOOP 1**: Scegliere un attributo, che sia IMP o DIP e calcolare i costi di tutte le tuple tranne quelle intaccate dal join.
- **LOOP 2**: Una volta finito procediamo a scegliere tutte le tuple dell'altra relazione affette da indici.

Il costo del join è quindi `C = CR1 + ER1 * CR2.`

**FORMULARIO FINALE**

![[Formule I.png]]![[Formule II.png]]
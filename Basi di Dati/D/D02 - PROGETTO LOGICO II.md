**TRADUZIONE STANDARD**
- Ogni entità è tradotta con una relazione con gli stessi attributi. La chiave sarà la chiave dell'entità stessa.
- Ogni associazione è tradotta con una relazione che comprende l'unione delle chiavi delle entità che verrano indicate in FK ed i suoi attributi.

![[Traduzione standard.png]]

**ASSOCIAZIONE BINARIA 1:N**
In questo caso un entità ha come cardinalità (0,1) / (1,1) mentre l'altra (1,n).
Dato un valore di K1 corrisponderà un solo valore di K2, quindi c'è una dipendenza funzionale tra K1 e K2. Possiamo effettuare due soluzioni:
- PRIMA SOLUZIONE: Cambiare lo schema tradizionale. L'unico cambiamento sarà togliere la chiave forte e segnalarla come FK. 
- SECONDA SOLUZIONE: Possiamo fare due relazioni, quella dell'entità "debole" comprende tutti gli attributi e le chiavi, avrà come chiave la sua e le altre chiavi vengono espresse come FK. Quella "forte" rimane invariata rispetto allo schema tradizionale.

In caso di identificatori esterni esse rimangono chiavi che andranno espresse.

![[Traduzione standard non funziona.png]]![[Associazione binaria (1,n).png]]
![[ID Esterno.png]]

**ASSOCIAZIONE BINARIA 1:1**
Possiamo tradurre tutto con un unica relazione che comprende tutti gli attributi e le chiavi. La chiave primaria va a scelta, quindi sarà K1 o K2. Quella non primaria verrà citata come AK. 
- Se la cardinalità di E2 è (0,1) e la cardinalità di E1 è (1,1) allora la chiave scelta sarà K2. Se scegliessimo come chiave K1 allora non avremmo modo di esprimere i casi dove E2 è nullo e non usufruisce di E1.
- Se la cardinalità è (0,1) da entrambe le parti allora le relazioni sono per forza due siccome sarà impossibile assegnare una chiave in assenza di entrambe le istanze.

![[Associazione 1.1.png]]

**PER RIASSUMERE...**
- Per associazioni (n,m) dobbiamo usare tre relazioni.
- Per associazioni (1,n) possiamo usare due relazioni, una che "ingloba" l'altra e avere la chiave dell'altra entità in FK e l'altra entità rappresenta i propri dati.
- Per associazioni (1,1) possiamo usare una relazione che comprende tutto e avrà una AK. L'unico caso in cui cambia è quando entrambe le entità hanno cardinalità (0,1) le relazioni saranno due.

**AUTO-ASSOCIAZIONI**
- CASO (N:M): Viene tradotta con una relazione per l'entità ed una per la associazione, quest'ultima contiene due volte la chiave. La soluzione è: STATO (**NOME**, AREA) e CONFINA        (**STATO_A**, **STATO_B**) con FK (STATO_A REFERENCES STATO) e (STATO_B REFERENCES STATO).

![[Auto-Associazione N,M.png]]

- CASO (1:N): E' traducibile con una sola relazione che contiene due volte l'attributo chiave, una volta come chiave e una come riferimento all'istanza di entità, con nome diverso per specificare il ruolo. DIPENDENTE (**MATR**, NOME, **CAPO**) con FK (CAPO REFERENCES DIPENDENTE).

![[Auto-Associazione 1,N.png]]

- CASO (1:1): Su entrambi i rami è meglio specificare il ruolo, conviene la soluzione a due relazioni. DIPENDENTE (**MATR**, NOME) e SPOSATI (**MOGLIE**, MARITO) con FK1 (MOGLIE REFERENCES DIPENDENTE) e FK2 (MARITO REFERENCES DIPENDENTE) e come AK una delle due chiavi, come nel caso dell'associazione binaria.

![[Auto-Associazione 1,1.png]]

**SUPERCHIAVE**
Essa è la chiave ottenuta componendo le chiavi di tutte le entità presenti, quindi una chiave composta il cui set di componenti non è minimale, quindi la chiave singola è un sottoinsieme della superchiave.
Il **modello relazionale** è una teoria matematica che offre gli strumenti per analizzare e modificare le basi di dati in termini di valori **atomici**.

- Definizione informale
	- E' una tabella dotata di colonne e righe. C'è uno schema iniziale che dice com'è strutturato il dato e ogni riga rappresenta n istanze.

- Definizione formale
	- E' un prodotto cartesiano su n domini. D1 x D2 x Dn... Insieme di tutte le n-ple (tuple).
	- Ci sono delle relazioni R tra domini. Un qualunque sottoinsieme di D tale che:
	  R contiene D1 x D2 x Dn.

Il grado della relazione è il numero di domini.
La cardinalità della relazione sono il numero di tuple.
L'attributo è il nome assegnato ad un dominio in una relazione.

Lo schema di una relazione R è R(attr1, ... , attrN), ogni attributo deve avere un nome distinto.
ESEMPIO: R1(A, B) con R la relazione e A, B gli attributi.

L'istanza della relazione R è l'insieme di tuple su (attr1, ... ,attrN).
ESEMPIO: Dato lo schema R1(A, B) <a, 1> e <b, 3> sono le istanze.

Uno schema di basi di dati è un insieme di schemi di relazione. R = {R1(X1), ... ,Rk(Xk)}
Tutti i nomi di relazioni della base di dati devono essere differenti.

Un istanza della base di dati su uno schema R = {R1(X1), ... ,Rk(Xk)} è un insieme di relazioni
r = (r1, ... ,rn) con Ri in relazione con RI.









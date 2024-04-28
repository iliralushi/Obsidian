**DEFINIZIONE INFORMALE MODELLO RELAZIONALE**
![[Tabella informale.png]]

**DEFINIZIONE FORMALE MODELLO RELAZIONALE**
- DOMINIO: Un qualunque insieme di valori (dominio dei nomi di città, dominio dei voti...)
- PRODOTTO CARTESIANO: L'insieme di tutte le tuple componibili prendendo gli elementi dei vari domini. Si ha <d1, d2, dN> con d1 appartenente al primo dominio, d2 al secondo etc...
- RELAZIONE: Un qualunque sottoinsieme del prodotto cartesiano di N domini.

![[Esempio definizione formale modello relazionale.png]]

**PROPRIETÀ DELLE RELAZIONI**
- GRADO: Il numero di domini (n).
- CARDINALITÀ: Il numero di tuple.
- ATTRIBUTO: Nome ben distinto dato ad un dominio in una relazione.
- SCHEMA: Comprende il nome che diamo alla relazione seguita dalla lista ordinata dei nomi degli attributi (tabella(attributo1, attributo2, ... , attributoN)).
- ISTANZA: Un insieme di tuple dello schema. Se lo schema dell'esempio in alto è studente(MATR, NOME, CITTÀ, C-DIP) allora una istanza sarà "307 Giovanni Milano Log".

**CONFRONTO DELLA TERMINOLOGIA**
![[Confronto della terminologia 1.png]]

**PROPRIETÀ DELLE BASI DI DATI**
- SCHEMA: Un insieme di schemi di relazione.
- ISTANZA: Un insieme di istanze di relazione. Date due relazioni R1(A,B) con varie e tuple e R2(C,D) con altrettante varie tuple si avrà che lo schema è R1(A,B) e R2(C,D) mentre l'istanza comprende tutto.

**VINCOLI DI INTEGRITÀ**
Sono vincoli che escludono alcune istanze che pur essendo sintatticamente corrette non sono accettate perchè non possibili nel mondo applicativo.

**NOZIONE DI CHIAVE**
Sottoinsieme di attributi che possiede le proprietà di unicità e minimalità.
- UNICITÀ: Non esistono due tuple con chiave uguale.
- MINIMALITÀ: Sottraendo un qualsiasi attributo dallo schema si perde la unicità. Per esempio la chiave (matr, nome) è sbagliata perchè sottraendo l'attributo nome noi non perdiamo unicità.
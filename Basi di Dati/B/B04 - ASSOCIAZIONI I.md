**ASSOCIAZIONE**
Un associazione viene fatta per unire due o più entità. La chiave di un istanza dell'associazione è sempre composta ed è composta dalle chiavi delle entità che vengono unite. L'associazione di per sè non può avere chiavi, però compongono il tipo come in questo esempio.

![[Associazione.png]]

**VINCOLO DI INTEGRITÀ**
Il fatto che la chiave dell'associazione è una chiave composta derivata dalle chiavi delle entità porta ad un vincolo di integrità. Ogni valore componente di una chiave di una istanza di associazione deve essere presente come chiave di istanza dell'entità associata.

![[Vincolo di integrità.png]]

**CARDINALITÀ DELLE ASSOCIAZIONI**
Per cardinalità si intende il numero di volte che una data istanza di entità deve oppure può partecipare all'associazione.
- (0,1) - può esserci una sola istanza.
- (1,1) - deve esserci una sola istanza.
- (0,n) - possono esserci più istanze.
- (1,n) - devono esserci una o più istanze.
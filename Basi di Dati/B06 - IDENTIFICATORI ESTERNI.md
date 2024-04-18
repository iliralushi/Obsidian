**ENTITA DEBOLE** 
Un entità debole è un entità che contiene un istanza la cui presenza è accettata solo se è presente un altra istanza di un entità forte da cui dipende l'entità debole.
- In caso di eliminazione dell'entità forte viene eliminata anche l'entità debole.
- L'identificatore dell'entità debole DEVE contenere l'identificatore dell'entità forte.

**IDENTIFICATORE ESTERNO**
L'entità dipendente è quella forte, l'entità auto quella debole. Quando nel testo un entità dipende da un altra usiamo un identificatore esterno. La chiave di auto sarà matricola e un attributo di auto, quindi in questo caso la coppia (matr, n_a). Sto associando la matricola al numero dell'auto.

![[Identificatore Esterno.png]]

**REGOLE**
- L'identificatore esterno si può applicare SOLO con un'associazione binaria.
- Un identificatore esterno può coinvolgere un altro identificatore esterno a patto che non si creino cicli di identificazione.
- La cardinalità dell'entità a cui si applica un identificatore esterno DEVE essere (1,1).


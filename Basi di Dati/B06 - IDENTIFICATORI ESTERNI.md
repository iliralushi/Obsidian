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

**COME USARE GLI IDENTIFICATORI ESTERNI**
- Di solito si usa un identificatore esterno quando un'istanza di entità deve fare una sola volta un istanza di un altra entità. 
- Ragionare in "data x entità oppure data x e y entità allora z sarà impattata."
- Se è semplice usiamo l'identificatore esterno sull'attributo/i che ci interessa.
- Se è composta, quindi ci sono due entità forti e una debole, reifichiamo, quindi creiamo un'altra entità intermezzo che avrà come chiave la combinazione delle chiavi delle entità forti. Ci saranno anche 2 associazioni in più (deve essere binario)

**ESEMPIO IDENTIFICATORI ESTERNI COMPOSTI**

![[Identificazione esterna composta I.png]]
![[Identificazione esterna composta II.png]]![[Identificazione esterna composta III.png]]

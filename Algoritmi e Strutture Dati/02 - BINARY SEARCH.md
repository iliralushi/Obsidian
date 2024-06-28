**PROBLEMA**
- **INPUT**: Un array che contiene valori ordinati non decrescentemente e un valore **key** dello stesso tipo degli elementi dell'array.
- **OUTPUT**: La posizione dell'elemento **key**.

**PRIMA SOLUZIONE**
Fare una scansione lineare che parte dal primo elemento e confrontarlo con key. Se key esiste allora ritorno l'indice, altrimenti ritorno -1. La soluzione funziona ma possiamo avere un costo computazionale migliore.

**IDEA BINARY SEARCH**
- Confronto key con l'elemento centrale nell'array.
- Il caso base è quando l'elemento centrale è key, possiamo ritornare l'indice.
- Se non è così procediamo coi casi ricorsivi, ovvero se `L[k] > key` allora vado nella sottosequenza di sinistra, altrimenti in quella di destra.

**INDICE CENTRALE**
L'indice si trova con la seguente formula:
- `k = ⌊i+j/2⌋` con i l'indice a sinistra dell'array e j quello a destra.

**VERSIONE ITERATIVA**
Costo computazionale: `O(log(n)).`

Questo perchè abbiamo che, indipendentemente dal numero di elementi nell'array il costo del while sarà sempre logaritmico, inoltre tutte le altre istruzioni al di fuori del while hanno costo costante.

``` C++
BinarySearch(L, n, key)
{
	i = 0;
	j = n-1;

	while (i <= j) do
	{
		k = ⌊i+j/2⌋;
		
		if (L[k] == key) then
			return k;
			
		if (L[k] > key) then
			j = k-1;
		else
			i = k+1;	
	}
	
	return -1;
}
```

**VERSIONE RICORSIVA**
Chiamata principale: `BinarySearch(L, 0, n-1, key);`

Prendiamo indici come parametri e passiamo la dimensione dell'array originale nella chiamata principale. 

Se il caso base non è stato soddisfatto allora passiamo al caso ricorsivo, questo va avanti finchè ci troviamo in una situazione dove abbiamo raggiunto un caso base, nel mentre le chiamate fatte vengono lasciate in sospeso. Una volta raggiunto un caso base che in questo caso è il ritorno di un numero passiamo al ritroso ad ogni chiamata il valore trovato nel caso base, fino ad arrivare alla prima chiamata.

TUTTI I POSSIBILI FLUSSI DI ESECUZIONE TERMINANO CON UN RETURN!

``` C++
BinarySearch(L, i, j, key)
{
	if (i < j) then
		return -1;
		
	k = ⌊i+j/2⌋;
	if (L[k] = key) then
		return k;

	if (L[k] > key) then
		return BinarySearch(L, i, k-1, key);
	else
		return BinarySearch(L, k+1, j, key);
}
```
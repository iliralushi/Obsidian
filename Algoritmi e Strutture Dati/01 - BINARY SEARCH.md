- **INPUT**: Una sequenza ordinata di N elementi memorizzata in un array L, un elemento key dello stesso tipo degli elementi in L.
- **OUTPUT**: **Posizione** di key in L se key sta in L, altrimenti -1.

**SOLUZIONE NAIVE**
Un ciclo che controlla tutti gli elementi dell'array. Confrontiamo ogni elemento con la chiave; se `L[i] = key` allora restituiamo i, altrimenti restituiamo -1.
- Costa O(n), possiamo fare di meglio.

**BINARY SEARCH**
- Confrontiamo key con l'elemento in posizione centrale k di L.
- Se sono uguali abbiamo trovato k.
- Se `key > L[k]` allora ci spostiamo a destra di k, altrimenti cerco a sinistra.

**TROVARE INDICE K**
L'array va da una posizione i ad una posizione j. Per trovare k facciamo:
- `k = parte bassa di ⌊(i+j)/2⌋.`
- **ES**: Con `i = 0 e j = 9` abbiamo 4.5. Dato che prendiamo la parte bassa il nostro indice vale 4.

**BINARY SEARCH ITERATIVA**
Nel caso peggiore, ovvero quando l'elemento non è presente nell'array si ha che il while verrà eseguito al più `log(n)` volte. Dato che le altre operazioni sono tutte costanti allora l'algoritmo costa al più `O(log(n))`.

``` C++
BinarySearch(L, n, key)
{
	i = 0             
	j = n-1 // O(1)

	while (i < j) // O(log(n))
	{
		k = ⌊i+j/2⌋
		if (L[k] == key)
			return k
		if (L[k] > key)
			j = k-1
		else
			i = k+1
	}

	return -1 // O(1)
}
```

**BINARY SEARCH RICORSIVA**
In questo caso prendiamo gli indici come parametri e la dimensione dell'array la passiamo nella chiamata principale, che è obbligatoria in un algoritmo ricorsivo. 
- **PRIMA CHIAMATA**: `i = 0, j = 9, quindi k = 4.` L'array finisce nel valore 11, che è diverso dalla nostra chiave, inoltre `L[k] < key` quindi i diventerà k+1 e j rimane invariato. La prima chiamata viene sospesa e passiamo alla seconda.
- **SECONDA CHIAMATA**: `i = 5, j = 9, quindi k = 7.` L'array finisce nel valore 23, che è uguale alla nostra chiave. Ritorniamo quindi k che è 7, passando al ritroso il valore 7 anche alle altre chiamate di funzione.

``` C++
// Supponiamo che l'array è composto da 10 elementi
// L = [1, 2, 5, 10, 11, 14, 17, 23, 24, 30] e key = 23

BinarySearch(L, i, j, key)
{
	if (i > j)
		then
			return -1
	else 
		k = ⌊(i+j)/2⌋
		if (L[k] == key)
			return k
		if (L[k] > key)
			then
				return BinarySearch(L, i, k-1, key)
			else
				return BinarySearch(L, k+1, j, key)
}

// CHIAMATA PRINCIPALE: BinarySearch(L, 0, n-1, key)
```
**PROBLEMA**
- **INPUT**: Una sequenza di valori in un array A che appartengono ad un insieme ordinabile.
- **OUTPUT**: A ordinato in modo non decrescente.

**DIVIDE ET IMPERA**
Il Merge Sort è un algoritmo di sorting che sfrutta il divide et impera:

- **DIVIDE**: Dividi l'array in sequenze di n/2 elementi ciascuna.
- **IMPERA**: Ordina ciascuna sequenza ricorsivamente.
- **COMBINA**: Fondi le due metà ordinate in un unica sequenza (**MERGE**).

**IDEA MERGE SORT**
Chiamata principale: `MergeSort(A, 0, n-1);`

- **DIVIDE**: Abbiamo due chiamate di Merge Sort che dividono il nostro array in sequenze di n/2. Una si occupa gli elementi in posizione `0...k` mentre l'altra si occupa degli elementi in posizione `k+1...j`.
- **IMPERA**: Continuiamo ricorsivamente finchè abbiamo sequenze di un elemento che per definizione saranno ordinate.
- **COMBINA**: Usiamo la funzione **MERGE**.
  
Il caso base lo abbiamo quando abbiamo un unico elemento (è già ordinato).

``` C++
MergeSort(A, i, j)
{
	if (i < j) then
	{
		k = (i+j)/2;
		MergeSort(A, i, k);
		MergeSort(A, k+1, j);
		Merge(A, i, k, j);
	}
}
```

**PROCEDURA MERGE**
- **INPUT**: Due porzioni ordinate dell'array A. La prima va dall'indice `i..k`, la seconda invece da `k+1...j`. 
- **OUTPUT**: L'array intero ordinato.

IDEA:
1) Creiamo un array di appoggio B che ha `j-i+1` elementi.
2) Creiamo due indici left e right che li usiamo per scorrere rispettivamente la prima e la seconda porzione dell'array A. Inoltre ci serve un altro indice per scorrere B.
3) Per ogni iterazione confrontiamo gli elementi in `A[left] e A[right]` , il più piccolo dei due elementi finisce in B. Incrementiamo t e left/right rispettivamente. Finiamo l'iterazione quando una delle due metà è stata copiata interamente in B.
4) Se finiamo la porzione di sinistra allora gli ultimi elementi saranno a destra e sono nella posizione giusta. Invece se finiamo la porzione di destra copiamo gli elementi a partire da k nelle ultime posizioni dell'array A.
5) Copiamo gli elementi da B ad A.


``` C++
Merge(A, i, k, j)
{
	B = new array[0..j-i];
	left = i;
	right = k+1;
	idx = 0;
	
	while (left <= k AND right <= j) do
	{
		if A[left] < A[right] then
		{
			A[left] = B[idx];
			left = left + 1;
		}
		else
		{
			A[right] = B[idx];
			right = right + 1;
		}
		
		idx = idx + 1;
	}
	
	for (h = k downto 1) do
	{
		A[j] = A[h];
		j = j-1;
	}
	
	for (h = 0 to t-1) do
		A[i+h] = B[h];
}
```

**COSTO COMPUTAZIONALE**
Il costo di Merge Sort è `O(n * log(n))` perchè abbiamo che Merge al peggio costa j-i confronti, quindi un costo lineare e il divide/impera invece ci costa `2 * log(n)` perchè ad ogni iterazione dividiamo l'input a metà. Possiamo anche trovare il costo usando il Master Theorem:

- a = 2 - b = 2 - d = 1
- `logb(a) = d = O(n * log(n)).`
**DIVIDE ET IMPERA**
Il quick sort è l'altro algoritmo che sfrutta la tecnica di divide et impera.
- **DIVIDE**: Consiste nel scegliere un indice t tra `0 ed n-1,` ordinare gli elementi `> A[t]` a destra e gli elementi `<= A[t]` a sinistra, mettere `A[t]` nel posto giusto, ovvero in mezzo agli elementi di destra e sinistra.
- **IMPERA**: Ordina `A[0..q-1] e A[q+1..n-1]` ricorsivamente.
- **COMBINA**: Niente da fare.

**QUICK SORT**
Scriviamo una procedura che opera nell'array che prenda un pivot, porta tutti gli elementi più grandi del pivot alla sua destra, quelli più piccoli o uguali alla sua sinistra e metta il pivot nel posto giusto. Inoltre deve ordinare ricorsivamente le due sequenze.

``` C++
QuickSort(A, p, r)
{
	if (p < r)
		then
		{
			q = PARTITION(A, p, r)
			QUICKSORT(A, p, q-1) // Chiamata ricorsiva su prima sequenza
			QUICKSORT(A, q+1, r) // Chiamata ricorsiva su seconda sequenza
		}
}
```

**PARTITION**
- **INPUT**: Array A e due indici `0 <= p <= r <= n-1.`
- **OUTPUT**: Indice q, con `p <= q <= r` dove tutti gli elementi a sinistra di `A[q] sono <= di A[q]` e tutti gli elementi a destra di `A[q] sono > di A[q].`

``` C++
PARTITION(A, p, r)
{
	x = A[r] // Assegnazione pivot all'ultimo elemento
	i = p-1

	for j = p to r-1
	{
		if A[j] <= x // Se A[j] <= x allora sposterai l'elemento a sinistra
		             // altrimenti non fai niente. Alla fine si ha che tutti
		             // gli elementi più piccoli saranno da una parte, quelli
		             // più grandi dall'altra
			then
			{
				i = i+1
				swap(A[i], A[j]) // Scambia elemento piccolo nella posizione
				                 // all'inizio dell'array. i parte da zero.
			}
			
	}

	swap(A[r], A[i+1]) // Scambia il pivot con la posizione i+1 che è la
	                   // posizione in mezzo tra il più grande dei piccoli
	                   // e il più piccolo dei grandi.
	                   
	return i+1 // Ritorna l'indice del pivot
}

// Esattamente r - p confronti
```

**COSTO COMPUTAZIONALE**
Abbiamo due casi:
- **PARTIZIONE BILANCIATA**: `q = n-q-1.` A quel punto basta fare il Master Theorem, analogo a quello del Merge Sort con `a = 2, b = 2, d = 1.`
- **PARTIZIONE SBILANCIATA**: `q = 0 e n-q-1 = n-1.` In questo caso dato che partition costa N e abbiamo che dobbiamo eseguire il Quick Sort per ogni elemento. Il costo sarà `O(n^2).`

Il Quick Sort usa meno spazio rispetto al Merge Sort dato che non deve creare un array di supporto. Per poter avvicinarci al caso migliore randomizziamo il pivot.
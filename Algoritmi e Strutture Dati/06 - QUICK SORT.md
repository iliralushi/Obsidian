**PROBLEMA**
- **INPUT**: Una sequenza di valori in un array A che appartengono ad un insieme ordinabile.
- **OUTPUT**: A ordinato in modo non decrescente.

**DIVIDE ET IMPERA**
Il Quick Sort è l'altro algoritmo di sorting che sfrutta il divide et impera:

- **DIVIDE**: Scegli un indice t che va da `0 a n-1`, metti a sinistra tutti gli elementi che sono `<= di A[t],` a destra gli elementi che sono `> A[t]` e infine mettere `A[t]` in posizione q, ovvero in mezzo alle due sequenze create nell'array.
- **IMPERA**: Ordina le due sequenze dell'array, ovvero `A[0...q-1] e A[q+1...n-1]`.
- **COMBINA**: /

**QUICK SORT**
Chiamata principale: `QuickSort(A, 0, n-1);`

- **DIVIDE**: Abbiamo la chiamata di Partition che sceglie l'ultimo elemento dell'array, porta a sinistra gli elementi che son minori/uguali e a destra quelli maggiori. Infine posiziona l'elemento scelto come pivot nella posizione q.
- **COMBINA**: Richiama ricorsivamente QuickSort prima nella metà di sinistra e poi in quella di destra.
- **IMPERA**: /

Il caso base lo abbiamo quando abbiamo un unico elemento (è già ordinato).

``` C++
QuickSort(A, p, r)
{
	if (p < r) then
	{
		q = PARTITION(A, p, r);
		QuickSort(A, p, q-1);
		QuickSort(A, q+1, r);
	}
}
```

**PARTITION**
- **INPUT**: Array A e due indici tale che `0 <= p <= r <= n-1`.
- **OUTPUT**: L'indice del pivot q. Deve essere compreso tra p ed r, inoltre tutti gli elementi di `A[q]` più piccoli devono essere `<=` e quelli più grandi devono essere `>`.

IDEA:
1) Prendiamo come pivot x l'ultimo elemento dell'array, quindi t = r, creiamo un indice i che avrà come valore iniziale p-1.
2) Confrontiamo x con tutti gli elementi dell'array a partire dal primo fino ad arrivare ad x, se l'elemento è minore/uguale allora verranno spostati a sinistra, altrimenti non facciamo nulla (rimangono a destra). Incrementiamo p prima di fare lo scambio.
3) Scambiamo il pivot x e lo mettiamo al suo posto, esattamente in mezzo tra le due sequenze dell'array.

``` C++
PARTITON(A, p, r)
{
	x = A[r];
	i = p-1;
	
	for (j = p to r-1) do
	{
		if (A[j] <= x) then
		{
			i = i+1;
			swap(A[j], A[i]);
		}
	}
	
	swap(A[r], A[i+1]);
	return i+1;
}
```

**COSTO COMPUTAZIONALE**
Il costo del Quick Sort dipende dalla partizione. Generalmente Partition costa r-p confronti, quindi ha un costo lineare.
- **PERFETTAMENTE BILANCIATA**: `q = n-q-1`. In questo caso possiamo applicare il Master Theorem che sarà analogo a MergeSort e abbiamo un costo di `O(n * log(n)).`
- **SBILANCIATA**: `q = 0 e n-q-1 = n-1.` In questo caso abbiamo che dobbiamo eseguire QuickSort per ogni elemento dell'array. Il costo sarà `O(n^2).`

Per poter avvicinarci sempre al caso migliore possiamo randomizzare il pivot.

**CONFRONTO TRA MERGE SORT E QUICK SORT**
Il Merge Sort è meglio perchè seppur più lento (costa di più spazialmente, usa un array aggiuntivo) è più stabile rispetto al Quick Sort.
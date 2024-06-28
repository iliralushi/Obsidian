**PROBLEMA**
- **INPUT**: Una sequenza di valori in un array A che appartengono ad un insieme ordinabile.
- **OUTPUT**: A ordinato in modo non decrescente.

**PRIMA SOLUZIONE**
Provare la permutazione di tutti i valori in A e per ogni permutazione controllare se sono ordinati.
Ha un costo di O(n * n!) che ovviamente è inaccettabile.

**IDEA INSERTION SORT**
- Partiamo dal secondo elemento dell'array A.
- Confrontiamo ogni elemento con il suo precedente. Se esso è più piccolo allora dobbiamo far spazio per l'elemento più piccolo. Procediamo finchè arriviamo ad `A[0]` oppure finchè troviamo un elemento più piccolo di quello attuale. Dopo aver finito i confronti per un elemento passiamo a quello successivo.
- Ci fermiamo quando non abbiamo più elementi.

``` C++
InsertionSort(A, n)
{
	for (j = 1 to n-1) do
	{
		i = j-1;
		tmp = A[j];
		
		while (i >= 0 AND tmp < A[i]) do
		{
			A[i+1] = A[i];
			i = i-1;
		}
		
		A[i+1] = tmp;
	}
}
```

**COSTO COMPUTAZIONALE**
- Il ciclo esterno verrà eseguito sempre a partire da 1 fino a n-1. 
- Il ciclo interno verrà eseguito al più j volte. Questo succede quando tutti gli elementi sono distinti ed in ordine decrescente.
- Le operazioni all'interno dei cicli sono tutte costanti, quindi il costo di Insertion Sort sarà, nel caso peggiore di `O(n^2)`.
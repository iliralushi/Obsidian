**INPUT/OUTPUT DEI SORT**
- **INPUT**: Una sequenza di valori memorizzati in un array dello stesso tipo, quindi che possono essere ordinati.
- **OUTPUT**: La sequenza A ordinata in modo non decrescente.

**SOLUZIONE NAIVE**
Provare la permutazione di tutti gli elementi in A e per ogni permutazione controlliamo se i valori sono ordinati.
- Ovviamente è una soluzione pesantissima, costa O(n * n!) (Bogosort).

**INSERTION SORT**
- Partiamo dal secondo elemento dell'array e lo confrontiamo col primo.
- Se il secondo elemento è più piccolo allora scambiamo di posto gli elementi, altrimenti lasciamo invariato.
- Procediamo per ogni elemento in questo modo, confrontando ogni elemento con tutti gli elementi in precedenza.
- Ci fermiamo quando non abbiamo più elementi.

``` C++
InsertionSort(A, n)
{
	for j = 1 to n-1 // Il for parte dal secondo elemento
	{
		i = j-1 // Elemento precedente
		tmp = A[j] // Elemento successivo ad i

		// Se vero allora A[j] diventa A[i] e decrementa.
		// Se falso allora tmp, quindi A[j] è in i+1.
		
		while (i >= 0 AND A[i] > tmp) 
			do
				{
					A[i+1] = A[i]
					i = i-1
				}
				
		A[i+1] = tmp // Swap finale
	}	
}
```

**COSTO COMPUTAZIONALE**
Il ciclo esterno nel caso peggiore viene eseguito al più n-1 volte mentre il ciclo interno viene eseguito al più n volte. Abbiamo quindi che:
- `T(n) ∈ O(n^2) perchè i cicli nel caso peggiore costano (n-1)n / 2.`
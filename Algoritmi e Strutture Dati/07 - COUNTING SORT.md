**PROBLEMA**
- **INPUT**: Una sequenza di valori in un array A che appartengono ad un insieme ordinabile.
- **OUTPUT**: A ordinato in modo non decrescente.

**COUNTING SORT**
1) Creiamo due array di appoggio; un array C che avrà size di k che sarà il valore massimo contenuto nell'array A e un array B che avrà size di A, esso conterrà gli elementi ordinati di A.
2) Per ogni valore in A contiamo le sue occorrenze nell'array di appoggio C. Per fare ciò aggiungiamo +1 alla cella di `C[A[j]]`.
3) Modifichiamo C. Non deve contenere le occorrenze per ogni numero ma dobbiamo fare in modo che `C[i]` sarà uguale al numero di valori in `A <= i`.  Contiamo questi elementi a partire da 1 e per ogni cella controlliamo le occorrenze. Se in i abbiamo delle occorrenze allora sommiamo le occorrenze di i in quella cella.
4) Usiamo B per copiare gli elementi di A in modo ordinato partendo dal fondo. Sfruttiamo C, che ci dirà quante volte dobbiamo copiare un certo elemento.
5) Copiamo B in A.

``` C++
CountingSort(A, k)
{
	n = length(A);
	B = new array[0..n-1];
	C = new array[0..k];
	
	for (i = 0 to k) do
		C[i] = 0;
		
	for (j = 0 to n-1) do
		C[A[j]] = C[A[j]] + 1;
		
	for (i = 1 to k) do
		C[i] = C[i] + C[i-1];
		
	for (j = n-1 downto 0)
	{
		B[C[A[j]] - 1] = A[j];
		C[A[j]] = C[A[j]] - 1;
	}
	
	for (j = 0 to n-1) do
		A[j] = B[j];
}
```

**COSTO COMPUTAZIONALE**
Counting Sort stabile costa `O(n+k)` sia temporalmente che spazialmente.
Counting Sort non stabile invece dipende da k. Può avere un lower bound di n come lo può avere di `2^n`.
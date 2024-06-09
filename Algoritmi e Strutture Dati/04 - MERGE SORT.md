**DIVIDE ET IMPERA**
Il merge sort è un algoritmo di sorting che sfrutta il concetto di divide et impera.
- **DIVIDE**: Dividi l'array in due sequenze di n/2 elementi ciascuna.
- **IMPERA**: Agisci su entrambe le sequenze ordinandole ricorsivamente.
- **COMBINA**: Fondi le due metà ordinate in un unica sequenza ordinata (MERGE).

**MERGE SORT**
Scriviamo una procedura ricorsiva che divide il nostro array in due, che operi sulle due metà e ordini l'array e che unisca le due metà in un unico array ordinato.
- **CASO BASE**: Quando l'elemento è uno, quindi già ordinato.

``` C++
MergeSort(A, i, j)
{
	if (i < j) // Finchè abbiamo elementi divisibili allora:
		then
		{
			k = ⌊i+j/2⌋
			MergeSort(A, i, k) // Divisione della prima sottometà
			MergeSort(A, k+1, j) // Divisione della seconda sottometà
			Merge(A, i, k, j) // Fondere le metà ordinate in una
		}
}

// CHIAMATA PRINCIPALE: MergeSort(A, 0, n-1)
```

**MERGE**
L'idea è quella di avere tre indici; un indice left che controlla la prima sequenza, un indice right che controlla la seconda sequenza, un array di supporto dove inseriamo i nostri elementi ordinati e un indice t che usiamo per scorrere l'array di supporto. Costa j-i nel caso peggiore (1).

- **INPUT**: Array diviso in due sequenze già ordinato. Una va da `i a k, l'altra da k+1 a j.`
- **OUTPUT**: La porzione di array che va da i a j ordinata.

``` C++
Merge(A, i, k, j)
{
	 B[0..j-i] // Array di appoggio per inserire gli elementi
	 l = i // Indice per scorrere l'array di sinistra
	 r = k+1 // Indice per scorrere l'array di destra
	 t = 0 // Indice per scorrere B

	// Confrontiamo ad ogni istanza le due sequenze. Se il primo elemento
	// della sequenza di sinistra è più piccolo della sequenza di destra
	// allora lo inseriamo nell'array di appoggio ed aumentiamo di 1 solo
	// l'indice dell'array da cui vien preso l'elemento. Ad ogni iterazione
	// viene aggiunto un elemento quindi aumentiamo l'indice di B sempre di 1.
	
	while (l <= k AND r <= j) do
	{
		if A[l] <= A[r]
			then 
			{
				B[t] = A[l]
				l = l+1
			}
			else 
			{
				B[t] = A[r]
				r = r+1
			}
			
		t = t+1
	}

	// Copia gli elementi rimasti nell'array di A che saranno i più
	// grandi e li mette negli ultimi indici dell'array.
	
	for h = k downto 1 do
	{
		A[j] = A[h]
		j = j-1
	}

	// Copia gli elementi da B in A
	
	for h = 0 to t-1 do
		A[i+h] = B[h]
}
```

**COSTO COMPUTAZIONALE**
Per trovare il costo del Merge Sort usiamo il Master Theorem.
Abbiamo `a = 2, b = 2, d = 1.` 
`logb(a) = d = 1, quindi T(n) ∈ O(n^logb(a) * log(n)) = nlogn `
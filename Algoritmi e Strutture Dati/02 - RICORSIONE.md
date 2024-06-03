**FUNZIONE RICORSIVA**
Una funzione ricorsiva è una funzione che richiama se stessa.
- Ci devono essere dei **CASI BASE** in cui la funzione restituisce un valore senza chiamare se stessa.
- Ci sono dei **CASI NON BASE** in cui la funzione restituisce un risultato chiamando se stessa con parametri che si avvicinano sempre di più ai casi base.

**FATTORIALE**
Con `n = 5` la funzione esegue cinque chiamate. Ogni chiamata di funzione fino al caso base viene lasciata in sospeso. Una volta arrivata al caso base la funzione si ferma e inizia a restituire il nostro risultato, quindi `5 * 4 * 3 * 2 * 1.`

``` C++
Factorial(n)
{
	if (n == 1)
		then
			return 1 // CASO BASE
		else
			return n * Factorial(n-1) // CASO RICORSIVO
}
```

**FIBONACCI**
In questo caso abbiamo un return più complesso.
- Partiamo con `n = 5.` La funzione verrà chiamata sul 5, il return ci dice che deve restituire Fibonacci(n-1) + Fibonacci(n-2). `Fib(5) si scompone in Fib(4) e Fib(3) quindi.` Dato che è una funzione ricorsiva a sua volta Fib(4) e Fib(3) verranno scomposte. Fib(4) diventa `Fib(3) + Fib(2)` mentre Fib(3) diventa `Fib(2) + Fib(1).` e chiamate continuano finchè non arriviamo al caso base, una volta arrivati a Fib(1) o Fib(0) restituiamo zero.
- Arrivati a quel punto ci resta soltato restituire i valori alla chiamata di funzione principale. Fib(2) per esempio vale 2, dato che viene scomposta in Fib(1) + Fib(0) ed entrambe restituiscono 1.

``` C++
Fibonacci(n)
{
	if (n == 0 OR n == 1)
		then
			return 1
		else
			return Fibonacci(n-1) + Fibonacci(n-2)
}
```

**MASTER THEOREM**
Serve per stabilire la complessità temporale degli algoritmi divide-et-impera.
`T(n) = c₁ // CASO BASE`
`T(n) = a * T(n/b) + c₂ * nᵈ // CASO RICORSIVO`

- **n**: Indica la dimensione del problema originale.
- **a**: Indica il numero dei sottoproblemi. Nel caso della binary search è uno perchè l'array rimane unico, nel caso del merge sort è due perchè si divide l'array in due sequenze.
- **n/b**: indica la dimensione del sottoproblema. Nella binary search è due perchè ogni sottoproblema ha metà della dimensione dell'array.
- **c₂ * nᵈ**: indica il costo del lavoro extra oltre alle chiamate ricorsive.

`T(n) ∈ O(n^d) se d > logb(a)`
`T(n) ∈ O(n^logb(a) * log(n)) se d = logb(a)`
`T(n) ∈ O(n^logb(a)) se d < logb(a)`

**ESEMPIO MASTER THEOREM CON BINARY SEARCH**
Abbiamo `a = 1, b = 2, d = 0.`
A questo punto confrontiamo `d con logb(a)` e vediamo che `log2(1) = 0 e d = 0.`
Infine possiamo constatare che `T(n) ∈ O(n^log2(1) * log(n)), quindi O(log(n)).`



**DEFINIZIONE**
Una funzione ricorsiva è una funzione che richiama se stessa.
- **CASI BASE**: Sono obbligatori. Sono i casi che fan terminare la funzione, ritornano un risultato senza chiamare se stessa (sottoproblemi).
- **CASI NON BASE**: Sono i casi che restituiscono un valore chiamando se stessa con parametri che si avvicinano sempre di più al caso base.

**ESEMPIO: FATTORIALE**

``` C++
Fattoriale(n)
{
	if (n == 0) then
		return 1;
	else
		return n * Fattoriale(n-1);
}
```

Ogni chiamata svolta prima di raggiungere il caso base viene lasciata in sospeso. Una volta raggiunto il caso base svolgiamo tutti i ritorni al ritroso.
Elenco di chiamate e ritorni con `N = 4`:

**CHIAMATE**
1) 4 è diverso da 1, allora ritorno 4 * fattoriale(3).
2) 3 è diverso da 1, allora ritorno 3 * fattoriale(2).
3) 2 è diverso da 1, allora ritorno 2 * fattoriale(1).
4) 1 è uguale ad 1.

**RITORNI**
1) Nell'ultima chiamata raggiungiamo il caso base, ritorniamo quindi 1.
2) Ritorniamo 2 * fattoriale(1) quindi 2 * 1.
3) Ritorniamo 3 * fattoriale(2) quindi 3 * 2 * 1.
4) Ritorniamo 4 * fattoriale(3) quindi 4 * 3 * 2 * 1.

**ESEMPIO: FIBONACCI**
In questo caso abbiamo un return più complesso.
- Partiamo con `n = 5.` La funzione verrà chiamata sul 5, il return ci dice che deve restituire Fibonacci(n-1) + Fibonacci(n-2). `Fib(5) si scompone in Fib(4) e Fib(3) quindi.` Dato che è una funzione ricorsiva a sua volta Fib(4) e Fib(3) verranno scomposte. Fib(4) diventa `Fib(3) + Fib(2)` mentre Fib(3) diventa `Fib(2) + Fib(1).` e chiamate continuano finchè non arriviamo al caso base, una volta arrivati a Fib(1) o Fib(0) restituiamo zero.
- Arrivati a quel punto ci resta soltato restituire i valori alla chiamata di funzione principale. Fib(2) per esempio vale 2, dato che viene scomposta in Fib(1) + Fib(0) ed entrambe restituiscono 1.

``` C++
Fib(n)
{
	if (n == 0 OR n == 1) then
		return 1;
	else
		return Fib(n-1) + Fib(n-2);
}
```

Abbiamo un return più complesso. Vale la situazione di prima. Questo problema forma una specie di albero, ogni chiamata di funzione la scomponiamo due volte fino ad arrivare al caso base.
Elenco di chiamate e ritorni con `N = 4`:

**CHIAMATE**
1) 4 è diverso dal caso base, allora ritorno Fib(3).
2) 3 è diverso dal caso base, allora ritorno Fib(2).
3) 2 è diverso dal caso base, allora ritorno Fib(1) che corrisponde al caso base.
4) 2 è diverso dal caso base, allora ritorno Fib(0) che corrisponde al caso base.
5) 3 è diverso dal caso base, allora ritorno Fib(1) che corrisponde al caso base.
6) 4 è diverso dal caso base, allora ritorno Fib(2).
7) 2 è diverso dal caso base, allora ritorno Fib(1) che corrisponde al caso base.
8) 2 è diverso dal caso base, allora ritorno Fib(1) che corrisponde al caso base.

**RITORNI**
Partiamo dal "sottoalbero" di sinistra, prima volta che raggiungiamo il caso base.
1) Ritorniamo Fib(1) quindi 1.
2) Ritorniamo Fib(0) quindi 1.
3) Ritorniamo Fib(2) quindi Fib(1) + Fib(0) quindi 1+1 = 2.
4) Ritorniamo Fib(1) quindi 1.
5) Ritorniamo Fib(3) quindi Fib(2) + Fib(1) quindi 2+1 = 3.

Scorriamo tutto il "sottoalbero" di destra e arriviamo ai casi base.
6) Ritorniamo Fib(1) quindi 1.
7) Ritorniamo Fib(0) quindi 1.
8) Ritorniamo Fib(2) quindi Fib(1) + Fib(0) quindi 1+1 = 2.
9) Ritorniamo Fib(4) quindi Fib(3) + Fib(2) quindi 3+2 = 5.

**EQUAZIONE DI RICORRENZA**
Sono metodi che stabiliscono la complessità temporale di un algoritmo.
1) Metodo iterativo (fattoriale, fibonacci...)
2) Albero di ricorsione e Master Theorem.

**MASTER THEOREM**
Strumento matematico utilizzato per risolvere equazioni di ricorrenza. Serve per trovare la complessità temporale di un algoritmo basato su divide-et-impera.

``` C++
T(n) = c₁ // caso base
T(n) = a * T(n/b) + c₂ * nᵈ // caso ricorsivo
```

**SIGNIFICATO LETTERE**
- T(n): Indica la dimensione del problema originario.
- a: Indica il numero di sottoproblemi.
- n/b: Indica la dimensione del sottoproblema.
- c₂ * nᵈ: Indica il costo extra oltre alle chiamate ricorsive.

Prendendo come esempio la binary search abbiamo che:
- a = 1 perchè il problema viene diviso in un sottoproblema.
- b = 2 perchè una volta diviso l'array la dimensione viene dimezzata.
- d = 0 perchè le altre operazioni costano O(1).

**SOLUZIONE MASTER THEOREM**

``` C++
T(n) ∈ O(nᵈ) // d > logᵦ(a)
T(n) ∈ O(nˡᵒᵍᵇ⁽ᵃ⁾ * log(n)) // d == logᵦ(a)
T(n) ∈ O(nˡᵒᵍᵇ⁽ᵃ⁾) // d < logᵦ(a)
```

**MASTER THEOREM CON BINARY SEARCH**
Confrontiamo d con logᵦ(a). Osserviamo che:
- `d = 0 e logᵦ(a) = 0, quindi d = logᵦ(a), quindi:`
- `T(n) ∈ O(n⁰ * log(n)) = O(log(n)).`




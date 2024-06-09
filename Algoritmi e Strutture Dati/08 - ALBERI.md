**DEFINIZIONE DI ALBERO**
Un albero radicato T = (V,E) è una coppia di insiemi con le seguente proprietà:
- V è un insieme di nodi.
- E è un insieme di archi orientati che congiungono nodi di V.
- Un nodo di V sarà radice di T.
- Ogni nodo, a parte la radice di T, ha un solo arco entrante (no cicli, un cammino unico).

**DEFINIZIONE RICORSIVA**
Un albero radicato è dato da:
- Un albero vuoto oppure da:
- Un nodo **radice** ed uno o più **sottoalberi**. La radice è connessa ad ogni radice del sottoalbero.

**ALTEZZA E LIVELLO**
- **LIVELLO DI UN NODO**: Lunghezza del cammino semplice dalla radice ad un nodo.
- **ALTEZZA DELL'ALBERO**: Profondità massima delle foglie.

**ALBERO BINARIO**
Un albero binario è un albero che può avere 0, 1 o 2 figli.

**ALBERO COMPLETO + PERFETTAMENTE BILANCIATO**
- Un albero è completo se ogni nodo ha 0 figli oppure 2 figli. 
- Un albero è perfettamente bilanciato se le foglie sono tutte allo stesso livello.
- Un albero può essere entrambi.

**TEOREMA**
- **ENUNCIATO**: `Un albero completo e perfettamente bilanciato di altezza >= 0 di zero ha esattamente n = 2^h+1 - 1 nodi con 2^h foglie.`

Dimostriamo che un albero completo e perfettamente bilanciato ha `2^h` foglie tramite il principio di induzione.
- **CASO BASE**: Un albero ha altezza h = 0, quindi ha 1 nodo.
- **IPOTESI INDUTTIVA**: Un albero di altezza `h - 1 >= 1 ha 2^h-1` foglie.
- **PASSO INDUTTIVO**: L'albero di altezza h contiene un albero di altezza h-1; le sue foglie sono i nodi del penultimo livello dell'albero. Ogni nodo del penultimo livello ha esattamente due figli. Il numero di foglie quindi è `2^h-1 * 2 = 2^h`
  
Dimostriamo che un albero completo e perfettamente bilanciato ha `2^h+1-1`:
- Per ogni `i = 0...h` il numero di nodi a livello i è uguale al numero di foglie di un albero binario completo perfettamente bilanciato di altezza i. Quindi il numero di nodi equivale al numero di `∑i=0 2^i = 2^h+1 - 1`.

**NODO DI UN ALBERO BINARIO**
- **CAMPO LEFT**: Puntatore al figlio sinistro.
- **CAMPO RIGHT**: Puntatore al figlio destro.
- **CAMPO VAL**: Contiene il valore del nodo.

**RICORSIONE NELL'ALBERO**
- **PROBLEMA1**: Contare i nodi dell'albero T.
- **CASO BASE**: L'albero è vuoto, quindi il numero di nodi è pari a zero.
- **CASO RICORSIVO**: L'albero è non vuoto. Il numero di nodi è equivalente alla somma dei nodi del sottoalbero sinistro + i nodi del sottoalbero destro + 1.

``` C++
ContaNodi(T)
{
	if (T = NIL) then
		return 0
	else
		return 1 + ContaNodi(t.left) + ContaNodi(t.right)
}

// In questa versione alternativa la radice è il caso base.
// Dobbiamo salvare le chiamate ricorsivamente su una variabile
// altrimenti andrebbero perse.

ContaNodi(T)
{
	if (t.left = t.right = NIL) then
		return 1
	else
		n_s = 0, n_d = 0
		if (t.left = NOT NIL) then
			n_s = ContaNodi(t.left)
		if (t.right = NOT NIL) then
			n_d = ContaNodi(t.right)
		return 1 + n_s + n_d
}
```

- **PROBLEMA2**: Calcolare l'altezza di un albero binario T.
- **CASO BASE**: L'albero è vuoto, restituisco -1.
- **CASO RICORSIVO**: Albero non vuoto. L'altezza è uguale ad 1 + il massimo dell'altezza del sottoalbero sinistro e destro.
  
``` C++
Altezza(T)
{
	if (T = NIL) then
		return -1
	if (t.left = NIL AND t.right = NIL) then
		return 0
	else
		return 1 + max{Altezza(t.left), Altezza(t.right)
}

// Radice come caso base. Dobbiamo salvare come prima le chiamate
// su una variabile altrimenti andrebbero perse.

Altezza(T)
{
	if (t.left = t.right = NIL) then
		return 0
	else
		n_s = 0, n_d = 0
	if (t.left = NOT NIL) then
		h_s = Altezza(t.left)
	if (t.right = NOT NIL) then
		h_d = Altezza(t.right)
	return 1 + max(h_s, h_d)
}
```

**DEPTH FIRST SEARCH ALBERI**
La visita di un albero in DFS avviene in maniera ricorsiva ed implicitamente usiamo una **PILA**. 
Il costo computazionale è di `O(n * f(n)) dove O(f(n)) è il costo di analisi per nodo.` Abbiamo tre tipi di DFS:
- **PRE-ORDER**: Prima visito la radice, poi il sottoalbero sinistro e infine il sottoalbero destro.
- **IN-ORDER**: Prima visito il sottoalbero sinistro, poi la radice e infine il sottoalbero destro.
- **POST-ORDER**: Prima visito il sottoalbero sinistro, poi il sottoalbero destro e infine la radice.

``` C++
// DFS PRE ORDER

DFS1(T)
{
	if (T = NOT NIL) then
	{
		// Analisi di t
		// print t.val
		DFS1(t.left)
		DFS1(t.right)
	}
}

// DFS IN ORDER

DFS2(T)
{
	if (T = NOT NIL) then
	{
		DFS2(t.left)
		// Analisi di t
		// print t.val
		DFS2(t.right)
	}
}

// DFS POST ORDER

DFS3(T)
{
	if (T = NOT NIL) then
	{
		DFS3(t.left)
		DFS3(t.right)
		// Analisi di t
		// print t.val
	}
}
```

**BREADTH FIRST SEARCH ALBERI**
La visita BFS per un albero avviene in maniera iterativa. I nodi vengono inseriti in una **CODA**. Costa sempre `O(n * f(n)).`
- Prima visita la radice, poi i nodi nel livello sotto, poi il livello sotto ancora fino ad arrivare alle foglie.

``` C++
BFS(T)
{
	Q = new_queue()
	enqueue(Q, T) // Inseriamo la radice nella coda fuori dal ciclo
	
	while NOT is_empty_queue(Q) do
	{
		u = dequeue(Q) // Variabile si salva il nodo che esce dalla coda
		               // per decidere se dobbiamo inserire altri nodi
		               // in coda.

		// Analisi di t
		// print t.val
		if (u.left = NOT NIL) then
			enqueue(Q, u.left)
		if (u.right = NOT NIL) then
			enqueue(Q, u.right)
	}
}
```


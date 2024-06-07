**DEFINIZIONE DI ALBERO**
Un albero radicato T = (V,E) è una coppia di insiemi con le seguente proprietà:
- V è un insieme di nodi.
- E è un insieme di archi orientati che congiungono nodi di V.
- Un nodo di V sarà radice di T.
- Ogni nodo, a parte la radice di T, ha un solo arco entrante (no cicli, un cammino unico).

**DEFINIZIONE RICORSIVA**
Un albero radicato è dato da:
- Un albero vuoto.
- Un nodo radice ed uno o più sottoalberi. La radice è connessa ad ogni radice del sottoalbero.

**ALTEZZA E LIVELLO**
- **LIVELLO DI UN NODO**: Lunghezza del cammino semplice dalla radice ad un nodo.
- **ALTEZZA DELL'ALBERO**: Profondità massima delle foglie.

**ALBERO BINARIO**
Un albero binario è un albero che può avere 0, 1 o 2 figli. Il figlio sinistro e il figlio destro sono definiti dalla struttura dell'albero, non possono essere scambiati.

**ALBERO COMPLETO + PERFETTAMENTE BILANCIATO**
- Un albero è completo se ogni nodo ha 0 figli oppure 2 figli. 
- Un albero è perfettamente bilanciato se le foglie sono tutte allo stesso livello.
- Un albero può essere entrambi.

**TEOREMA**
- **ENUNCIATO**: Un albero completo e perfettamente bilanciato di altezza `>=0` di zero ha esattamente `n = 2^h+1 - 1 nodi con 2^h foglie.`

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

**COME USARE LA RICORSIONE NELL'ALBERO**
- **PROBLEMA**: Dobbiamo contare i nodi di un albero binario.
- **CASO BASE**: L'albero è vuoto, quindi il numero di nodi è pari a zero.
- **CASO RICORSIVO**: L'albero è non vuoto. Il numero di nodi è equivalente alla somma dei nodi del sottoalbero sinistro + i nodi del sottoalbero destro + 1 (radice).

``` C++
ContaNodi(T)
{
	if (T = NIL) then
		return 0
	else
		return 1 + ContaNodi(t.left) + ContaNodi(t.right)
}

// Versione alternativa dove il caso base è la radice

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

// Calcolare l'altezza di un albero

Altezza(T)
if (T = NIL) then
	return -1
if (t.left = NIL AND t.right = NIL) then
	return 0
else
	return 1 + max{Altezza(t.left), Altezza(t.right)}

// Versione alternativa dove il caso base è la foglia

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

**DFS E BFS ALBERI**
- **PRE-ORDER**: Prima visito la radice, poi il sottoalbero sinistro e infine il sottoalbero destro.
- **IN-ORDER**: Prima visito il sottoalbero sinistro, poi la radice e infine il sottoalbero destro.
- **POST-ORDER**: Prima visito il sottoalbero sinistro, poi il sottoalbero destro e infine la radice.

``` C++
// Pre-order
DFS1(T)
{
	if (T = NOT NIL) then
	{
		print t.val
		DFS1(t.left)
		DFS1(t.right)
	}
}

// In-order
DFS2(T)
{
	if (T = NOT NIL) then
	{
		DFS2(t.left)
		print t.val
		DFS2(t.right)
	}
}

// Post-order
DFS3(T)
{
	if (T = NOT NIL) then
	{
		DFS3(t.left)
		DFS3(t.right)
		print t.val
	}
}
```
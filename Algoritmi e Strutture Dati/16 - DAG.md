**DAG**
Un DAG è un Grafo Diretto Aciciclo. Chiamiamo sorgente tutti i nodi che non hanno archi entranti, mentre chiamiamo pozzi i nodi che non hanno archi uscenti.

**ORDINAMENTO TOPOLOGICO**
Dato un DAG G = (V, E) un ordinamento topologico è un ordinamento dei suoi nodi tale per cui se (u, v) ∈ E allora u precede sempre v nell'ordinamento.
- Se un grafo non-DAG ha un arco Back allora è impossibile trovare un ordinamento topologico dato che ci sarà sempre un arco che torna indietro.

**LINEARIZZAZIONE DAG**

**ALGORITMO 1**:
Questo algoritmo funziona perchè avremo sempre un nodo sorgente, quindi un nodo senza archi entranti. Una volta rimosso la sorgente non abbiamo più degli archi che erano entranti per certi nodi nel nostro DAG, possiamo quindi selezionare questi nodi. Alla fine avremo il pozzo che, una volta rimossi tutti i nodi non avrà archi entranti. L'algoritmo consiste nel:

- Scegliere un nodo senza archi entranti.
- Metterlo nell'ordinamento.
- Rimuovere il nodo e i suoi archi dal grafo.
- Ripetere le istruzione fino a quando non abbiamo più nodi nel grafo.

**ALGORITMO 2**:
Eseguiamo una DFS sul DAG e inseriamo i nodi nell'ordine inverso rispetto ai post, quindi dal più grande al più piccolo. Funziona perchè con gli archi tree, cross e forward abbiamo sempre che u è prima di v, mentre non abbiamo archi back.

``` C++
TopologicalSort(G)
{
	visited[1..n] new array
	S = new_stack()

	for all v ∈ v do
		visited[v] = FALSE
	for all v ∈ V do
		if visited[v] = FALSE
			then DFS-TS(G, v)
			
	return S
}

DFS-TS(G, u)
{
	visited[v] = TRUE

	for all (v, u) ∈ E do
		if (visited[u] = FALSE) then
			DFS-TS(G, u)

	push(S, v)
}

// O(V+E)
```
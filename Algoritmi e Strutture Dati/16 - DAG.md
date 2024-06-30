**DEFINIZIONE**
Un DAG è un grafo diretto senza cicli, infatti DAG sta per Directed Acyclic Graph. Esso può avere uno o più nodi detti sorgente che avranno solo archi uscenti, mentre ci sarà un pozzo unico che non avrà archi entranti.

**ORDINAMENTO TOPOLOGICO**
L'ordinamento topologico in un DAG è tale che per ogni coppia di nodi (u, v) ∈ E allora abbiamo che u precederà sempre v nell'ordinamento.

**LINEARIZZAZIONE**
Per linearizzare un DAG, quindi per dargli un ordinamento topologico possiamo procedere in due modi:

1) Il primo algoritmo consiste nel trovare un nodo senza archi entranti, aggiungerlo all'ordinamento, rimuoverlo dal DAG assieme a tutti gli archi uscenti e di iterare questi tre passaggi affinchè il DAG sia vuoto. Funziona perchè abbiamo sempre un nodo da cui partire, ovvero le sorgenti, che non hanno archi entranti. Una volta tolta la sorgente non abbiamo più degli archi entranti che puntavano ad altri nodi, quindi avremo altri nodi da poter selezionare. L'ultimo nodo rimasto sarà un pozzo e, siccome è solo non avrà archi entranti.
   
2) Il secondo algoritmo consiste nell'applicare una DFS sul DAG e inserire i nodi nell'ordinamento topologico inverso rispetto ai valori di `post[].` Funziona perchè in un DAG non abbiamo archi back, solo tree, forward e cross. Dato che usiamo una pila possiamo procedere usando una DFS post-order e una pila per salvare i valori. Il costo computazionale è di `O(V+E).`

``` C++
TopologicalSort(G)
{
	visited[1..n] new array;
	S = new_stack();
	
	for all (v ∈ V) do
		visited[v] = false;
		
	for all (v ∈ V) do
		if (visited[v] = false) then
			DFS-TS(G, v);
	
	return S;
}

DFS-TS(G, v)
{
	visited[v] = true;
	
	for all (v, u ∈ E) do
		if (visited[u] = false) then
			DFS-TS(G, u);
	
	push(S, v)
}
```
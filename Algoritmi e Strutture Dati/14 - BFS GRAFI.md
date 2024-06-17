**BREADTH FIRST SEARCH GRAFI**
La BFS per i grafi è un'estensione della BFS per gli Alberi. Partendo da un nodo si visitano prima i vicini, poi i vicini dei vicini fino a terminare i nodi. Visitiamo quindi a livelli.
- Strategia utilizzata per visitare tutti i nodi raggiungibili **A PARTIRE DA UN NODO SORGENTE**.

**CAMMINI MINIMI PARTENDO DA SORGENTE**
La BFS trova i cammini minimi a partire da un nodo sorgente. La distanza (u,v) è il cammino minimo per passare dal nodo u al nodo v. Per poter risolvere il problema modifichiamo lo pseudocodice:
- **PREV[]**: Indica il padre del nodo.
- **DIST[]**: Indica la distanza dalla sorgente al nodo di cui vogliamo trovare il percorso.

**CODICE BFS**

``` C++
// BFS normale

BFS(G, s)
{
	visited[1..n] new array
	for all v ∈ V do
		visited[v] = FALSE
	visited[s] = TRUE

	Q = new_queue()
	enqueue(Q, s)

	while NOT is_empty_queue(Q) do
	{
		u = dequeue(Q)
		// Esame di u
		for all (u, v) ∈ E do
			if visited[v] = FALSE then
			{
				enqueue(Q, v)
				visited[u] = TRUE
			}
}

// BFS per cammini minimi

BFS(G, s)
{
	dist[1..n] new array
	prev[1..n] new array
	
	for v ∈ V do
	{
		dist[v] = +∞
		prev[v] = 0
	}

	dist[s] = 0
	Q = new_queue()
	enqueue(Q, s)

	while NOT is_empty_queue(Q) do
	{
		u = dequeue(Q)
		// Esame di u
		for all (u, v) ∈ E do
			if (dist[v] = +∞) then
			{
				enqueue(Q, s)
				dist[v] = dist[u] + 1
				prev[v] = u
			}
	}
}

// O(V+E)
```
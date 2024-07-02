**DEFINIZIONE**
La BFS sui grafi è un estensione della BFS sugli alberi, quindi si parte dai vicini di un nodo, per andare dai vicini dei vicini fino ad arrivare ad un punto dove non possiamo più procedere. Strategia usata per visitare tutti i nodi raggiungibili da un nodo sorgente.

**BFS**
In questa sezione descrivo due varianti della BFS:
1) BFS normale che, partendo da un nodo sorgente, visita prima i suoi vicini, poi i vicini dei vicini... fino a finire i cammini disponibili. Sfrutta la coda ed è simile alla BFS degli alberi.
2) BFS che trova il cammino minimo con arco non pesato a partire da un nodo sorgente. Usiamo un array `prev[]` per trovare il padre del nodo e un array `dist[]` per memorizzare le distanze di ogni singolo percorso, inoltre controlla anche se il nodo è già stato visitato. Verrà quindi scelto il percorso col costo minore.

Il costo di entrambe le versioni è di `O(V+E).`

``` C++
BFS(G, s)
{
	visited[1..n] new array;
	for all (v ∈ V) do
		visited[v] = false;
	
	visited[s] = true;
	Q = new_queue();
	enqueue(Q, s);
	
	while NOT (is_empty_queue(Q)) do
	{
		u = dequeue(Q);
		// esame del nodo estratto
		
		for all ((u, v) ∈ E) do
			if (visited[v] = false) then
			{
				enqueue(Q, v);
				visited[u] = true;
			}
	}
}

BFS(G, s)
{
	prev[1..n] new array;
	dist[1..n] new array;
	
	for all (v ∈ V) do
	{
		prev[v] = 0;
		dist[v] = +∞;
	}
	
	dist[s] = 0;
	Q = new_queue(Q);
	enqueue(Q, s);
	
	while NOT (is_empty_queue(Q)) do
	{
		u = dequeue(Q);
		// esame del nodo estratto
		
		for all ((u, v) ∈ E) do
			if (dist[v] = +∞) then
			{
				enqueue(Q, v);
				dist[v] = dist[u] + 1;
				prev[v] = u;
			}
	}
}
```
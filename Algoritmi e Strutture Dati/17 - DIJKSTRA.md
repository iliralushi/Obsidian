**CAMMINI MINIMI SU GRAFI**
- **LUNGHEZZA DI UN CAMMINO**: Composto dal numero di archi.
- **PERCORSO PIU BREVE**: Composto dal numero minore di archi possibile.

- **ANDARE DA NODO A NODO**: Basta una BFS che si ferma una volta raggiunto il nodo.
- **ANDARE DA NODO A TUTTI GLI ALTRI**: Basta una BFS.
- **DA OGNI NODO A TUTTI GLI ALTRI**: Dobbiamo fare una BFS per nodo.

**ALBERO DEI CAMMINI MINIMI**
L'albero dei cammini minimi per un nodo s è un albero di copertura per i nodi raggiungibili da s avente un cammino minimo per ogni nodo raggiungibile partendo dalla sorgente.

**BFS CON ARCHI PESATI**
Non possiamo usarla. La BFS visita i vicini, poi i vicini dei vicini e così via, quindi non avremo mai la certezza di prendere gli archi giusti. Un cammino con più archi può essere il cammino più breve.

**PROBLEMA DA RISOLVERE**
- **INPUT**: Un grafo G = (V, E), un arco c con un peso non negativo ed un nodo sorgente s ∈ V.
- **OUTPUT**: L'albero dei cammini minimi radicato in s.

**ALGORITMO DI DIJKSTRA**
**COME** nella BFS:
- Usiamo `dist[1..n]` per memorizzare le distanze dei nodi alla sorgente.
- Ci sono nodi scoperti `(dist != +∞)` e nodi NON scoperti `(dist = +∞)`.
- Ad ogni iterazione fatta scopriamo un nodo e visitiamo per livello.

**DIVERSAMENTE** dalla BFS:
- Ci sono nodi scoperti con distanza calcolata **NON** effettiva e nodi scoperti con distanza calcolata **EFFETTIVA**.
- La distanza del nodo u dalla sorgente viene aggiornata solo se viene trovato un cammino più breve.
- Ad ogni iterazione scegliamo sempre il nodo con distanza minima.

``` C++
Dijkstra(G, s, c)
{
	dist[1..n] new array
	prev[1..n] new array

	for all v ∈ V do
	{
		dist[v] = +∞
		prev[v] = 0
	}

	dist[s] = 0
	Q = Make_Priority_Queue()
	enqueue(Q, s)

	while NOT is_empty_queue(Q) do
	{
		u = DeQueue(Q)

		for all (u, v) ∈ E do
		{
			if (dist[v] > dist[u] + c(u, v))
				then dist[v] = dist[u] + c(u, v)
				prev[v] = u
				Decrease_Priority(Q, v, dist[v])
		}
	}
	
	return prev[]
}

// O(V+E)
```
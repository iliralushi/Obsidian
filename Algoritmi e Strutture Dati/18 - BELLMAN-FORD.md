**PROBLEMA DA RISOLVERE**
Se gli archi sono negativi, allora non è possibile risolvere il problema con Dijkstra!
- **INPUT**: Un grafo G = (V, E), un arco che può essere positivo/negativo c, un nodo sorgente s.
- **OUTPUT**: L'albero dei cammini radicato in s.

**CODICE BELLMAN-FORD**
L'algoritmo di Bellman-Ford consiste nel rilassare per ogni nodo tutti i suoi archi. Bastano V-1 iterazioni perchè avremo un nodo senza archi uscenti. Funziona perchè rilassando tutti gli archi per ogni nodo non dobbiamo cambiare mai il percorso, ad ogni iterazione verrà scelto il miglior percorso.

``` C++
Bellman-Ford(G, c, s)
{
	dist[1..n] new array
	prev[1..n] new array

	for all v ∈ V do
	{
		dist[v] = +∞
		prev[v] = 0
	}

	dist[s] = 0

	for i = 1 to V-1 do
		for all (u, v) ∈ E do
		{
			if dist[v] > dist[u] + c(u, v)
				then
				{
					dist[v] = dist[u] + c(u, v)
					prev[v] = u
				}
		}

	return prev[]
}

// O(V*E)
```
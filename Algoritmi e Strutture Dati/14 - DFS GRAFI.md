**DEFINIZIONE**
La DFS sui grafi è un estensione della pre/post order sugli alberi. Viene usata per visitare tutti i nodi del grafo, anche se non è connesso.

**ALBERO DI COPERTURA**
Sottografo G' di G = (V, E) che contiene tutti i nodi del cammino di G. Sarà sempre diverso, dipende dal nodo da cui si parte. Esiste anche la **FORESTA** di copertura che sono semplicemente più alberi di copertura. 

**DFS**
Chiamata principale: Non c'è, abbiamo due procedure.

Usiamo la ricorsione, quindi dopo aver visitato un nodo visitiamo ricorsivamente tutti i nodi non ancora visitati. Ci salviamo la visita di un nodo usando l'array `visited[1..n].` Il costo computazionale sarà di `O(V+E).`

Per comporre la foresta di copertura usiamo un array di `prev[1..n]` che memorizzerà i padri di ogni nodo e verrà restituito.

``` C++
DFS(G)
{
	visited[1..n] new array;
	// prev[1..n] new array;
	
	for all (v ∈ V) do
	{
		visited[v] = false;
		// prev[v] = 0;
	}
		
	for all (v ∈ V) do
		if (visited[v] = false) then
			DFS-Visit(G, v);
	
	// return prev[];
}

DFS-Visit(G, v)
{
	visited[v] = true;
	
	// esamina nodo v caso pre-visita
	
	for all ((v, u) ∈ E) do
		if (visited[u] = false AND prev[ ]) then
		{
			// prev[u] = v;
			DFS-Visit(G, u);
		}
	
	// esamina nodo v caso post-visita
}
```

**ARCHI GRAFO ORIENTATO**
Esistono quattro tipo di archi orientati:
- **TREE**: Fa parte dell'albero di copertura.
- **BACK**: Porta ad un antenato, crea cicli.
- **FORWARD**: Porta ad un discendente.
- **CROSS**: Porta ad un nodo già visitato che non è nè antenato nè discendente.

Oltre all'array di prev, possiamo usare un array di post per dire se il nodo ha finito la visita o no, quindi se ha altri archi da poter visitare o meno.
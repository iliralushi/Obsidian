**DEPTH FIRST SEARCH GRAFI**
La DFS sui grafi è un estensione della DFS pre/post order sugli alberi. Una volta visitato il primo nodo si cerca di andare il più lontano possibile dall'origine.
- Strategia usata per **VISITARE TUTTI I NODI DEL GRAFO**, anche se ci sono più componenti connesse.

**ALBERO DI COPERTURA**
Sottografo che contiene **TUTTI** i nodi e gli archi usati durante la visita. L'albero di copertura sarà sempre diverso, dipende dal nodo da cui si parte.
- **FORESTA**: Insieme di sottografi che uniti devono contenere tutti i nodi di G.

**CODICE DFS**
Ha due procedure. La procedura principale chiama la procedura ricorsiva, mentre la procedura ricorsiva richiama la visita per ogni nodo non visitato.
- Come per la BFS è possibile implementare un array di prev(parent) e altre strutture.

``` C++
DFS(G)
{
	visited[1..n] new array
	for all v ∈ V do
		visited[v] = FALSE
	for all v ∈ V
		if visted[v] = FALSE
			then DFS-Visit(G, v)
}

DFS-Visit(G, v)
{
	visited[v] = TRUE
	// esamina nodo v (pre-visita)
	for all (v, u) ∈ E do
		if (visited[u] = FALSE)
			then DFS-Visit(G, u) // Visiterà solo grafi connessi
			                     // dato che continua solo se
			                     // c'è un altro nodo collegato
			                     // ad un arco.
			                 
	// esamina nodo v (post-visita)
}
// O(V+E)
```

**ARCHI IN UN GRAFO ORIENTATO**
- **TREE**: Fanno parte dell'albero di copertura.
- **BACK**: Arco che porta ad un antenato, quindi causa un ciclo.
- **FORWARD**: Arco che porta ad un discendente.
- **CROSS**: Arco che porta ad un nodo che non è ne antenato ne discendente.
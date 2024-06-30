**CONFRONTO CON DIJKSTRA**
L'algoritmo di Bellman-Ford ci permette di calcolare l'albero dei cammini minimi quando gli archi possono assumere valori negativi. 

Questo Dijkstra non lo può fare perchè il confronto tra i dist e l'arco può risultare VERO se l'arco è sufficientemente piccolo, creando quindi un albero dei cammini minimi falso.

**PROBLEMA**
- **INPUT**: Grafo G = (V, E) che può essere diretto/indiretto, senza cicli negativi con una funzione di costo C non negativa sugli archi E e un nodo sorgente S.
- **OUTPUT**: L'albero dei cammini radicato in S.

**BELLMAN-FORD**
L'algoritmo di Bellman-Ford è simile strutturalmente a Dijkstra. Abbiamo bisogno di un array di `dist[1..n]` e `prev[1..n]` per memorizzare le distanze per nodo dalla sorgente ed i padri. La differenza sta nell'iterare per tutti i nodi invece di usare una coda con priorità. Rilassiamo tutti gli archi ripetutamente e scegliamo quello col costo minore, ci basta ripetere per V-1 nodi.

Bellman-Ford funziona perchè abbiamo la certezza di scegliere sempre l'arco migliore dato che rilassiamo ogni singolo arco per il nodo che stiamo visitando.

Costo computazionale: `O(V*E).`

``` C++
Bellman-Ford(G, c, s)
{
	dist[1..n] new array;
	prev[1..n] new array;
	
	for all (v ∈ V) do
	{
		dist[v] = +∞;
		prev[v] = 0;
	}
	
	dist[s] = 0;
	
	for (i = 1 to V-1) do
		for all ((u, v) ∈ E) do
			if (dist[v] > dist[u] + c(u, v)) then
			{
				dist[v] = dist[u] + c(u, v);
				prev[v] = u;
			}
			
	return prev[];
}
```
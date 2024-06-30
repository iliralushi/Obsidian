**CAMMINI MINIMI SU GRAFI**
- PROBLEMA: Determinare percorsi più brevi tra i nodi di un grafo. La lunghezza di un cammino è composto dal numero di archi, mentre il percorso più breve dal numero minore di archi possibile. Abbiamo tre casistiche:

1) **DA NODO A NODO**: BFS che si ferma una volta raggiunto il nodo.
2) **DA SORGENTE AGLI ALTRI NODI**: BFS.
3) **DA OGNI NODO A TUTTI GLI ALTRI NODI**: BFS per nodo.

**PESO SUGLI ARCHI**
Possiamo avere un costo associato agli archi. Se non lo abbiamo possiamo usare la BFS per calcolare i cammini minimi, altrimenti dobbiamo usare l'algoritmo di Dijkstra. Non possiamo usare la BFS perchè non abbiamo la certezza di prendere gli archi giusti, dato che un cammino con più archi può essere quello che costa di meno.

**PROBLEMA**
- **INPUT**: Un grafo G = (V, E) che può essere diretto o indiretto, una funzione di costo C non-negativa sugli archi e un nodo sorgente S.
- **OUTPUT**: L'albero dei cammini minimi radicato in S.

**ALBERO DEI CAMMINI MINIMI**
Albero di copertura per un nodo sorgente che comprende tutti i nodi raggiungibili dalla sorgente col costo degli archi minore possibile.

**ALGORITMO DI DIJKSTRA**
Prendiamo certi elementi dalla BFS, mentre altri saranno nuovi.
Costo computazionale: `O(V+E).`

**BFS-LIKE**:
1) Usiamo un array di `dist[1..n]` per memorizzare le distanze dei vari nodi dalla sorgente.
2) Ci sono nodi scoperti `(dist[] != +∞)` e nodi non ancora scoperti `(dist[] = +∞).`
3) Ad ogni iterazione scegliamo un nodo tra quelli scoperti ed esploriamo i vicini.

**NON BFS**:
1) Ci sono nodi scoperti con distanza calcolata non definitiva e nodi scoperti con distanza calcolata definitiva.
2) La distanza di un nodo u dalla sorgente viene aggiornata solo se viene trovato un cammino più breve.
3) Scegliamo i nodi con `dist[.]` minima.

``` C++
Dijkstra(G, c, s)
{
	prev[1..n] new array;
	dist[1..n] new array;
	
	for all (v ∈ V) do
	{
		prev[v] = 0;
		dist[v] = +∞;
	}
	
	dist[s] = 0;
	Q = Make_priority_queue({v, dist[v]} | v = 1..n);
	
	while NOT (is_empty_queue(Q)) do
	{
		u = DeQueue(Q);
		
		for all ((u, v) ∈ E) do
			if (dist[v] > dist[u] + c(u, v)) then
			{
				dist[v] = dust[u] + c(u, v);
				prev[v] = u;
				Decrease_Priority(Q, v, dist[v]);
			}
	}
	
	return prev[];
}
```
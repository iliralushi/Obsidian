**PROBLEMA**
- **INPUT**: Grafo G = (V, E) connesso non diretto, una funzione di peso C sugli archi positiva.
- **OUTPUT**: Albero di copertura di peso minimo.

**RAGIONAMENTO GREEDY**
1) La soluzione ammissibile è un qualsiasi albero di copertura per G.
2) Il costo della soluzione sarà il peso dell'albero di copertura.
3) La funzione obiettivo è minima.
4) La soluzione ottima è l'albero di copertura con peso minimo.

**MST VS CAMMINI MINIMI**
Sono due problemi diversi:
- **MST**: Albero di copertura che collega tutti i nodi del grafo attraverso gli archi con peso minimo assoluto. Possono esserci diversi MST, dipende dall'algoritmo che si usa. Come problema ha una sottostruttura ottima, gli alberi in T' sono MST per l'insieme di vertici connessi in T'.
- **CAMMINO MINIMO**: Albero di copertura che, a partire da un nodo sorgente trova il cammino con peso degli archi minore.

**ALGORITMO DI KRUSKAL**
1) Ordina gli archi dal peso minore al peso maggiore.
2) Sceglie gli archi che compongono l'MST iterativamente; ad ogni iterazione si prende l'arco con peso minore che non crea cicli.
3) Termina quando tutti i nodi son connessi.

Per implementarlo:
1) Usiamo una lista per memorizzare gli archi scelti nell'MST.
2) Usiamo un disjoint set sull'insieme dei nodi per controllare di non formare cicli.
3) Terminiamo dopo aver scelto n-1 archi.

Costo computazionale: `O(m * log(n)).`

``` C++
Kruskal(G, c)
{
	S = make_set(V);
	T = new_list();
	count = 0;
	// ordina gli archi di E in ordine crescente di costo.
	
	while (count < n-1) do
	{
		// scegli il prossimo arco (u, v) ∈ E nell'ordinamento.
		if (find-set(S, u) != find-set(S, v)) then
		{
			p = new_list_node();
			p.val = (u, v);
			insert_head(T, p);
			union(S, u, v);
			count = count + 1;
		}
	}
	
	return T;
}
```

**ALGORITMO DI PRIM**
1) Sceglie un nodo sorgente.
2) Costruisce l'MST incrementalmente: ad ogni iterazione sceglie l'arco che costa di meno a patto che uniscano un nodo non ancora nell'albero di copertura.
3) Termina quando tutti i nodi sono connessi.

Per implementarlo:
1) Teniamo traccia del fatto che un nodo sia o meno nell'MST.
2) Teniamo traccia del costo per raggiungere un nodo.
3) Usiamo una coda con priorità per scegliere il nodo giusto ad ogni iterazione.
4) Teniamo traccia dei nodi del padre.

Costo computazionale: `O(m * log(n)).`

``` C++
Prim(G, c)
{
	prev[1..n] new array;
	cost[1..n] new array;
	S[1..n] new array; // array per tener conto se il nodo è stato inserito.
	
	for all (v ∈ V) do
	{
		prev[v] = 0;
		cost[v] = +∞;
		S[v] = 0;
	}
	
	// scelta di un nodo s ∈ V
	cost[s] = 0;
	S[s] = 1;
	Q = make_priority_queue(V+) // + = coda con priorità, coppia (V, cost[]).
	
	while NOT (is_empty_queue(Q)) do
	{
		u = DeQueue(Q);
		S[u] = 1;
		
		for all ((u, v) ∈ E) do
		{
			if (S[v] = 0 AND cost[v] > c(u, v)) then
			{
				cost[v] = c(u, v);
				prev[v] = u;
				Decrease_Priority(Q, v, cost[v]);
			}
		}
	}
	
	return prev[];
}
```

**DIMOSTRAZIONE FUNZIONAMENTO**
- **KRUSKAL**: L'algoritmo funziona perchè ad ogni iterazione andiamo a prendere sempre l'arco col peso minore e ci assicuriamo che non crei cicli con l'implementazione del Disjoint Set. Alla fine dell'esecuzione dell'algoritmo avremo un albero di copertura con tutti i nodi.
- **PRIM**: L'algoritmo funziona perchè ad ogni iterazione, partendo da un nodo sorgente ci assicuriamo di prendere l'arco col costo minore che non crei cicli. Inoltre, facciamo un controllo per verificare che l'arco unisca un nodo non ancora compreso nell'albero di copertura.



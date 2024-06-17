**MINIMUM SPANNING TREE**
- **INPUT**: Grafo G (V, E) indiretto connesso, funzione di peso sugli archi di G.
- **OUTPUT**: Albero di copertura di peso minimo.

**ASPETTO GREEDY MST**
- **SOLUZIONE AMMISSIBILE**: Alberto di copertura per il grafo G.
- **COSTO SOLUZIONE**: Peso dell'albero di copertura, Spanning Tree.
- **FUNZIONE OBIETTIVO**: Minimo.
- **SOLUZIONE OTTIMA**: Minimum Spanning Tree. Non unica!

**MST VS CAMMINI MINIMI**
**NON** SONO LA STESSA COSA!
- L'MST è l'albero di copertura che collega i tutti i nodi e ha peso minimo assoluto. Sottostruttura ottima, gli alberi in T' sono MST per gli insiemi di vertici connessi in T'.
- Un cammino minimo invece è il cammino di peso minore a partire da un nodo sorgente.

**ALGORITMO DI KRUSKAL**
- Ordinare gli archi per peso dal minore al maggiore.
- Scegliere gli archi dell'MST iterativamente: partiamo dagli archi più piccoli che non creano cicli.
- Termina quando i nodi sono tutti connessi.

**IMPLEMENTAZIONE**
- Usiamo un Disjoint Set per verificare che non si creino cicli.
- Usiamo una Lista per memorizzare gli archi scelti nell'MST.
- Terminiamo dopo aver scelto N-1 archi.

``` C++
Kruskal(G, c)
{
	S = make_set(V)
	T = new_list()
	
	// Ordina gli archi di E per avere gli archi col peso minore
	// prima.

	count = 0
	while count < n-1 do
	{
		// Scegli il prossimo arco nell'ordinamento.
		
		if find-set(S, u) != find-set(S, v)
		{
			then p = new_list_node()
			p.val = (u, v)
			insert_head(T, p)
			union(S, u, v)
			count = count+1
		}
	}

	return T
}

// O(mlog(n))
```

**ALGORITMO DI PRIM**
- Sceglie un nodo sorgente.
- Costruisce l'MST incrementalmente: ad ogni iterazione scegliere l'arco di peso minimo che unisca un nodo non ancora nell'albero ad un nodo già nell'albero.
- Termina quando tutti i nodi son connessi.

**IMPLEMENTAZIONE**
- Dobbiamo tener conto che un nodo sia o meno dell'MST.
- Dobbiamo tener conto del costo per raggiungere un nodo.
- Dobbiamo tener traccia dei padri.
- Usa una CODA CON PRIORITA per scegliere il nodo in ogni iterazione.

``` C++
Prim(G, c)
{
	for all v ∈ V do
	{
		cost[v] = +∞
		prev[v] = NIL
		S[v] = 0
	}

	// scegli un nodo s ∈ V
	cost[s] = 0
	S[s] = 1

	Q = make_priority_queue(V*) // coppia nodi di V e cost[]
	while NOT is_empty_queue(Q) do
	{
		u = DeQueue(Q)
		S[u] = 1

		for all (u, v) ∈ E do
		{
			if S[v] = 0 AND cost(v) > c(u, v) then
				cost[v] = c(u, v)
				prev[v] = u
				Decrease_Priority(Q, v, cost[v])
		}
	}

	return prev[]
}

// O(mlog(n))
```

**DIMOSTRAZIONE FUNZIONAMENTO**
- Prim: In ogni passo scegliamo sempre l'arco di peso minimo possibile in quel momento senza formare cicli. Funziona perchè termina quando tutti i nodi sono inseriti nell'MST e scegliamo sempre il bordo minimo.
- Kruskal: Funziona perchè a partire dalla prima iterazione scegliamo sempre gli archi di peso più piccolo senza formare cicli e ci fermiamo quando abbiamo collegato tutti i nodi.
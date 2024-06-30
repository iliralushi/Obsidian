**DEFINIZIONE**
Un grafo G = (V, E) è una coppia di insiemi dove:
- V è un insieme di vertici.
- E è un insieme di archi.

**TERMINOLOGIA**

- **GRAFO NON DIRETTO**: Le coppie di E non sono ordinate.
- **GRAFO DIRETTO**: Le coppie di E seguono un ordine, sono diretti.
- **NODO ADIACENTE**: Un nodo u si dice adiacente a v se esiste la coppia (u,v) ∈ E.
- **ARCO ORIENTATO**: Un arco (u, v) è orientato dal nodo u se esiste la coppia ∈ E.
- **GRADO DEL NODO**: Il numero di archi (u, v) ∈ E a partire da u.
  
- **CAMMINO DI UN GRAFO**: Una sequenza di vertici in cui ogni coppia di nodi è collegata attraverso un arco.
- **LUNGHEZZA CAMMINO**: Il numero di archi impiegati per un cammino.
- **CAMMINO SEMPLICE**: Cammino che contiene nodi non ripetuti.
- **CICLO**: Una sequenza di nodi che si ripete all'infinito.

- **SOTTOGRAFO**: Un grafo G' = (V', E') si dice sottografo se esso è contenuto in un grafo G.
- **CONNESSO**: Un grafo G è connesso quando ogni nodo è connesso da un vertice.
- **FORTEMENTE CONNESSO**: Esiste un cammino diretto che connette ogni coppia di nodi del grafo.

**COSTO COMPUTAZIONALE DI ALGORITMI**
Il costo computazionale di algoritmi su grafi è spesso espresso in `O(V + E)` dato che nel caso peggiore dobbiamo visitare ogni nodo, quindi anche ogni arco.

**CASI PARTICOLARI**
- **GRAFO COMPLETO**: Un grafo è completo quando esiste un arco per ogni singola coppia di nodi, in questo caso il costo sarà di `O(n^2).`
- **GRAFO SPARSO**: Ha pochi archi, conviene usare liste di adiacenza.
- **GRAFO DENSO**: Ha tanti archi, conviene usare matrici di adiacenza.
  
**MATRICI DI ADIACENZA**
Matrice G che è `n * n`. La casella `G[i, j]` sarà 1 se esiste un arco tra i nodi in posizione `(i,j)` altrimenti sarà zero. La matrice è simmetrica se il grafo è non orientato.
Occupa `O(n^2)` come spazio.

**LISTE DI ADIACENZA**
Array G di `card(V)` liste. `G[v]` è una lista, quindi un puntatore al primo elemento della lista che contiene tutti i vicini di v. Occupa `O(V+E)` come spazio.

**ACCESSO A GRAFI**
1) Itera su tutti i nodi.
2) Itera su tutti gli archi.
3) Itera prima su tutti i nodi, e per ogni nodo accede ai suoi archi.

``` C++
for all (v ∈ V) do
	// Istruzioni

for all (u, v) ∈ E do
	// Istruzioni

for all (v ∈ V) do
	// Istruzioni
	for all (u, v) ∈ E do
		// Istruzioni
```

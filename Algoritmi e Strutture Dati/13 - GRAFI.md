**DEFINIZIONE DI GRAFO**
Un grafo G = (V, E) è una coppia di insiemi dove i V è l'insieme dei vertici mentre E è l'insieme degli archi.

**TERMINOLOGIA GRAFO**
- **GRAFO NON ORIENTATO**: Gli archi di G **NON** sono ordinati, quindi **NON** hanno direzione.
- **GRAFO ORIENTATO**: Gli archi di G **SONO** ordinati, quindi **HANNO** direzione.
- **NODO ADIACENTE**: Se esiste la coppia (u, v) ∈ E.
- **SOTTOGRAFO**: Dato che il grafo è una coppia di insiemi esiste il sottografo, che è un grafo G' che contiene alcuni degli elementi contenuti nel grafo G.
- **CONNESSO**: Un grafo G è connesso quando ogni nodo è connesso da un vertice. Si dice fortemente connesso per i grafi diretti quando esiste un cammino diretto che connette ogni coppia di nodi.

**CAMMINO DI UN GRAFO**
Sequenza di nodi `<v0, v1, v2, v3, ... vK>` tale che `(vI, vI+1) ∈ E` per `i = 0...k-1`
- **LUNGHEZZA DI UN CAMMINO**: Il numero di archi del grafo.
- **CAMMINO SEMPLICE**: Cammino che non contiene nodi ripetuti.
- **CICLO**: Sequenza di nodi che si ripete all'infinito.

**DIMENSIONI DEL GRAFO**
Il costo computazionale di un algortimo usato sui grafi è di generalmente `O(|V| + |E|).`
- n = IVI numero dei nodi.
- m = IEI numero degli archi.

Esistono casi particolari:
- **GRAFO COMPLETO**: Un grafo è completo quando esiste un arco per ogni coppia di nodi. In questo caso il costo è `O(n^2).`
- **GRAFO SPARSO**: Ha pochi archi e conviene usare le liste di adiacenza. Il contrario è un grafo denso, per cui conviene usare matrici di adiacenza.

**MATRICI E LISTE DI ADIACENZA**
Sono dei metodi per rappresentare il contenuto del grafo. Per convenzione i nodi del grafo sono rappresentati dagli indici (1,n).
- **MATRICI**: La matrice è simmetrica se il grafo non è orientato.
- **LISTE**: Viene creato un array G di liste. `G[v]` è una lista che contiene i vicini di un nodo.

**RAPPRESENTAZIONE GRAFI**

``` C++
// Iterare su tutti i nodi:

for all (v ∈ V) do
	// Istruzioni

// Iterare su tutti gli archi:

for all (u, v) ∈ E do
	// Istruzioni

// Iterare su ogni nodo. Per ogni nodo iterare gli archi incidenti:

for all (v ∈ V) do
	// Istruzioni
	for all (u, v) ∈ E do
		// Istruzioni
```

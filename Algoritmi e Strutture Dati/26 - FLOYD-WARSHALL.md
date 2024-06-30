**PROBLEMA**
- **INPUT**: Grafo G = (V, E) con funzione peso sugli archi C che non genera cicli negativi.
- **OUTPUT**: Cammini minimi tra ogni coppia di nodi di G.

**PRIMA SOLUZIONE**
Usare l'algoritmo di Bellman-Ford usando ogni nodo del grafo come sorgente, invocandolo tante volte quanti sono i nodi nel grafo.

**FLOYD-WARSHALL**
Sottoproblema: Dati tre nodi i, j, k di V abbiamo:
- `dist(i, j, k)` = lunghezza del cammino minimo tra i e j che usa solo i nodi in {1, 2, k}. Se il cammino non esiste allora `dist(i, j, k) = +∞.`

Siamo in grado di calcolare `dist(i, j, 0)` che sarà uguale a:
- `c(i, j)` se esiste l'arco `(i, j).`
- 0 se `i = j`
- `+∞` se non esiste l'arco `(i, j) e i != j.`

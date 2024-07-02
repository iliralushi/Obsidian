**PROGRAMMAZIONE DINAMICA**
Se non sappiamo quali sottoproblemi risolvere allora li risolviamo tutti e conserviamo i risultati per risolvere il problema di dimensione più grande. La programmazione dinamica si può applicare, come per gli algoritmi greedy, se la sottostruttura è ottima. 

È possibile combinare le soluzioni ottime dei sottoproblemi per trovare la soluzione al problema principaleoltre queste soluzioni ottime non devono essere modificate una volta che diventa parte della soluzione più grande.

**CAMMINI MINIMI SU DAG**
- **INPUT**: DAG G = (V, E), un nodo sorgente s di G e una funzione costo sugli archi.
- **OUTPUT**: Distanze minime dei nodi di G da s.

Per trovare la distanza minima di s da un nodo conviene prima calcolare la distanza dalla sorgente ad un nodo e poi procedere calcolando tutte le distanze possibili da un nodo ad un altro.

Il sottoproblema relativo al nodo v in questo caso è trovare la distanza minima dalla sorgente. Il numero di sottoproblemi è il numero di nodi presenti nel DAG. Risolviamo i problemi seguendo l'ordinamento topologico.

``` C++
Shortest_Path_DAG(G, c, s)
{
	TS = Topological_Sort(G);
	
	for all (v ∈ V) do
		dist[v] = +∞;
	dist[s] = 0;
	v = pop(TS);
	
	while (v != s) do
		v = pop(TS);
	while NOT is_empty(TS) do
		dist[v] = min(u, v ∈ E) {dist[u] + c(u, v)};
		v = pop(TS);
		
	return dist[]
}
```

**PROBLEMA**
- **INPUT**: Sequenza di n numeri A.
- **OUTPUT**: La più lunga sottosequenza crescente.

1) Sottosequenza ammissibile: sottosequenza crescente.
2) Costo soluzione: numero di valori nella sottosequenza.
3) Funzione obiettivo: massimo.
4) Soluzione ottima: Sottosequenza crescente più lunga.

**BRUTE FORCE APPROACH**
Per ogni sequenza, controllare se è crescente oppure no. Teniamo traccia della sottosequenza più lunga trovata. Il costo computazionale dipende dal numero di sottoinsiemi degli indici, quindi 2^n.

**LONGEST INCREASING SUBSEQUENCE**




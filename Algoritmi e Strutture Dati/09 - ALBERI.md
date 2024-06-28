**DEFINIZIONE**
Un albero radicato T = (V, E) è una coppia di insiemi dove:
- V è un insieme di nodi.
- E è un insieme di archi orientati che collegano coppie di nodi.
- Un nodo di V sarà la radice dell'albero T.
- Ogni nodo, a parte la radice R, avrà esattamente un arco entrante per nodo. Esiste un cammino unico dalla radice ad ogni nodo e NON esistono cicli.

**ALBERI E RICORSIONE**
L'albero è una struttura dati perfetta per la ricorsione. Un albero radicato è dato da:
- Un albero vuoto.
- Un nodo radice e uno o più sottoalberi; ogni sottoalbero è un albero e la radice è connessa ad ogni radice di sottoalbero tramite arco orientato.

**TERMINOLOGIA**

![[Terminologia Albero.png]]

**LIVELLO ED ALTEZZA DI UN ALBERO**
- LIVELLO: Lunghezza del cammino semplice dalla radice ad un nodo.
- ALTEZZA: Profondità massima delle foglie.

**ALBERO BINARIO**
Un albero binario è un albero in cui ogni nodo ha zero, uno o due figli, identificati come figlio sinistro o figlio destro.

**TERMINOLOGIA ALBERI BINARI**
Un albero può essere sia completo che perfettamente bilanciato:

- COMPLETO: Un albero binario è completo se ogni nodo ha zero o due figli.
- PERFETTAMENTE BILANCIATO: Un albero binario è completamente bilanciato se ogni foglia dell'albero è allo stesso livello.

**TEOREMA ALBERO BINARIO**
Un albero binario completo e perfettamente bilanciato di altezza maggiore o uguale a zero ha `2^h+1 - 1` nodi e `2^h` foglie.

Dimostrazione per il caso dei nodi
Per ogni i = `0...h` il numero di nodi a livello i è uguale al numero di foglie di un albero completo e perfettamente bilanciato di altezza i. Il numero di nodi equivale quindi alla quantità:
- `h∑i=0 2^i = 2^h+1 - 1.`

Dimostrazione per il caso delle foglie
Usiamo il principio di induzione:
- **CASO BASE**: Un albero ha altezza = 0, quindi avrà un solo nodo.
- **IPOTESI INDUTTIVA**: Un albero di altezza `h - 1 >= 1 ha 2^h-1` foglie.
- **PASSO INDUTTIVO**: L'albero di altezza h contiene un albero di altezza `h-1` e le sue foglie sono i nodi del penultimo livello dell'albero. Ogni nodo del penultimo albero ha esattamente due figli, quindi il numero di foglie è `2^h-1 * 2 = 2^h.`

**NODO DI UN ALBERO BINARIO**
T è il puntatore alla radice. Il nodo di un albero comprende tre campi;
- **LEFT**: Puntatore al figlio sinistro.
- **RIGHT**: Puntatore al figlio destro.
- **VAL**: Contiene il valore associato al nodo.

**RICORSIONE**
Chiamata principale: `ContaNodi(T);`

Abbiamo un problema da risolvere; contare i nodi di un albero.
- **CASO BASE**: L'albero è vuoto, quindi il numero di nodi è pari a zero.
- **CASO RICORSIVO**: L'albero è non vuoto. Il numero di nodi è equivalente alla somma del sottoalbero sinistro, del sottoalbero destro e della radice.

``` C++
ContaNodi(T)
{
	if (T = NIL) then
		return 0;
	else
		return 1 + ContaNodi(t.left) + ContaNodi(t.right);
}

// Stesso problema con caso base diverso. Abbiamo come caso base la radice
// e il caso ricorsivo è uguale.

ContaNodi(T)
{
	if (t.left = t.right = NIL)
		then return 1;
	else
	{
		if (t.left != NIL) then
			n_s = ContaNodi(t.left);
		if (t.right != NIL) then
			n_d = ContaNodi(t.right);
	}
	
	return 1 + n_s + n_d;
}
```

Chiamata principale: `Altezza(T);`

Abbiamo un altro problema da risolvere, trovare l'altezza di un albero.
- **CASO BASE**: L'albero è vuoto, restituisco -1.
- **CASO RICORSIVO**: Albero non vuoto. L'altezza è uguale ad 1 + il massimo dell'altezza del sottoalbero sinistro e destro.
  
``` C++
Altezza(T)
{
	if (T = NIL) then
		return -1;
	else
		return 1 + max{Altezza(t.left), Altezza(t.right)};
}

// Stesso problema con caso base diverso. Abbiamo come caso base la radice
// e il caso ricorsivo è uguale.

AltezzaAlbero(T)
{
	if (T = NIL) then
		return -1;
	else
		return Altezza(T);
}

Altezza(T)
{
	if (t.left = t.right = NIL) then
		return 0;
	else
	{
		if (t.left != NIL) then
			h_s = Altezza(t.left);
		if (t.right != NIL) then
			h_d = Altezza(t.right);
	}
	
	return 1 + max{h_s, h_d};
}

// Stesso problema con due casi base, albero vuoto e radice.

Altezza(T)
{
	if (T = NIL) then
		return -1;
	if (t.left = t.right = NIL) then
		return 0;
	return 1 + max{Altezza(t.left), Altezza(t.right)};
```

**DFS**
La visita DFS di un albero visita ricorsivamente i sottoalberi. Viene implicitamente implementata attraverso uno stack. Il costo computazionale è di `O(n * f(n))` dove `f(n)` è il costo di visita per nodo. Abbiamo tre tipi di DFS:

- **PRE-ORDER**: Visito la radice, poi il sottoalbero sinistro, poi il sottoalbero destro.
- **IN-ORDER**: Visito il sottoalbero sinistro, poi la radice, poi il sottoalbero destro.
- **POST-ORDER**: Visito il sottoalbero sinistro, poi il sottoalbero destro, poi la radice.

``` C++
Pre_Order(T)
{
	if (T != NIL) then
	{
		// analisi di t, per esempio print t.val
		Pre_Order(t.left);
		Pre_Order(t.right);
	}
}

In_Order(T)
{
	if (T != NIL) then
	{
		In_Order(t.left);
		// analisi di t, per esempio print t.val
		In_Order(t.right);		
	}
}

Post_Order(T)
{
	if (T != NIL) then
	{
		Post_Order(t.left);
		Post_Order(t.right);
		// analisi di t, per esempio print t.val
	}
}
```

**BFS**
La visita BFS per un albero visita iterativamente ogni livello dell'albero partendo dalla radice. Inseriamo i nodi implicitamente in una coda. Il costo è uguale alla DFS.

- **BFS**: Prima visita la radice, poi i figli della radice, poi i figli dei figli etc...

``` C++
BFS(T)
{
	Q = new_queue();
	enqueue(Q, T); // inserimento in coda del primo nodo
	
	while NOT (is_empty_queue(Q)) do
	{
		u = dequeue(Q); // rimozione di un nodo in coda
		print u.val; // esempio
		
		if (u.left != NIL) then
			enqueue(Q, u.left); // inserimento di figlio sx
		if (u.right != NIL) then
			enqueue(Q, u.right); // inserimento di figlio dx
	}
}
```


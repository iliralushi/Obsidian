**DIFFERENZE TRA ARRAY E LISTE**
Il nome di entrambe le strutture dati rappresenta il primo elemento.

- **ARRAY**: L'array è una struttura dati statica. Possiamo accedere ad un elemento in tempo costante, però l'inserimento/rimozione in testa ci costa `O(n).`
- **LISTA**: La lista è una struttura dati dinamica. Possiamo inserire/rimuovere elementi in testa in tempo costante, però l'accesso ad un elemento ci costa `O(n).`

**COSA CONTIENE UN NODO DELLA LISTA**
I nodi di una lista sono i suoi elementi, essi contengono due campi;
- **VAL**: Contiene il valore del nodo.
- **NEXT**: Contiene il puntatore al nodo successivo.

**PRIMITIVE LISTA**
1) new_list(): Restituisce il puntatore ad una lista vuota, `O(1).`
2) is_empty_list(): Vero se la lista è vuota, falso altrimenti, `O(1).`
3) insert_head(L, e): Inserisce in testa il nodo e, `O(1).`
4) insert_next(p, e): Inserisce il nodo e nella posizione del nodo p, `O(1).`
5) search(L, i): Ricerca del nodo in posizione i, restituisce il puntatore del nodo, `O(i).`
6) insert_pos(L, e, i): Inserisce il nodo e in posizione i, `O(i).`
7) delete(L, p): Cancella un nodo dato, `O(n).`

``` C++
new_list()
{
	return NIL;
}

is_empty_list(L)
{
	return L = NIL;
}

insert_head(L, e)
{
	e.next = L;
	L = e;
}

insert_next(p, e)
{
	e.next = p.next;
	p.next = e;
}

search(L, i)
{
	j = 0;
	p = L;
	
	while (p != NIL AND i > j) do
	{
		p = p.next;
		j = j+1;
	}
	
	return p;
}

insert_pos(L, e, i)
{
	p = search(L, i-1);
	
	if (p != NIL) then
		insert_next(p, e);
}

delete(L, p)
{
	if (p = L) then
		L = L.next;
	else
	{
		tmp = L;
		while (tmp.next != p AND tmp != NIL) do
			tmp = tmp.next;
		
		if (tmp != NIL)
			then tmp.next = p.next;
	}
}
```

**PILA (STACK)**
Viene creata tramite lista. Usa la strategia LIFO; l'ultimo elemento inserito nella pila sarà il primo rimosso (last-in first-out).

1) I valori memorizzati nella pila sono tutti dello stesso tipo.
2) I nuovi valori vengono inseriti in testa.
3) Un'estrazione restituisce il valore in testa, quindi l'ultimo inserito.

**PRIMITIVE STACK**
1) new_stack(): Restituisce il puntatore ad una lista, `O(1).`
2) is_empty_stack(S): Vero se la pila è vuota, falso altrimenti, `O(1).`
3) push(S, x): Inserisce l'elemento x in testa alla pila, `O(1).`
4) top(S): Restituisce il valore in testa alla pila, `O(1).`
5) pop(S): Rimuove l'elemento in testa alla pila e lo restituisce, `O(1).`

``` C++
new_stack()
{
	return NIL;
}

is_empty_stack(S)
{
	return S = NIL;
}

push(S, x)
{
	if (S != NIL) then
	{
		e = new_list_node() // Non possiamo inserire l'elemento direttamente,
		                    // è una lista, quindi creiamo un nodo.
		e.val = x;
		e.next = S;
		S = e;
	}
	else
		return error;
}

top(S)
{
	if (S != NIL) then
		return S.val;
	else
		return error;
}

pop(S)
{
	if (S != NIL) then
	{
		x = top(S);
		S = S.next;
		return x;
	}
	else
		return error;
}
```

**CODA**
Viene creata tramite puntatore di un nodo. Il puntatore avrà a sua volta due puntatori; tail che punta all'ultimo nodo della lista, head che punta al primo elemento della lista.

Usa la strategia FIFO, quindi l'elemento inserito per primo sarà anche il primo elemento a venire rimosso (first-in first-out).

1) I valori nella coda sono tutti dello stesso tipo.
2) I nuovi valori vengono inseriti in fondo alla coda.
3) Un estrazione restituisce il primo elemento in fondo alla coda.

**PRIMITIVE CODA**
1) new_queue(): Restituisce una nuova coda vuota, `O(1).`
2) is_queue_empty(Q): Vero se la coda è vuota, falso altrimenti, `O(1).`
3) enqueue(Q, x): Inserisce un elemento in fondo alla coda, `O(1).`
4) first(Q): Restituisce il valore in testa alla coda, `O(1).`
5) dequeue(Q): Rimuove il primo elemento in fondo alla coda e lo restituisce, `O(1).`

``` C++
new_queue()
{
	Q = new_queue_node();
	Q.tail = NIL;
	Q.head = NIL;
	return Q;
}

is_empty_queue(Q)
{
	return Q.head = NIL;
}

enqueue(Q, x)
{
	if (Q != NIL) then
	{
		e = new_queue_node();
		e.val = x;
		e.next = NIL;
	}
	
	if (Q.head = NIL) then
		Q.head = e;
	else
		Q.tail.next = e;
	
	Q.tail = e;
}

first(Q)
{
	if (Q.head != NIL) then
		return Q.head.val;
	else
		return error;
}

dequeue(Q)
{
	if (!is_empty_queue(Q)) then
	{
		x = first(Q);
		Q.head = Q.head.next;
		
		if (Q.head = NIL) then
			Q.tail = NIL;
		
		return x;
	}
	else
		return error;
}
```
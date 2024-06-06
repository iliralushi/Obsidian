**ARRAY VS LISTE**
- **ARRAY**: Contiene celle contigue. L'accesso ad un qualsiasi elemento ha costo costante, mentre inserire/cancellare elementi in testa costa O(n). **Sequenza statica.**
- **LISTE**: Contiene celle non contigue. L'accesso ad un qualsasi elemento ha costo O(n), mentre inserire/cancellare elementi in testa ha costo costante. **Sequenza dinamica.**

**NODO LISTA**
Gli elementi che compongono la lista si dicono nodi. I nodi sono composti da due campi:
- **VAL**: Contiene il valore del nodo. E.val è il dato associato a tale nodo.
- **NEXT**: Contiene il puntatore al prossimo nodo se c'è in lista. E.next è il puntatore al prossimo nodo.
- **L / LISTA**: Puntatore al primo nodo.

**PRIMITIVE DELLA LISTA**
1) Crea una nuova lista: new_list()
2) Test lista vuota: is_empty_list(L)
3) Inserimento di un nodo in testa: insert_head(L, e)
4) Inserimento di un nodo dopo un nodo: insert_next(p, e)
5) Ricerca del nodo in posizione i: search(L, i)
6) Inserimento di un nodo in posizione i: insert_pos(L, e, i)
7) Cancellazione di un nodo dato: delete(L, p)

``` C++
// Restituisce il puntatore ad una lista vuota
// O(1)
new_list()
{
	return NIL
}

// Restituisce vero se la lista vuota, falso altrimenti
// O(1)
is_empty_list(L)
{
	return L = NIL
}

// Inserimento di un nodo in testa
// O(1)
insert_head(L, e)
{
	e.next = L
	L = e
}

// Inserimento di un nodo dopo un nodo dato
// O(1)
insert_next(p, e)
{
	e.next = p.next
	p.next = e
}

// Ricerca nodo in posizione i, restituisce il puntatore del nodo/NIL
// O(i)
search(L, i)
{
	j = 0
	p = L
	
	while (j < i AND p != NIL) do
	{
		p = p.next
		j = j+1
	}

	return p
}

// Inserimento di un nodo in posizione data i
// O(i)
insert_pos(L, e, i)
{
	if (i = 0)
		then
			insert_head(L, i)
	else
	{
		p = search(L, i-1)
		if NOT (p = NIL)
			then
				insert_next(p, e)
	}
}

// Cancellazione di un nodo dato
// O(n)
delete(L, p)
{
	if (p = L)
		then
			L = L.next
	else
	{
		tmp = L
		while (tmp.next != p AND tmp != NIL) do
			tmp = tmp.next
		if (tmp != NIL)
			then
				tmp.next = p.next
	}
}
```

**STACK**
Implementa la strategia LIFO (Last-in First-Out). Viene realizzata tramite lista.
- I valori memorizzati nella pila sono tutti dello stesso tipo.
- Nuovi valori vengono aggiunti in testa.
- Un estrazione restituisce il valore dell'ultimo elemento aggiunto (valore in testa)

**PRIMITIVE STACK**
1) Crea una nuova pila: new_stack()
2) Verifica se la pila è vuota. is_empty_stack(S)
3) Inserimento di un valore in testa: push(S, x)
4) Restituisce il valore in testa: top(S)
5) Restituisce il valore in testa e lo rimuove dalla pila: pop(S)

``` C++
// Restituisce il puntatore ad uno stack vuoto
// O(1)
new_stack()
{
	return NIL
}

// Restituisce vero se la pila è vuota, falso altrimenti
// O(1)
is_empty_stack(S)
{
	return S = NIL
}

// Inserisce un elemento in testa alla pila
// O(1)
push(S, x)
{
	if NOT (S = NIL) then
	{
		e = new_list_node()
		e.val = x
		e.next = S
		S = e
	}
	else
		return error
}

// Restituisce il valore dell'elemento in testa
// O(1)
top(S)
{
	if NOT (S = NIL) then
		return S.val
	else
		return error
}

// Restituisce il valore dell'elemento in testa e lo toglie dalla pila
// O(1)
pop(S)
{
	if NOT (S = NIL) then
	{
		x = top(S)
		S = S.next
		return x
	}
	else
		return error
}
```

**CODA**
Implementa la strategia FIFO (First-in First-Out). Viene realizzata tramite lista.
- I valori memorizzati nella coda sono tutti dello stesso elemento.
- Nuovi elementi vengono aggiunti in fondo alla coda.
- Un estrazione restituisce il primo elemento di una coda.

La queue è un puntatore ad un nodo che contiene due puntatori; tail che punta all'ultimo nodo della lista, head che punta al primo nodo di una lista.

**PRIMITIVE CODA**
1) Crea una nuova coda: new_queue()
2) Restituisce vero se la coda è vuota: is_empty_queue(Q)
3) Aggiunge un elemento in fondo alla coda: enqueue(Q, x)
4) Restituisce il valore in testa alla coda: first(Q)
5) Restituisce il valore in testa alla coda e lo rimuove: dequeue(Q)

Il nodo della queue contiene due puntatori; head che punta al primo nodo di una lista che memorizza i valori nella coda, tail che punta all'ultimo nodo della lista.

``` C++
// Crea una coda nuova
// O(1)
new_queue()
{
	Q = new_queue_node()
	Q.head = NIL
	Q.next = NIL
}

// Restituisce una coda vuota
// O(1)
is_empty_queue(Q)
{
	return Q.head = NIL
}

// Inserimento di un valore in fondo alla coda
// O(1)
enqueue(Q, x)
{
	e = new_list_node()
	e.val = x
	e.next = NIL
	
	if (Q.head = NIL) then
		Q.head = e
	else
		Q.tail.next = e
	Q.tail = e
}

// Restituisce il valore in testa alla coda
// O(1)
first(Q)
{
	if (Q.head != NIL)
		return Q.head.val
	else
		return error
}

// Restituisce il valore in testa alla coda e lo elimina
// O(1)
dequeue(Q)
{
	if NOT (is_empty_queue(Q)) then
		x = first(Q)
		Q.head = Q.head.next
		if (Q.head = NIL) then
			Q.tail = NIL
		return x
	else
		return error
}
```
**ARRAY VS LISTE**
- **ARRAY**: Contiene celle contigue. L'accesso ad un qualsiasi elemento ha costo costante, mentre inserire/cancellare elementi in testa costa O(n). **Sequenza statica.**
- **LISTE**: Contiene celle non contigue. L'accesso ad un qualsasi elemento ha costo O(n), mentre inserire/cancellare elementi in testa ha costo costante. **Sequenza dinamica.**

**NODO LISTA**
Gli elementi che compongono la lista si dicono nodi. I nodi sono composti da due campi:
- **VAL**: Contiene il valore del nodo. E.val è il dato associato a tale nodo.
- **NEXT**: Contiene il puntatore al prossimo nodo se c'è in lista. E.next è il puntatore al prossimo nodo.
- **L**: Puntatore al primo nodo.

**PRIMITIVE DELLA LISTA**
1) **new_list()** - Crea una nuova lista.
2) **is_empty_list(L)** - Test lista vuota.
3) **insert_head(L, e)** - Inserimento di un nodo in testa.
4) **insert_next(p, e)** - Inserimento di un nodo dopo un nodo.
5) **search(L, i)** - Ricerca del nodo in posizione i.
6) **insert_pos(L, e, i)** - Inserimento di un nodo in posizione i.
7) **delete(L, p)** - Cancellazione di un nodo dato.

``` C++
// Restituisce il puntatore ad una lista vuota

new_list()
{
	return NIL
	// O(1)
}

// Restituisce vero se la lista vuota, falso altrimenti

is_empty_list(L)
{
	return L = NIL
	// O(1)
}

// Inserimento di un nodo in testa

insert_head(L, e)
{
	e.next = L
	L = e
	// O(1)
}

// Inserimento di un nodo dopo un nodo dato

insert_next(p, e)
{
	e.next = p.next
	p.next = e
	// O(1)
}

// Ricerca nodo in posizione i, restituisce il puntatore del nodo/NIL

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
	// O(i)
}

// Inserimento di un nodo in posizione data i

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
	// O(i)
}

// Cancellazione di un nodo dato

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
	// O(n)
}
```

**STACK**
Implementa la strategia LIFO (Last-in First-Out). Viene realizzata tramite lista.
- I valori memorizzati nella pila sono tutti dello stesso tipo.
- Nuovi valori vengono aggiunti in testa.
- Un estrazione restituisce il valore dell'ultimo elemento aggiunto (valore in testa).

**PRIMITIVE STACK**
1) **new_stack()** - Crea una nuova pila.
2) **is_empty_stack(S)** - Verifica se la pila è vuota.
3) **push(S, x)** - Inserimento di un valore in testa.
4) **top(S)** - Restituisce il valore in testa.
5) **pop(S)** - Restituisce il valore in testa e lo rimuove dalla pila.

``` C++
// Restituisce il puntatore ad uno stack vuoto

new_stack()
{
	return NIL
	// O(1)
}

// Restituisce vero se la pila è vuota, falso altrimenti

is_empty_stack(S)
{
	return S = NIL
	// O(1)
}

// Inserisce un elemento in testa alla pila

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
	// O(1)
}

// Restituisce il valore dell'elemento in testa

top(S)
{
	if NOT (S = NIL) then
		return S.val
	else
		return error
	// O(1)
}

// Restituisce il valore dell'elemento in testa e lo toglie dalla pila

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
	// O(1)
}
```

**CODA**
Implementa la strategia FIFO (First-in First-Out). Viene realizzata tramite lista.
- I valori memorizzati nella coda sono tutti dello stesso elemento.
- Nuovi elementi vengono aggiunti in fondo alla coda.
- Un estrazione restituisce il primo elemento di una coda.

La queue è un puntatore ad un nodo che contiene due puntatori; tail che punta all'ultimo nodo della lista, head che punta al primo nodo di una lista.

**PRIMITIVE CODA**
1) **new_queue()** - Crea una nuova coda.
2) **is_empty_queue(Q)** - Restituisce vero se la coda è vuota.
3) **enqueue(Q, x)** - Aggiunge un elemento in fondo alla coda.
4) **first(Q)** - Restituisce il valore in testa alla coda.
5) **dequeue(Q)** - Restituisce il valore in testa alla coda e lo rimuove.

Il nodo della queue contiene due puntatori; head che punta al primo nodo di una lista che memorizza i valori nella coda, tail che punta all'ultimo nodo della lista.

``` C++
// Crea una coda nuova

new_queue()
{
	Q = new_queue_node()
	Q.head = NIL
	Q.next = NIL
	// O(1)
}

// Restituisce una coda vuota

is_empty_queue(Q)
{
	return Q.head = NIL
	// O(1)
}

// Inserimento di un valore in fondo alla coda

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
	// O(1)
}

// Restituisce il valore in testa alla coda

first(Q)
{
	if (Q.head != NIL)
		return Q.head.val
	else
		return error
	// O(1)
}

// Restituisce il valore in testa alla coda e lo elimina

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
	// O(1)
}
```
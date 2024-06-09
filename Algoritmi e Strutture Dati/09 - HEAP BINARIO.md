**HEAP**
Dato un insieme di chiavi totalmente ordinabile, un Heap Binario è un albero binario che memorizza le chiavi in un ordine preciso a seconda se è MinHeap o MaxHeap.

**MIN-HEAP BINARIO**
Il Min-Heap binario è un Heap che:
- **PROPRIETÀ STRUTTURALE**: Un albero binario completo e quasi perfettamente bilanciato a sinistra.
- **PROPRIETÀ DI ORDINAMENTO**: Per ogni nodo v nell'albero, la chiave di v sarà ordinata `<=` rispetto alle chiavi nel sottoalbero radicato in v.

**MAX-HEAP BINARIO**
Il Max-Heap binario è un Heap che:
- **PROPRIETÀ STRUTTURALE**: Un albero completo quasi perfettamente bilanciato a sinistra.
- **PROPRIETÀ DI ORDINAMENTO**: Dato un nodo v nel Max-Heap, la sua chiave sarà ordinata `>=` rispetto alle chiavi nel sottoalbero radicato di v.

**PROPRIETÀ HEAP BINARIO**
- Il livello in un Heap Binario sarà sempre uguale a `h = log(n) con n = nodi.`
- Un Heap Binario ha almeno tanti nodi quanto un albero completo e perfettamente bilanciato di altezza h-1 mentre non avrà mai tanti nodi quanto un albero con le stesse caratetristiche di altezza h.

**RAPPRESENTAZIONE IN ARRAY**
I valori dei nodi dell'Heap sono inseriti nell'array per livello, partendo da sinistra verso destra, come una BFS.
- **LUNGHEAP**: Ultimo indice dell'array.
- **DIMHEAP**: Ultimo indice contenente una chiave nell'array.

``` C++
Padre(i)
	return ⌈i/2⌉ - 1
	
FiglioSinistro(i)
	return 2i + 1

FiglioDestro(i)
	return 2(i+1)
```

**PRIMITIVE MIN-HEAP**
Assumendo che l'heap sia rappresentato implicitamente con un array.
- **CostruisciHeap(H)**: Costruisce un Heap a partire da un insieme di chiavi memorizzate nell'Heap.
- **MinimoHeap(H)**: Restituisce la chiave minima nell'Heap.
- **DecrementaChiaveHeap(H, i, k)**: Decrementa il valore della chiave in posizione i, impostando il valore k.
- **InserzioneChiaveHeap(H, k)**: Inserisce la nuova chiave k nell'heap H.
- **Heapify(H, i)**: Una volta incrementata la chiave, la funzione Heapify viene usata per ripristinare la proprietà di ordinamento.
- **EstrazioneMinimoHeap(H)** - Restituisce la chiave minima nell'Heap, eliminandola.

``` C++
MinimoHeap(H)
{
	if DimHeap < 0
		then return error
	else return H[0]
	// O(1)
}

DecrementaChiaveHeap(H, i, k)
{
	if i > DimHeap or k > H[i]
		then return error
	H[i] = k
	while i > 0 AND H[Padre(i)] > k do
		Scambia H[i] con H[Padre(i)]
		i = Padre(i)
	// O(log(n))
}

InserzioneChiaveHeap(H, k)
{
	if DimHeap = LungHeap
		then return error
	DimHeap = DimHeap+1
	H[DimHeap] = k
	DecrementaChiaveHeap(H, DimHeap, k)
	// O(log(n))
}

Heapify(H, i)
{
	if i > DimHeap then return error
	min = i
	s = FiglioSinistro(i)
	d = FiglioDestro(i)

	if s <= DimHeap AND H[s] < H[i] // confronto figlio sx
		then min = s
	if d <= DimHeap AND H[d] < H[min] // confronto figlio dx
		then min = d
	if min != i
		then
			scambia H[i] con H[min]

	Heapify(H, min)
	// O(log(n))
}

EstrazioneMinimoHeap(H)
{
	if DimHeap < 0
		then return error
	min = H[0]
	H[0] = H[DimHeap]
	DimHeap = DimHeap - 1
	Heapify(H, 0)
	// O(log(n))
}

CostruisciHeap(H)
{
	DimHeap = length(H) - 1
	LungHeap = length(H) - 1
	for i = Padre(DimHeap) downto 0
		Heapify(H, i)
	// O(n)
}
```

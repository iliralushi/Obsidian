**DEFINIZIONE**k   
Dato un insieme di chiavi totalmente ordinabile un Heap Binario è un albero binario che memorizza chiavi nell'insieme e, a seconda dell'ordinamento, si classifica in Min e Max Heap.

**MIN-HEAP BINARIO**
- **TOPOLOGIA**: L'albero è binario, completo e quasi perfettamente bilanciato a sinistra.
- **PROPRIETÀ DI ORDINAMENTO**: Per ogni nodo v dell'albero si avrà che la chiave memorizzata in v dell'albero sarà `<=` rispetto alle chiavi dei nodi nel sottoalbero radicato in v.

**MAX-HEAP BINARIO**
- **TOPOLOGIA**: L'albero è binario, completo e quasi perfettamente bilanciato a sinistra.
- **PROPRIETÀ DI ORDINAMENTO**: Per ogni nodo v dell'albero si avrà che la chiave memorizzata in v dell'albero sarà `>=` rispetto alle chiavi dei nodi nel sottoalbero radicato in v.

**PROPRIETÀ**
- Un Heap con n nodi avrà sempre altezza `h = ⌊log(n)⌋ con n = nodi.`
- Un Heap ha almeno tanti nodi quanti ne ha un albero completo e perfettamente bilanciato di altezza h-1.
- Un Heap non ha mai più nodi di un albero completto e perfettamente bilanciato di altezza h.

**RAPPRESENTAZIONE IN ARRAY**
Le chiavi dei nodi sono inserite nell'array livello per livello e, per ogni livello, da sinistra verso destra. Abbiamo due definizioni:
- **LUNGHEAP**: Ultimo indice dell'array.
- **DIMHEAP**: Ultimo indice contenente una chiave dell'Heap.
  
Queste sono tre formule per trovare gli indici di Padre, FiglioSx e FiglioDx:

``` C++
Padre(i)
{
	return ⌈i/2⌉ - 1;
}
	
FiglioSinistro(i)
{
	return 2i + 1;
}

FiglioDestro(i)
{
	return 2(i+1);
}
```

**PRIMITIVE MIN-HEAP**
L'Heap deve essere implementato tramite array.

1) CostruisciHeap(H): Costruisce un Heap a partire dalle chiavi memorizzate nell'array, `O(n * log(n)).`
2) MinimoHeap(H): Restituisce la chiave minima memorizzata nell'Heap, `O(1).`
3) DecrementaChiaveHeap(H, i, k): Decrementa il valore della chiave con il valore k del nodo in posizione i, `O(log(n)).`
4) InserzioneChiaveHeap(H, k): Inserisci la chiave k all'interno dell'Heap, `O(log(n)).`
5) Heapify(H, i): Ripristina la proprietà di ordinamento al seguito dell'incremento di una chiave, `O(n * log(n)).`
6) EstrazioneMinimoHeap(H): Restituisce la chiave minima e la elimina dall'Heap, `O(log(n)).`

``` C++
MinimoHeap(H)
{
	if (DimHeap < 0)
		return error;
	else
		return H[0];
}

DecrementaChiaveHeap(H, i, k)
{
	if (i > DimHeap OR k > H[i]) then
		return error;
	else
	{
		H[i] = k;
		while (i > 0 AND H[Padre(i)] > k) do
		{
			swap(H[i], H[Padre(i)]);
			i = Padre(i);
		}
	}
}

InserzioneChiaveHeap(H, k)
{
	if (DimHeap = LungHeap) then
		return error;
	else
	{
		DimHeap = DimHeap + 1;
		H[DimHeap] = k;
		DecrementaChiaveHeap(H, DimHeap, k);
	}
}

Heapify(H, i)
{
	if (i > DimHeap) then
		return error;
	else
	{
		s = FiglioSinistro(i);
		d = FiglioDestro(i);
		
		if (s <= DimHeap AND H[s] < H[i]) then // confronto figlio sx
			min = s;
		if (d <= DimHeap AND H[d] < H[i]) then // confronto figlio dx
			min = d;
		
		if (min != i) then
		{
			swap(H[i], H[min]);
			Heapify(H, min);
		}
	}
}

EstrazioneMinimoHeap(H)
{
	if (DimHeap < 0) then
		return error;
	else
	{
		min = H[0];
		H[0] = H[DimHeap];
		DimHeap = DimHeap - 1;
		Heapify(H, 0);
	}
	
	return min;
}

CostruisciHeap(H)
{
	DimHeap = length(H) - 1;
	LungHeap = length(H) - 1;
	
	for (i = Padre(DimHeap) downto 0) do
		Heapify(H, i);
}
```

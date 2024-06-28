**DEFINIZIONE**
Dato un MaxHeap il valore massimo è memorizzato nella radice, quindi in `H[0].` Il valore massimo nella sequenza ordinata deve essere inserito in `H[LungHeap].`

L'Heap Sort restituisce i valori delle chiavi ordinate. Prima crea l'Heap tramite la primitiva CostruisciHeap(H), poi con un ciclo for partiamo dalla posizione finale ed inseriamo gli elementi a partire dal più grande usando la primitiva EstrazioneMassimoHeap(H). Essa si occupa anche di mantenere la proprietà di ordine tramite Heapify.

Il costo computazionale di Heap Sort è di `(O(n * log(n)) + log(n).`

``` C++
HeapSort(H)
{
	CostruisciHeap(H);
	
	for (i = length(H)-1 downto 1) do
		H[i] := EstrazioneMassimoHeap(H);
}
```
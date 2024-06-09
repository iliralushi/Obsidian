**HEAP SORT**
Questo codice funziona per il Min-Heap. Per il Max-Heap invece dobbiamo considerare il fatto che l'elemento più grande si trova ad `H[0]`, quindi il valore massimo deve stare in `H[LungHeap].`

L'Heap Sort restituisce i valori delle chiavi ordinate. Prima crea l'Heap, poi dall'elemento più grande a quello più piccolo li estrae.

``` C++
HeapSort(H)
{
	CostruisciHeap(H)
	for i = length(H)-1 downto 1
		H[i] := EstrazioneMassimoHeap(H)
}
```
**PROBLEMA**
Usare il minor numero di bit possibile per comprimere un file di testo.
- **INPUT**: Alfabeto finito Σ di caratteri, file di testo F con N caratteri di Σ, frequenza f(c) di occorrenza per ogni carattere dell'alfabeto c ∈ Σ.
- **OUTPUT**: Una codifica binaria di ogni carattere `cod : Σ -> {0,1}` tale per cui la lunghezza del file sia la minore possibile.

**RAPPRESENTAZIONE AD ALBERO**
Le codifiche per ogni lettera possono essere espresse tramite albero:
1) Etichette 0/1 sugli archi dove 0 è il nodo di sinistra e 1 quello di destra.
2) Abbiamo i caratteri nelle foglie.
3) Il cammino radice-foglia esprime la codifica del carattere.

**ALGORITMO DI HUFFMAN**
L'algoritmo di Huffman è un algoritmo greedy che, alle lettere dell'alfabeto più frequenti assegna una codifica più corta, quindi un cammino dell'albero più corto. Al contrario per le lettere che appaiono meno assegniamo codifiche più lunghe, quindi un cammino dell'albero più lungo. 

Per assicurarsi di ordinare la lista in modo giusto usiamo una coda con priorità.

1) Costruiamo una lista ordinata di nodi foglia, uno per ogni carattere dell'alfabeto. Il nodo sarà costituito dalla coppia `(lettera, frequenza(lettera)).`
2) Rimuoviamo dalla lista i due nodi con frequenza minore `fx` ed `fy.`
3) Creiamo un nuovo nodo di coppia `(-, frequenza(x) + frequenza(y))` e come figli i nodi rimossi al passo precedente.
4) Aggiungiamo il nuovo nodo nel posto giusto, quindi ordinato.
5) Terminiamo quando abbiamo un nodo unico nella lista.

Costo computazionale: `O(Σ * log * Σ)`

``` C++
Huffman(Σ, F, f)
{
	Q = new_priority_queue();
	
	for (i = 1 to Σ) do
	{
		t = new_tree_node();
		t.char = Σ[i];
		t.fr = f[i];
		t.left = NIL;
		t.right = NIL;
		EnQueue(Q, t, f[i]);
	}
	
	for (i = 1 to Σ-1) do
	{
		t1 = DeQueue(Q);
		t2 = DeQueue(Q);
		t = new_tree_node();
		t.char = -;
		t.fr = t1.fr + t2.fr;
		t.left = t1;
		t.right = t2;
		EnQueue(Q, t t1.fr + t2.fr)
	}
	
	return DeQueue(Q);
}
```

**PROCEDIMENTO ES PARTE 1 COI FILE**

![[Huffman.png]]

**STEP 1)** Vedere quanti caratteri abbiamo. Solitamente sono 5/6, quindi 3 bit. Abbiamo che il file con codice a lunghezza fissa equivale a `n * num.bit necessari per esprimere i caratteri.`

**STEP 2)** Svolgiamo l'albero di Huffman per trovare le codifiche di ogni singolo carattere.

**STEP 3)** Troviamo il numero di occorrenze dei caratteri facendo `n.simboli.file * percentuale di frequenza lettera.` Una volta trovate moltiplichiamo per i bit della codifica per lettera per trovare il file compresso con Huffman.

**STEP 4)** Troviamo il risparmio facendo `(file a lunghezza fissa - file compresso con Huffman) / file a lunghezza fissa * 100.`


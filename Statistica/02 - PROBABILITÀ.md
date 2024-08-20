**Basi di Probabilità**
- **Esperimento:** Un esperimento è un processo che produce delle osservazioni.
- **Esito:** Un esito è una possibile osservazione.
- **Sample Space**: Il sample space comprende tutti i possibili risultati.
- **Evento**: Un evento è un sottoinsieme del sample space.
- **Prova**: Una prova è una singola istanza di un esperimento.

**Basi di Insiemistica**
Abbiamo A e B che sono eventi in un sample space S. Allora:
- `A ∩ B:`Elementi inclusi sia in A che in B.
- `A ∪ B:` Tutti gli elementi di A e B.
- `A − B:` Tutti gli elementi compresi in A che NON sono compresi in B. Non è commutativo.
-  `Ā:` Comprende tutti gli elementi NON presenti in A ma presenti in S.
- `∅:` Insieme vuoto.
- `Disgiunzione:` Succede quando `A ∪ B = ∅.` 
- `A ⊂ B:` A è sottoinsieme di B se ogni elemento compreso in A è compreso anche in B.

**Assiomi della Probabilità**
Una probabilità per essere chiamata tale deve soddisfare le seguenti condizioni:
1) Non è un numero negativo. Per ogni evento abbiamo che `P(E) ≥ 0.`
2) La probabilità del sample space è 1. Quindi `P(S) = 1.`
3) Se abbiamo più insiemi disgiunti allora la probabilità è uguale alla loro somma.

**Simulazioni**
Lo scopo di una simulazione è di capire come funziona il mondo reale. Possiamo fare diversi esperimenti artificiali che prendono il nome di simulazioni stocastiche.

**Funzione Sample**
Permette di simulare una o più prove dell'esperimento. Sample tratta il sample space come un contenitore e prende un contenuto a caso.

1) **x**: Il vettore che farà da sample space.
2) **Size**: Numero di risultati da pescare.
3) **Replace**: Determina se vogliamo elementi ripetuti o no. Di default è settato a FALSE.
4) **Prob**: Il vettore che assegna le probabilità. Di default è a NULL, quindi ogni elemento ha la stessa probabilità. Se vogliamo aggiungere le nostre probabilità dobbiamo inserire un vettore che ha tanti elementi quanti il nostro vettore x.

``` R
sample(x = 1:10, size = 1, replace = FALSE, prob = NULL) # elem random
sample(x = 1:10, size = 30) # ERRORE! Size troppo grande e no ripetizione
```

**Stimare Probabilità con Sample**
Lo scopo generale delle simulazioni è stimare la probabilità di un evento.
1) Simula l'esperimento svariate volte in modo da produrre un vettore di risultati.
2) Testa se il vettore di risultati è in grado di produrre un vettori di TRUE/FALSE.
3) Svolgi la media dei TRUE/FALSE per stimare la probabilità.

**Teorema**
Dato un evento E con probabilità P e una X che rappresenta il numero di volte che l'evento si presenta in N prove. Abbiamo che:
$lim(n)→∞$ $X/N = P$

**Funzione Replicate**
È un loop. Ci permette di ripetere indefinite volte una espressione expr. Inoltre ha un parametro N che indica quante volte ripeterla.

``` R
outcome <- replicate(n, {
		# blocco di testo
		# blocco di testo
	})
```


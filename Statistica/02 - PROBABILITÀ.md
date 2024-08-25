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
- $lim(n)→∞:$ $X/N = P$

**Funzione Replicate**
È un loop. Ci permette di ripetere indefinite volte una espressione expr. Inoltre ha un parametro N che indica quante volte ripeterla. Le parentesi graffe indicano un blocco
di testo; solo il risultato dell'ultima istruzione viene salvato nel vettore via replicate.

``` R
event <- replicate(n, {
		# L'ESPERIMENTO VA QUI
		# L'ESPERIMENTO VA QUI
	})
	
mean(event) / 100
```

**Probabilità Condizionale**
Dati due eventi A e B, con la probabilità di B non nulla si dice probabilità condizionale la probabilità che l'evento A accada dato l'evento B. In formula, abbiamo:
- $P(A|B)$ $=$ $P(A∩B)$ / $P(B)$
- $P((A∩B)|B)$ $=$ $P(A|B)$
- $P((A∪B)|B)$ $=$ $1$

**Eventi Indipendenti**
Dati due eventi A e B, un evento la cui la probabilità di accadere NON viene influenzata dal fatto che un altro evento sia accaduto. In formula quindi, se due eventi sono indipendenti:
1) $P(A∩B)$ $=$ $P(A)$ $×$ $P(B)$
2) $P(A|B)$ $=$ $P(A)$
3) $P(B|A)$ $=$ $P(B)$

**Eventi Mutualmente Indipendenti**
Un insieme di eventi si dicono mutualmente indipendenti se la loro probabilità di accadere NON è influenzata da nessun evento presente nell'insieme. In forumula abbiamo:
- $P(Ai1∩Ai2∩⋯∩AiN)$ $=$ $P(Ai1)$ $×$ $P(Ai2)$ $×$ $…$ $×$ $P(AiN)$

**Simulare la Probabilità Condizionale**
1) Stimiamo la probabilità dell'evento $(A ∩ B)$ usando la funzione replicate per ripetere il blocco di testo e sample per creare il nostro esperimento. Assegniamo ad una variabile la media del nostro risultato.
2) Svolgiamo gli stessi passaggi per l'evento $B$.
3) Svolgiamo l'operazione $P(A∩B)$ $/$ $P(B)$.

**Legge della Probabilità Totale**
La legge della probabilità totale ci consente di trovare la probabilità complessiva di un evento A dividendolo in più casi, detti partizioni dello spazio degli eventi. Questo evento che chiamiamo B rappresenta uno scenario esclusivo, coprendo tutte le possibili situazioni in cui
l'evento A può verificarsi. 

La probabilità complessiva viene quindi trovata sommando tutte le probabilità condizionate A dato ciascun B, moltiplicato per ogni probabilità B. In formula:
- $P(A)$ $=$ $P(A$ $∩$ $B)$ + $P(A$ $∩$ $!B)$ $=$ $P(A$$|$$B)$$P(B)$ $+$ $P(A$$|$$!B)$$P(!B)$.
###### **ESISTE UNA VERSIONE GENERALE PER N PARTIZIONI DELL'EVENTO!**

**Legge di Bayes**
La legge di Bayes è una conseguenza della probabilità condizionale. Ci permette di aggiornare la nuova probabilità di un evento tenendo conto di nuove informazioni. In pratica ci aiuta a trovare la probabiltà condizionata inversa. In formula:
- $P(A)$ $=$ $P(B|A)P(A)$ $/$ $P(B)$ $=$ $P(B|A)P(A)$ $/$ $P(B|A)P(A)$ $+$ $P(B|!A)P(!A)$
###### **ESISTE UNA VERSIONE GENERALE PER N PARTIZIONI DELL'EVENTO!**

**Regola del Prodotto**
Se ci sono $m$ modi per fare una cosa, e per ciascuno di questi $m$ modi esistono altri $n$ modi per fare una seconda cosa, allora esistono $m$ $×$ $n$ modi per fare entrambe le cose.

**Combinazione Semplice**
Il numero di modi per scegliere $k$ oggetti distinti da un insieme $N$ è dato da:
$\binom{n}{k}$ $=$ $n!$ $/$ $k!(n - k!)$

Per svolgerlo in R usiamo la funzione `choose(n, k).`



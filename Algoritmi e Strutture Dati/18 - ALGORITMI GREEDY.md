**TIPI DI PROBLEMI**
- **PROBLEMI DECISIONALI**: Sono i problemi che come risposta hanno un valore booleano, quindi vero o falso.
- **PROBLEMI DI RICERCA**: Sono i problemi che come soluzione devono trovare un certo valore sotto determinate specifiche.
- **PROBLEMI DI OTTIMIZZAZIONE**: Ad ogni soluzione ammissibile è assegnato un costo e noi dobbiamo trovare la soluzione ottima, ovvero una soluzione ammissibile di costo minimo o massimo.

**ESEMPIO PROBLEMA DI OTTIMIZZAZIONE**
- **INPUT**: Grafo indiretto connesso, un nodo sorgente e una funzione peso sugli archi.
- **OUTPUT**: Cammini minimi dalla sorgente ad ogni nodo.
- **SOLUZIONE AMMISSIBILE**: Un ciclo che va dal primo a V-1 nodi, ognuno dei quali è un cammino di un nodo del grafo che passa dalla sorgente.
- **FUNZIONE OBIETTIVO**: Minimo.
- **SOLUZIONE OTTIMA**: La soluzione detta sopra.

**ALGORITMI GREEDY**:
Costituisce la soluzione al problema in maniera incrementale, effettua una serie di scelte in cui, ad ogni passo dell'algoritmo selezioniamo una parte di soluzione con costo ottimizzato fino ad arrivare alla soluzione ottima.

- **APPROCCIO GENERALE**: Ordina gli oggetti per appetibilità alla soluzione ottima, poi genera la soluzione in maniera incrementale, scegliendo iterativamente l'oggetto più appetibile tra quelli selezionabili (SCELTA GREEDY). Scelte mai modificate, saranno ottimali dal momento della selezione.
- **SOTTOSTRUTTURA OTTIMA**: Un Algoritmo Greedy per funzionare deve avere una sottostruttura ottima, non sono algoritmi generali.

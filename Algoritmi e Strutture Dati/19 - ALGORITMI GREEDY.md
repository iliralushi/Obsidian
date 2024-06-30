**CLASSIFICAZIONE DI PROBLEMI**
1) **PROBLEMI DECISIONALI**: La risposta al problema è un semplice SI/NO oppure un Vero/Falso. Determiniamo il valore grazie al nostro input che, a seconda delle nostre condizioni ritornerà un valore booleano.
2) **PROBLEMI DI RICERCA**: Tra tutte le soluzioni possibili se ne cerca una, detta soluzione ammissibile che soddisfa una certa condizione.
3) **PROBLEMI DI OTTIMIZZAZIONE**: Ad ogni soluzione ammissibile è associato un costo e cerchiamo tra tutte le soluzioni quella ottima, che sarà una soluzione ammissibile col costo minimo o massimo.

**ALGORITMI GREEDY**
Algoritmo che costruisce la soluzione in maniera incrementale, effettuando una serie di scelte in cui, ad ogni passo, si seleziona una parte di soluzione che permette di ottimizzare il costo della soluzione parziale fino a quel momento.

Un algoritmo greedy si può applicare solo se il problema ha una sottostruttura ottima. Se il problema ha una sottostruttura ottima allora contiene all'interno soluzioni ottime per i sottoproblemi.

**APPROCCIO GENERALE**
- Ordiniamo gli oggetti per "appetibilità" a far parte della soluzione ottima.
- Generiamo la soluzione in maniera incrementale, selezionando iterativamente l'oggetto più appetibile non ancora selezionato. Viene detta scelta greedy.


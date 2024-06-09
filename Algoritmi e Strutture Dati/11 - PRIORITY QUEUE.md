**PRIORITY QUEUE**
Una coda con priorità memorizza sequenze di **COPPIE** (el, pr).
- **EL**: Appartiene ad un insieme di elementi.
- **PR**: Priorità associabile ad un elemento di tipo EL.

**ESEMPIO**: Come EL abbiamo una coppia in coda (Esame, data), come PR abbiamo la priorità massima all'esame con data più vicina.
**ESEMPIO**: Come EL abbiamo una coppia in coda (Compito, compenso), come PR abbiamo la priorità massima al compito con voto più alto.

**PRIMITIVE PRIORITY QUEUE**
Vanno dall'elemento con più priorità all'elemento con meno priorità.
- **MAKE_PRIORITY_QUEUE(Q')**: Crea una coda con priorità che memorizza le coppie (el, pr) in un insieme di coppie Q'.
- **IS_EMPTY_QUEUE(Q)**: Restituisce TRUE se la coppia è vuota, altrimenti false.
- **ENQUEUE(Q, EL, PR)**: Inserisce nella coda una coppia di elementi (el, pr).
- **MINQUEUE(Q)**: Restituisce l'elemento con priorità massima (valore minimo) in coda.
- **DEQUEUE(Q)**: Rimuove la coppia (el, pr) che ha massima priorità (valore minimo) e lo restituisce.
- **DECREASE_PRIORITY(Q, EL, PR)**: Modifica la coppia (el, pr') in coda aggiornando la priorità di el al nuovo valore pr < pr'
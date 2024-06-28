**DEFINIZIONE**
Una coda con priorità memorizza sequenze di coppie (el, pr).
- **el:** Appartiene ad un insieme di elementi.
- **pr:** Priorità associata ad un elemento el.

**ESEMPI**:
1) Coppie in coda (esame, data) e priorità la priorità massima dell'esame con la data più vicina.
2) Coppie in coda (compito, compenso) e priorità massima il compito col compenso più alto.

**PRIMITIVE**
Massima priorità -> minima priorità.
1) make_priority_queue(Q'): Restituisce una coppia con priorità che memorizza coppie di elementi (el, pr).
2) is_empty_queue(Q): Restituisce true se la coda è vuota, false altrimenti.
3) EnQueue(Q, el, pr): Inserisce nella coda una coppia di elementi (el, pr).
4) MinQueue(Q) Restituisce l'elemento con priorità massima (valore minimo) in coda.
5) DeQueue(Q): Modifica la coppia con eliminazione della coppia (el, pr) dove pr ha massima priorità e restituisce el.
6) Decrease_Priority(Q, el, pr): Modifica la coppia (el, pr) in coda aggiornando la priorità di el al nuovo valore pr' < pr.
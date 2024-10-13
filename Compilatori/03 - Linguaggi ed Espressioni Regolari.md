**Linguaggio Regolare**
Sono i linguaggi che sono l'insieme di tutti gli identificatori o tutte le costanti numeriche. Sono regolari anche i linguaggi finiti. Si dice regolare se può essere definito tramite un numero finito di operazioni di unione/concatenazione. Se un linugaggio è regolare anche la sua chiusura riflessiva/transitiva è regolare.

**Linguaggi unitari**
I linguaggi unitari sono i linguaggi definiti da un singleton.

Ln,n {a^n b^n | n >= 0} non è un linguaggio regolare perchè possiamo prendere un numero variabile di a e b, anche diverso tra di loro. Un linugaggio è regolare se la memoria che serve per farlo funzionare è finita.

**Espressioni Regolari
- Base: epsilon è una espressione reoglare che denota il linguaggio composto della stringa vuota epsilon. Per ogni a appartenente all'alfabeto l'espressione regolare **a** denota il linguaggio costiutito dal linguaggio unitario {a}.
- Caso Ricorsivo: EF è una regex che denota il linguaggio EF (concatenazione). E|F denota l'unione, E* è una regex che denota il linguaggio E* (chiusura riflessiva).
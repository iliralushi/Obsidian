**Operazioni su Stringhe**
Un operazione fondamentale sulle stringhe è la concatenazione. 
La stringa vuota è l'elemento neutro (come l'1 nella moltiplicazione).
La potenza di una stringa è definitva ricorsivamente. Se x^k e k = 0 allora è una stringa vuota, altrimenti sarà uguale a x^k-1 x, quindi concatenata k volte.

**Linguaggio**
Un linguaggio formale su un alfabeto (sigma) è un insieme di strignhe di caratteri/o simboli di (sigma). La cosa più difficile è trovare se la stringa che vien passata fa parte del linguaggio. Se le stringhe sono finite in numero allora una possibilità consiste nella loro elencazione. Il nostro interesse verte sui linguaggi infiniti, vogliamo aggiungere una descrizione finita.

**Operazione coi linguaggi**
Poichè i linguaggi sono insiemi son definite le operazioni insiemistiche tipo unione intersezione differenza etc. La concatenazione dei 2 linguaggi è l'insieme delle stringhe dove per ogni stringa abbiamo 1 stringa del primo linguaggio ed 1 del secondo linguaggio.
- z = xy dove x è stringa del 1 linguaggio ed y stringa del 2 linguaggio.

**Potenza di un linguaggio**
- L^0 = stringa vuota
- L^n = L^n-1 * L con n > 0

**Chiusura riflessiva&transitiva di un linguaggio**
- L* = unione di tutte le potenze possibili
- B* insieme di tutte le stringhe binarie
- Sigma* = insieme di tutte le stringhe su un alfabeto sigma

**Specifica dei linguaggi**
Se il linguaggio è infinito può essere comunque possibile descriverlo con quantità finita di informazione.

**Specifica riconoscitiva**
- Tecnica riconoscitiva: Abbiamo un algoritmo a di decisione, il linguaggio risponde true se la stringa è presente nell'alfabeto del linguaggio.
- Caraterizzazione generativa: Si da un sistema di regola per cui tu puoi generare tutte le stringhe del linguaggio. Solo le stringhe generate da questo sistema fan parte di questo linguaggio.

**C++ standard template library**
- Set: Istanzia la struttura dati sugli elementi dati.
- Count: Ritorna il numero di volte in cui un elemento in un dato set compare.
- Rbegin: Prende i caratteri partendo dalla fine di una stringa (stringa rovesciata). Rbegin()[1] restituisce il penultimo carattere.
- Iterator: Struttura che definisce come percorrere un iterabile (la struttura dati).

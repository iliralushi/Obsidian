**AUTO-ASSOCIAZIONE**
Associazione che hanno come istanze di entità altre istanze della stessa entità.

**AUTO-ASSOCIAZIONI NON RICORSIVA DI EQUIVALENZA (N:M)**
Auto-associazione che va da n-m.

![[Auto-Associazioni N-M.png]]

**GRAFI AUTO-ASSOCIAZIONI**
Aggiungendo delle tuple alle nostre auto-associazioni possiamo ricondurci ad un grafo con archi orientati.
- ES: Memorizzando la coppia (R1, R2) nello schema di auto-associazione di equivalenza stiamo implicitamente progettando un arco orientato che va da R1 -> R2 e R2 -> R1.

**AUTO-ASSOCIAZIONI RICORSIVA DI GERARCHIA DI CONTROLLO**
Un impiegato è controllato da un altro impiegato (controllore). Un impiegato può essere controllore di più impiegati. Forma un grafo diretto aciclico con paternità singola.

![[Esempio 1 Auto-Associazione Ricorsiva.png]]

**AUTO-ASSOCIAZIONE RICORSIVA DI COMPOSIZIONE**
Un componente può essere composto da altri componenti. Un componente può essere componente di altri componenti. Forma un grafo diretto aciclico con paternità multipla.

![[Esempio 2 Auto-Associazione Ricorsiva.png]]

**SCHEMA OPERAI**

![[Schema Operai.png]]

**COSE CHE HO SBAGLIATO**
- Associazione tra squadre e operai ridondante. Meglio mettere un associazione capo siccome gli operai possono essere pescati già dall'auto-associazione, non c'è bisogno di fare l'associazione composti da.
- Pezzi di ricambio non trattata come entità. In questo caso era associata con gli interventi e le macchine.

**INCERTEZZE E RIDONDANZE**
Dalle frasi di specifica che vengono date possono emergere due situazioni, esempi nelle slide:
- Carenze di specifiche, quindi schemi incongruenti.
- Eccesso di specifiche, quindi schemi ridondanti.
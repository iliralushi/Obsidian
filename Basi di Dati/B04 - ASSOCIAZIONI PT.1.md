**CHIAVE DI UN ASSOCIAZIONE**
La chiave di una associazione è sempre composta ed è definita come composizione delle chiavi delle entità associate.

**VINCOLO DI INTEGRITA**
Ogni valore componente di una chiave di un istanza dell'associazione deve essere presente come valore chiave dell'istanza dell'entità associata.

**CARDINALITA DELLE ASSOCIAZIONI**
Si intende il numero di volte che una istanza di entità deve/può partecipare all'associazione.
- (1, 1): obbligatoria, una sola volta (appartengono, singolare).
- (1, n): obbligatoria, più volte (appartengono, plurale).
- (0, 1): opzionale, una sola volta (possono o non possono, singolare).
- (0, n): opzionale, più volte (possono o non possono, plurale).

**ESERCIZIO 2 COMPLETO**

![[Progetto di Ricerca.png]]

**COSE CHE HO SBAGLIATO (REMINDER PER ME STESSO)**
- CHIAVE SETTORE: Ho messo come chiave nome e comitato assieme, però i settori sono caratterizzati da una sola disciplina, quindi non ha senso.
- IMPOSTAZIONE COORDINATORE-RICERCATORE NORMALE: Lo avevo impostato usando un attributo "booleano" coordinatore. Soluzione corretta che però non è pulita perchè si ha un attributo in più e in caso di cambiamento futuro è peggio gestirlo. Per prima cosa gli attributi "MesiUomo" e "CostoOra" non sono attributi del ricercatore/progetto ma dell'azione che svolgono, quindi dell'associazione. Seconda cosa in questo caso si poteva modellare con due associazioni, una per i ricercatori normali e una per i coordinatori, stesso caso della città di partenza e arrivo.
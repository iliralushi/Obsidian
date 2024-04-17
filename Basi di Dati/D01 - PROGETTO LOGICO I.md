**MOTIVAZIONI PER LO SCHEMA LOGICO**
Lo schema E/R fornisce una descrizione sintetica della nostra base di dati, però non esistono DBMS che siano in grado di operare con gli schemi E/R. È necessario quindi tradurlo in un altro schema, quello logico.

**SCELTE ALTERNATIVE**
Il progetto logico in generale ha una serie di regole da rispettare ed applicare per arrivare alla soluzione. In certi casi sono disponibili anche soluzioni alternative che possono rivelarsi più o meno convenienti. Si possono individuare alcune regole:
- Le proprietà logiche hanno priorità rispetto all'efficienza.
- Tenere sulla stessa entità informazioni che verranno consultate insieme.
- Tenere su entità separate informazioni che vanno consultate separatamente.
- Limitare l'incidenza di valori nulli per attributi opzionali.

**FASI DEL PROGETTO**
Dopo le prime tre fasi il nostro schema sarà composto solo da entità, associazioni e attributi semplici, la quarta non è complessa, la quinta richiede molta attenzione:
1) Eliminazione delle gerarchie IS A.
2) Selezioni delle chiavi primarie, eliminazione delle identificazioni esterne.
3) Trasformazione degli attributi composti o multipli.
4) Traduzione di entità e associazioni in schemi di relazioni.
5) Verifica di normalizzazione.

> Ogni trasformazione impoverisce lo schema, non possiamo esprimere tutto dello schema E/R nello schema logico. Ciò che va perso bisogna esprimerlo come vincoli di integrità.

**ELIMINAZIONI DELLE GERARCHIE**
Il modello relazionale non rappresenta le gerarchie, vengono sostituite da entità ed associazioni. 
L'applicabilità e la convenienza delle soluzioni dipendono dalle proprietà di copertura e dalle operazioni preivste. Possiamo agire in tre modi:
1) Mantenimento delle entità con associazioni.
2) Collasso verso l'alto.
3) Collasso verso il basso. 

**MANTENIMENTO DELLE ENTITÀ CON ASSOCIAZIONI**
Soluzione sempre possibile, indipendentemente dalla copertura.
- Tutte le entità vengono mantenute.
- Le entità figlie sono in associazione con l'entità padre.
- Le entità figlie sono identificate esternamente tramite associazioni.

![[Trasformazione da Gerarchia ad Entità e Associazioni.png]]

**COLLASSO VERSO L'ALTO**
Soluzione sempre possibile.
Il collasso verso l'alto riunisce tutte le entità figlie nell'entità padre come attributi con cardinalità opzionale. Il selettore è un attributo che cambia a seconda del tipo di gerarchia e specifica se una istanza della classe padre è anche istanza della classe figlio.

![[Collasso verso l'alto.png]]

Il collasso verso l'alto favorisce le operazioni dove vengono consultati assieme gli attributi dell'entità. Gli attributi obbligatori per le entità figlie diventano attributi opzionali nell'entità padre siccome si avrà una certa percentuale di valori nulli.

**SELETTORE**
- TOTALE ESCLUSIVA: Il selettore ha N valori, quante sono le sottoentità.
- NON-TOTALE ESCLUSIVA: Il selettore ha N+1 valori, valore in più per le istanze non appartengono ad alcuna sottoentità.
- TOTALE/PARZIALE NON-ESCLUSIVA: Ci saranno tanti selettori booleani quanti entità figlie. Se la copertura è parziale possono essere tutti falsi. Le associazioni connesse alle entità figlie si connettono all'entità padre, le cardinalità minime diventeranno 0.

![[Esempio.png]]

ESEMPIO DI TRE ISTANZE:
- Studente(123, rossi) - laureando(123, DFD) - SELETTORE(L, DFD, NULL)
- Studente(218, bianchi) - SELETTORE(N, NULL, NULL)
- Studente(312, verdi) - diplomando(312, turbina) - SELETTORE(D, NULL, turbina)

- Esiste una relazione tra il valore del selettore e i campi che possono aver valore diverso a null.
- Campi prima obbligatori ora ammettono il NULL come valore.
- Per una stima delle percentuali NULL dobbiamo conoscere le percentuali di laureandi e diplomandi.

**COLLASSO VERSO IL BASSO**
Non è sempre possibile.
Consiste nell'eliminare l'entità padre e trasferiamo tutti i suoi attributi alle entità figlie.
Un associazione del padre è ripetuta tante volte quanto sono i figli. Può funzionare quando ci sono molti attributi di specializzazione (altrimenti si avrebbero molti valori nulli).

**LIMITI DI APPLICABILITÀ COLLASSO VERSO IL BASSO**
- Se la copertura non è totale non si può fare. Non si possono mettere da nessuna parte gli attributi del padre che non appartengono ad un figlio.
- Se la copertura non è esclusiva si applica ridondanza. Un istanza può essere presente in due entità figlio, quindi gli attributi del padre verranno ripetuti due volte.

![[Collasso verso il basso I.png]]![[Collasso verso il basso II.png]]

**SCELTA DELLA CHIAVE PRIMARIA**
È necessario che tra i diversi identificatori di un entità ci sia una chiave primaria, occorrerà che il DBMS sia provvisto di strumenti per garantire l'unicità dei valori. I criteri per sceglierla sono:
- Primo: scegliere che la chiave che viene usata di più per accedere all'entità.
- Secondo: si preferiscono chiavi semplici invece che composte, interne anzichè esterne.

**IDENTIFICATORI ESTERNI**
Per poter ridefinire lo schema senza identificatori esterni possiamo spostare la chiave primaria dell'entità forte all'entità debole. In questo modo possiamo eliminare l'associazione La chiave trasportata sarà la chiave esterna.

**TRASFORMAZIONE DEGLI ATTRIBUTI COMPOSTI**
Le relazioni non possono avere attributi composti oppure ripetuti ma solo attributi atomici.
1) Eliminare solo l'attributo composto e considerare i suoi componenti come attributi semplici. Perdiamo la visione unitaria però manteniamo l'articolazione dei componenti.
2) Eliminare i componenti e considerare l'attributo composto come semplice. In questo modo semplifichiamo lo schema, perdendo parte dei dettagli.

**TRASFORMAZIONE DEGLI ATTRIBUTI MULTIPLI**
Le relazioni non possono avere attributi composti oppure ripetuti ma solo attributi atomici.
- La definizione di relazione impone che se un entità E ha un attributo A multiplo, si crei una nuova entità che contenga l'attributo e sia collegata ad E. L'entità creata sarà debole dell'entità originale e avrà come foreign key l'attributo + la chiave dell'entità originale.
- Se un valore compare più volte nella ripetizione l'entità creata ha un identificatore composto con l'identificatore dell'entità forte + un valore identificante sintetico.
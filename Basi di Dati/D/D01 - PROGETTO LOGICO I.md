**MOTIVAZIONI PER LO SCHEMA LOGICO**
Lo schema E/R fornisce una descrizione sintetica della nostra base di dati, però non esistono DBMS che siano in grado di operare con gli schemi E/R. È necessario quindi tradurlo in un altro schema, quello logico.

**SCELTE ALTERNATIVE**
Il progetto logico in generale ha una serie di regole da rispettare ed applicare per arrivare alla soluzione. In certi casi sono disponibili anche soluzioni alternative che possono rivelarsi più o meno convenienti. Si possono individuare alcune regole:
- Le proprietà logiche sono prioritarie rispetto all'efficienza.
- Tenere sulla stessa entità informazioni che verranno consultate insieme.
- Tenere su entità separate informazioni che vanno consultate separatamente.
- Fare in modo che ci siano meno valori nulli possibili in attributi opzionali.

**FASI DEL PROGETTO**
Dopo le prime tre fasi il nostro schema sarà composto solo da entità, associazioni e attributi semplici, la quarta non è complessa, la quinta richiede molta attenzione:
1) Eliminazione delle gerarchie isa.
2) Selezioni delle chiavi primarie, eliminazione delle identificazioni esterne.
3) Trasformazione degli attributi composti o multipli.
4) Traduzione di entità e associazioni in schemi di relazioni.
5) Verifica di normalizzazione.

> Ogni trasformazione impoverisce lo schema, non possiamo esprimere tutto dello schema E/R nello schema logico. Ciò che va perso bisogna esprimerlo come vincoli di integrità.

**ELIMINAZIONI DELLE GERARCHIE**
Per eliminare le gerarchie dobbiamo tenere in considerazione le proprietà di copertura e le operazioni previste. Sostituiamo le gerarchie con le entità e le associazioni.
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
Il collasso verso l'alto riunisce le entità figlie sull'entità padre come i loro attributi con cardinalità opzionale. Viene inoltre creato un attributo selettore che specifica se un istanza del padre appartiene ai figli. Il collasso verso l'alto favorisce le operazioni dove vengono consultati assieme gli attributi dell'entità, il suo contro è che ci possono essere una grande quantità di valori nulli.

![[Collasso verso l'alto.png]]

**SELETTORE**
- TOTALE + ESCLUSIVA: Il selettore ha N valori, uno per ogni figlio.
- NON-TOTALE + ESCLUSIVA: Il selettore ha N+1 valori, uno per ogni figlio più un valore utilizzato per indicare un istanza di entità che non appartiene ad alcun figlio.
- TOTALE/PARZIALE NON-ESCLUSIVA: Ci saranno tanti **SELETTORI** booleani quanto il numero di figli. Le associazioni connesse alle entità figlie si connettono all'entità padre e la cardinalità minima delle associazioni diventerà zero.

![[Esempio.png]]

ESEMPIO DI TRE ISTANZE:
- Studente(123, rossi) - laureando(123, DFD) - SELETTORE(L, DFD, NULL)
- Studente(218, bianchi) - SELETTORE(N, NULL, NULL)
- Studente(312, verdi) - diplomando(312, turbina) - SELETTORE(D, NULL, turbina)

- Esiste una relazione tra il valore del selettore e i campi che possono aver valore diverso a null.
- Campi prima obbligatori ora ammettono il NULL come valore.
- Per una stima delle percentuali NULL dobbiamo conoscere le percentuali di laureandi e diplomandi.

**COLLASSO VERSO IL BASSO**
Non è sempre possibile/conveniente.
Consiste nell'eliminare l'entità padre e trasferire tutti i suoi attributi alle entità figlie.
Un associazione del padre è ripetuta tante volte quanto sono i figli. Può funzionare quando ci sono molti attributi di specializzazione (altrimenti si avrebbero molti valori nulli).

**LIMITI DI APPLICABILITÀ COLLASSO VERSO IL BASSO**
- Se la copertura non è totale non si può fare. Non si possono mettere da nessuna parte le istanze del padre che non appartengono ai figli.
- Se la copertura non è esclusiva si applica ridondanza. Un istanza può essere presente in due entità figlio, quindi gli attributi del padre verranno ripetuti due volte.

![[Collasso verso il basso I.png]]![[Collasso verso il basso II.png]]

**SCELTA DELLA CHIAVE PRIMARIA**
È necessario che tra i diversi identificatori di un entità ci sia una chiave primaria, occorrerà che il DBMS sia provvisto di strumenti per garantire l'unicità dei valori. Le altre chiavi non vengono eliminate, diventano semplicemente alternative keys. I criteri per sceglierla sono:
- Primo: scegliere che la chiave che viene usata di più per accedere all'entità.
- Secondo: si preferiscono chiavi semplici invece che composte, interne anzichè esterne.

**IDENTIFICATORI ESTERNI**
Per poter ridefinire lo schema senza identificatori esterni possiamo copiare la chiave primaria dell'entità forte all'interno dell'entità debole. In questo modo l'associazione è rappresentata attraverso la chiave e può essere eliminata, inoltre l'entità trasportata sarà la foreign key e si creerà una chiave composta tra la foreign key e l'attributo che l'identificatore esterno designava prima.

**TRASFORMAZIONE DEGLI ATTRIBUTI COMPOSTI**
Le relazioni non possono avere attributi composti oppure ripetuti ma solo attributi singoli (atomici).
1) Eliminare solo l'attributo composto e considerare i suoi componenti come attributi semplici. Perdiamo la visione unitaria dell'attributo però manteniamo tutte le informazioni.
2) Eliminare i componenti e considerare l'attributo composto come semplice. Semplifichiamo lo schema avendo soltanto un attributo però perdiamo informazioni.

**TRASFORMAZIONE DEGLI ATTRIBUTI MULTIPLI**
Le relazioni non possono avere attributi composti oppure ripetuti ma solo attributi atomici.
- **CASO A)** - La definizione di relazione impone che se un entità E ha un attributo A multiplo allora si deve creare un entità separata che contiene l'attributo e sia collegata all'entità che conteneva l'attributo multiplo in foreign key, quindi trasportando la chiave dell'entità E all'entità creata. La soluzione è applicabile solo quando il valore di quell'attributo si ripete solo una volta. Nell'esempio sotto la qualifica era un attributo multiplo di dipendente.
  
  ![[Trasformazione attributo multiplo in entità.png]]
  
- **CASO B)** - Se un valore appare più di una volta (il marcatore di una partita potrà essere lo stesso per più volte) allora l'entità creata avrà l'identificatore composto dell'identificatore di E + un valore identificante sintetico che può essere per esempio un numero d'ordine.
  
  ![[Attributo ripetuto caso B 1.png]]
  ![[Attributo ripetuto caso B 2.png]]
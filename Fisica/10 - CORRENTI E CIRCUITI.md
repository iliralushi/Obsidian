**CORRENTE**
La corrente (amp) è la misura del flusso di carica elettrica attraverso un materiale conduttore:
- `I = △q/△t.`

**FEM E CIRCUITI**
Una batteria ideale mantiene una differenza di potenziale costante tra i suoi morsetti. Questa differenza si chiama forza elettromotrice della batteria (FEM ε).

Il lavoro svolto da una batteria ideale nello spostare una carica q tra i due morsetti è di:
- `W = q * ε.`

Le batterie funzionano convertendo energia chimica in energia elettrica. Una batteria si esaurisce quando non può più sostenere le reazioni chimiche, quindi non può più produrre lavoro per spostare le cariche.

**LEGGE DI OHM**
Un materiale si dice Ohmico se il potenziale è direttamente proporzionale alla corrente. La legge di Ohm conferma la relazione tra potenziale e corrente, aggiungendo la costante di proporzionalità che è la resistenza (ohm).
- `V = IR.`

**RESISTENZA E RESISTIVITA**
Con ρ la resistività del materiale, L la lunghezza del conduttore ed A l'area, la resistenza è:
- `R = ρ * L / A.`

La resistività di un materiale dipende dalla sua temperatura. ρ0 è la resistività inerente alla temperatura T0 ed α il coefficiente di temperatura della resistività. Abbiamo che:
- `ρ = ρ0 * (1 + α(△T)).`

**MISURA DI CORRENTI E VOLTAGGI**
Le correnti si misurano con un amperometro. Un amperometro è posizionato in serie al componente di interesse. La caduta di potenziale si misura col voltometro, viene posizionato in parallelo rispetto al componente.

**POTENZA ED ENERGIA NEI CIRCUITI**
Abbiamo tre formule; una generale, una per una sorgente di FEM e una per le resistenze:
- `P = △U / △t = q / △t * △V = I * △V.`
- `P = Iε.`
- `P = I * △V = I^2 * R = △V^2 / R.`

**PRINCIPI DI KIRCHOFF**
Per introdurre le due leggi di Kirchoff partiamo dall'introduzione di due concetti:
- **NODO**: Punto in cui 3+ fili si incontrano.
- **MAGLIA**: Percorso chiuso all'interno di un circuito.

- **LEGGE DEI NODI**: La corrente che entra in un nodo è la stessa che esce da esso. Questo è il principio che esprime la conservazione della carica elettrica.
- **LEGGE DELLE MAGLIE**: La somma delle cadute di potenziale in una maglia è zero. Questo è il principio che esprime la conservazione dell'energia.

**RESISTENZE IN SERIE**
La corrente I attraverso le resistenze in serie è la stessa. Applicando la legge di Kirchoff sulle maglie abbiamo: 
- `ε - IR1 - IR2 = 0.`
- `ε = IR1 + IR2 = I(R1 + R2) = IReq.`

La coppia di resistenze (R1, R2) si può sostituire con un unica resistenza `Req.`
In generale, per le resistenze in serie abbiamo che `Req = R1 + R2 + ... RN`

**RESISTENZE IN PARALLELO**
La corrente I attraverso le resistenze in parallelo non è la stessa. Quando la corrente raggiunge un estremo del circuito la corrente si divide. Applicando la legge di Kirchoff sulle maglie:
- `ε - I1R1 = 0`.
- `ε - I2R2 = 0.`
- `ε = I1R1 = I2R2.`

Applicando la legge dei nodi quindi abbiamo:
- `I = I1 + I2.`
- `I = ε / R1 + ε / R2.`
- `I / ε = 1 / R1 + 1 / R2.`

La coppia di resistenze (R1, R2) si può sostituire con un unica resistenza `Req.`
In generale, per le resistenze in parallelo abbiamo `Req = 1 / R1 + 1 / R2 ... + 1 / RN.`

**CONDENSATORI IN SERIE**
Se i due condensatori nelle armature hanno la stessa quantità di carica sono collegati in serie. Applicando la legge di Kirchoff sulle maglie abbiamo:
- `ε = Q / C1 = Q / C2.`
- `ε / Q = 1 / C1 + 1 / C2 = 1 / Ceq.`

La coppia di condensatori si può sostituire con un solo condensatore di capacità `1 / Ceq.`
In generale abbiamo che `1 / Ceq = 1 / C1 + 1 / C2 ... 1 + CN.`

**CONDENSATORI IN PARALLELO**
Se i due condensatori nelle armature hanno carica diversa allora sono collegati in parallelo. Applicando la legge di Kirchoff sulle maglie abbiamo:
- `ε - Q1 / C1 = 0`
- `ε - Q2 / C2 = 0`
- `Qeq = Q1 + Q2.`
- `εCeq = εC1 + εC2.`

La coppia di condensatori può essere sostituita con un solo condensatore di capacità `Ceq.`
In generale, per i condensatori in parallelo abbiamo `Ceq = C1 + C2 + ... CN`
**Corrente Elettrica**
La corrente è una misura della quantità che carica attraverso un area perpendicolare al flusso di carica. Si misura in ampere. Se la corrente scorre nella stessa direzione allora si dice che è una **corrente continua**.
- $I$ $=$ $Δq$  $/$ $Δt$

**Corrente in un Filo**
Supponiamo di avere un filo di metallo. Se abbiamo una differenza di potenziale negli estremi del filo allora si crea un moto di elettroni che fluirà finchè la $ddp$ non si annulla. 
Per convenzione supponiamo che la corrente sia trasportata da cariche positive, quindi
la direzione di scorrimento della corrente è opposto al flusso degli elettroni.

**Batterie**
Una batteria funziona convertendo energia chimica in energia elettrica. Essa smette di funzionare quando non riesce più a sostenere le reazioni chimiche, quindi non riesce più a produrre lavoro per spostare le cariche.

**FEM**
Una batteria ideale mantiene una $DDP$ costante tra i suoi morsetti. Questa $DDP$ si chiama Forza Elettromotrice. Il lavoro svolto da una batteria per spostare una carica da un morsetto all'altro è:
- $W$ $=$ $q$ $×$ $ε$

**Materiale Ohmico**
Un materiale è considerato Ohmico se:
- $ΔV$ $∝$ $I$

**Legge di Ohm**
La legge di Ohm rappresenta la relazione tra potenziale elettrico, corrente e resistenza.
- $ΔV$ $=$ $I$ $×$ $R$

**Resistenza**
La resistenza di un conduttore misura la capacità dell'oggetto all'opporsi al flusso della corrente elettrica. Comprende la resistività del materiale, la lunghezza del conduttore e l'area della sezione trasversale.
- $R$ $=$ $ρ$ $×$ $L$ $/$ $A$

**Resistività**
La resistività di un materiale misura la sua resistenza al passaggio della corrente elettrica. Essa dipende dalla temperatura.
- $ρ$ $=$ $ρ0$ $×$ $($$1$ $+$ $α$ $×$ $($$T$ $-$ $T0$$)$$)$

**Misurare Correnti e Voltaggi**
- Le correnti si misurano con un amperometro. Un amperometro è posizionato in serie rispetto al circuito da ispezionare.
- La caduta di potenziale su un circuito invece si misura con un voltmetro. Un voltmetro è posizionato in parallelo rispetto alle resistenze del circuito.

**Potenza ed Energia nei Circuiti**
- Potenza: $P$ $=$ $ΔU$ $/$ $Δt$ $=$ $q$ $×$ $ΔV$ $/$ $Δt$ $=$ $I$ $×$ $ΔV$
- Per FEM: $P$ $=$ $I$ $×$ $ε$
- Per resistenza: $P$ $=$ $I$ $×$ $ΔV$ $=$ $I^2$ $×$ $R$ $=$ $ΔV^2$ $×$ $R$

**Nodi e Maglie**
Un nodo è un punto in un circuito dove tre o più fili si incontrano, mentre una maglia è un percorso chiuso all'interno di un circuito.

**Principi di Kirchhoff**
Abbiamo due leggi; la legge dei nodi e la legge delle maglie.
- **Legge dei Nodi**: essa stabilisce che la corrente che entra in un nodo è la stessa corrente che esce da stessa. Esprime il principio di conservazione della carica elettrica.
- **Legge delle Maglie**: essa stabilisce che la somma delle cadute di potenziale in una maglia è pari a zero. Esprime la conservazione dell'energia.

**Dimostrazione Kirchhoff Circuiti in Serie**
Si dice che le resistenze sono in serie se la corrente attraverso queste resistenze è la stessa, in pratica dobbiamo avere un circuito chiuso.
1) Partiamo applicando la legge delle maglie sul nostro circuito. Abbiamo quindi:
   $ε$ $-$ $IR1$ $-$ $IR2$ $=$ $0$
2) Spostiamo le resistenze a destra e raggruppiamo le resistenze per la corrente. 
   $ε$ $=$ $I$ $×$ $($$R1$ $+$ $R2$$)$ $=$ $IReq$
3) La coppia di resistenze può essere sostituita con un unica resistenza equivalente $Req$. In generale per le resistenze in serie abbiamo che $Req$ $=$ $R1$ $+$ $R2$ $+$ $...$ $+$ $Rn$.

**Dimostrazione Kirchhoff Circuiti in Parallelo**
Si dice che le resistenze sono in parallelo quando non abbiamo un circuito chiuso. In questo caso la corrente si divide quando raggiungiamo una parte del circuito che ha una resistenza.
1) Partiamo applicando la legge delle maglie sul nostro circuito. Abbiamo quindi:
   $ε$ $-$ $I1R1$ $=$ $0$ 
   $ε$ $-$ $I2R2$ $=$ $0$
2) Di conseguenza sempre per la legge delle maglie abbiamo che $ε$ $=$ $I1R1$ $=$ $I2R2$.
3) Applicando la legge dei nodi, e poi sostituendo per I abbiamo:
   $I$ $=$  $ε$ $/$ $R1$ + $ε$ $/$ $R2$
   $I$ $/$ $ε$ $=$ $1$ $/$ $R1$ $+$ $1$ $/$ $R2$ $=$ $1$ $/$ $Req$
4) La coppia di resistenze può essere sostituita con un unica resistenza equivalente $Req$. In generale per le resistenze in parallelo abbiamo che: $1/Req$ $=$ $1$ $/$ $R1$ $+$ $...$ $+$ $1$ $/$ $Rn$. 

**Dimostrazione Kirchhoff Condensatori in Serie**

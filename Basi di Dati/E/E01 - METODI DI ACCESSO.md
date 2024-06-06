**DATA SERVER**
Un server in cui siamo interessati a memorizzare permanentemente i nostri dati. La qualità principale che deve avere un data server è:
- Capacità e velocità delle memorie permanenti.

**TIPI DI MEMORIE PERMANENTI**
- **MEMORIE MAGNETICHE**: Dischi rigidi, dischi paralleli.
- **MEMORIE OTTICHE**: CD, DVD, BlueRay.
- **MEMORIE ELETTRONICHE**: Memorie flash.

**HARD DISK**
Il tipo di memoria principale usata nei data server.
I dati vengono memorizzati su piatti. I piatti contengono una serie di tracce. Le tracce a loro volta contengono settori.

![[Struttura HDD.png]]

**MECCANICA DEL DISCO**
I piatti ruotano mentre il pettine effettua un movimento. Una volta raggiunto il cilindro desiderato viene attivata la testa una volta raggiunta la traccia desiderata. Infine si ha l'attesa del settore ed avviene la lettura/scrittura.
- **SETTORE**: Unità minima di trasferimento, possono essere raggruppati in blocchi/page.

**TEMPO DI SERVIZIO**
- **Ts**: Tempo di posizionamento (seek time). Viene indicato dal costruttore come il tempo medio di spostamento tra due tracce.
- **Tr**: Tempo di latenza rotazionale. Mediamente la metà del tempo di rotazione.
- **Tb**: Tempo di lettura/scrittura. Dipende dalla dimensione del blocco.
- **Tc**: Tempo impiegato dal controller. Indicato dal costruttore.

**READ AFTER WRITE**
Dato che le scritture valgono di più delle letture se vogliamo trovare le scritture dobbiamo ricontrollare dopo un giro.
- **TRANSFER RATE**: Misurato in MB/s.

**TEMPO DI ACCESSO HDD**
`Ts = 9ms, transfer rate 30MB/sec, blocco 4096 bytes, Tc = 1ms, rotazione 7200rpm.`
`Dobbiamo accedere al blocco di 4096 bytes:`

- **FORMULA**: `Ts + Tr + Tb + Tc.`
- `9ms + (0.5 / 7200rpm) + (4KB/30MB/s) + 1ms = 9 + 4.15 + 0.1 + 1ms = 14.3ms`
- **READ AFTER WRITE**: `14.3ms + 2 * 4.15ms = 22.6ms`

**SSD**
- Le pagine degli SSD variano da 4KB a 512KB.
- Dati vengono scritti/letti per pagina.
- Scritture possibili solo su pagine vuote/cancellate.

**LETTURE SU SSD**
Nessun tempo di seek o latenza rotazionale.
- **TEMPO DI ACCESSO**: `Tq (tempo di queue) + Tb + Tc.`

**SCRITTURE SU SSD**
Scrivere dati su SSD è complesso dato che è possibile solo su pagine cancellate/vuote. Possiamo cancellare un insieme di pagine nell'intervallo (32, 128).
- **RULE OF THUMB**: Scrittura = 10x lettura.

**STRUTTURA DEI FILE**
Le prestazioni generali per l'accesso ad un file vengono valutate come la somma del numero di blocchi dati che vengono scritti/letti da un operazione.

**TERMINI ACCESSO SEQUENZIALE/ORDINATO**
- **NT**: Numero totale di tuple.
- **NB**: Numero totale di blocchi.
- **NM**: Disponibilità nella memoria centrale.

**COME AVVIENE L'ACCESSO SEQUENZIALE**

![[Accesso Sequenziale.png]]

- Cittadini è una relazione che contiene NT tuple contenuta in un file di NB blocchi.
- Dato che la relazione non è ordinata, vengono visitati i blocchi in maniera sequenziale finchè troviamo CF, quindi se lo ha trovato si ferma, altrimenti continua per tutto il file.

- Se **NON** abbiamo trovato CF abbiamo visitato tutto il file, quindi il numero di accessi è NB.
- Se **ABBIAMO** trovato CF operiamo come sul disco; consideriamo il caso migliore e peggiore (accesso al primo ed ultimo blocco) e troviamo la media che sarà di NB/2.

- Assumendo NB = 10000 e Td (Tempo di accesso ad un blocco) = 20ms allora:
- `Ta = NB/2 * Td = 10000/2 * 20 * 10^-3 = 100s`

**ORDINARE UN FILE**
Utile non solo per la presentazione del contenuto ma anche per velocizzare la ricerca. Un file molto grande viene ordinato attraverso il metodo **Sort/Merge (ad M way).**

**SORT**
- Vengono portati in memoria NM blocchi per volta e le tuple ordinate con un algoritmo di Sort. Ogni gruppo di NM blocchi viene memorizzato in un file distinto `(NF = NB/NM file).`
- I blocchi costituenti gli NF file (che contengono gli NB) vengono ordinati.

**MERGE**
**PASSO**: Vengono portati gradualmente in memoria i blocchi di M file, si opera una fusione ordinata delle tuple contenute. Il processo finisce quando finiamo gli NF file. I passi si ripetono finchè abbiamo fuso tutti gli NF file, quindi abbiamo finito.
- **Passi di Merge** = `PM = Logm(NB/NM).`
- **Costo del Sort** = `Csort = 2 * NB * (PM+1)`

**BINARY SEARCH**

![[Binary Search.png]]

- **Costo ricerca binaria medio:** `Cbin = Log2(NB) - 1`
- **Costo ricerca binaria caso peggiore** : `Cbin = Log2(NB) + 1`

**CALCOLO DEL COSTO DI LETTURA**
`Blocco = 512 byte, NB = 100000, Lb = 512.`

- **TLETTURA**: `Td = Ts (16ms) + Tr (8.3ms) + Tb (512/3MB/s = 0.17ms) = 24.47ms.`
- **RICERCA SEQUENZIALE**: Supponendo di trovare il nostro record abbiamo accesso medio NB/2. `Tempo di accesso = Ta = NB/2 * Td = 50000 * 24.47 = 1223.5s`
- **RICERCA BINARIA**: Abbiamo accesso medio di `Log2(NB) - 1 = 16`
  `Tempo di accesso = Ta = Log2(NB) - 1 * Td = 16 * 24.47 = 392ms`

**METODI DI ORGANIZZAZIONE**
In un file può esistere un solo tipo di ordinamento:
- Può essere NON ordinato, e a quel punto i blocchi vengono accessi in modo sequenziale.
- Può essere ordinato tramite Merge/Sort, è costoso da mantenere, specialmente quando si aggiungono nuove tuple.
- Esistono ordinamenti primari (Merge/Sort) e secondari.
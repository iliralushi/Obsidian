**ATTRIBUTO SCALARE**
Un attributo semplice, che ha solo un valore.
- ES: Matricola, voto, nome...

**ATTRIBUTO MULTIPLO**
Un attributo che ammette n valori. Il simbolo (n, m) esprime la cardinalità della proprietà.
- ES: Titolo, qualifica, specialità...

**ATTRIBUTO COMPOSTO**
Un insieme di attributi. L'attributo si rappresenta con una spilla grande, i suoi "sottoattributi" con spille piccole.
- ES: Data (spillo grande) è composta da giorni, mesi, anni (spilli piccoli)

![[Attributo Composto.png]]

**ATTRIBUTO MULTIPLO COMPOSTO**
Un attributo multiplo (quindi di cardinalità (1, n)) che è composto, quindi ha dei "sottoattributi" che lo aiutano a descrivere.
- ES: Telefono (spillo grande, può essere più di uno) è composto da stato, città, numero (spilli piccoli)

**ATTRIBUTO OPZIONALE**
Un attributo dove è ammessa la non-esistenza del valore. Si esprime con cardinalità (0, n).
- ES: Telefono, qualifica, voto

> **ATTENZIONE!**
> "Non-esistenza" è diverso da "non si sa" oppure "non è applicabile".

**ATTRIBUTO TOTALE**
Il contrario dell'attributo opzionale. Deve esserci un valore. Si esprime con cardinalità (≥1, n).
- ES: Codice fiscale, cognome sono attributi totali, nome, indirizzo sono attributi opzionali (caso ipotetico ovviamente)

**ATTRIBUTO COSTANTE**
Un attributo che non può cambiare valore. In alternativa l'attributo si dice **modificabile**.
- ES: C.F, cognome sono generalmente costanti. Parametro, indirizzo invece modificabili

**ATTRIBUTO CALCOLATO**
Un attributo a cui il valore è calcolato con un certo algoritmo. In alternativa l'attributo si dice **esplicito**.
- ES: C.F, cognome sono espliciti, lo stipendio è calcolato

**ATTRIBUTO UNICO**
Un attributo dove tutte le istanze della classe hanno valore diverso. In alternativa l'attributo si dice **generico**.
- ES: C.F, p.iva sono unici perchè ogni persona li ha diversi, il cognome può essere generico

**ATTRIBUTO TEMPORALE**
Un attributo le cui variazioni vanno memorizzate. Ci interessa non solo l'attributo in sè ma come si comporta nel corso del tempo.
- SNAPSHOT: Memorizzo periodicamente le variazioni del mio attributo (stipendio, quantità...)
- STORICO: Modellare direttamente nel database la variazione e il tempo di variazione (prezzo, indirizzo, mansione...)

**ATTRIBUTO CHIAVE**
Un attributo che identifica in modo univoco la singola istanza di entità (o di associazione). Si rappresenta con uno spillo colorato tutto di nero.
- Deve essere un attributo totale, unico, esplicito
- Può essere composto, si rappresenta con n spilli bianchi quanti sono gli attributi e in mezzo verticalmente si mette un spillo nero
- Non è generalmente modificabile

**VINCOLI DEGLI ATTRIBUTI**
Non sempre i valori degli attributi possono crescere liberamente ma sono vincolati da **regole**.
I vincoli non vengono rappresentati graficamente ma su specifiche a parte.

**VINCOLI STATICI**
1) Un vincolo che controlla se il valore di un attributo appartiene ad un dominio preciso.
2) Esiste un altro tipo di vincolo statico, ovvero dove il vincolo su un attributo è dipendente da valori di altri attributi.
3) Il controllo del vincolo ci può servire in ogni fase, ovvero quella di caricamento dati, quella dell'interrogazione o quella dell'aggiornamento.

- ES1: Composizione di stringhe di caratteri. Il vincolo dell'attributo nome è che deve contenere solo le lettere che vanno dalla A alla Z. T1berio non va bene ma Tiberio si
- ES1: Verifica all'interno di intervalli. Il vincolo dell'attributo peso può essere che deve essere 50 < peso < 600
- ES2: Se la gara è slalom, sesso M e categoria internazionale allora il dislivello è tra 180-220m. L'attributo dislivello dipende dai valori di altri attributi, ovvero gara, sesso e categoria

**VINCOLI DINAMICI**
Un vincolo statico può non essere sufficiente. Esso è un vincolo che varia nel tempo. Lo si esprime con un **diagramma di stato**, sono necessarie regole sugli eventi che fanno cambiare stato.
- ES: Stipendio precedente < Stipendio successivo deve essere sempre valido, cosa che non è accertata col vincolo statico

**COME SCEGLIERE L'ATTRIBUTO CHIAVE**
- Criteri che dipende dall'entità (matricola, cod. inventario, targa...)
- Chiave scelta da altre organizzazioni (cod.fiscale, num.telaio...)
- Uso pregresso in azienda (codice parlante, codice che può essere spezzato in altri sottocodici, es. matricola 21 07 42379 che comprende dipartimento, cdl e numero matricola)
- Scelta condizionata dai fattori esterni (dipende)

**CHIAVI ALTERNATIVE**
Ci possono essere più chiavi per la stessa entità.
- ES: Albergo, una chiave è hotel_id, un attributo chiave composto che comprende nome e località. Un'altra chiave può essere un codice_hotel che è un numero che identifica l'hotel. Entrambi gli attributi rispettano i requisiti per essere attributi chiave.

**SCHEMA ESERCIZIO 1**

![[Schema Agenzia di Viaggi.png]]




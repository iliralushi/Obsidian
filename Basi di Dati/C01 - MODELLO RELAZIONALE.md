**MODELLO RELAZIONALE INFORMALE**
- TABELLA
- COLONNA
- RIGA
- SCHEMA: E' la struttura della base di dati
- ISTANZA: Sono i dati memorizzati in un certo tempo

![[Modello Relazionale.png]]

**MODELLO RELAZIONALE FORMALE**
- DOMINIO: Un qualunque insieme di valori
- PRODOTTO CARTESIANO DI N DOMINI: Insieme di tutte le n-ple
- RELAZIONE: Un qualunque sottoinsieme del prodotto cartesiano

**PROPRIETA RELAZIONI**
- GRADO: Il numero di domini
- CARDINALITA: Il numero di tuple
- ATTRIBUTO: Nome del dominio. Devono essere tutti distinti tra di loro
- SCHEMA: Tabella con tutti gli attributi della relazione
- ISTANZA: Insieme di tuple su uno schema della relazione

**CONFRONTO TERMINOLOGIA**
- RELAZIONE = TABELLA
- ATTRIBUTO = COLONNA
- TUPLA = RIGA
- DOMINIO = TIPO DI DATO
- CARDINALITA = NUM. RIGHE
- GRADO = NUM. COLONNE

**BASE DI DATI**
- SCHEMA: E' un insieme di schemi di relazione. Tutti i nomi delle relazioni devono essere differenti
- ISTANZA: E' un insieme di istanze di relazioni

**INFORMAZIONE INCOMPLETA IN UNA BASE DI DATI**
- VALORE NULLO: Denota l'assenza di un valore del dominio (non è un valore del dominio)
- Si devono imporre restrizioni sui valori nulli

**VINCOLI DI INTEGRITA**
Esso esclude alcune istanze che pur essendo sintatticamente corrette non rappresentano informazioni possibili per l'applicazione di interesse
- Ad uno schema associamo dei vincoli di integrità e tutte le istanze che soddisfano i vincoli sono istanze accettabili

**CHIAVE**
Essa è un sottoinsieme degli attributi che soddisfa le condizioni di
- UNICITA: Non esistono due tuple con chiave uguale
- MINIMALITA: Sottraendo un qualunque attributo alla chiave si perde la proprietà di unicità
- CHIAVE PRIMARIA: La chiave principale che trova univocamente ogni record della tabella
- CHIAVE SECONDARIA (AK): Tutte le altre chiavi
- SUPERCHIAVE: E' un insieme di chiavi che trova univocamente ogni record della tabella








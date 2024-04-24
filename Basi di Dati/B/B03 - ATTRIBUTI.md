**CARDINALITÀ**
- (0,1) - può esserci una sola istanza.
- (1,1) - deve esserci una sola istanza.
- (0,n) - possono esserci più istanze.
- (1,n) - devono esserci una o più istanze.

**ELENCO ATTRIBUTI**
- **Attributo scalare**: Semplice, ad un solo valore (matricola, voto).
- **Attributo multiplo**: Semplice, ammessi n valori (qualifica, titolo).
- **Attributo composto**: Attributo che contiene più attributi (data contiene gg, mm, aaaa).
- **Attributo multiplo composto**: Telefono (stato, città, numero).
- **Attributo opzionale**: Possono non esserci istanze, quindi ha cardinalità 0,n (telefono, nome).
- **Attributo totale**: Deve esserci minimo una istanza, quindi ha cardinalità 1,n (CF).
- **Attributo costante**: Non può cambiare valore (CF, cognome, nome).
- **Attributo modificabile**: Può cambiare valore (voto, indirizzo).
- **Attributo unico**: Ha tutte le istanze con valore diverso (CF, matricola).
- **Attributo generico**: Le istanze possono uguagliarsi (nome, cognome).
- **Attributo chiave**: Identifica in modo univoco una singola istanza di entità o associazione. Deve essere totale, unico, esplicito, può essere composto e non è modificabile.

**VINCOLI SUGLI ATTRIBUTI**
I vincoli degli attributi sono regole imposte agli attributi in modo che non assumano valori illegali.
Spesso possono essere rappresentati nello schema E/R, altri vengono gestiti su specifiche a parte.
- Vincoli statici: Sono i vincoli più semplici. Controllano se il valore di un attributo appartiene ad un certo dominio. Un vincolo di un attributo può essere dipendente da valori di altri attributi.
- Vincoli dinamici: Un vincolo dinamico è un vincolo che varia nel tempo.

**TIPO DELLA CHIAVE**
- Può essere un criterio dipendente dall'entità (matricola, codice inventario, targa...).
- Può essere una chiave scelta da altre organizzazioni (CF, numero telaio...).
- Può essere una scelta condizionata da fattori esterni.
- Può essere un serial che mantiene l'unicità (spesso sconsigliati perchè poco significativi).

**ALTERNATIVE KEY**
Possono esserci più chiavi per una singola entità. 
- ES: Nell'entità albergo abbiamo due chiavi. La chiave primaria è l'hotel_id che è una chiave molto significativa dato che ci dice nome e località dell'albergo. Una possibile chiave secondaria è un codice hotel.

![[Alternative Key.png]]
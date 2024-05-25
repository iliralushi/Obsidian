**ECCEZIONE**
Evento che capita durante l'esecuzione che sconvolge il flusso normale dell'esecuzione.
In Java la gestione degli errori avviene attraverso le eccezioni.

**APPROCCIO IF-THEN**
Solitamente le eccezioni vengono gestite con il costrutto if. Questo approccio ha due svantaggi:
- Se dobbiamo gestire tante eccezioni complica il programma notevolmente.
- Se dobbiamo gestire le eccezioni in una funzione che può restituire un qualsiasi numero intero non possiamo restituire un numero.

**APPROCCIO JAVA**
Java unisce un costrutto apposito (try-catch) ad un approccio orientato agli oggetti.
Esistono classi per rappresentare le eccezioni. La radice della gerarchia delle eccezioni è la classe Throwable, che a sua volta ha due sottoclassi principali:
- **ERROR**: Per definire errori interni non recuperabili.
- **EXCEPTION**: Per definire anomalie che possono essere recuperate.

**SOLLEVARE UN'ECCEZIONE**
Ogni metodo può sollevare una o più eccezioni:
- **THROW**: Solleva un'eccezione.
- **THROWS**: Indica quali eccezioni può sollevare.

**ESEMPIO DI TRY-CATCH**
Il metodo read() solleva una IOException se non riesce a leggere da file.
- Possiamo avere anche più catch per catturare più eccezioni.
- Non confondiamo il valore di ritorno con la segnalazione di un'eccezione.
- Ci sono alcune eccezioni che non vanno catturate, come le RuntimeException, ArrayIndexOutOfBoundsException...

``` Java
try
{
	c = f.read();
}
catch (IOException e)
{
	System.err.println("Impossibile leggere: " + e);
}
catch (IllegalFormatException e)
{
	Syste.err.println("Formato illegale: " + e);
}
```

**RILANCIO DI UNA ECCEZIONE**
Un metodo che invoca un altro metodo a rischio può anche non gestire l'eccezione direttamente, ma rilanciarla a sua volta.
- m() scarica la gestione dell'eccezione a chi lo invocherà.
- La chiamata di m() deve essere in un try-catch.

``` Java
public int m() throws IOException
{
	c = f.read();
}
```

**I/O DI JAVA**
Questo package definisce quattro classi base **astratte** per l'I/O:
- **INPUTSTREAM / OUTPUTSTREAM**: Leggono/scrivono stream di **byte**.
- **READER / WRITER**: Leggono/scrivono stream di **caratteri**.

**BYTE VS CARATTERI**
In Java sono tipi diversi (il tipo char occupa due byte) quindi è necessario distinguerli nell'I/O.
Se si legge un file di testo come sequenza di byte, Java potrebbe non riuscire ad interpretare i byte letti come caratteri.

**CLASSI DERIVATE**
Le quattro classi citate sopra sono astratte, contengono una varietà di sottoclassi concrete che leggono/scrivono tipi specifici di stream. Le sottoclassi si dividono in due categorie;
- **CLASSI SORGENTE/POZZO**: Specificano le classi astratte rispetto alla sorgente/destinazione dei flussi, non aggiungono funzionalità. L'I/O può diventare un file o un buffer.
- **CLASSI FILTRO**: Specializzano e aumentano le funzionalità delle classi astratte. Per esempio, fanno leggere più stream di byte/caratteri in contemporanea o anche dati strutturati quali tipi primitivi ed oggetti.

**INCAPSULAMENTO (NON OOP)**
L'incapsulamento per l'I/O consiste nel comporre tutte le classi concrete che ci interessano in modo da avere una composizione di oggetti che contiene tutte le funzionalità richieste.
1) Si crea un oggetto da una classe sorgente per definire il flusso dei dati.
2) Si crea un oggetto da una classe di filtraggio concreta e si passa al costruttore l'oggetto sorgente creato.

``` Java
import java.io.*;

public class GestioneFile
{
	FileInputStream f = null;
	f = new FileInputStream("Prova.dat");
	
	// creiamo uno stream di input associato ad un file
	// tramite la classe sorgente.
	
	DataInputStream is = new DataInputStream(f);

	// incapsuliamo l'oggetto della classe sorgente
	// in una classe filtro che da le funzionalità
	// necessarie per leggere i tipi primitivi.
	...
}
```

**METODI DI INPUTSTREAM**
- read() - Legge uno o più byte.
- available() - Riporta quanti byte sono già disponibili in input.
- skip() - Salta N byte in input.
- mark() - Ricava la posizione corrente sullo stream.
- reset() - Torna alla posizione marcata.

**METODI DI OUTPUTSTREAM**
- write() - Scrive uno o più byte.
- flush() - Svuota il buffer di scrittura.
- close() - Chiude lo stream.

**LETTURA DI UNO STREAM**
- **APERTURA**: Lo stream viene aperto una volta che l'oggetto di tipo stream è stato istanziato.
- **LETTURA**: read() restituisce un intero che vale tra 0 e 255 se la lettura è andata a buon fine e -1 se lo stream è finito.
- **FINE**: Controlliamo il valore che restituisce read(), se è -1 allora non ci sono più byte da leggere.

``` Java
// Usiamo un intero per controllare e un byte per leggere.

int i;
byte b;

i = in.read();
if (i != -1)
	b = (byte) i;
```

**CLASSI DI INPUT NOTEVOLI**
- **ByteArrayInputStream**: Classe che deriva da InputStream, implementa i suoi metodi nel caso dove l'input è un buffer, quindi un array di byte.
- **FileInputStream**: Classe che deriva da InputStream, implementa i suoi metodi nel caso in cui l'input è un file.


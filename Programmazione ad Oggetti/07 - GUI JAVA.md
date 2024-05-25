**JAVA SWING**
Sono librerie evolute da AWT che ci permettono di creare interfacce grafiche.
Esse seguono la filosofia Object-Oriented; ogni componente è implementato tramite una classe. Da questa classe puoi creare oggetti e specializzarle. I package da inserire sono:
- java.awt
- javax.swing

**CLASSI SWING**
Tutti i componenti grafici sono sottoclassi di Component. Le classi Component sono AWT, per quello si dice che le classi di Swing derivano da AWT. Anche i Container sono sottoclassi di Component.

**JFRAME**
La classe JFrame è quella che implementa la finestra della nostra applicazione. Ha un bordo ed una barra in alto con pulsanti per le azioni sulla finestra. Lo stile dipende dal Window Manager del sistema, anche se è possibile cambiarlo.

**POSIZIONE E DIMENSIONI DEL FRAME**
Se creiamo un oggetto JFrame senza specificare nulla creiamo un frame piccolissimo. Possiamo quindi impostare la posizione e la dimensione iniziale del frame con dei metodi.

``` Java
public void setBounds(int x, int y, int width, int length)

// Possiamo settare entrambe le cose separatamente
public void setLocation(int x, int y) // Posizione
public void setSize(int width, int length) // Dimensione
```

``` Java
import java.awt.*;
import javax.swing.*;

public class EsSwing1
{
	public static void main(String args[])
	{
		JFrame f = new JFrame("Esempio 1")
		// Creo un JFrame con titolo "Esempio 1"

		f.setBounds(200, 100, 300, 150);
		// Setto la posizione e le dimensioni

		f.setVisible(true);
		// Il frame ora è visibile (di default è nascosto)
	}
}
```

**CHIUSURA DELL'APPLICAZIONE**
È possibile specificare cosa deve fare il frame quando si preme il pulsante di chisura della finestra con il metodo elencato sotto. Il parametro operation può assumere i seguenti valori:
- **DO_NOTHING_ON_CLOSE**: Non fa niente.
- **HIDE_ON_CLOSE**: Nasconde il frame.
- **DISPOSE_ON_CLOSE**: Nasconde e distrugge il frame.
- **EXIT_ON_CLOSE**: Termina l'applicazione.

``` Java
public void setDefaultCloseOperation(int operation)
```

**ESTENSIONE JFRAME**
Possiamo estendere la classe JFrame e personalizzarla.

``` Java
import java.awt.*;
import javax.swing.*;

public class MyFrame extends JFrame
{
	public MyFrame() {this("")}
	// Costruttore senza parametri, il MyFrame sarà inizializzato
	// senza nome.
	
	public MyFrame(String titolo)
	{
		super(titolo);
		setBounds(200, 100, 300, 150);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
	}
	// Costruttore con un parametro titolo, il MyFrame sarà inizializzato
	// con il nome che inseriamo.
}

public class EsSwing2
{
	public static void main(String[] v)
	{
		MyFrame f = new MyFrame("Esempio 2");
		f.setVisible(true);
	}
}
```

**JPANEL**
La classe JPanel implementa un pannello da inserire dentro un frame. Sul pannello puoi:
- Inserire componenti grafici come JLabel, JButtons, immagini (oggetti). Per aggiungere i componenti devo sfruttare il costruttore del pannello.
- Disegnare.

**INSERIRE COMPONENTI NEL JFRAME**
In Swing aggiungiamo direttamente al nostro JFrame i componenti. In questo esempio aggiungiamo un JPanel attraverso il metodo add().

``` Java
import java.awt.*;
import javax.swing.*;

public class EsSwing3
{
	public static void main(String[] v)
	{
		MyFrame f = new MyFrame("Esempio 3");
		JPanel panel = new JPanel();
		f.add(panel);
		f.setVisible(true);
	}
}
```

**JLABEL**
La classe JLabel rappresenta un etichetta, quindi una stringa.
- Posso cambiare la scritta della stringa.
- Posso cambiare la posizione della stringa.
- Posso ricavare il contenuto della label.

``` Java
import java.awt.*;
import javax.swing.*;

public class Es7Panel extends JPanel
{
	public Es7Panel()
	{
		super(); // richiamo il costruttore della superclasse
		JLabel l = new JLabel("Etichetta");
		add(l); // aggiungo una label al frame
	}
}

public class EsSwing7
{
	public static void main(String args[]);
	{
		JFrame f = new JFrame("Esempio 7");
		Es7Panel p = new Es7Panel();
		f.add(p);
		f.pack(); // dimensiona il frame in modo da contenere il pannello
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		f.setVisible(true);
	}
}
```

**PROGRAMMAZIONE AD EVENTI**
Negli esempi visti fino ad ora l'utente poteva soltanto guardare e non interagire con la GUI. Java mette a disposizione la programmazione ad eventi per poter gestire l'interazione tra utente:
- Il componente viene associato ad un ascoltatore.
- Quando si verifica un evento, l'ascoltatore viene notificato.
- L'ascoltatore esegue il codice corrispondente.

**ASCOLTATORE**
Un ascoltatore è un oggetto che implementa un interfaccia di tipo Listener.

**JBUTTON**
La classe JButton implementa un bottone che può essere premuto dall'utente.
- Quando viene premuto genera un evento di classe ActionEvent.
- L'evento viene quindi mandato all'ascoltatore associato all'evento.
- L'ascoltatore dell'evento si occupa di gestirlo eseguendo codice. Deve implementare l'interfaccia ActionListener e il metodo actionPerformed.

``` Java
void actionPerformed(ActionEvent e)
// Gestisce l'evento
```

**JBUTTON ES I**
Il codice crea un applicazione con un etichetta ed un pulsante. Ogni volta che l'utente preme il pulsante l'etichetta passa da Tizio a Caio e viceversa. L'ascoltatore del bottone in questo caso è il pannello stesso.

``` Java
import java.awt.event.*;
import javax.swing;

public class Es8Panel implements ActionListener extends JPanel
{
	private JLabel l; // deve essere visibile a tutti i metodi
	
	public Es8Panel()
	{
		super();
		l = new JLabel("Tizio");
		add(l);
		JButton b = new JButton("Tizio/Caio");
		b.addActionListener(this);
		// Registra l'oggetto panel come ascoltatore degli eventi
		this.add(b); // Aggiunge il bottone al pannello
	}

	public void actionPerformed(ActionEvent e)
	{
		if (l.getText().equals("Tizio"))
			l.setText("Caio");
		else
			l.setText("Tizio");
	}
}

public class EsSwing8
{
	public static void main(String args[])
	{
		JFrame f = new JFrame("Esempio 8");
		Es8Panel p = new Es8Panel();
		f.add(p);
		f.pack();
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		f.setVisible(true);
	}
}

```

**JBUTTON ES II**
Il codice crea un applicazione con due bottoni che permettono di scegliere il colore dello sfondo tra rosso ed azzurro.

``` Java
public class Es9Panel implements ActionListener extends JPanel
{
	private JButton b1, b2;

	public Es9Panel()
	{
		super();
		b1 = new JButton("Rosso");
		b2 = new JButton("Azzurro");
		b1.addActionListener(this);
		b2.addActionListener(this);
		// Il pannello fa da ascoltatore per entrambi i pulsanti
		add(b1);
		add(b2);
	}

	public void actionPerformed(ActionEvent e)
	{
		String nome = e.getActionCommand();
		// Restituisce la stringa associata all'evento, quindi
		// la stringa del bottone

		if (nome.equals("Rosso"))
			setBackground(Color.red);
		if (nome.equals("Azzurro"))
			setBackground(Color.cyan);
	}
}

// In questo caso usiamo un listener per entrambi i bottoni, è meglio fare
// un listener per bottone.

// getSource() restituisce il riferimento all'oggetto che ha generato
// l'evento.
```

**EVENTI DI FINESTRA**
Le operazioni sulle finestre generano un WindowEvent. Gli eventi di finestra sono gestiti dai metodi dichiarati dall'interfaccia WindowListener.

**JTEXTFIELD**
La classe JTextField offre un campo di testo, usabile per scrivere e visualizzare una riga di testo.
- Il campo di testo può essere editabile o no.
- Il testo è accessibile con getText() / setText().

**EVENTI JTEXTFIELD**
JTextField è parte di un oggetto Document.
- Ogni volta che il testo cambia si genera un DocumentEvent.
- Se è sufficiente registrare i cambiamenti avvenuti col tasto INVIO basta gestire l'ActionEvent.

**JTEXTFIELD ES I**
Un applicazione che comprende un pulsante e due campi di testo. Quando si preme il pulsante il testo del secondo campo viene cambiato e reso uguale a quello del primo.
Non usiamo DocumentEvent, l'unico evento è il pulsante premuto.

``` Java
import java.awt.event.*;
import javax.swing.*;

public class Es10Panel implements ActionListener extends JPanel
{
	private JTextField txt1, txt2;
	private JButton b;

	public Es10Panel()
	{
		super();
		b = new JButton("Aggiorna");
		txt1 = new JTextField("Scrivere qui il testo", 25);
		txt2 = new JTextField(25);
		txt2.setEditable(false);
		b.addActionListener(this);
		add(txt1);
		add(txt2);
		add(b);
	}

	public void actionPerformed(ActionEvent e)
	{
		String s = txt1.getText();
		txt2.setText(s);
	}
}
```

**JCHECKBOX**
La classe JCheckBox permette di creare appunto una checkbox, quindi una casella di opzione che può essere selezionata o deselezionata.
- Lo stato è verificabile con isSelected() e modificabile con setSelected().

**JCHECKBOX EVENTI**
Ogni volta che lo stato della casella cambia viene si generano:
- **ACTIONEVENT**: Come per ogni pulsante.
- **ITEMEVENT**: Gestito da ItemListener. Conviene gestire questo perchè più specifico.

L'ItemListener dichiara il metodo public void itemStateChanged(ItemEvent e) che deve essere implementato dalla classe che fa da ascoltatore.

**JRADIOBUTTON**
La classe JRadioButton permette di creare una checkbox dove può essere attiva solo una spunta per volta.

**SWING**
Swing è una libreria che deriva da AWT. Ci permettono di creare GUI. La programmazione delle GUI segue la filosofia ad oggetti, quindi ogni componente di Swing è una classe da cui puoi creare oggetti e specializzarli. I package da implementare sono:
- java.awt
- javax.swing

**GERARCHIA SWING**
I componenti di Swing sono sottoclassi di Component (AWT). Anche i Container sono sottoclassi di Component.

**JFRAME**
La classe JFrame implementa la finestra generale dell'applicazione.
- Contiene i bordi, una barra con i pulsanti di interazione con la finestra.
- Lo stile dipende dal Window Manager dell'SO, anche se si può cambiare.

**DIRETTIVE PER CREARE UN JFRAME**
Creare un oggetto JFrame senza specificare nulla non porta ad un buon risultato. Dobbiamo specificare posizione e dimensione attraverso i seguenti metodi:

``` Java
public void setBounds(int x, int y, int width, int length) // Tutto
public void setLocation(int x, int y) // Solo posizione
public void setSize(int width, int length) // Solo dimensione
```

**ESEMPIO JFRAME**

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

**CHIUSURA DEL JFRAME**
Specifichiamo il comportamento del frame quando premiamo il pulsante di chiusura attraverso il metodo setDefaultCloseOperation(int operation). Operation può avere i seguenti valori:
- **DO_NOTHING_ON_CLOSE**: Non fa niente.
- **HIDE_ON_CLOSE**: Nasconde il frame.
- **DISPOSE_ON_CLOSE**: Nasconde e distrugge il frame.
- **EXIT_ON_CLOSE**: Termina l'applicazione.

**PERSONALIZZAZIONE DELLA CLASSE JFRAME**

``` Java
import java.awt.*;
import javax.swing.*;

public class MyFrame extends JFrame
{
	public MyFrame() {this("")}
	// Costruttore senza parametri, il MyFrame sarà inizializzato
	// senza nome se non si specificano parametri.
	
	public MyFrame(String titolo)
	{
		super(titolo);
		setBounds(200, 100, 300, 150);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
	}
	// Costruttore con un parametro, il MyFrame sarà inizializzato
	// con il nome che inseriamo nel parametro. 
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
- Inserire componenti grafici attraverso il metodo add()
- Disegnare.

**JLABEL**
La classe JLabel implementa un etichetta. A differenza di una stringa disegnata:
- Si può cambiare la scritta.
- Si può cambiare la posizione.
- Può dirmi che scritta contiene.

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
Java mette a disposizione la programmazione ad eventi per poter far interagire l'utente con la GUI:
- Il componente viene associato ad un ascoltatore.
- Quando si verifica un evento, l'ascoltatore viene notificato.
- L'ascoltatore esegue il codice corrispondente.

**ASCOLTATORE**
Un oggetto diventa **ASCOLTATORE** quando implementa un interfaccia di tipo **LISTENER**.

**JBUTTON**
La classe JButton implementa un classico bottone, premibile dall'utente.
- L'evento generato dal JButton è di tipo ActionEvent, viene quindi inviato all'ascoltatore.
- L'ascoltatore deve implementare l'interfaccia ActionListener ed implementare il metodo sotto.
- L'ascoltatore può essere il pannello stesso come può essere un oggetto non inerente alla GUI.
- Possiamo usare lo stesso ascoltatore per tutti gli oggetti JButton oppure ascoltatori diversi per pulsanti diversi.

``` Java
void actionPerformed(ActionEvent e)
```

**JBUTTON ES I**
Il codice crea un applicazione con un etichetta ed un pulsante. Ogni volta che il pulsante viene premuto l'etichetta passa da Tizio a Caio e viceversa.

``` Java
import java.awt.event.*;
import javax.swing.*;

public class Es8Panel implements ActionListener extends JPanel
{
	private JLabel l; // visibilità a tutti i metodi
	
	public Es8Panel()
	{
		super();
		l = new JLabel("Tizio");
		add(l);
		JButton b = new JButton("Tizio/Caio");
		b.addActionListener(this); // il panel diventa ascoltatore
		this.add(b); // aggiunge il bottone al panel
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
Il codice implementa un applicazione con due bottoni, che ci permettono di scegliere il colore dello sfondo. Possiamo anche comparare i riferimenti del bottone premuto ai vari bottoni usando il metodo getSource().

``` Java
public class Es9Panel implements ActionListener extends JPanel
{
	private JButton b1, b2;

	public Es9Panel()
	{
		super();
		b1 = new JButton("Rosso");
		b2 = new JButton("Azzurro");
		b1.addActionListener(this); // panel fa da ascoltatore per b1
		b2.addActionListener(this); // panel fa da ascoltatore per b2
		add(b1);
		add(b2);
	}

	public void actionPerformed(ActionEvent e)
	{
		String nome = e.getActionCommand();
		// recupera il nome del bottone che ha generato l'evento

		if (nome.equals("Rosso"))
			setBackground(Color.red);
		if (nome.equals("Azzurro"))
			setBackground(Color.cyan);
	}
}
```

**JTEXTFIELD**
La classe JTextField implementa un campo di testo in cui puoi scrivere.
- Il campo di testo può essere editabile.
- getText()/setText() servono per accedere al testo.
- Genera un DocumentEvent ed un ActionEvent. Se è sufficiente registrare i cambiamenti solo quando si preme ENTER conviene gestire l'ActionEvent.

**JTEXTFIELD ES**
Questo codice implementa un applicazione che comprende un pulsante e due campi di testo (uno per scrivere, uno per leggere). Quando si preme il pulsante il testo del secondo campo viene cambiato e reso uguale al primo.
- L'unico evento è il pulsante premuto, non si usa DocumentEvent.

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
La classe JCheckBox implementa una casella di opzione.
- La casella può essere selezionata o deselezionata.
- Lo stato è verificabile/modificabile con isSelected()/setSelected().

**JCHECKBOX EVENTI**
- Quando lo stato della casella cambia vengono generati un ActionEvent ed un ItemEvent, solitamente conviene gestire l'ItemEvent.
- L'ItemListener dichiara Il metodo public void itemStateChanged(ItemEvent e).
- e.getItemSelectable() restituisce un riferimento all'oggetto sorgente dell'evento.

**JRADIOBUTTON**
La classe JRadioButton implementa una casella di opzione.
- Le caselle di opzioni fanno parte di un singolo gruppo.
- Può essere attiva solo una casella di opzione.
- Si creano due ItemEvent ed un ActionEvent. Conviene gestire l'ultimo.

**RAGGRUPPARE JRADIOBUTTONS**
Per includere tutte le caselle di opzione in un gruppo serve:
- Creare le caselle di opzioni necessarie.
- Creare un oggetto di tipo ButtonGroup.
- Inserire le caselle di opzioni al gruppo.

**JLIST**
La classe JList implementa una lista di valori fra cui si può sceglierne uno o più.

**JLIST EVENTI**
- Quando si sceglie una voce si genera un evento di tipo ListSelectionEvent, gestito da un ListSelectionListener.
- Il listener implementa il metodo void valueChanged(ListSelectionEvent e).
- Per recuperare una voce si usa getSelectedValue(), per recuperare l'oggetto che contiene tutte le voci della lista usi getSelectedValueList().

**JSCROLLPANE**
La classe JScrollPane implementa una barra di scorrimento.
- Bisogna inserire la lista all'interno dello scroll pane.
- Bisogna fissare un numero massimo di elementi visualizzabili per la lista, tramite il metodo setVisibleRowCount(int n).

**JCOMBOBOX**
La classe JComboBox implementa una lista di valori a discesa.
- Si può scegliere un valore oppure scrivere un valore diverso.
- Per configurare l'elenco delle voci proposte si usa il metodo addItem(), mentre per recuperare la voce scritta/scelta si usa il metodo getSelectedItem().
- L'evento migliore da gestire è l'ActionEvent.

**JTABLE**
La classe JTable implementa una tabella. 
Ogni JTable recupera i dati da rappresentare tramite un modello, istanza di una classe che implementa l'interfaccia TableModel.

**TABLEMODEL**
L'interfaccia mette a disposizione metodi per trovare il numero di righe/colonne, il valore di ogni singola cella o se sono editabili etc...
- Per modificare i valori del modello implementiamo setValueAt().
- Dopo aver modificato informiamo la tabella delle modifiche tramite il metodo fireTableDataChanged().

**ABSTRACTTABLEMODEL**
La classe astratta AbstractTableModel implementa la maggior parte dei metodi del TableModel, lascia al programmatore da implementare questi tre metodi:
- public int getRowCount();
- public int getColumnCount();
- public Object getValueAt(int row, int column);

**MENU IN SWING**
Swing mette a disposizione alcune classi per creare menu in Java.
- **JMENUITEM**: Rappresenta la voce del menu.
- **JMENU**: Rappresenta il menu.
- **JMENUBAR**: Rappresenta la barra dei menu.
- L'evento generato dal menu è di tipo ActionEvent.


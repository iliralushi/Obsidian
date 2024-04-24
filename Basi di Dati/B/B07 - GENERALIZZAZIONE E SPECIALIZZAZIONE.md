**GERARCHIE SOMMARIO**
Più entità possono risultare simili o casi particolari di altre entità. La gerarchia di **specializzazione** è il legame logico che esiste tra classi e sottoclassi. 
- Gerarchia: La gerarchia concettuale è il legame logico tra un entità padre e una o più entità figlio. L'entità a cui puntano le freccie viene detta generalizzazione (entità padre). l'entità che puntano le freccie vengono dette specliazziazioni (entità figlio).
- Un istanza dell'entità figlio è istanza dell'entità padre, un istanza dell'entità padre può essere un istanza dell'entità figlio.
- I figli ereditano tutti gli attributi del padre, non è vero il viceversa.

![[Esempio Gerarchia 1.png]]
![[Esempio Gerarchia 2.png]]

**TIPO DI GERARCHIA**
- T - TOTALE: Ogni istanza dell'entità padre deve far parte di un entità figlia.                             **ES.1:** La gerarchia è totale perchè il personale è diviso in dipendente o esterno.
- NT - NON TOTALE: Un istanza dell'entità padre **può** far parte delle entità figlie.                        **ES.2**: i cittadini sicuramente non sono solo pescatori.
- E - ESCLUSIVA: Ogni istanza dell'entità padre deve far parte di una sola entità figlia.               **ES.1**: la gerarchia è esclusiva perchè un personale o è dipendente o è esterno.
- NE - NON ESCLUSIVA: Ogni istanza dell'entità padre può fare parte di più di un'entità figlia.      **ES**: un ingegnere può essere meccanico e anche elettronico.

**GERARCHIE ISA**
Esse sono un sinonimo della gerarchia concettuale.
- ES: Dipendente è un (is a) personale, esterno è un (is a) personale.

**SOTTOCLASSE INTERSEZIONE**
Può essere creata una sottoclasse intersezione perchè essa beneficia di certi aspetti. In questo caso viene creata la specializzazione studente-lavoratore.

![[Sottoclasse intersezione.png]]

**GERARCHIE ISA E AUTOASSOCIAZIONI**
Sono diverse tra di loro, le gerarchie ISA modellano a livello di schema varie entità che hanno attributi in comune tra di loro. Ci si ferma ad un certo livello di gerarchia, gli impiegati son diretti da un dirigente. Con le auto-associazioni possiamo creare un qualsiasi livello di gerarchia siccome agiamo su istanze e viene modellata a livello di tuple.

![[ISA vs Autoassociazioni.png]]
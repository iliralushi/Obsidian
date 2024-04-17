**GERARCHIA DI SPECIALIZZAZIONE**
Si definisce gerarchia di specializzazione il legame tra classi e sottoclassi. Viene usata quando esistono casi particolari di una determinata entità.
- Clienti -> Clienti tesserati
- Articolo -> Articolo in serie

**GERARCHIA**
La gerarchia concettuale è il legame logico tra un entità padre E ed alcune entità figlie tipo E1, E2, E3... En. Un istanza di En è anche un istanza di E, un istanza di E **può** essere istanza di una specializzazione. Essendo una gerarchia può crearsi una gerarchia che parte da una specializzazione.
- E è la **generalizzazione** di E1, E2, EN.
- E1, E2, EN sono **specializzazioni** di E.

**ESEMPIO GERARCHIA**

![[Esempio Personale.png]]

![[Esempio Pescatore.png]]

**DEFINIZIONI DI GERARCHIA**
- T: **Totale** - Ogni istanza dell'entità padre deve far parte di una delle entità figlie. 
  Nel primo esempio il personale si divide completamente in dipendenti o esterni.
- NT: **Non totale** - Le istanze dell'entità padre possono far parte di una delle entità figlie. 
  Nel secondo esempio non tutti i cittadini sono pescatori.
- E: **Esclusiva** - Ogni istanza dell'entità padre deve far parte di UNA SOLA delle entità figlie.
  Nel primo esempio il personale o è dipendente o è esterno, non entrambi.
- NE: **Non esclusiva** - Ogni istanza dell'entità padre può far parte di una o più entità figlie.
  
**EREDITARIETA DELLE PROPRIETA**
Le proprietà dell'entità padre non devono essere replicate nelle entità figlie perchè esse ereditano tutti gli attributi dell'entità padre MA non è vero il viceversa.

**SINONIMO DI GERARCHIA CONCETTUALE**
Gerarchia ISA:
- Dipendente è un (is a) personale
- Esterno è un (is a) personale

**SOTTOCLASSE INTERSEZIONE**

![[Sottoclasse Intersezione.png]]

In alcuni casi se viene specificato si possono modellare entità intersezione, come in questo caso.
Per lo schema in questione si sono unite due entità per creare una sottoentità intersezione, studente-lavoratore.

**CONFRONTO TRA GERARCHIE ISA E AUTO-ASSOCIAZIONI**

![[Confronto tra ISA e Auto-Associazioni.png]]

Sono diversi e non ce n'è uno migliore dell'altro:
- Con le gerarchie ISA si va a modellare a livello di schema varie entità che hanno attributi non in comune tra di loro, cosa che non succede con l'auto-associazione. Ci si ferma ad un certo livello, qui abbiamo che i dirigenti dirigono gli impiegati e fine.
- Con l'auto-associazione possiamo creare un qualsiasi livello di gerarchia perchè viene modellata a livello di tuple.
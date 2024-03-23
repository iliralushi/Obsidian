# **PARTE 1**

Un falegname costruisce sedie e tavoli.
- Abbiamo 15 unità di legno e ore disponibili.
- Il costo di un tavolo è di 3 unità, il tempo impiegato è di 2 ore e ci frutta 80€.
- Il costo di una sedia è di 2 unità, il tempo impiegato è di 3 ore e ci frutta 70€.
**Quanti tavoli e sedie deve produrre il falegname per massimizzare i guadagni?**

Iniziamo costruendo la nostra soluzione seguendo 3 step:
- Step 1) Identificare le variabili decisionali del nostro problema.
- Step 2) Dare dei limiti al nostro problema usando equazioni o disequazioni.
- Step 3) Definire il nostro obiettivo matematicamente.

Step 1:
- In questo problema abbiamo due variabili decisionali. 
  Usiamo x per i tavoli e y per le sedie.

Step 2:
- Abbiamo tre limiti da rispettare; le unità di legno, il tempo, il vincolo di non negatività (non possiamo usare risorse negative, fornirebbe una soluzione irrealistica).
  - Per le unità di legno abbiamo 3x + 2y ≤ 15.
  - Per il tempo disponibile abbiamo 3y + 2x ≤ 15.
  - Per il vincolo di non negatività abbiamo x, y ≥ 0.

Step 3:
- In questo caso definire il nostro obiettivo è semplice. Dobbiamo produrre il massimo guadagno possibile.
  - z = 80x + 70y.

Una volta risolti gli step si può procedere alla prossima parte, la creazione del grafico.
Dalle equazioni che abbiamo ricavato possiamo trovare le coordinate delle rette. Queste rette ci servono per trovare i punti dove NON sarà possibile la nostra soluzione. Tracciando le rette del tempo e delle unità avremo che il semipiano superiore alle nostre due rette saranno punti da escludere. Inoltre per il vincolo di non negatività abbiamo che tutti i punti negativi sono esclusi.

A questo punto prendiamo la funzione obiettivo, ovvero la funzione che ci darà il nostro guadagno massimo. La retta avrà pendenza negativa e sarà come nel grafico con x, y = (0,0).

> **ATTENZIONE!** 
> Il semipiano da scegliere non dipende dal segno della disequazione. Per capire quale prendere possiamo sostituire le coordinate al punto di origine (0,0). Se la disequazione è valida allora il semipiano sarà quello superiore, altrimenti sarà quello inferiore.

# **PARTE 2**

Per trovare la soluzione ottima dobbiamo prendere il punto che ci offre il valore massimo possibile.
Se le nostre coordinate saranno (0,0) allora la soluzione sarà la nostra origine, zero.

Traslando la retta iniziale verso l'alto i valori della nostra funzione obiettivo crescono. 
- Per esempio, sostituendo il valore di MAX con un valore casuale (200) abbiamo che c'è ancora un intersezione tra la retta e la regione ammissibile. 200 è una soluzione valida. 

La soluzione ideale si trova visivamente. Possiamo spostare la nostra retta fino ad arrivare al punto più lontano possibile, l'intersezione tra le rette. Notiamo che x, y = (3,3).

> **ATTENZIONE!**
> In un problema di massimo la nostra soluzione non sarà mai all'interno della soluzione ammissibile, ma saranno sempre lungo alla frontiera.

Soluzione grafica dell'esercizio del falegname:

![[Obsidian/OLI/PNG/1 - FALEGNAME.png]]

---

Una funzione lineare obiettivo è una funzione del tipo z = 80x + 70y.
Genericamente si può esprimere come f(x1, x2, xn).

Il gradiente di f si indica come ∇f ed è la somma delle derivate parziali delle coordinate moltiplicato a ciascun versore. Esso indica, in un punto a caso della nostra funzione, la direzione di massima crescita della funzione in quel punto. Il nostro vettore obiettivo quindi sarà perpendicolare al vettore gradiente.

**In una funzione lineare il gradiente è dato dai coefficenti della nostra funzione.**
- Nella funzione di prima per esempio, il gradiente è dato da (80,70).

Soluzione grafica dell'esercizio di minimo con soluzione il punto (2,2):

![[2 - PROBLEMA DI MINIMO.png]]

---

# **PARTE 3**

La forma standard di un problema comprende solo **equazioni** ed esse contengono variabili esclusivamente non-negative.

Le variabili **slack** sono variabili che fanno da riempitivo rispetto al valore che si ottiene con x, y. Esse saranno uguali al valore che manca per soddisfare l'uguaglianza.

Una soluzione ammissibile immediata è quella di porre x ed y = 0.
- z = 80x + 70y 
- s1 = - 3x - 2y + 15
- s2 = - 3y - 2x + 15
- La soluzione è z = 0, abbiamo (0, 0, 15, 15) con (x, y, s1, s2).

Questa, ovviamente, non è la soluzione ottima. Possiamo risolvere il sistema per altre variabili. Prendiamo x perchè nella funzione obiettivo ha il valore più alto. Questa dovrà sostituire una delle due variabili con cui è stato impostato il sistema per ora, ovvero s1 ed s2.

##### **RISOLUZIONE PER X:**
Poniamo y = 0.
Per i vincoli di non negatività poniamo tutta l'espressione maggiore-uguale di zero.
- s1 = - 3x + 15 ≥ 0                              x ≤ 5
- s2 = - 2x + 15 ≥ 0                              x ≤ 7.5

La variabile quindi che esce dalla soluzione sarà s1 siccome il valore massimo che la x può assumere è 5 prima che s1 diventi negativa. Abbiamo quindi che x = 5, y = 0, s1 = 0, s2 = 5 (s2 si può trovare risolvendo la seconda equazione). Ottieniamo la soluzione dal sistema iniziale.
- z = + 50/3y - 80/3s1 + 400
- x = - 2/3y - 1/3s1 + 5
- s2 = - 5/3y + 2/3s1 + 5
- La soluzione è z = 400, abbiamo (5, 0, 0, 5) per (x, y, s1, s2)

Possiamo provare un altra soluzione, andiamo avanti fino a quando entrambe le variabili nella funzione obiettivo sono negative. Scelgo y come prossimo test.

##### **RISOLUZIONE PER Y:**
Poniamo s1 = 0.
Per i vincoli di non negatività poniamo tutta l'espressione maggiore-uguale di zero.
- x = - 2/3y + 5 ≥ 0                              y ≤ 7.5
- s2 = - 5/3y + 5 ≥ 0                            y ≤ 3

La variabile quindi che esce dalla soluzione sarà s2 siccome il valore massimo che la y può assumere è 3 prima che s2 diventi negativa. Abbiamo quindi che x = 3, y = 3, s1 = 0, s2 = 0 (x si può trovare risolvendo la seconda equazione). Ottieniamo la soluzione dal sistema iniziale.
- z = - 20s1 - 10s2 + 450
- x = - 3/5s1 + 2/5s2 + 3
- y = + 2/5s1 - 3/5s2 + 3
- La soluzione è z = 450, abbiamo (3, 3, 0, 0) per (x, y, s1, s2), soluzione ottima.

# **PARTE 4**
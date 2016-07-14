### 1.6.4 Polygonnetzoperationen

#####Im letzten Abschnitt haben wir die grundlegende Struktur von Polygonnetzen angeschaut. In diesem Abschnitt werden wir Wege ansehen, wie man Polygonnetzgeometrien manipulieren kann.

####1.6.4.1 Gl�ttung

![IMAGE](images/1-6-4/smooth.png)

Glattere Polygonnetze k�nnen erreicht werden, indem die Anzahl der Netzfl�chen erh�ht wird. Dieser Prozess wird *Unterteilung* genannt. Dies kann oft zu sehr gro�en Datens�tzen f�hren, welche viel Rechenzeit und zus�tzliche Erweiterungen f�r Grasshopper ben�tigen. In dieser Situation kann die **Smooth** Komponente als Alternative genutzt werden, um weniger facettierte Polygonnetze zu erzeugen ohne die Anzahl der Eckpunkte und Netzfl�chen zu erh�hen oder die Topologie zu ver�ndern. Die *St�rke*, *Anzahl der Iterationen* und *Versatzbegrenzung* k�nnen genutzt werden, um die Art zu beeinflussen, in der die Gl�ttung passiert.

Verbindung eines boolschen Wertes mit einem Eingabeparameter N gibt uns die Option freie Eckpunkte zu �berspringen. Eckpunkte sind frei, wenn sie mit einer offenen Kante verbunden sind, mit der Bedeutung, dass sie sich in der �u�eren Begrenzung des Polygonnetzes befindet. Indem Du diese Option einschaltest, kannst Du die �u�eren Begrenzungen eines Polygonnetzes erhalten, w�hrend Du die inneren Kanten des Polygonnetzes gl�ttest.

![IMAGE](images/1-6-4/03_smooth.png)
>1. Urspr�ngliches Polygonnetz einer Kiste mit drei Netzfl�chen entfernt
2. Gl�ttung nach 2 Iterationen
3. 6 Iterationen
4. 25 Iterationen
5. 50 Iterationen

####1.6.4.2 Unsch�rfe

![IMAGE](images/1-6-4/blur.png)

Die **Blur** Komponente verh�lt sich �hnlich wie die "Smooth" Komponente, abgesehen von den Eckpunktfarben. Es kann auch benutzt werden, um die gezackte Erscheinung von Farbpolygonnetzen weichzuzeichnen, auch wenn der Effekt geringer ist, da die Geometrie nicht ver�ndert wird.

![IMAGE](images/1-6-4/04_blur.png)
>1. Urspr�ngliches Polygonnetz
2. Weichzeichnen nach 1 Iteration
3. 6 Iterationen
4. 12 Iterationen
5. 20 Iterationen

####1.6.4.3 Triangulierung

![IMAGE](images/1-6-4/triangulate.png)

Um die Planarit�t einer jeden Netzfl�che zu sichern oder um das Polygonnetz zu anderen Programmen zu exportieren, die keine viereckigen Netzfl�chen erlauben, ist es manchmal n�tig ein Polygonnetz zu triangulieren. Mit der Nutzung der **Triangulate** Komponente, wird jede viereckige Netzfl�che durch zwei dreieckige ersetzt. Grasshopper nimmt immer die k�rzeste Diagonale der Netzfl�che, um eine Netzfl�che mit einer neuen Kante zu unterteilen.

![IMAGE](images/1-6-4/05_triangulate.png)
>1. Urspr�ngliches Polygonnetz mit viereckigen Netzfl�chen
2. Hinzugef�gte Kanten in �bereinstimmung mit der k�rzesten Distanz zwischen viereckigen Netzfl�chen
3. Trianguliertes Polygonnetz als Ergebnis

####1.6.4.4 Schwei�en

![IMAGE](images/1-6-4/weld.png)

Im letzten Abschnitt haben wir festgestellt, dass ein einzelner Eckpunkt von benachbarten Netzfl�chen geteilt werden kann und dass die Normale f�r diesen Eckpunkt aus dem Durchschnitt der Normalen der angrenzenden Netzfl�chen berechnet wird, was eine glattere Darstellung ergibt. Manchmal ist es jedoch gew�nscht, dass eine scharfe Kante oder ein Saum erzeugt werden, an welchen ein glatter �bergang zwischen einer Netzfl�che und der benachbarten nicht stattfinden soll. In dieser Situation ist es notwendig f�r jede Netzfl�che an einem Schnittpunkt eine eigene Exkpunktnormale zu definieren. Die Liste von Eckpunkten w�rde mindestens zwei Punkte enthalten, die eine Koordinate teilen aber verschiedene Indizes besitzen.

![IMAGE](images/1-6-4/06_simple-weld.png)
>1. Verschwei�te Netzfl�che - Beide Netzfl�chen teilen die Eckpunke 1 und 2. Die Eckpunktnormalen an diesen Eckpunkten entsprechen dem Durchschnitt der Netzfl�chennormalen der angrenzenden Netzfl�chen.
2. Unverschwei�te Netzfl�che - Duplizierte Eckpunkte wurden der Liste hinzugef�gt. Eckpunkte 1 und 6 und Eckpunkte 2 und 5 haben identische Koordinaten, aber unterschiedliche Eckpunkte. Sie haben jeweils ihre eigenen Eckpunktnormalen. Der Prozess zwei Eckpunkte in derselben Position zu nehmen und sie zu einem gemeinsamen Eckpunkt zusammenzuf�hren nennen wir *schwei�en*, wobei *entschwei�en* bedeutet einen einzelnen Eckpunkt in mehrere Eckpunkte zu teilen.

Die **Weld** Komponente nutzt einen Grenzwinkel als Eingabeparameter. Alle benachbarten Netzfl�chen mit einem eingeschlossenen Winkel kleiner dem Grenzwinkel werden miteinander verschwei�t, wodurch gemeinsame Eckpunkte mit geteilten Eckpunktnormalen entstehen, die die Werte der angrenzenden Fl�chennormalen mitteln. **Unweld** funktioniert auf die entgegengesetzte Art und Weise, in der angrenzende Netzfl�chen mit einem Winkel gr��er dem Grenzwinkel entschwei�t werden und die bisher geteilten Eckpunkte dupliziert werden.

![IMAGE](images/1-6-4/07_box-weld.png)
>1. Die Standardpolygonnetzkiste hat 726 Eckpunkte. Das Polygonnetz ist an den Ecken der Kiste gekantet und die Eckpunkte an den angrenzenden Eckpunkten sind dupliziert.
2. Wenn das Polygonnetz mit einem Winkel gr��er als 90 Grad verschwei�t wird, werden die Netzfl�chen alle verschwei�t und die Anzahl der Endpunkte wurde auf 602 reduziert, w�hrend die Anzahl der Netzfl�chen dieselbe bleibt.
3. Wenn wir uns die Vorschaugeometrie ansehen, k�nnen wir auch feststellen, dass das gerenderte verschwei�te Polygonnetz gegl�ttete Ecken hat.
4. Entgegen der "Smooth" Komponente, welche die Polygonnetzgeometrie ver�ndert, wirkt dieses Polygonnetz nur gegl�ttet, weil die Eckpunktnormalen eine Rolle in Rendering und Schattierung spielen. Die eigentliche Position der Eckpunkte bleibt unver�ndert.

Im oben gezeigten Bild haben wir einen Winkel von 91 Grad angenommen, weil wir wissen, dass die Seiten eines Quadrats 90 Grad Winkel enthalten. Um ein Polygonnetz vollst�ndig zu verschwei�en solltest Du einen Winkel von 180 Grad angeben.
###2.1.3. Komponenten

![IMAGE](images/2-1-3/2-1-3_001_Components-Tabs.png)

####2.1.3.1 Analyse

![IMAGE](images/2-1-3/2-1-3_002_Analyse-Components.png)
>1. Mesh Closest Point 
2. Mesh Evaluate
3. Mesh Sample Plus

**Element\* Mesh Closest Point**

Abweichend von Grasshopper's **Mesh Closest Point** Komponente, berechnet diese Komponente auch den Normalenvektor und die Farbe der ausgegebenen Punkte und �berkommt die Notwendigkeit der **Mesh Eval** Komponente, was den Graphen auf der Leinwand vereinfacht.

**Element\* Mesh Evaluate**

Die grasshoppereigene **Mesh Eval** Komponente ben�tigt einen Polygonnetzparameter als Eingabe, der von der **Mesh Closest Point** Komponente ausgegeben wird, aber recht schwierig h�ndisch zu erstellen ist. Element's "Closest Point" Komponente erm�glicht die direkte Eingabe des Index einer Netzfl�che und ihrer baryzentrischen Koordinaten.

Merke - baryzentrische Koordinaten sind auf eine Art und Weise definiert, dass sie immer zu eins aufaddieren. Wenn die Eingabewerte U, V und W nicht auf eins aufaddieren, wird diese Komponente das Verh�ltnis der drei Werte beibehalten, w�hrend sie normalisiert werden. Zum Beispiel, wenn Du die Eingabewerte 2, 2 und 4 eingibst, wird der Polygonnetzparameter mit {0.25;0.25;0.5} berechnet.

**Element\* Mesh Sample Plus**

Diese Komponente wird benutzt, um schnell Farbinformation aus einem Polygonnetz zu extrahieren. Sie gibt Alpha, Rot, Gr�n, Blau, Farbton, S�ttigung, und Leuchtkraftwerte der eingegebenen Punkte aus. Wenn ein gegebener Punkt nicht auf dem Polygonnetz liegt, wird diese Komponente den naheliegensten Punkt auf dem Polygonnetz berechnen. Diese Komponente nutzt parallele Datenverarbeitung, um die Geschwindigkeit zu erh�hen.


####2.1.3.2 Daten

![IMAGE](images/2-1-3/2-1-3_003_Data-Components.png)
>1. Datenvisualisierer
2. Benachbarte Kanten
3. Benachbarte Netzfl�chen
4. Benachbarte Eckpunkte


**Element\* Data Visualizer**

Diese Komponente wird verwendet, um Halbkantendaten der Netzfl�chen eines Eingabepolygonnetzes zu visualieren.

**Element\* Edge Neighbors**

Diese Komponente bietet die M�glichkeit Daten zur Nachbarschaft von Kanten eines Eingabepolygonnetzes strukturiert auszugeben. Die Ausgabedaten werden als Baum mit einem Ast f�r jede Kante in dem Polygonnetz ausgegeben. Sie gibt die Meshkanten, deren Endpunkte und die Mittelpunkte der Netzfl�chen angrenzend an jeder Kante ("dual graph"), die benachbarten Kanten als Linienobjekte (in Reihe entgegen dem Uhrzeigersinn) und benachbarte Netzfl�chenmittelpunkte (Mittelpunkte der Netzfl�chen angrenzend zu den Kantenstart- und endpunkten) aus.

![IMAGE](images/2-1-3/2-1-3_004_Edge-Neighbors.png)
> **Edge Neighbors** - Kanten, Eckpunkte an den Enden, angrenzende Netzfl�chenmittelpunkte, benachbarte Kanten und benachbarte Netzfl�chenmittelpunkte

**Element\* Face Neighbors**

Diese Komponente ist �hnlich zu den anderen in diesem Abschnitt, aber die Daten im Baum sind entsprechend der Netzfl�chen geordnet, mit einem Ast pro Netzfl�che. Die Ausgabeparameter sind die Netzfl�chenmittelpunkte, die Eckpunkte jeder Netzfl�che (angeordnet entgegen dem Uhrzeigersinn), benachbarte Kanten (angeordnet entgegen dem Uhrzeigersinn) und die Mittelpunkte der benachbarten Fl�chen (angeordnet entgegen dem Uhrzeigersinn).

![IMAGE](images/2-1-3/2-1-3_005_Face-Neighbors.png)
> **Face Neighbors** - Netzfl�chenmittelpunkte, Netzfl�cheneckpunkte, benachbarte Kanten und benachbarte Netzfl�chenmittelpunkte

**Element\* Vertex Neighbors**

Diese Komponente gibt die Polygonnetzeckpunkte, benachbarte Eckpunkte (angeordnet entgegen dem Uhrzeigersinn), benachbarte Kanten (angeordnet entgegen dem Uhrzeigersinn) und benachbarte Netzfl�chenmittelpunkte (angeordnet entgegen dem Uhrzeigersinn) in einem strukturierten Datenbaum entsprechend den Eckpunkten des Polygonnetzes aus.

![IMAGE](images/2-1-3/2-1-3_006_Vertex-Neighbors.png)
> **Vertex Neighbors** - Eckpunkte, benachbarte Eckpunkte, benachbarte Kanten, benachbarte Netzfl�chenmittelpunkte

####2.1.3.3 Primitive Polygonnetzk�rper

Element\* stellt vier zus�tzliche primitve Polygonnetzk�rper zur Verf�gung: den Dodekaeder, Tetraeder, Oktaeder und Ikosaeder. Diese Komponente nimmt eine einzelne Zahl als Eingabeparameter f�r den Radius und produziert ein Polygonnetz mit dem Koordinatenursprung als Zentrum, das aus einer Netzfl�che pro Seite besteht. Mit dem zus�tzlichen Einsatz des W�rfels, der bereits in Grasshopper zur Verf�gung steht, macht das f�nf platonische K�rper. 

![IMAGE](images/2-1-3/2-1-3_007_Primitives.png)
>1. Dodekaeder
2. Tetraeder
3. Oktaeder
4. Ikosaeder

####2.1.3.4 Gl�ttung

**Element\* Smooth** stellt einen optimierten Gl�ttungsalgorithmus zur Verf�gung, der effizienter arbeitet als Grasshopper's **Smooth Mesh**, wenn er f�r gr��ere Datens�tze eingesetzt wird. Er nutzt den Laplaceschen Gl�ttungsalgorithmus f�r halbkantenstrukturierte Polygonnetze. Er ver�ndert nicht die Topologie oder die Anzahl der Eckpunkte eines verschwei�ten Polygonnetzes, wird aber identische Eckpunkte zusammenf�hren, die aus einem unverschwei�ten Polygonnetz resultieren. Wir k�nnen die Gl�ttungsst�rke, Grenzbedingungen, Grenztoleranzen, sowie die Anzahl der Iterationen angeben.

![IMAGE](images/2-1-3/2-1-3_008_Smooth.png)

####2.1.3.5 Unterteilung

**Element\* Catmull Clark Subdivision** 

Dies ist eine rekursive Unterteilung basierend auf dem Catmull Clark Algorithmus. Wir k�nnen die Anzahl der Iterationen, sowie die Art des Umgangs mit offenen Kanten bestimmen.

**Element\* Constant Quad**

Diese Unterteilungskomponente wird ein Polygonnetz mit ausschlie�lich viereckigen Netzfl�chen erzeugen, indem sie eine weitere Netzfl�che f�r jede Kante des Polygonnetzes hinzuf�gt.

![IMAGE](images/2-1-3/2-1-3_009_Subdivide.png)
>1. Constant Quad Unterteilung
2. Catmull Clark Unterteilung

####2.1.3.6 Transformation

![IMAGE](images/2-1-3/2-1-3_010_Transform-Components.png)
>1. Mesh Windown
2. Mesh Frame
3. Mesh Thicken
4. Mesh Offset
5. Mesh Poke Face

Diese Komponenten stellen eine Anzahl von unterschiedlichen Transformationen zur Verf�gung, die unten beschrieben werden. Jede Komponente hat die zus�tzliche M�glichkeit Distanzdaten pro Eckpunkt anzunehmen, um eine Variation der Transformationsst�rke �ber das Polygonnetz zu erreichen.

**Element\* Mesh Window**

Stellt ein neues Polygonnetz innerhalb der Netzfl�chen mit einem Versatzwert her. Diese Komponente akzeptiert entweder ein Polygonnetz oder eine Liste von geschlossenen Polylinien als Eingabe.

**Element\* Mesh Frame**

Die Ausgabe ist ein Rahmen um die Netzfl�chen. Jede resultierende Netzfl�che wird ein neues Loch im Zentrum haben. Diese Komponente akzeptiert entweder ein Polygonnetz oder eine Liste von geschlossenen Polylinien als Eingabe.

**Element\* Mesh Thicken**

Diese Komponente wird einem Eingabepolygonnetz Materialst�rke entsprechend der Eckpunktnormalen der zur Verf�gung gestellten Eingabewerte zuweisen.

**Element\* Mesh Offset**

Diese Komponente erstellt einen Versatz zum urspr�nglichen Polygonnetz entsprechend der Eckpunktnormalen.

**Element\* Mesh Poke Face**

Zuerst werden die Netzfl�chen mit einer "Frame" Operation geteilt und dann die Innenfl�che nochmals mittig unterteilt. F�r diesen Teil der Netzfl�che kann ein Wert angegeben werden, der die innenliegenden Netzfl�chen entlang der Fl�chennormalen verschiebt. Zum Beispiel wird ein vierseitiges Polygon ("Quad") in vier dreiseitige Polygone, mit einem gemeinsamen Eckpunkt in deren Mitte, unterteilt. Der H�heneingabeparameter erlaubt es, den Eckpunkt entsprechend zu transformieren.

![IMAGE](images/2-1-3/2-1-3_011_Transform.png)
>1. Mesh Window
2. Mesh Frame
3. Ikosaeder nach der aufeinanderfolgenden Anwendung der "Mesh Frame", "Mesh Thicken" und Polygonnetzteilung Komponenten.

####2.1.3.7 Dienstprogramme

![IMAGE](images/2-1-3/2-1-3_012_Utility-Component.png)
>1. Mesh Combine & Clean
2. Mesh Edges
3. Mesh Status

**Element\* Mesh Combine and Clean** 

Diese Komponente verbindet verschiedene Polygonnetze mit den zus�tzlichen Optionen, das Polygonnetz basierend auf einem Winkel zu verschwei�en oder identische Eckpunkte zu verbinden. Diese Komponente stellt ebenso m�gliche topologische Probleme fest und gibt diese als Anmerkungen und Warnungen mit detaillierten Beschreibungen aus. Im Fall, dass die Zusammenf�hrung von identischen Eckpunkten eine schlechte Topologie erzeugt, wird die Komponente die unver�nderten Eingabepolygonnetze ausgeben, anstatt sie zusammenzuf�hren. Der Nutzer kann auch angeben, das Polygonnetz zusammenzuf�hren ohne die Eckpunkte zu ver�ndern.

**Element\* Mesh Edges** 

Diese Komponente gibt die offenen Kanten, Kanten, Netzfl�chenpolylinien und f�r unverschwei�te Polygonnetze die unverschwei�ten Polygonnetzkanten aus.

**Element\* Mesh Status** 

Diese Komponente gibt Polygonnetzinformationen basierend auf der Topologie aus. Es gibt zwei verschiedene Modi, in denen wir die Informationen ansehen k�nnen. Die erste ist die Ausgabe von Daten zur Geometrie, wie Polygonnetzvalidit�t, Anzahl der Eckpunkte, Anzahl der Netzfl�chen und Anzahl der Normalen. Die andere ist die Ausgabe des Polygonnetzstatus, welcher den Zustand des Polygonnetzes beschreibt, ob es nicht-mannigfaltige Kanten, degenerierte Netzfl�chen, die Anzahl der offenen Kanten oder die Anzahl unverbundener Netzfl�chen ist. Diese Komponente operiert nicht auf einem Polygonnetz, es gibt lediglich Informationen f�r den Nutzer aus. Es gibt auch eine Option f�r die Kombination identischer Eckpunkte, wodurch der Nutzer den Effekt dieser Option auf die entsprechenden Daten beobachten kann.
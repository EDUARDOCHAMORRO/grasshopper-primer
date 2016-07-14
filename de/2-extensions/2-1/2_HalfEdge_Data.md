###2.1.2. Halbkanten Daten

Im Grasshopper Primer haben wir uns angesehen, wie ein Polygonnetz in Grasshopper mit der Netzfl�chen-Eckpunkte-Datenstruktur beschrieben werden kann. Diese ist eine relativ einfache Datenstruktur und wird f�r viele Polygonnetzapplikationen genutzt, kann aber bei komplexeren Algorithmen recht ineffizient werden. Die Element\* Erweiterung restrukturiert Polygonnetze mit der Halbkanten Datenstruktur, eine kantenfokusierte Datenstruktur, die effiziente Aufrufe von benachbarten Eckpunkten, Netzfl�chen und Kanten erm�glicht, was die Geschwindigkeit und Performance von Algorithmen stark erh�hen kann. Diese Struktur kann [...] Informationen �ber Eckpunkte, Netzfl�chen und Kanten erhalten. Diese Methode erm�glicht die Generierung von neuen Mustern und Geometrien, komplett basiered auf der topologischen Nachbarschaft der Basisgeometrie.

Die Halbkantendatenstruktur ist eine Repr�sentation eines Polygonnetzes, in dem jede Kante in zwei Halbkanten unterteilt ist, die in entgegengesetzte Richtungen zeigen. Dies erlaubt expliziten und impliziten Zugang zu Daten von einem Polygonnetzelement zu benachbarten Elementen.

![IMAGE](images/2-1-2/2-1-2_001_Half-Edge.png)

####2.1.2.1 Halbkantenkonnektivit�t
Die in blau hervorgehobenen Halbkanten speichern Indizes mit Informationen �ber die jeweiligen Endpunkte, benachbarte Halbkanten und den zugeh�rigen Netzfl�chen. Die anderen Informationen (in grau dargestellt) sind implizit zug�nglich.
![IMAGE](images/2-1-2/2-1-2_002_Half-Edge.png)
####2.1.2.2 Eckpunktkonnektivit�t
Die in blau hervorgehobenen Eckpunkte speichern einen Index zu den jeweiligen ausgehenden Halbkanten. Die anderen Informationen (in grau dargestellt) sind implizit zug�nglich.
![IMAGE](images/2-1-2/2-1-2_003_Half-Edge.png)



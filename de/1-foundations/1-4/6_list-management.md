### 1.4.6. Listen Managen
{% if gitbook.generator == "pdf" or "mobi" or "epub" %}
>Beispiele zu diesem Abschnitt: [http://grasshopperprimer.com/appendix/A-2/1_gh-files.html](http://grasshopperprimer.com/appendix/A-2/1_gh-files.html)
{% else %}
>Beispiele zu diesem Abschnitt: [Download](../../appendix/A-2/gh-files/1.4.6_list management.gh)
{% endif %}

#####Eine der m�chtigsten Eigenschaften von Grasshopper ist die M�glichkeit schnell Listen zu erstellen und zu bearbeiten. Wir speichern viele verschiedene Datentypen in einer Liste (Nummern, Punkte, Vektoren, Kurven, Fl�chen, Breps, usw.) und es gibt eine Menge n�tzlicher Werzeuge hierf�r unter der "Sets/List" Unterkategorie.

####1.4.6.1. LISTENL�NGE
Die "List Length" Komponente (Sets/List/List Length) misst grunds�tzlich die L�nge einer Liste. Da unsere Listen immer bei null beginnen, ist der h�chste m�gliche Wert unseres Indexes einer Liste gleich der L�nge der Liste minus eins. In diesem Beispiel haben wir unsere Ausgangsliste mit dem L Eingabeparameter der "List Length" Komponente verbunden, um zu zeigen, dass in der Liste 6 Eintr�ge vorhanden sind.

![IMAGE](images/1-4-6/1-4-6_001-list-length.png)

##>#1.4.6.2. LISTENELEMENTE
Unsere Liste wird mit einer "List Item" Komponente (Sets/List/List Item) verbunden, um einen bestimmten Eintrag aus der Liste zu erhalten. Wenn wir auf ein individuelles Element einer Liste zugreifen wollen, muessen wir den i Eingabeparameter bestimmen; welcher mit dem Index �bereinstimmt, auf den wir zugreifen wollen. Wir k�nnen einen einzelnen Integerwert oder eine Liste von Integerwerten in den i Eingabeparameter eingeben, abh�ngig davon, welche Elemente wir erhalten wollen. Der L Eingabeparameter definiert die Ausgangsliste, die wir analysieren wollen. In diesem Beispiel haben wir den i Eingabeparameter mit 5.0 angegeben, so dass die "List Item" Komponente uns die Daten, die mit dem f�nften Eintrag der Liste verkn�pft sind, ausgibt.

![IMAGE](images/1-4-6/1-4-6_002-list-item.png)

####1.4.6.3. LISTEN UMKEHREN
Wir k�nnen eine Liste in ihrer Reihenfolge umkehren, indem wir die "Reverse List" Komponente (Sets/List/Reverse) anwenden. Wenn wir eine aufsteigende Liste mit Zahlen von 0.0 bis 9.0 in die "Reverse List" Komponente eingeben, gibt uns der Ausgabeparameter eine absteigende Liste von 9.0 bis 0.0 zur�ck.

![IMAGE](images/1-4-6/1-4-6_003-reverse-list.png)

####1.4.6.4. VERSCHIEBEN VON LISTEN
Die "Shift List" Komponente (Sets/Sequence/Shift List) wird die Reihenfolge der Liste nach oben oder unten verschieben, je nachdem welchen Wert wir f�r die Verschiebung angeben. Wir habn den Ausgabeparameter der Liste mit dem L Eingabeparameter der "Shift List" Komponente verbunden, w�hrend wir eine Zahl mit dem S Eingabeparameter verkn�pfen. Wenn wir die Verschiebung mit -1 angeben, werden alle Werte in der Liste um einen Eintrag nach unten verschoben. Ebenso werden alle Werte in der Liste um einen Eintrag nach oben verschoben, wenn wir die Verschiebung mit +1 angeben. In diesem Beispiel haben wir die Verschiebung mit +1 festgelegt, so dass unsere Leiste um einen Eintrag nach oben verschoben wird. Wenn wir den "Wrap" Wert auf "false" stellen, wird der letzte Eintrag nach oben verschoben und aus der Liste fallen, was den Wert grunds�tzlich aus der Liste entfernt (so dass die L�nge der Liste sich um eins reduziert). Jedoch, wenn wir den "Wrap" Wert auf "true" setzen, wird der letzte Eintrag der Liste wieder unten an der Liste angef�gt.

![IMAGE](images/1-4-6/1-4-6_004-shift-list.png)

####1.4.6.5. ELEMENTE EINF�GEN
Die "Insert Items" Komponente (Sets/Lists/Insert Items) erm�glicht es eine Menge an Werten in eine Liste einzuf�gen. Damit dies anst�ndig funktioniert, m�ssen wir f�r jedes Element wissen, welche Elemente wir an welcher Indexposition einf�gen wollen. Im unteren Beispiel werden wir die Buchstaben A, B und C an die Indexposition drei einf�gen.
![IMAGE](images/1-4-6/1-4-6_005-insert-item.png)

####1.4.6.6. WEBEN
Die "Weave" Komponente (Sets/Lists/Weave) f�hrt zwei Listen basierend auf einem Webemuster (P Eingabeparameter) zusammen. Wenn das Muster und die Datenstr�me nicht perfekt aufeinander abgebildet werden k�nnen, wird die Komponente entweder "null" Werte in die Eingabestr�me einf�gen, oder sie kann Str�me ignorieren, die noch nicht ersch�pft wurden.

![IMAGE](images/1-4-6/1-4-6_006-weave.png)

####1.4.6.7. AUSSORTIEREN MIT MUSTER
Die "Cull" Komponente (Sets/Sequence/Cull Pattern) entfernt Elemente einer Liste mit einer sich wiederholenden Maske. Die Maske ist definiert als eine Liste boolscher Werte (wahr oder falsch). Die Maske wird wiederholt, bis alle Elemente der Datenliste ausgewertet wurden.

![IMAGE](images/1-4-6/1-4-6_007-cull-pattern.png)


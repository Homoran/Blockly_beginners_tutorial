# Blockly_beginners_tutorial

# Einleitung

Um Einsteigern in Javascript das grundlegende Verständnis der Strukturen und Befehle zu erleichtern
bietet sich die Verwendung von Blockly an.

Dies ist ein JavaScript-Editor mit grafischer Oberfläche, bei der die Befehle per drag & drop
zusammengesetzt werden.

Hier sollen zuerst die Wichtigsten Strukturen eines Blockly-Skripts erklärt werden und später 
anhand von Beispielen auch die wichtigsten Bausteine.

Um zu zeigen, dass einfache Steuerungen mit ioBroker kein Hexenwerk sind, zeigt das Tutorial die Erstellung 
von Skripten mittels Blockly an einem ganz einfachen Beispiel:

![Hier soll das Bild sein](/Media/Licht_an_20_00.jpg "ein einfaches Programm")

Jeden Tag um 20:00 wird das Licht im Schlafzimmer angemacht.
Dass man aber auch komplexere Abläufe mit Blockly realisieren kann zeigt das Tutorial später, indem dieses 
Skript später noch schrittweise erweitert wird.


# Eine JavaScript-Struktur

Javascript ist eine ereignisbasierende Programmiersprache. Das bedeutet, dass die Programme immer laufen 
(also nicht deaktiviert und wieder gestartet werden) und auf einen Auslöser wartet, der dann dafür sorgt, 
dass das Programm abgearbeitet wird.

Anschließend kann über viele verschiedenen Routinen zum einen die Bedingungen für eine Abarbeitung, 
zum anderen die durchzuführende Aktion programmiert werden.

Zu jeder Gruppe gibt es auf der linken Seite in der Block-Sidebar diverse Blöcke, die die notwendigen 
Befehle oder Operationen enthalten:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Block_Sidebar.jpg "Die Block-Sidebar")



## Trigger-Bausteine

Um das Skript abzuarbeiten muss ein Ereignis passieren, das im Skript erfasst wird. Dazu bietet Blockly 
die so genannten Trigger-Bausteine an. Diese befinden sich auf der linken Seite in der Block-Sidebar:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_Trigger.jpg "Die Triggerbausteine")

Mit diesen Bausteinen wird das Ereignis abgefragt, was die Abarbeitung des Programms auslösen soll.
Für die verschiedenen Möglichkeiten (z.B. Events, Zeitsteuerung) stehen entsprechende Bausteine zur Verfügung.

Die Bausteine, die nicht die Form einer Klammer haben, verarbeiten weitere Informationen des jeweiligen Triggerbausteins.

#### **ACHTUNG!**
**Bitte beachten:**
* Es darf nur ein Triggerbaustein pro Script verwendet werden.
* Der Triggerbaustein muss der Baustein sein der am weitesten außen liegt und die übrigen Befehle einschließt (Außer Variablenzuweisungen)
* Alle Bausteine, die sich außerhalb des Triggerbausteins befinden werden nur einmalig zu Skriptstart abgearbeitet und 
**nicht** nach der Auslösung des Triggers.


---

Das einfachste Script ( Trigger = Zeitplan -> Lampe an!) würde jetzt auf diesen Trigger reagieren. Dazu würde z.B. 
einfach ein Datenpunkt eines Schalters über einen weiteren Baustein auf den entsprechenden Wert gesetzt.

---

## Systembausteine

Eine weitere Gruppe an Blöcken in der Block-Sidebar sind die Systembausteine. Mit ihnen werden die wichtigsten 
Aktionen innerhalb der Datenpunkte von ioBroker umgesetzt.

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_System.jpg "Die Systembausteine")

Hier werden jetzt die Blöcke "steuere..." und "aktualisiere..." zur Änderung von Werten der Datenpunkte in ioBroker verwendet.

### Der steuere-Block

muss bei der Änderung eines Wertes bei einem Adapter verwendet werden, damit der Adapter darauf reagiert. 
Der zu ändernde Datenpunkt wird über die Object ID ausgewählt und der einzutragende Wert wird in das leere Feld eingetragen.
Hierbei bitte den Typ des Datenpunktes beachten und einen Text-, einen Mathematik- oder einen Logik-Baustein verwenden.

### Der aktualisiere-Block
darf nur bei der Verwendung von eigenen Datenpunkten verwendet werden. Diese selbst angelegten DAtenpunkte dienen z.B. 
der Darstellung in vis oder als scriptübergreifende "Systemvariable" als Rechengrundlage o.ä..

Der zu ändernde Datenpunkt wird über die Object ID ausgewählt und der einzutragende Wert wird in das leere Feld eingetragen.
Hierbei bitte den Typ des Datenpunktes beachten und einen Text-, einen Mathematik- oder einen Logik-Baustein verwenden

---

Damit erhalten wir das oben gezeigte Programm 

---

## Logik-Bausteine

Ein "richtiges" Programm benötigt oft mehr oder weniger viele Logik-Bausteine um diverse Eventualitäten abzudecken. 
Entweder sollen diese Möglichkeiten einfach unberücksichtigt bleiben, oder zu jeder Möglichkeit soll eine 
jeweils andere Aktion erfolgen.

Um dies umzusetzen befindet sich in der Block-Sidebar ebenfalls eine Gruppe:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_Logik.jpg "Die Logikbausteine")

---

In dem ersten Schritt soll das Licht nur um 20:00 angehen, wenn es bereits dunkel ist. Also muss hier eine weitere Abfrage auf die Helligkeit geschehen.

Ein strukturiertes Denken hilft jetzt ungemein, indem die gewünschte Funktionalität formuliert wird:
*Prüfe um 20:00 ob es bereits dunkel ist und schalte in ddas Licht anSchalte um 20:00 das Licht an 
falls es dann bereits dunkel ist*

Das Programm triggert also weiter um 20:00; vor dem Schalten der Lampe wird aber die Helligkeit geprüft.

![Hier soll das Bild sein](/Media/Licht_an_20_00_dunkel.jpg "ein Programm mit Bedingung")

Ein wichtiger Logik-Baustein ist der FALLS-Block.
Hier wird der *Wert von* einem Sensor (hier Lichtsensor:Helligkeit) überprüft, ob er bereits unter einer Schwelle liegt.

Nur dann geht das Licht um 20:00 an.

Der Vergleichsbaustein (X = Y) aknn für viele Vergleiche eingesetzt werden. Über den Pulldownpfeil können verschiedene 
Vergleichsoperatoren ausgewählt werden.

Bei dem anschließend einzugebenden Vergleichswert muss wiederum auf den Typ des zu vergleichenden Datenpunktes geachtet werden.
Dementsprechend einen einen Text-, einen Mathematik- oder einen Logik-Baustein verwenden.


## Datum und Zeitbausteine

Leider wird es mit dem erstellten Programm geschen, dass eines Abends das Licht nicht angeht. 
Was ist passiert?

Das Programm wird per Zeitplan um 20:00 getriggert und überprüft um exakt 20:00 ob die tatsächliche Helligkeit bereits 
unter dem eingestellten Wert liegt.

Fällt die Helligkeit erst um 20:01 (oder später) unter diesen Wert, passiert gar nichts.

Also muss das Ganze andersherum angegangen werden:
*Wenn die Helligkeit unter Wert x fällt, prüfe ob es bereits 20:00 ist*

Dazu werden die Zeitbausteine benötigt:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_Trigger.jpg "Die Zeitbausteine")

Das Programm sieht dann so aus:

![Hier soll das Bild sein](/Media/Licht_an_dunkel_20_00.jpg "ein Programm mit Bedingung")

Der Auslöser zur Abarbeitung des Skripts ist diesmal die Änderung der Helligkeit.

Jetzt wird zum einen geprüft ob es bereits nach 20:00 ist, UND zum anderen, ob die Änderung zu einem Wert <500 führt. 
Die Verwendung des UND Bausteins verlangt jetzt, dass beite Bedingungen wahr werden.

**Hinweis**
Der UND-Baustein hat standardmäßig nicht die abgebildete Form. Damit ein Blockly übersichtlicher wird, kann man desen (und andere) Baustein zusammenfalten. Dazu klickt man mit der rechten Maustaste den Baustein an un wählt "externe Eingänge"

---

Leider wir jetzt das Licht nur angehen, wenn es nach 20:00 dunkel wird.

Um zu erreichen, dass beide Fälle dazu führen, dass das Licht um oder nach 20:00 angeht wenn es entsprechend dunkel ist muss man einen Trick anwenden, da es keinen kombinierten Trigger gibt und kein Trigger innerhalb eines Triggers sein darf.

Es müssen daher zwei unabhängige Blocklys -so wie sie abgebildet sind- geschrieben werden.

Diese dürfen allerdings auf einer Arbeitsfläche (nebeneinander oder wie hier übereinander) angeordnet werden:

![Hier soll das Bild sein](/Media/Licht_an_Kombi.jpg "Zwei Trigger")

---

## Programm speichern

Bevor man die Arbeitsfläche verlässt muss das Programm über den Button "Speichern", der sich links oben 
von der Arbeitsfläche befindet, gespeichert werden, wenn es Änderungen am Programm gegegebn hat.
In diesem Fall ist der Button in rot beschriftet.


## Programm starten

Wie bereits geschrieben muss ein JavaScript immer laufen.
Dazu startet man das Programm mit dem START-Button in dem Programme Explorer, links neben der Areitsfläche

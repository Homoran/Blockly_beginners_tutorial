# Blockly_beginners_tutorial

## Einleitung
Um Einsteigern in Javascript das grundlegende Verständnis der Strukturen und Befehle zu erleichtern
bietet sich die Verwendung von Blockly an.

Dies ist ein JavaScript-Editor mit grafischer Oberfläche, bei der die Befehle per drag & drop
zusammengesetzt werden.

Hier sollen zuerst die Wichtigsten Strukturen eines Blockly-Skripts erklärt werden und später 
anhand von Beispielen auch die wichtigsten Bausteine,

## Eine JavaScript-Struktur
Javascript ist eine ereignisbasierende Programmiersprache. Das bedeutet, dass die Programme immer laufen 
(also nicht deaktiviert und wieder gestartet werden) und auf einen Auslöser wartet, der dann dafür sorgt, 
dass das Programm abgearbeitet wird.
Anschließend kann über viele verschiedenen Routinen zum einen die Bedingungen für eine Abarbeitung, 
zum anderen die durchzuführende Aktion programmiert werden.

Zu jeder Gruppe gibt es auf der linken Seite in der Block-Sidebar diverse Blöcke, die die notwendigen 
Befehle oder Operationen enthalten:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Block_Sidebar.jpg "Die Block-Sidebar")



### Der Trigger-Baustein
Um das Skript abzuarbeiten muss ein Ereignis passieren, das im Skript erfasst wird. Dazu bietet Blockly 
die so genannten Trigger-Bausteine an. Diese befinden sich auf der linken Seite in der Block-Sidebar:

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_Trigger.jpg "Die Triggerbausteine")

Mit diesen Bausteinen wird das Ereignis abgefragt, was die Abarbeitung des Programms auslösen soll.
Für die verschiedenen Möglichkeiten (z.B. Events, Zeitsteuerung) stehen entsprechende Bausteine zur Verfügung.

Die Bausteine, die nicht die Form einer Klammer haben, verarbeiten weitere Informationen des jeweiligen Triggerbausteins.

#### **ACHTUNG!**
Bitte beachten:
* Es darf nur ein Triggerbaustein pro Script verwendet werden.
* Der Triggerbaustein muss der Baustein sein der am weitesten außen liegt und die übrigen Befehle einschließt (Außer Variablenzuweisungen)
* Alle Bausteine, die sich außerhalb des Triggerbausteins befinden werden nur einmalig zu Skriptstart abgearbeitet und 
**nicht** nach der Auslösung des Triggers.


---

Das einfachste Script ( Trigger = Zeitplan -> Lampe an!) würde jetzt auf diesen Trigger reagieren. Dazu würde z.B. 
einfach ein Datenpunkt eines Schalters über einen weiteren Baustein auf den entsprechenden Wert gesetzt.

---

### Systembausteine
Eine weitere Gruppe an Blöcken in der Block-Sidebar sind die Systembausteine. Mit ihnen werden die wichtigsten 
Aktionen innerhalb der Datenpunkte von ioBroker umgesetzt.

![Hier soll das Bild sein](/Media/ioBroker_Blockly_Blocks_System.jpg "Die Systembausteine")

Hier werden jetzt die Blöcke "steuere..." und "aktualisiere..." zur Änderung von Werten der Datenpunkte in ioBroker verwendet.

#### Der steuere-Block
muss bei der Änderung eines Wertes bei einem Adapter verwendet werden, damit der Adapter darauf reagiert. 
Der zu ändernde Datenpunkt wird über die Object ID ausgewählt und der einzutragende Wert wird in das leere Feld eingetragen.
Hierbei bitte den Typ des Datenpunktes beachten und einen Text-, einen Mathematik- oder einen Logik-Baustein verwenden

#### Der aktualisiere-Block
darf nur bei der Verwendung von eigenen Datenpunkten verwendet werden. Diese selbst angelegten DAtenpunkte dienen z.B. 
der Darstellung in vis oder als scriptübergreifende "Systemvariable" als Rechengrundlage o.ä..
Der zu ändernde Datenpunkt wird über die Object ID ausgewählt und der einzutragende Wert wird in das leere Feld eingetragen.
Hierbei bitte den Typ des Datenpunktes beachten und einen Text-, einen Mathematik- oder einen Logik-Baustein verwenden

---

Das Programm sähe dann so aus:
![Hier soll das Bild sein](/Media/Licht_a_20_00.jpg "ein einfaches Programm")

Jeden Tag um 20:00 wird das Licht im Schlafzimmer angemacht.

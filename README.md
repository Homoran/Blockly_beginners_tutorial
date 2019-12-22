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

Mit diesen Bausteinen wird das Eereignis abgefragt, was die Abarbeitung des Programms auslösen soll.
Für die verschiedenen Möglichkeiten (z.B. Events, Zeitsteuerung) stehen entsprechende Bausteine zur Verfügung.

####**ACHTUNG!**
Bitte beachten:
* Es darf nur ein Triggerbaustein pro Script verwendet werden.
* Der Triggerbaustein muss der Baustein sein der am weitesten außen liegt und die übrigen Befehle einschließt (Außer Variablenzuweisungen)
* Alle Bausteine, die sich außerhalb des Triggerbausteins befinden werden nur einmalig zu Skriptstart abgearbeitet und 
**nicht** nach der Auslösung des Triggers.



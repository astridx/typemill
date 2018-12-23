# Relationale Datenbanken

Aus den vielen verschiedenen Modellen, 
die für die Erstellung einer Datenbank definiert wurden, 
ist die am häufigsten verwendete die **relationale Datenbank**[^1]. 
Dies ist nicht nur im GIS-Kontext so.
Relationale Datenbanken verwendet ein auf **Tabellen** beruhendes Schema, 
das sowohl leicht zu verstehen als auch gut für Analyse- und Datenabfragen geeignet ist. 
Tabellen haben eine bestimmte Anzahl von **Datensätzen** (Zeilen) und **Feldern** (Spalten).

Die Tabelle selbst wird Relation genannt, 
da sie die Beziehung zwischen ihren Elementen enthält. 
Spalten stellen die Attribute dar, 
die einem Feature zugeordnet sind.
Die Zeilen enthalten die Datensätze. 
Eine Zeile wird mit einer Menge von n Attributen gebildet, 
die ein **Tupel** bilden.

Eine Datenbank enthält in der Regel mehr als eine Tabelle, 
da es sich bei den zu speichernden Informationen um 
viele verschiedene Arten handelt und es praktisch ist, 
sie in mehrere Tabellen zu unterteilen. 
Abgesehen von den Beziehungen, die die Tabelle selbst beinhaltet, 
können auch Beziehungen zwischen Tabellen definiert werden. 
Dies wird allgemein als **Join** bezeichnet. 
Um eine Tabellenverknüpfung durchzuführen, 
müssen wir ein Attribut haben, 
das zur eindeutigen Darstellung eines Tupels verwendet werden kann. 
Dieses Attribut wird auch Schlüsselattribut genannt. 
Es muss für jedes Tupel eindeutig und unveränderlich sein. 
Wenn wir beispielsweise eine Tabelle haben, 
in der jede Zeile eine Person darstellt, 
kann ein Attribut, das die Sozialversicherungsnummer enthält, 
als Schlüsselattribut verwendet werden.

Bei der Arbeit mit geografischen Daten wird die räumliche Komponente 
häufig als Schlüssel verwendet, da sie normalerweise eindeutig ist.

Beziehungen zwischen Tabellen können verschiedenen Typen entsprechen, 
abhängig von den Datensätzen einer Tabelle, 
die mit denen der anderen Tabelle verwandt sind. 
Wir können 
- eins zu eins, 
- eins zu vielen und 
- viele zu vielen  

Beziehungen unterschieden. 

Wenn wir zum Beispiel eine Tabelle mit Städten und eine andere mit Personen 
haben und wir möchten in einer Beziehung beschreiben in welcher Stadt Menschen leben, 
wird eine Eins-zu-Viele-Beziehung das Ergebnis sein: 
Viele Menschen können in einer einzigen Stadt leben aber jede Person kann 
nur in einer Stadt leben. todo beispiele bild

[^1]: https://de.wikipedia.org/wiki/Relationale_Datenbank
[^2]: https://de.wikipedia.org/w/index.php?title=Datenbank&oldid=178992365

*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute




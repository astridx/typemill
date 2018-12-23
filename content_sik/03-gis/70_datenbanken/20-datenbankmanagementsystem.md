# Datenbankmanagementsystem 

Neben den Daten sind Datenbankmanagementsysteme (DBMS) das grundlegende Element, 
um geografische Daten zu nutzen. 
Diese Systeme sind ein Mittler zwischen den Daten und der Software, 
die sie verwendet. 
Software wie ein Desktop-GIS greift nicht direkt auf die Datenbank zu, 
sondern über ein DBMS.

> Eine Datenbank[^1] besteht aus zwei Teilen: der Verwaltungssoftware, 
genannt Datenbankmanagementsystem (DBMS), und der Menge der zu verwaltenden Daten, 
der Datenbank (DB) im engeren Sinn, zum Teil auch Datenbasis genannt. 

Im Folgenden sind einige der Eigenschaften aufgeführt, die ein DBMS haben muss:

- **Transparenter Zugriff auf Daten**  
Das DBMS erstellt eine Abstraktion der Daten, die die Arbeit erleichtert. 
Dabei werden die internen Elemente verborgen, 
die für die Auswertung der Daten nicht relevant sind.
Prozeduren wie Abfragen werden über ein DBMS durchgeführt, 
das sich darum kümmert, sie zu interpretieren, 
sie auf die Datenbank anzuwenden und das entsprechende Ergebnis zurückzugeben. 
Das GIS fragt die Datenbank nicht ab, sondern kommuniziert mit dem DBMS.
- **Datenschutz**  
Wenn die Datenbank vertrauliche Informationen enthält, 
muss ein DBMS den Zugriff darauf steuern, 
es auf bestimmte Benutzer beschränken und 
die erforderlichen Schutzmechanismen implementieren.
- **Effizienz**  
Ein DBMS muss in der Lage sein, 
eine große Menge von Daten und eine große Anzahl von Operationen -
beispielsweise viele Benutzer, die gleichzeitig zugreifen - 
effizient zu handhaben und 
eine schnelle Antwort auf Benutzeranforderungen bereitzustellen.
- **Transaktionsmanagement**  
Vorgänge in einer Datenbank - 
beispielsweise Hinzufügen oder Löschen eines Datensatzes - 
werden mithilfe einer Transaktion ausgeführt. 
Eine Transaktion ist eine Arbeitseinheit, 
die in einem Datenbankverwaltungssystem mit einer Datenbank ausgeführt wird. 
Ein DBMS wird als transaktional bezeichnet, 
wenn es die Integrität der Daten garantieren kann und 
Transaktionen nicht unvollständig bleiben.

Da Software wie ein GIS mit dem DBMS kommuniziert und nicht direkt 
auf die Datenbank zugreift, wird eine Sprache benötigt, 
um diese Kommunikation aufzubauen. 
Sprachen, die verwendet werden, um Abfragen an ein DBMS vorzunehmen, 
werden als Abfragesprachen bezeichnet. 
Die beliebteste dieser Sprachen ist die strukturierte Abfragesprache SQL[^2].

## Räumliche Datenbanken (Spatial databases)

Wir haben die grundlegenden Ideen über allgemeine Datenbanken überprüft, 
die jede Art von Daten enthalten können. 
Das Hinzufügen von räumlichen Daten ist nicht trivial, 
da es mehr Komplexität hinzufügt und es notwendig macht, 
einen anderen Ansatz zu verwenden. 
Damit eine Datenbank als räumlich betrachtet werden kann, 
sollte sie an die besondere Beschaffenheit von Geodaten angepasst werden und 
zusätzliche Elemente enthalten.

Erstens muss die Datenbank in der Lage sein, räumliche Daten nativ zu speichern. 
Das bedeutet, dass eine Geometrie in der Tabelle gespeichert werden kann, 
genau wie andere Datentypen, die für Tabellenattribute verwendet werden können, 
wie z. B. numerische Werte oder Textzeichenfolgen. 
Die Datenbank muss in der Lage sein, räumliche Daten nicht nur zu speichern, 
sondern auch zu verstehen und sich ihrer Eigenschaften bewusst zu sein, 
damit sie Abfragen in Bezug auf diese Daten unterstützen kann.

Dies macht die Datenbank im Gegensatz zu einem Speichermechanismus, 
in dem die Geometrie unter Verwendung einiger der grundlegenden Datentypen 
gespeichert wird - 
beispielsweise mit einer Zeichenfolge, die die Geometriekoordinaten enthält - 
vollständig räumlich aktiviert, und 
die Datenbank weiß nichts über ihre räumliche Beschaffenheit.
Die Datenbank unterscheidet nicht zwischen dieser Zeichenfolge und anderen, 
die andere Arten von Informationen enthalten.

Obwohl auch Rasterdaten gespeichert werden können, 
arbeiten räumliche Datenbanken meist mit Vektordaten und sind besser an sie angepasst. 
Die Geometrien werden als Teil der Attribute eines Tabellensatzes gespeichert, 
der einem Merkmal im Vektordarstellungsmodell entspricht. 
Die thematische Komponente kann ohne weitere Anpassung in der Datenbank gespeichert werden.

Unter der Annahme, dass die Datenbank bereit ist, 
räumliche Daten zu speichern und korrekt damit zu arbeiten, 
müssen wir nun die Abfragesprache anpassen. 
Neben den üblichen Operationen, die ein DBMS ausführen kann, 
werden neue hinzugefügt, 
die die räumlichen Eigenschaften von räumlichen Daten verwenden. 
Eine Abfragesprache, die Abfragen unterstützt, 
die sich auf die räumliche Komponente der Daten beziehen, 
wird als räumliche Abfragesprache bezeichnet.

[^1]: https://de.wikipedia.org/wiki/Datenbank
[^2]: https://de.wikipedia.org/w/index.php?title=SQL&oldid=180497490

*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute
*[DBMS]: Datenbankmanagementsystem
*[SQL]: Structured Query Language“ (auf Deutsch: „Strukturierte Abfrage-Sprache“)
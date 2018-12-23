# Queries 

Abfragen

Eine Abfrage ist eine Operation, bei der wir die geographischen Daten 
nach den von ihnen erfassten Informationen abfragen. 
Diese Art der Analyse ist eines der Schlüsselelemente von GIS, 
da sie einen großen Teil der Arbeit mit einer GIS-Software darstellt.

Obwohl eine Abfrage eine Datenbanken nicht voraussetzen, 
werden sie mit Hilfe eines DBMS und einer Abfragesprache leistungsfähiger 
und effizienter.

Im Kontext von GIS stellt eine Abfrage etwas Ähnliches dar, 
was wir tun, wenn wir eine klassische Papierkarte verwenden, 
und wir antworten auf Fragen wie *"Welcher ist der nächste Fluss zu Stadt x?"* 
oder 
*"Welche Flüsse kreuzen die Provinz Y?"*. 
Wir dürfen jedoch nicht vergessen, 
dass geografische Daten aus zwei Komponenten bestehen: 
Einer *thematischen* und einer *räumlichen*. 
Fragen wie die obigen beziehen sich nur auf die räumliche Komponente, 
aber wir können Abfragen erstellen, die sich auf die thematische oder 
beide gleichzeitig beziehen.

Ein sehr einfaches Beispiel für eine Abfrage ist die Auswahl. 
Dies ist eine Operation, die normalerweise in einem GIS ausgeführt wird, 
um nur mit einer Teilmenge aller Features in einer Ebene zu arbeiten. 
In Abbildung 9.1 sehen Sie, 
wie der GIS-Benutzer einen rechteckigen Bereich definiert und Funktionen, 
die innerhalb seiner Grenzen liegen, ausgewählt werden. 
Die Auswahlkriterien können so einfach wie diese oder komplexer sein und 
sie können auch die thematische Komponente enthalten - 
hier verwenden wir nur die räumliche Komponente.

![Manuelle Auswahl von Features durch Definition einer rechteckigen Region](../media/img/Selection.png)
*Abbildung: Manuelle Auswahl von Features durch Definition einer rechteckigen Region.*

Eine Abfrage kann auch verwendet werden, 
um bestimmte Informationen aus einer Datenbank nach unseren Bedürfnissen zu extrahieren und 
später eine neue Ebene damit zu erstellen. 
Diese Operation ist sehr nützlich, wenn die Datenbank eine große Menge an Daten enthält, 
aber wir nur einen Teil dieser Daten benötigen. 
Wir könnten eine Teilmenge basierend auf 
- räumlichen Kriterien erstellen - 
beispielsweise wenn die Datenbank Informationen für die ganze Welt enthält und 
wir nur Daten für ein bestimmtes Land wünschen. 
- eine thematische - die Datenbank enthält viele Attribute, die nur jedem Merkmal zugeordnet sind - 
einige von ihnen sind für uns von Interesse, oder eine Kombination von beidem. 
Um diese Informationen zu extrahieren und eine Teilmenge der ursprünglichen Daten 
zu erstellen, verwenden wir eine Abfrage.

Es gibt weitere Beispiele für Abfragen. 
Nehmen wir an, 
wir haben eine Ebene mit den Ländern der Welt und 
eine Reihe von wirtschaftlichen und sozialen Parametern, 
die mit jedem von ihnen verbunden sind. 
Für jedes Land haben wir auch ein Polygon, das seine Grenzen darstellt.

Wir können Abfragen wie die folgenden vornehmen:

- Welche Länder haben ein höheres BIP als Spanien?
- Welche Länder sind im letzten Jahr wirtschaftlich gewachsen?
- In welchen Ländern leben mehr als 200 Millionen Menschen?

In diesen Abfragen verwenden wir nicht die räumliche Komponente - 
das mit jedem Land verknüpfte Polygon ist nicht erforderlich. 
Wir könnten diese Abfragen durchführen, 
wenn wir Länderdaten ohne räumliche Komponente hätten und 
eine reguläre Datenbank ohne räumliche Fähigkeiten verwenden würden.

Abfragen können mehrere Kriterien enthalten. Zum Beispiel:

- In welchen Ländern, 
die im letzten Jahr wirtschaftlich gewachsen sind, leben mehr als 40 Millionen Menschen?
- In welchen Ländern, 
in denen Englisch gesprochen wird, hat die Bevölkerung im letzten Jahr zugenommen?

Um Abfragen so auszudrücken, 
dass sie später an eine Abfragesprache angepasst werden können, 
müssen wir logische Operatoren verwenden. 
Die obigen Abfragen würden wie folgt umgeschrieben werden.

- Welche Länder sind im letzten Jahr wirtschaftlich gewachsen 
und haben eine Bevölkerung von mehr als 40 Millionen Menschen?
- In welchen Ländern wird Englisch gesprochen und 
die Bevölkerung hat sich im letzten Jahr vermehrt?

Abfragesprachen, 
die für die Kommunikation mit einem DMBS verwendet werden können, 
unterstützen diese Operatoren für Abfragen.

Wenn das DBMS räumlich ist und versteht, 
dass bestimmte Spalten einer Tabelle räumliche Informationen enthalten, 
unterstützt es Abfragen, die diese Informationen verwenden, beispielsweise die folgenden:

- Welches Land umfasst die meisten Breitengrade?
- Wie viele Länder sind vollständig in der südlichen Hemisphäre enthalten?
- Welche Länder liegen weniger als 2000 km von Deutschland entfernt?

Um auf diese Anfragen zu antworten, 
müssen wir nur die räumliche Komponente analysieren und 
benötigen nicht den Rest der Attributdaten. 
Diese Abfragen sind rein räumlich. 
Obwohl sie das, was wir vorher gemacht haben, erweitern, 
fügen wir hier keine neue Art der Untersuchung von geografischen Daten hinzu, 
die ohne ein GIS nicht möglich wäre. 
Wir könnten auf diese Anfragen nur mit einer klassischen Papierkarte antworten.

Die wahre Stärke räumlicher Abfragen besteht darin, 
sowohl die thematische als auch die räumliche Komponente abzufragen. 
Zum Beispiel mit Abfragen wie diesen:

- Welche Länder der südlichen Hemisphäre haben eine höhere Bevölkerungsdichte als Peru?
- Wie viele Länder mit mehr als 10 Millionen Einwohnern teilen ihre Grenzen mit Russland?

Diese Abfragen erfordern eine Analyse der thematischen Komponente und 
enthalten gleichzeitig Kriterien, 
die auf den räumlichen und topologischen Beziehungen der zugehörigen Geometrien basieren.

Abfragen können mehrere Ebenen umfassen. 
Zum Beispiel, wenn wir zusammen mit der Länderebene, 
die wir benutzt haben, eine Ebene mit Flüssen haben, 
könnten wir auf eine Frage wie *Welche Länder kreuzt der Nil?* antworten. 
Dies ist eine rein räumliche Abfrage, die zwei Ebenen verwendet.

Tabellen-Joins, die für reguläre Datenbanken ohne räumliche Daten diskutiert wurden, 
können auch mit einem räumlichen Kriterium durchgeführt werden. 
Diese sind als räumliche Joins bekannt.

Hier ist ein Beispiel für einen räumlichen Join. 
Angenommen, wir haben eine Ebene mit Weltstädten und die Ebene mit Ländern, 
die wir in vorherigen Beispielen verwendet haben. 
Wir können eine Beziehung zwischen den beiden entsprechenden Tabellen definieren, 
die jeder Stadt alle Attribute des Landes, zu dem sie gehört, zuordnen. 
Ein Feld mit dem Ländernamen in beiden Tabellen wird benötigt, 
damit diese Tabellen verknüpgt werden können.

Aber selbst wenn wir kein solches Feld haben, 
können wir den Tabellen beitreten, 
wenn wir räumliche Daten für Städte und Länder haben todo?. 
Alle Städte, die zu einem bestimmten Land gehören, 
müssen innerhalb der Grenzen des Landes liegen. 
Diese Feststellung kann verwendet werden, 
um die Beziehung zwischen den Tabellen zu definieren, 
und wir wissen, zu welchem Land eine Stadt gehört, 
indem wir das Polygon aus der Länderliste finden, 
in der sich der Punkt befindet, der die Stadt darstellt.

## Räumliche Indizes (Spatial indexes)

Wenn wir eine Abfrage an eine Spatial-Datenbank senden, 
kann die Beantwortung einer Spatial-Datenbank eine große Anzahl von Operationen erfordern. 
Wenn wir anhand unserer Länderebene wissen wollen, 
welche Länder eine Bevölkerung von mehr als 10 Millionen Menschen haben, 
müssen wir die Bevölkerung jedes einzelnen Landes in unserer Tabelle lesen und 
mit diesem Wert vergleichen. 
Wenn die Tabelle eine große Anzahl an Datensätze enthält, 
kann die Verarbeitung der Abfrage lange dauern. 
Es ist klar, 
dass dies nicht die optimale Art ist, 
eine Anfrage zu bearbeiten.

Durch die Verwendung so genannter Indizes können wir die Daten, 
die die Antwort unserer Anfrage bilden, 
in kürzerer Zeit erreichen, 
ohne alle in der Datenbank enthaltenen Daten durchlaufen zu müssen.

Dies ist an einem Beispiel leicht zu verstehen. 
Stellen Sie sich ein Telefonbuch vor. 
Es enthält eine große Anzahl von Einträgen, 
aber Sie können einen Namen leicht finden, 
ohne alle Einträge lesen zu müssen. 
Dies liegt daran, dass 
- die Daten in einer bestimmten Weise (alphabetisch) geordnet (indiziert) sind und 
- Sie wissen, wie Sie diese Indizierung verwenden 
(Sie kennen die Reihenfolge der Buchstaben im Alphabet). 

Damit wissen Sie, dass es keinen Sinn macht, 
auf den Seiten, die den Buchstaben A oder B entsprechen, 
nach einem bestimmten Herrn Müller zu suchen - Sie können diese Seiten überspringen.

Neben Indizes für numerische oder alphanumerische Werte, 
die leicht zu erstellen sind, 
ist eine andere Art von Indizes, 
die als räumliche Indizes bezeichnet werden, 
im Zusammenhang mit GIS von großer Bedeutung. 
Das Konzept ähnelt nicht-räumlichen Indizes und dient dem gleichen Zweck: 
Die Suche anhand einer korrekten Datenstruktur zu optimieren, 
in diesem Fall basierend auf seiner räumlichen Komponente.

Sehen wir uns ein anderes Beispiel an, 
um zu verstehen, wie ein räumlicher Index funktioniert. 
Angenommen, wir verwenden unsere Schicht mit Ländern und möchten diejenigen finden, 
die sich weniger als 2000 km von Deutschland entfernt befinden. 
Wie würden wir auf diese Anfrage antworten?

Eine naive Herangehensweise wäre, 
die Entfernung zwischen Spanien und allen anderen Ländern zu messen und 
dann jene in einer Entfernung von weniger als 2000 km auszuwählen. 
Wir würden das richtige Ergebnis erhalten, 
aber dieser Ansatz ist bei weitem nicht optimal.

Einen besseren Ansatz zu finden ist einfach. 
Zum Beispiel können wir mit ein wenig Wissen über die Weltgeographie alle Länder in Amerika sofort ausschließen. 
Wir können sicher sein, dass sie nicht Teil der Antwort sein werden, 
da die Entfernung zwischen Spanien und Amerika bereits größer als 2000 km ist. 
Wir kennen die Entfernung zwischen diesen Ländern und Spanien nicht, 
aber wir sind sicher, dass es mehr als 2000 km sind. 
Daher macht es keinen Sinn, die Entfernungen zu allen zu messen.

Dieses Wissen über die Weltgeographie, 
das es uns ermöglicht, 
die Anzahl der Länder zu reduzieren, 
ist eigentlich wie ein räumlicher Index. 
Es kann nicht verwendet werden, 
um auf die Abfrage zu antworten, 
aber es bietet eine Annäherung, 
die es einfacher macht, darauf zu antworten. 
Wir können eine große Anzahl von Ländern verwerfen und 
dann die komplexere Operation - die Messung - mit nur einer Teilmenge durchführen.

Dank räumlicher Indizes sind Abfragen effizienter und 
wir können mit größeren Datenmengen arbeiten.

Indizes - sowohl räumliche als auch nicht-räumliche - werden zusammen mit 
den Daten gespeichert, 
auf die sie sich beziehen. 
Die Speicherung erfolgt entweder in separaten Dateien oder 
in der Datenbank selbst. 
Spatial DBMS verfügen über integrierte Funktionen, 
um diese Indizes zu berechnen und zu speichern. 
Sobald sie berechnet wurden, 
werden sie immer dann verwendet, 
wenn das DBMS auf eine räumliche Abfrage reagieren muss.


[^1]: 
[^2]: 

*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute
*[DBMS]: Datenbankmanagementsystem
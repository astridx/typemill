# Beispiele für die räumliche Analyse

In den folgenden Abschnitten werden einige gebräuchliche Arten der 
räumlichen Analyse beschrieben.

## Räumliche Abfragen

Wir haben bereits Fragen in dem Kapitel über Datenbanken besprochen.

Abfragen können beispielsweise mit anderen Analysewerkzeugen kombiniert werden, 
um eine Teilmenge von Funktionen auszuwählen, 
mit denen wir später eine andere Analyse durchführen.

## Topologische Analyse

Abfragen können nicht nur auf die Position geografischer Elemente, 
sondern auch auf ihre Beziehung zu anderen Elementen bezogen werden. 
Wenn wir topologische Informationen haben, 
können wir Analysen durchführen, die auf folgende Fragen antworten:

- Wie erreiche ich eine Koordinate von meiner aktuellen Position aus über 
das bestehende Straßennetz?
- Welche Länder teilen eine Grenze mit Frankreich?

## Messung

Räumliche Eigenschaften können quantifiziert und gemessen werden. 
Zu den einfachsten gehören Länge, Fläche, Umfang oder Formfaktoren. 
Ausgereiftere wie Slope oder multiple Indizes aus Basismessungen 
können ebenfalls mit Hilfe von GIS berechnet werden.


## Kombination

Eine der typischsten Prozeduren innerhalb von GIS ist die Kombination 
und Überlagerung von Layern. 
Die Trennung geographischer Daten in Schichten erleichtert diese Art 
von Operationen und macht GIS zur optimalen Plattform für die Durchführung von Analysen, 
bei denen Informationen aus verschiedenen Variablen kombiniert werden müssen.

Im Falle von Vektorlayern werden Overlay-Operationen wie 
- Vereinigung, 
- Schnittpunkt, 
- Differenz oder 
- Clipping häufig verwendet. 

Abbildung 10.1 zeigt ein Beispiel für eine Überlagerungsoperation zwischen Polygon-Layern.

![Schnittpunkt zwischen zwei Polygon-Layern](../media/img/Intersection.png)
*Abbildung: Schnittpunkt zwischen zwei Polygon-Layern.*

## Transformationen

Wir fügen in diese Gruppe eine große Menge von Operationen ein, 
die die Eingabedaten auf verschiedene Arten verändern. 
Darunter finden wir 
- Koordinatentransformationen, 
- Vereinfachung von Geometrien oder 
- die Schaffung von Einflussbereichen (Puffern). 

Diese Transformationen können sowohl die räumliche Komponente als auch 
die thematische Komponente der Daten betreffen.

Ein spezieller Fall, 
der bereits in einem früheren Kapitel erwähnt wurde, 
ist die Konvertierung zwischen Repräsentationsmodellen. 

Abbildung 10.2 zeigt ein Beispiel. 
Ausgehend von einer gescannten Karte - einer Rasterebene - mit Konturlinien 
können diese nachverfolgt und anhand dieser einen Vektorebene erstellt werden. 
Die Linien in dieser Vektorschicht können später unter Verwendung von 
Interpolationstechniken in ein Raster-DEM konvertiert werden. 
Aus dem Raster-DEM ist es möglich, 
Konturlinien in einem beliebigen Konturabstand zu erhalten - 
natürlich innerhalb der Detailebene der Originaldaten.

![Konvertierung zwischen Darstellungsmodellen für eine Höhenebene](../media/img/Conversions.png)
*Abbildung: Konvertierung zwischen Darstellungsmodellen für eine Höhenebene*

## Geländeanalyse

Die Geländeanalyse ist eine der leistungsstärksten Funktionen, 
die wir in GIS finden. 
Von grundlegenden Parametern wie Steigung oder 
Aspekt bis hin zu hochspezifischen morphometrischen Parametern und 
dem Durchlaufen einer großen Sammlung von Werkzeugen für die hydrologische Analyse 
stehen in diesem Bereich eine Vielzahl von Analysefunktionen zur Verfügung.

## Beschreibende Statistik

Die gemeinsamen Elemente der klassischen Statistik haben ihre Entsprechung 
bei der Arbeit mit geografischen Daten und ermöglichen es uns, die Daten, 
mit denen wir arbeiten, 
quantitativ zu beschreiben. 
Hier enthalten wir Zentralität und Dispersion Maßnahmen, 
Musteranalyse und viele andere. 
Diese können selbst in Hypothesentests verwendet werden, 
falls eine räumliche Komponente beteiligt ist.

Diese statistischen Werte erlauben es uns, auf Fragen zu antworten wie:

- Ist die durchschnittliche Höhe ein konstanter Wert in einem bestimmten Land?
- Gibt es eine vorherrschende Bewegungsrichtung für Individuen einer bestimmten Spezies, 
oder bewegen sie sich unregelmäßig?

## Inferenz

Eine weitere wichtige statistische Analyse in GIS ist diejenige, 
die hilft, 
das Verhalten von Variablen und ihre Entwicklung abzuleiten.

Änderungsmodellierung ist eines der vielen Felder, 
die sich dank der Hilfe von GIS schnell entwickeln.

## Optimierung und Entscheidungsfindung

Die geschichtete Struktur von geographischen Informationen in einem GIS, 
die, wie wir gesehen haben, 
ideal für Overlay-Operationen war, 
bietet auch einen optimalen Rahmen für die Untersuchung der kombinierten Wirkung 
mehrerer Phänomene. 
GIS ist der perfekte Rahmen für die Analyse mehrerer Kriterien.

Fragen wie die folgenden können mit GIS beantwortet werden:

- Welches ist der beste Ort, um ein neues Kraftwerk zu bauen, 
wenn man seine Auswirkungen auf die Umwelt und die Menschen, 
die in der Nähe des Kraftwerks wohnen, berücksichtigt?
- Wo sollte ein Krankenhaus liegen, 
um den Bewohnern einer Region den bestmöglichen Service zu bieten?
# Geografische Informationsmodelle

Der Prozess der Umwandlung eines gegebenen geografischen Gebiets und der 
Informationen darüber in Daten, die innerhalb von GIS verwendet werden können, 
kann in drei verschiedene Phasen unterteilt werden.

- Etablierung eines geografischen Modells Das heißt, ein konzeptionelles Modell einer Realität und ihres Verhaltens.
- Erstellen eines Repräsentationsmodells Das heißt, eine Art, das konzeptionelle Modell zu kodieren und es auf eine endliche Menge von Elementen zu reduzieren.
- Erstellen eines Speichermodells Das heißt, eine Speicherstrategie zum Speichern der Elemente des Repräsentationsmodells.

Repräsentationsmodelle sind die wichtigsten und wir konzentrieren uns hier auf sie. 
Die zwei Hauptdarstellungsmodelle sind das Rastermodell und das Vektormodell. Ebenen, die diese Modelle verwenden, werden allgemein als Raster-Layer und Vektor-Layer bezeichnet.

## Rastermodell

Das Rastermodell basiert auf einer systematischen Raumaufteilung. Der gesamte Raum ist durch eine Reihe von Elementen charakterisiert, die ihn jeweils mit einem assoziierten Wert abdecken.

Das gebräuchlichste Rastermodell basiert auf einem Gitter aus quadratischen oder manchmal rechteckigen Zellen. Wenn man die Ausrichtung des Gitters, die Größe der Zellen (die für alle gleich ist) und zumindest die Koordinaten eines Gitters kennt, kann man dank seiner regelmäßigen Struktur die Position aller Zellen erkennen. Damit sind die Werte der Variablen, mit der wir arbeiten, in allen Punkten des von der Ebene abgedeckten Bereichs bekannt. Die Zellengröße ist ein Parameter, der sich auf die Skalierung der Ebene bezieht, da sie ihre Auflösung definiert und von der Detailebene abhängt, die bei der Ausführung der entsprechenden Maßnahmen verwendet wurde.

Die nächste Abbildung zeigt ein Beispiel für ein Raster.

![Zellen in einem Raster mit den zugehörigen Werten](../media/img/Raster_closeup.png)
*Abbildung: Zellen in einem Raster mit den zugehörigen Werten.*

Die Anzahl der für jede Zelle gespeicherten Werte definiert die Anzahl der Bänder in einer Raster-Ebene. Ein Band enthält einen einzelnen Wert für jede Zelle. Wir können eine Raster-Ebene mit mehreren Bändern als eine Gruppe von Unterschichten verstehen, die alle die gleiche räumliche Struktur (Ausdehnung und Zellengröße) aufweisen und als einzelne Ebene umschlossen sind.

Ein deutliches Beispiel dafür finden wir in digitalen Farbbildern. Ein digitales Bild besteht aus einem Raster von Werten (Pixel genannt), die jeweils eine Farbe haben. Im häufigsten Fall wird diese Farbe mit drei Werten ausgedrückt, die der Intensität der Farben Rot, Grün und Blau entsprechen, die zusammen die Pixelfarbe ergeben. Das heißt, ein Bild wie dieses ist eine Raster-Ebene mit drei Bändern, von denen jedes eine der roten, grünen und blauen Komponenten enthält.

Eine weitere typische Verwendung des Rastermodells ist für die sogenannten Digital Elevation Models (DEM), die die Topographie eines bestimmten Bereichs enthalten. Dies sind immer Single-Band-Layer.

In den meisten Fällen sind die Werte einer Rasterebene numerisch, und GIS-Software ist normalerweise nicht dafür geeignet, andere Arten von Werten in der thematischen Komponente einer Rasterebene zu verarbeiten. Aus diesem Grund können Raster-Layer als Matrizen angesehen werden, und die entsprechenden mathematischen Werkzeuge können für ihre Analyse verwendet werden.

## Vektor-Modell

Das andere Hauptdarstellungsmodell ist das Vektormodell. In diesem Modell gibt es keine grundlegenden Einheiten, die den modellierten Bereich teilen und überdecken. Stattdessen werden die Variabilität und Merkmale dieses Bereichs mithilfe von Merkmalen modelliert, die Elemente darstellen, in denen sich diese Merkmale nicht ändern. Der geografische Teil eines Features besteht aus geometrischen Primitiven, die aus drei verschiedenen Typen bestehen können: Punkte, Linien und Polygone (Abbildung).

![Geometrische Grundelemente im Vektordarstellungsmodell und einige Beispiele für jeden von ihnen und ihre zugehörigen Attribute](../media/img/Primitives.png)
*Abbildung: Geometrische Grundelemente im Vektordarstellungsmodell und einige Beispiele für jeden von ihnen und ihre zugehörigen Attribute.*

Unter Verwendung von Punkten, Linien und Polygonen kann der geographische Raum durch Assoziieren von Werten mit diesen Grundelementen modelliert werden. Ein Feature kann mehrere Primitive haben. Zum Beispiel benötigt ein Land wie die Vereinigten Staaten in einer Schicht, die Länder enthält, mehrere Polygone (kontinentale US-, Alaska-, Hawaii-Inseln usw.). All diese Polygone bilden ein einziges Merkmal, da sie alle demselben Land angehören und die gleichen zugeordneten Werte aufweisen.

Ein Layer kann Features mit unterschiedlichen Grundtypen enthalten, ist aber normalerweise auf nur einen Typ beschränkt. Es ist üblich, von einer "Punkteebene" oder einer "Polygonenebene" zu sprechen, um dies anzuzeigen.

Elemente können unter Verwendung verschiedener Arten von Grundelementen dargestellt werden. Zum Beispiel kann eine Stadt als ein einzelner Punkt oder als ein Polygon mit seinem Umfang dargestellt werden. Die Verwendung der einen oder anderen Geometrie sollte unter anderem von der Art des Phänomens abhängen, das wir modellieren möchten, oder von der Detailtiefe, die benötigt wird.

Die thematische Komponente im Vektormodell wird über Attribute definiert. Eine Ebene enthält normalerweise mehrere Attribute. Attribute sind Features zugeordnet, können Informationen aller Art enthalten und sind vielseitiger als die Werte, die Raster-Layern zugeordnet sind, die normalerweise nur numerische Werte enthalten. Aufgrund seiner besonderen Struktur (eine Menge von Attributen, die einem Merkmal zugeordnet sind) kann die thematische Komponente im Vektormodell als Tabelle dargestellt und in einer Datenbank gespeichert werden (wir werden mehr darüber in dem Kapitel über Datenbanken sprechen). Außerdem kann es unabhängig von der räumlichen Komponente analysiert werden.

Ein bestimmtes Element des Vektordarstellungsmodells ist die Topologie. Eine Vektorschicht soll Topologie enthalten, wenn sie die räumlichen Beziehungen zwischen ihren Merkmalen enthält. Topologie ist für bestimmte Analysen erforderlich und ändert die Art und Weise, in der einige Operationen, z. B. die Geometriebearbeitung, in GIS ausgeführt werden.

![Ein Straßenlayer ohne Topologie (a) und mit Topologie (b). Kreise in diesem letzten Fall zeigen Verbindungen zwischen Straßen an](../media/img/Topology_roads.png)
*Abbildung: Ein Straßenlayer ohne Topologie (a) und mit Topologie (b). Kreise in diesem letzten Fall zeigen Verbindungen zwischen Straßen an.*

Obwohl die meisten Vektor-Layer-Operationen ohne Topologie durchgeführt werden können, sind einige von ihnen wie Netzwerkanalyse ohne sie nicht möglich. Wenn wir über eine Straßenschicht nachdenken, wenn sie nur Linien enthält, die Straßen darstellen, aber keine Informationen darüber, wie sie miteinander verbunden sind, gibt es keine Möglichkeit, das Netzwerk aus ihnen aufzubauen. Die Punkte, an denen sich Linien kreuzen, können Kreuzungen oder Kreisverkehre sein (so ist es möglich, von einer Straße zur anderen zu wechseln), aber sie können auch Punkte ohne Verbindung zwischen den Straßen sein (eine über der anderen). Ohne das zu wissen, fehlen uns Informationen und die Netzwerkanalyse kann nicht durchgeführt werden. (Abbildung)

Liniendaten ohne Topologie werden im Volksmund als Spaghetti-Daten bezeichnet.

## Ein Vergleich der unterschiedlichen Modelle: Raster versus Vektor

Sowohl die Raster- als auch die Vektordarstellungsmodelle können zum Speichern 
jeglicher geografischer Informationen verwendet werden. Die mächste Abbildung 
enthält ein Beispiel dafür. Sie zeigt eine Straßenebene, die mit beiden Modellen 
dargestellt wird.

Wir haben DEMs als typischen Fall von Raster-Layern erwähnt. Die Darstellung von Elevation als Rasterebene hat viele Vorteile, insbesondere für die Durchführung von Analysen, ist aber nicht die einzige Option. Wir können eine Vektorebene mit Punkten haben (dies ist der Fall, wenn die Höhendaten für eine topographische Vermessung verwendet werden) oder eine Linienebene mit Höhenlinien (die häufigste Art, Höhen in einer traditionellen Karte darzustellen).

![Vergleich zwischen Repräsentationsmodellen für Vektor (a) und Raster (b)](../media/img/Representation_models.png)
*Abbildung: Vergleich zwischen Repräsentationsmodellen für Vektor (a) und Raster (b).*

Es ist klar, dass beide Modelle viele Unterschiede haben und jedes von ihnen hat Vor- und Nachteile. Im Folgenden sind einige Faktoren zu vergleichen.

- Ansatz. Das Rastermodell konzentriert sich auf die Eigenschaften des dargestellten Raumes (was und wie), während das Vektormodell auf den Ort dieser Eigenschaft (wo) fokussiert.
- Richtigkeit. Raster-Modell hat seine Präzision durch die Zellengröße begrenzt. Obwohl dies so klein sein kann, wie wir es wünschen, würde dies zu sehr großen Datenmengen führen. Merkmale, die kleiner als diese Größe sind, können nicht dargestellt werden, und es wird angenommen, dass innerhalb einer Zelle keine Variabilität besteht.  
Außerdem sind Formen auf gerade Winkel beschränkt, da die Basiseinheit für das Rastergitter, wie wir gesehen haben, ein Quadrat oder ein Rechteck ist (Abbildung)
![Einschränkungen des Rasterdarstellungsmodells Da der Raum in quadratische Einheiten unterteilt ist, können Elemente wie Kurven nicht getreu dargestellt werden](../media/img/Raster_accuracy.png)
*Abbildung: Einschränkungen des Rasterdarstellungsmodells Da der Raum in quadratische Einheiten unterteilt ist, können Elemente wie Kurven nicht getreu dargestellt werden.*
- Komplexität. Analysealgorithmen, insbesondere solche, bei denen mehrere Schichten verwendet und kombiniert werden, sind in der Regel aufgrund ihrer Regelmäßigkeit und Systematik einfacher und einfacher mit Rasterlayern zu implementieren. Das Arbeiten mit Vektorebenen, die keine Regelmäßigkeit aufweisen, ist vom algorithmischen Standpunkt aus gesehen komplexer.

Insgesamt gibt es kein besseres Repräsentationsmodell als das andere. Je nach Fall wird einer geeigneter sein als der andere. Die folgenden Faktoren sollten bei der Beurteilung der Eignung dieser Modelle für einen bestimmten Umstand berücksichtigt werden:

- Typ der zu repräsentierenden Variablen oder Erscheinung. Im Allgemeinen ist es besser, Raster-Layer für kontinuierliche Variablen wie Elevation zu verwenden, um die Analyse basierend darauf zu erleichtern. Diskrete Variablen werden dagegen mit einem Vektoransatz besser dargestellt.
- Schichtzweck. Es ist wichtig zu wissen, wie wir eine Ebene verwenden wollen, um das Repräsentationsmodell zu bestimmen, das unserem Fall besser entspricht. Wenn wir beispielsweise Höhendaten haben und planen, eine Analyse durchzuführen, ist es besser, ein Raster-DEM zu haben, da die meisten Algorithmen verlangen, dass die Höhendaten eine Rasterebene sind. Wenn wir diese Höhendaten jedoch nur zur Visualisierung verwenden und sie mit anderen Layern kombinieren möchten, um eine Karte zu erstellen, ist es möglicherweise besser, eine Vektorebene mit Konturlinien zu verwenden, da diese eine bessere kartografische Lösung darstellen und weniger störend wirken die restlichen Variablen.
- Kontext. Der Kontext könnte es besser (oder sogar obligatorisch) machen, mit einem gegebenen Repräsentationsmodell zu arbeiten. Wenn wir zum Beispiel mit Bildern arbeiten und planen, auch mit anderen Ebenen etwas zu analysieren, sollten dies Raster-Ebenen sein, da Bilder, wie wir gesehen haben, immer Raster-Ebenen sind.

Es gibt Algorithmen, die die Konvertierung zwischen den Raster- und Vektordarstellungsmodellen ermöglichen. Wenn wir also unsere Daten in einem von ihnen haben, können wir eine neue Ebene erhalten, die das andere Modell verwendet und für unsere Arbeit besser geeignet ist.
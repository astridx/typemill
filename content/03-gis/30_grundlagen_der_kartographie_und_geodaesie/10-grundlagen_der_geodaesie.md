# Grundlegende Konzepte der Geodäsie

Alle georeferenzierten Informationen habe eine gemeinsame Eigenschaft: 
Alle georeferenzierten Informationen können einem 
Ort auf der Erde zugeordnet werden. Dieser Ort wird mit Koordinaten angegeben. Um die Koordinaten 
koorekt interpretierne zu können, ist ein *Bezugssystem* erforderlich.

Was ist Geodäsie[^1]? Geodäsie kennt man in Deutschland auch unter dem Namen *Vermessungskunde*. 
Geodäsie ist die Wissenschaft, die den theoretischen Rahmen 
für ein Bezugssystem liefert. Einfach ausgedrückt untersucht die Geodäsie die Form der Erde.

> Geodäsie ist die Wissenschaft von der Ausmessung und Abbildung der Erdoberfläche.
>
> -- Friedrich Robert Helmert[^2]; (1843–1917, deutscher Geodät, Begründer der theoretischen Geodäsie)

Die Geodäsie bietet durch ihre verschiedenen Zweige Methoden und Konzepte, die es ermöglichen, 
Koordinaten zu definieren und zu verwenden, um Elemente und 
Phänomene auf der Erde zu lokalisieren.

Geodäsie wird benötigt, weil die Erde nicht flach ist 
und wenn die untersuchte Fläche groß genug ist, kann der Effekt der Erdkrümmung nicht 
ignoriert werden. 
Aus diesem Grund implementieren GIS die erforderlichen Elemente zur 
Verwaltung geographischer Informationen unter Berücksichtigung der 
Ideen und Prinzipien der Geodäsie.

Ein Hauptzweck der Geodäsie besteht darin, 
ein Bezugssystem zu erstellen und eine Reihe von Punkten 
(bekannt als geodätische Scheitelpunkte) zu definieren, 
deren Position mit hoher Genauigkeit bekannt ist. 
Basierend auf diesen Punkten, die ein geodätisches Netzwerk bilden, 
können Koordinaten für jeden Punkt auf der Erdoberfläche berechnet werden.

## Referenzflächen

todo http://kartenkunde-leichtgemacht.de/handbuch.php?page=Kartenerstellung 

Um Koordinaten für jeden Punkt auf der Erdoberfläche berechne zu können, 
definiert die Geodäsie zwei grundlegende Referenzflächen: *Referenzellipsoid[^3]* und *Geoid[^4]*.

> Ein *Ellipsoid* ist die 3-dimensionale Entsprechung einer Ellipse.
> Ein *Referenzellipsoid* ist ein an den Polen abgeplattetes Ellipsoid
> Das *Geoid* ist ein physikalisches Modell der Erdfigur

Die Erde hat eine kugelförmige Form. Es ist jedoch keine perfekte Kugel, 
sondern ein sogenanntes *Ellipsoid[^5]*. In einem Ellipsoid ist der Radius nicht 
konstant. Der Radius hängt von der Position relativ zur Oberfläche ab. 
Mit einem Ellipsoid kann die Form der Erde genauer nachbildet werden, als mit einer Kugel. 
Und diese genauere Nachbildung ist notwendig, um Karten genau erstellen zu können.
Insbesondere dann, wenn mit einem kleinen Maßstab gearbeite wird. Also, wenn ein großes Gebiet 
der Erde auf einem kleinen Papierabschnitt abgebildet wird.

> Je nach dem Inhaltsreichtum und dem Detaillierungsgrad der Karten werden große Maßstäbe, mittlere Maßstäbe und kleine Maßstäbe unterschieden. Die Adjektive „groß“ und „klein“ beziehen sich auf die Größe eines Objektes auf der Karte und nicht auf die Maßstabszahl. Diese Begriffe werden gerne verwechselt, wenn der Unterschied von Maßstab und Maßstabszahl nicht beachtet wird. Bei einer Karte in großem Maßstab ist die Maßstabszahl daher klein und umgekehrt. Eine Karte 1:25.000 ist zum Beispiel großmaßstäbiger (der Inhalt also größer bzw. detaillierter dargestellt) als eine Karte 1:100.000.
>
> -- Wikipedia[^6]

Das Ellipsoid liefert einen theoretischen Ausdruck der Erdform und der 
nächste Schritt besteht darin, die Parameter zu bestimmen, die es definieren. 
Im Fall einer Kugel ist der einzige benötigte Parameter der Radius. 
Im Fall eines Ellipsoids müssen zwei Parameter bestimmt werden: 
Die Länge der halben Hauptachse und die kleine Halbachse.

> Die **halben Hauptachse** ist die Hälfte der längsten möglichen Entfernung von 
> einer Seite der Ellipse zur anderen - durch die Ellipse in Längsrichtung.
>
> Die **kleinen Halbachse** ist die die Hälfte der kürzesten Entfernung 
> von einer Seite der Ellipse zur anderen.

Aus historischen Gründen existieren viele Ellipsoide. 
Alle stammen aus verschiedenen Zeiten und Orten. 
Die ersten allgemeinen Ellipsoide, die für die Darstellung eines beliebigen Ortes 
auf der Erdoberfläche verwendet werden können, 
erschienen vor etwa hundert Jahren. Sie sollten als als internationale Referenz dienen. 
Mit Hilfe dieser internationalen Referenzen konnten nun Landkarten für jedes Gebiet 
unseres Planeten erstellt werden. 
Das *WGS-84-Ellipsoid[^7]* ist derzeit eines der beliebtesten und wird vom 
GPS - Positionierungssystem verwendet.

Die andere nenneswerte Bezugsfläche ist das *Geoid[^8]*. 
Das Geoid ist als die dreidimensionale Fläche definiert, 
bei der jeder Punkt die gleiche Anziehungskraft hat. 
Ein Geoid ist ein physikalisches Modell der Erdfigur.
Es stellt die Fläche der Erde dar und wählt dazu die mittlere Höhe über Meer. 
Durch die unterschiedliche Massenverteilung auf der Erde bekommt das Geoid im 
Erdmantel Beulen und Dellen. 


Wie bei den Ellipsoiden gibt es auch mehrere Geoiden. 
Diese sind nicht konstant und entwickeln sich, um sich an die Veränderungen anzupassen, 
die auf der Erdoberfläche stattfinden.

Die nächste Abbildung zeigt einen Vergleich der drei Oberflächen: 
Erdoberfläche, Geoid und Ellipsoid.

![Vergleich der drei Grundflächen: Erdoberfläche, Geoid und Ellipsoid (nach Wikipedia)](../media/img/Three_surfaces.png)

*Abbildung: Vergleich der drei Grundflächen: Erdoberfläche, Geoid und Ellipsoid (nach Wikipedia).*

In einem allgemeinen Ellipsoid stimmen sowohl der Schwerpunkt als auch die 
Äquatorebene mit denen der Erde überein. In einem lokalen Ellipsoid muss dies nicht so sein, 
und das Ellipsoid alleine reicht nicht aus, da wir nicht wissen, wie wir es relativ 
zur realen Erdoberfläche platzieren sollen.

Das Konzept des Datums löst dieses Problem. 
Ein Bezugspunkt ist die Kombination einer Bezugsoberfläche (das Ellipsoid) 
und eines Punktes, an dem es mit dem Geoid verbunden ist. 
Dieser Punkt wird als fundamentaler Punkt bezeichnet, und das Ellipsoid ist dort 
tangential zum Geoid. 
Am fundamentalen Punkt ist eine Linie senkrecht zum Geoid identisch mit einer 
Linie senkrecht zum Ellipsoid.

## Koordinatenreferenzsysteme

Sobald wir ein Modell haben, um die Form der Erde zu definieren, 
können wir ein System einrichten, um jede Position über seiner Oberfläche 
zu kodieren und ihr eine entsprechende Koordinate zuzuweisen. 
Die Kombination eines Koordinatensystems und eines Datums wird als 
Koordinatenreferenzsystem (CRS) bezeichnet.

In Bezug auf das Koordinatensystem haben wir zwei Hauptalternativen: Verwenden der Elemente der sphärischen Geometrie unter Verwendung der Konzepte der Ebenengeometrie. In letzterem benötigen wir ein Projektionssystem, um die Elemente auf der Oberfläche des Ellipsoids in eine Ebene zu bringen.

Geographische Koordinaten verwenden ein sphärisches Koordinatensystem, in dem die Position jedes Punktes durch zwei Winkelwerte definiert ist: Längen- und Breitengrad. Linien gleicher Breite werden Parallelen genannt, während Linien gleicher Länge Meridiane genannt werden.

Geographische Koordinaten sind von großem Nutzen, besonders wenn man mit großen Regionen arbeitet. Es ist jedoch kein kartesisches System, und es ist schwierig, Aufgaben wie das Messen von Entfernungen oder von Bereichen auszuführen. Um Operationen wie diese zu vereinfachen, benötigen wir kartesische Koordinaten. Um jedem Punkt auf der Erdoberfläche (der keine Ebene ist) eine Ebenenkoordinate zuzuordnen, müssen wir eine kartographische Projektion verwenden.

Die Erdoberfläche ist nicht entwickelbar. Das heißt, es kann nicht ohne Verzerrung abgeflacht werden. Aus diesem Grund brauchen wir eine Methode, um Punkte auf dieser Oberfläche in Punkte auf einer Ebene umzuwandeln. Abbildung 5.2 zeigt diese Idee.

![Grafische Darstellung einer Projektion. Die Punkte A, B und C auf der Oberfläche des Ellipsoids werden in ihre äquivalenten Punkte a, b und c auf einer Ebene umgewandelt](../media/img/Projection.png)

*Abbildung: Grafische Darstellung einer Projektion. Die Punkte A, B und C auf der Oberfläche des Ellipsoids werden in ihre äquivalenten Punkte a, b und c auf einer Ebene umgewandelt.*

In dem in der Figur dargestellten Fall werden Punkte direkt auf die Ebene projiziert. Eine andere Alternative besteht darin, sie auf eine Oberfläche zu projizieren, die anders als die Oberfläche, die durch eine Kugel oder ein Ellipsoid definiert ist, entwickelt werden kann (das heißt, sie kann später ohne Verzerrung abgeflacht werden). Die üblichsten Oberflächen dafür sind der Zylinder und der Kegel. Die entsprechenden Vorsprünge werden als konische Vorsprünge und zylindrische Vorsprünge bezeichnet.

Es kann in der Figur gesehen werden, dass Projektionspunkte Verzerrungen einführen. Zum Beispiel ist der Abstand zwischen den Punkten A und B nicht derselbe wie der Abstand zwischen den Punkten a und b. Alle Projektionen führen unabhängig von ihren Eigenschaften zu einer gewissen Verzerrung. Abhängig von den metrischen Eigenschaften, die unverzerrt beibehalten werden, haben wir Flächenprojektionen (die die Fläche erhalten), konform (Winkel und Formen beibehalten) oder äquidistant (Abstände beibehalten).

Je nach Kontext und Zweck unserer Daten können wir die eine oder andere Art der Projektion verwenden.

Eine der am weitesten verbreiteten Projektionen ist heutzutage der Universal Transverse Mercator, der die Grundlage für das UTM-Koordinatensystem bildet. Dieses System ist nicht nur eine Projektion, sondern ein komplettes System von vielen. Die Erdoberfläche ist in rechteckige Bereiche unterteilt, und für jede von ihnen wird eine andere Projektion und ein anderer Satz geodätischer Parameter verwendet. Es verwendet ein einzelnes Ellipsoid: WGS-84.

Im UTM-System werden Koordinaten nicht als absolute Koordinaten ausgedrückt, sondern sie werden als entsprechende Koordinaten in das entsprechende Rechteck referenziert.

Das UTM-Gitter enthält 60 Zonen mit jeweils 6 ° Länge. Zone 1 ist zwischen 180 ° und 174 ° West lokalisiert, und die Nummerierung nimmt nach Osten zu.

Jede Zone ist in 20 Breitengrade unterteilt, die von 80 ° Süd bis 84 ° Nord reichen. Diese sind mit Buchstaben von C bis X codiert, ausgenommen I und O aufgrund ihrer Ähnlichkeit mit den Ziffern eins und null. Jede Band hat 8 ° in der Höhe, mit Ausnahme der X-Band, die 12 hat.

Ein UTM-Rechteck wird daher durch eine Zahl und einen Buchstaben definiert, und die Koordinaten, die zur Lokalisierung eines bestimmten Punktes auf der Erdoberfläche verwendet werden, beziehen sich auf die Zone, zu der es gehört. Koordinaten werden in Metern ausgedrückt und stellen die Entfernung zwischen dem Punkt und dem Ursprung des UTM-Rechtecks ​​dar. Der Ursprung befindet sich am Schnittpunkt zwischen dem Meridian, der durch das Zentrum der Zone verläuft, und dem Äquator.

Um negative Zahlen zu vermeiden, wird angenommen, dass der Ursprung eine X-Koordinate von 500000 Metern und eine Y-Koordinate von 10000000 Metern aufweist, so dass alle Koordinaten, auf die Bezug genommen wird, nur positive Werte haben.

## Koordinatenkonvertierung und -transformation

Es ist üblich, bei der Arbeit mit GIS Schichten in mehreren verschiedenen Koordinatensystemen oder im selben Koordinatensystem zu verwenden, jedoch unterschiedliche Parameter (z. B. ein anderes Datum) zu verwenden. Um diese Schichten zusammen verwenden zu können, müssen wir in einem Koordinatensystem arbeiten, und zumindest einige dieser Schichten müssen in dieses Koordinatensystem konvertiert werden. Das ist bekannt als Koordinatenumwandlung. Wenn das Ursprungs- und das Zielkoordinatensystem ein anderes Datum haben, wird die Koordinatenumwandlung Koordinatentransformation genannt.

In einem GIS können mithilfe von Konvertierungs- und Transformationsfunktionen neue Layer generiert werden, die ein anderes CRS verwenden. GIS bietet auch die Möglichkeit, sie beim Rendern von Layern direkt auszuführen, sodass wir eine Karte mit Layern erstellen können, die nicht dasselbe CRS verwenden. Diese werden auf der Karte korrekt dargestellt und "stimmen" miteinander überein, da das GIS automatisch die entsprechenden Änderungen an ihren Koordinaten vornimmt, um sie in einem gemeinsamen CRS zu haben.

Um die Verwendung von Koordinatenreferenzsystemen zu erleichtern, gibt es Initiativen, die sie organisieren und codieren, so dass jedes System leicht durch einen eindeutigen Code identifiziert werden kann (der als SRID (Spatial Reference System Identifier) ​​bezeichnet wird). Das gebräuchlichste Kodierungssystem ist das von der European Petroleum Survey Group (EPSG) geschaffene.


[^1]: https://de.wikipedia.org/wiki/Geod%C3%A4sie
[^2]: https://de.wikipedia.org/wiki/Friedrich_Robert_Helmert
[^3]: https://de.wikipedia.org/wiki/Referenzellipsoid
[^4]: https://de.wikipedia.org/wiki/Geoid
[^5]: https://de.wikipedia.org/wiki/Ellipsoid
[^6]: https://de.wikipedia.org/w/index.php?title=Ma%C3%9Fstab_(Kartografie)&oldid=177646260#Gro%C3%9Fe_und_kleine_Ma%C3%9Fst%C3%A4be
[^7]: https://de.wikipedia.org/wiki/World_Geodetic_System_198
[^8]: https://de.wikipedia.org/w/index.php?title=Geoid&oldid=177470783

*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GPS]: Global Positioning System
*[WGS-84-Ellipsoid] World Geodetic System 1984


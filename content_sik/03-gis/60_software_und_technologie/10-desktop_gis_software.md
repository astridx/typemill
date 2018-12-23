# Geografische Informationssysteme - Desktop Software 

Mithilfe von Desktop GIS Anwendunge können Sie 
geografische Daten bearbeiten. 

Allgemein unterscheiden wir fünf grundlegende Funktionalitäten: 
- Dateneingabe und -ausgabe, 
- Visualisierung, 
- Bearbeitung, 
- Analyse und 
- Kartendesign.  

Die meisten Desktop-GIS-Tools verfügen über diese fünf Funktionen - wenn 
auch in unterschiedlicher Art und Weise. 
Beispielsweise sind einige Tools besser für die Datenbearbeitung 
vorbereitet, während andere sich auf die Analyse konzentrieren.

## Dateneingabe und -ausgabe

Ein Desktop-GIS muss in der Lage sein, Daten zu lesen und optional 
zu speichern. Ein Speichern wird nur dann benötigt, 
wenn das GIS neue Daten erzeugen kann - also eine Analyse- oder 
Editierfunktion bietet.

Es gibt eine schier unzählige Anzahl von Formaten in den 
geografische Daten gespeichert werden. 
Die meisten GIS verwenden Bibliotheken, 
um diese Formate lesen und schreiben zu können. 
So sind die Daten untereinander austauschbar.

Neben dem Lesen von Datendateien ist es heutzutage wichtig, 
eine Verbindung zu Datenbanken und anderen entfernten Diensten 
oder Remote Services herstellen zu können.

> Remote Service ist ein Verfahren, über das technische Dienstleistungen 
mit Hilfe von Telekommunikationsnetzwerken an einem entfernten Ort erbracht 
werden[^4]. 

todo link Wir werden über die später in diesem Kapitel sprechen.

## Visualisierung

Daten zu visualisieren ist eine wichtige Aufgabe von GIS. 
Der Hauptzweck der Verwendung von GIS ist die Erstellung von 
Landkarten. 
Aber auch bei der Datenbearbeitung oder -analyse, spielt die 
Visualisierung eine große Rolle.

Vereinfacht ausgedrückt werden alle Daten auf einem Canvas-Element[^1] 
dargestellt. Meist geschieht dies mithilfe von verschiedenen Ebenen. 
Der Benutzer kann Ebenen hinzufügen oder entfernen und auch Symbole ändern. 
Insbesonder kann er die Art und Weise, in der die Daten 
in grafische Elemente umgewandelt werden, beeinflussen. Wenn er eine Karte für 
Radfahrer anbieten möchte, dann kann er Waldwege mehr hervorheben. Möchte er 
eine Karte für Autofahrer erstellen, dann wir er Waldwege vielleicht gar nicht 
anzeigen.
Die Ebenen werden in einer bestimmten Reihenfolge gezeichnet. 
Sie entsteht eine Art Hierarchie. Die unteren Ebenen werden von den 
darüber liegenden Ebenen überdeckt.

> Das englische Wort Canvas[^1] bedeutet auf deutsch "Leinwand" und ist 
ziemlich genau das: Eine Leinwand, auf die man zeichnen kann. 
Im Kontext von GIS werden Daten nicht einfach dargestellt oder gezeichnet - 
sie werden gerendert[^2]. 
Für eine Ebenen wird in der Regel der englische Begriff Layer[^3] verwendet.

Neben der Canvas-Element, also der Arbeitsfläche, gibt es 
Navigationswerkzeuge, mit denen der Benutzer den angezeigten 
Bereich durch Vergrößern, Verkleinern oder Verschieben ändern kann 
(Abbildung 8.1).

![Navigationswerkzeuge, die in einem Desktop-GIS üblich sind. a) herauszoomen, b) hineinzoomen und c) schwenken](../media/img/Navigation_tools.png)
*Abbildung 8.1: Navigationswerkzeuge, die in einem Desktop-GIS üblich sind. a) herauszoomen, b) hineinzoomen und c) schwenken.*

Anders als bei einer klassischen gedruckten Karte, 
kann der Benutzer eines GIS auswählen, 
was er sieht und wie er es sieht. Auch wenn er die 
geografischen Informationen nicht ändern kann.
Eine Linie mit dem Attribut *highway=motorway[^5]* kann er entweder für eine 
Straßenkarte rot als Autobahn hervorheben oder trägt sie 
unscheinbar in eine Wanderkarte ein. Hier soll sie nur zur Orientierung dienen 

> WICHTIG: Geografische Daten sind unabhängig von den Informationen, 
die zur Visualisierung erforderlich sind, 
und können daher auf verschiedene Arten dargestellt werden.

Dies gilt auch für Daten bei denen schon eine Darstellungsform gibt -  
zum Beispiel Bilder. Aber selbst bei Bildern kann das Rendering vom Benutzer 
angepasst und modifiziert werden.

Obwohl ein Canvas normalerweise zweidimensional ist, 
können bestimmte GIS auch dreidimensionale Darstellungen wiedergegeben werden. 
In diesem Fall sind Navigationstools komplexer und ermöglichen unter 
anderem die Anpassung von 
- Perspektiven[^6], 
- Sichtwinkeln und/oder 
- vertikaler Überhöhung.

## Bearbeitung

Die geografischen Daten, mit denen wir in GIS arbeiten, sind nicht statisch. 
Informationen, die in einem Layer enthalten sind, müssen möglicherweise geändert 
oder korrigiert werden. Das ein Benutzer Daten bearbeiten kann ist wichtig, 
wenn das GIS-Tool vielseitig und flexibel sein soll. 
Ohne sie verlieren geografische Daten einen Teil ihres Potenzials. 
Aus diesem Grund bieten die meisten Desktop-GIS-Tools eine Menge Bearbeitungsmöglichkeiten.

Diese Funktionen können verwendet werden, um neue Layer zu erstellen oder 
vorhandene zu aktualisieren. 
Im Folgenden sind einige Bearbeitungsaufgaben aufgeführt, 
die mit GIS durchgeführt werden können:

- Bearbeiten der Geometrien eines Vektorlayer-Features
- Bearbeiten der Attributwerte eines Vektorlayer-Features, 
einschließlich Bearbeiten der Liste der Attribute des Layers, 
Hinzufügen oder Entfernen von ihnen.
- Neue Funktionen zu einer Vektorebene hinzufügen oder vorhandene entfernen.
- Bearbeiten von Zellenwerten in einer Rasterebene

Werkzeuge, die zum Bearbeiten von Geometrien verwendet werden, 
müssen nicht in jedem Fall das Rad neu erfinden. Sie können eine Menge 
Funktionalitäten von CAD[^7]-Software übernehmen. 
In bestimmten Fällen werden sie um neue Funktionalitäten erweitert, 
wie dies bei der Bearbeitung geographischer Daten mit Topologie[^8] der Fall ist.
 
> Die Topologie ist wörtlich übersetzt *die Lehre vom Ort* und handelt von der 
Form und gegenseitigen Lage geometrischer Objekte, wie Punkte, 
Kurven und Flächen.
Sehr anschauliche und kurzweilige Erkäuterungen zum Begriff Topologie 
bietet die Website der Uni Stuttgart[^9]. 
CAD[^7]-Software berücksichtigt keine Topologie[^8].

## Analyse

Die Analyse ist seit ihrer Entstehung eine grundlegende Funktion von GIS. 
Andere Funktionen waren in den frühen Tagen sehr begrenzt. Zum Beispiel 
die Visualisierung die uns heute oft als die wichtigste erscheint, weil sie sofort 
ins Auge springt.
Die Analyse war jedoch schon immer der Kern von GIS und mit ihr hat alles begonnen.

Der aktuelle Trend bei GIS besteht darin, 
Analysefunktionen als modulare Tools zu betrachten. 
Diese Tools werden auf einer Art Basisplattform ausgeführt und nutzen 
die die Dateneingabe- und -ausgabefunktionen zusammen mit der 
Visualisierungskomponente. 
Die einzelnen Analysewerkzeuge sind unabhängig, 
können jedoch zusammen verwendet werden, 
um komplexere Analysen zu erstellen.

Analysewerkzeuge können vollständig unabhängig von der 
Visualisierungskomponente sein -  
sie können aber auch mit ihr verknüpft sein. 
Im ersten Fall wird die Analyse an einer Menge von 
Schichten und Parametern ohne jegliche Interaktion mit der Karte durchgeführt.
Im zweiten Fall kann der Benutzer mit der Ansicht interagieren, 
um zu definieren, wie die Analyse durchgeführt wird.
Er kann beispielsweise eine Koordinate oder eine Region in der Zeichenfläche auswählen, 
die dann als Parameter für das Analysetool verwendet wird.

Das Ergebnis eines Analyse-Tools in GIS kann geographisch (eine neue Ebene) sein 
oder nicht. 
Eine geographische Ausgabe des Analyse-Tools könnte ein neue Layer mit Daten sein. 
Ein nicht geografische Ausgeabe kann man sich als einen einfachen Wert, 
der sich aus einer statistischen Analyse der Eingabedaten ergibt, vorstellen.

Analysetools können in Workflows organisiert werden, 
die Analyse-Routinen unterstützen. 
Darüber hinaus kann die Analysefunktionalität von Desktop-GIS in der Regel 
aus Skriptsprachen verwendet werden, die die Definition komplexerer Modelle 
und Datenflüsse ermöglichen. 
Dies ist eine der Hauptstärken aktueller GIS-Tools, da sie dem Benutzer 
mehr Leistung und Flexibilität bietet.

## Kartengestaltung

Die meisten Desktop-GIS sind in der Lage, 
kartographische Dokumente zu erstellen, 
die später gedruckt und als klassische Papierkarte verwendet werden können. 
Diese Karten oder Dokumente werden im GIS aus den Daten zusammengesetzt 
und verwenden dieselbe Funktionalität, die für das 
On-Screen-Rendering (Symbologie usw.) verwendet wird.

Darüber hinaus ermöglichen andere Werkzeuge dem Benutzer das 
Entwerfen und Verfassen der Karte sowie das Anpassen der 
Elemente (gerenderte Ebenen, Legende, Titel usw.) und sind von 
denen in der Entwurfssoftware inspiriert.

Einige Desktop-GIS enthalten Elemente zur Automatisierung der 
kartografischen Produktion, z. B. Vorlagen oder Tools zum Generieren von 
Kartenserien (Abbildung 8.2).

![Automatisierte Erstellung von Kartenserien in einem GIS](../media/img/Map_series.png)
*Abbildung 8.2: Automatisierte Erstellung von Kartenserien in einem GIS.*

Dies ist möglich dank der Trennung zwischen geographischen Daten und 
der Gestaltung des Endprodukts, also des kartographischen Dokuments. 
Erinnern Sie sich: Genau diese Trennung wurde im Kapitel Visualisierung schon einmal 
hervorgehoben.



[^1]: https://de.wikipedia.org/w/index.php?title=Canvas_(HTML-Element)&oldid=176880399
[^2]: https://de.wikipedia.org/w/index.php?title=Rendern_(Design)&oldid=168315753
[^3]: https://de.wikipedia.org/w/index.php?title=Layertechnik&oldid=73960532
[^4]: https://de.wikipedia.org/w/index.php?title=Remote_Service&oldid=160831705
[^5]: https://wiki.openstreetmap.org/w/index.php?title=Attributierung_von_Stra%C3%9Fen_in_Deutschland&oldid=1500682
[^6]: https://de.wikipedia.org/w/index.php?title=Perspektive&oldid=177871864
[^7]: https://de.wikipedia.org/w/index.php?title=CAD&oldid=180412935
[^8]: https://de.wikipedia.org/w/index.php?title=Geodaten&oldid=177215946#Topologie
[^9]: http://www.igt.uni-stuttgart.de/eiserm/lehre/2010/Topologie/


*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute


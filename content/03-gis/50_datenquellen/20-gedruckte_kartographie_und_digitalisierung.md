# Gedruckte Kartographie und Digitalisierung

Eine große Menge Kartographie existiert in gedruckter Form, wie Karten oder alten analogen Luftbildern. Um in einem GIS verwendet zu werden, muss diese Kartographie digitalisiert werden, was bedeutet, dass aus ihnen Raster- oder Vektorschichten erzeugt werden. In diesem letzteren Fall bedeutet es auch, die verschiedenen Arten von Informationen zu trennen, die die Karte enthalten könnte, da die Informationen in einer einzelnen gedruckten Karte in unabhängigen Schichten in GIS gespeichert würden

Die Digitalisierung eines gedruckten kartographischen Dokuments umfasst drei Schritte:

- Georeferenzierung des Originaldokuments Das heißt, einen geografischen Kontext (Koordinatensystem, Kontrollpunkte usw.) einstellen, so dass die erzeugten digitalisierten Elemente korrekt referenziert werden.
- Digitalisierung der räumlichen Komponente. Das heißt, die entsprechenden Geometrien erstellen.
- Digitalisierung der thematischen Komponente. Erstellen von Zellenwerten für Rasterlayer oder Attribute im Falle von Vektorlayern.

Die Digitalisierung kann manuell oder automatisch erfolgen. Wenn manuell, führt ein Operator den Wert ein, während ein automatischer Ablauf durch einen Algorithmus erfolgt.

Zum Erstellen von Raster-Layern wird das Originaldokument am häufigsten mit einem Scanner gescannt, der ein digitales Bild aus einem analogen Dokument erstellt.

High-End-Scanner, die speziell für das Arbeiten mit kartographischen Dokumenten entwickelt wurden, sind verfügbar. Generische Scanner können jedoch für diese Aufgabe mit akzeptablen Ergebnissen in Bezug auf Genauigkeit und Verzerrung verwendet werden.

Zwei Parameter definieren die Eigenschaften eines Scanners: seine räumliche Auflösung und seine radiometrische Auflösung. Die erste wird normalerweise in DPI (Dots per Inch) gemessen und gibt die Anzahl der Punkte (Zellen) an, die der Sensor im resultierenden Bild für jede Längeneinheit im Originaldokument erstellt. Die radiometrische Auflösung definiert die Fähigkeit des Sensors, zwischen zwei verschiedenen Farben zu trennen.

Die Ideen, die im Kapitel \ ref {Fundamentals} zur Skalierung diskutiert werden, sollten hier ebenfalls berücksichtigt werden. Arbeiten mit einer höheren Auflösung (wenn der Scanner dies zulässt) bedeutet nicht immer, dass dem resultierenden Bild mehr Informationen hinzugefügt werden, da es im Originaldokument möglicherweise nicht vorhanden ist. Wir hätten nur ein Datenvolumen, das größer ist als das, das benötigt wird, um alle Informationen im gedruckten Dokument zu erfassen, aber nicht mehr Informationen.

Im Fall von Vektorschichten ist die manuelle Digitalisierung die gebräuchlichste Methode. Ein Operator definiert die Features, verfolgt deren Geometrien und gibt die zugehörigen Attributdaten ein.

Um Geometrien zu digitalisieren, kann der Bediener die Bearbeitungsfunktionen eines GIS verwenden und auf dem Bildschirm des Computers mit seiner Maus als Ortungsgerät arbeiten oder spezielle Peripheriegeräte wie ein Digitalisiertablett verwenden. Im ersten Fall findet die Digitalisierung auf dem Bildschirm statt, so dass eine digitale Version des gedruckten Dokuments benötigt wird (obwohl keine Vektorvorlage), die durch Scannen erhalten werden kann. Der vollständige Digitalisierungsprozess umfasst zwei Schritte, die zwei verschiedene Arten der Digitalisierung umfassen: von der gedruckten Karte zum Rasterbild (automatisch) und von den Bild- zu den Vektormerkmalen (manuell). Wenn Sie ein Tablett verwenden, kann die gedruckte Karte direkt zum Verfolgen von Geometrien verwendet werden.

Die automatische Digitalisierung von Geometrien in einer Vektorschicht wird als Vektorisierung bezeichnet. Ein digitales Bild wird benötigt, daher muss das Originaldokument zuerst gescannt werden. Der Vektorisierungsalgorithmus analysiert die Karte und findet die Elemente, die sie enthält, und erzeugt daraus die entsprechenden Vektorschichtelemente. In der Regel ist manuelle Arbeit erforderlich, um die resultierenden Daten zu vervollständigen und zu korrigieren, da dies ein komplexer und fehleranfälliger Prozess ist, bei dem die Datenaufbereitung eine große Bedeutung hat und eine vollautomatische Alternative meistens nicht möglich ist.

Ein besonderer Fall der Digitalisierung ist die Erzeugung von Schichten aus einer Menge von Werten, die einen räumlichen Prozess darstellen. Das heißt, wenn das ursprüngliche analoge Dokument keine Karte ist, sondern nur ein Satz von Werten. Dieser Prozess wird als Geocodierung bezeichnet. Dabei werden diesen Werten Koordinaten zugewiesen und anschließend die entsprechenden Ebenen mit der Kombination der ursprünglichen thematischen Daten und der geografischen Informationen (der räumlichen Komponente) erstellt, die sich aus dem Geokodierungsprozess ergeben haben.

Die ursprünglichen alphanumerischen Daten können manuell oder unter Verwendung eines automatisierten Ansatzes eingegeben werden, beispielsweise durch Scannen des Dokuments und anschließendes Verwenden einer Zeichenerkennungs- (OCR) -Software.

Ein besonderer und sehr beliebter Fall der Geocodierung (obwohl in diesem Fall das Dokument nicht analog ist) ist Geotagging, bei dem Koordinaten digitalen Bildern zugeordnet werden.

## Digitalisierungsqualität

Einer der wichtigsten Aspekte der Digitalisierung ist die Qualität ihres Ergebnisses, das der Qualität des zu digitalisierenden Dokuments möglichst nahe kommt. Die Digitalisierung ist niemals perfekt, unabhängig von der Genauigkeit der verwendeten Ausrüstung oder den Fähigkeiten der Person, die sie ausführt. Es wird immer Fehler und Mängel geben.

Neben den Fehlern, die in den verschiedenen Phasen des Digitalisierungsprozesses eingeführt wurden, können die ursprünglichen Quelldokumente auch ihre eigenen Fehler enthalten. Zum Beispiel könnte das Scannen einer Karte Fehler aufgrund von geometrischen Verzerrungen verursachen, aber diese Karte könnte selbst Verzerrungen aufgrund ihrer früheren Verwendung enthalten.

In einem kartografischen Dokument enthaltene Informationen können Elemente enthalten, die problematisch sind und die Qualität der resultierenden Daten beeinträchtigen. Eine Karte, die Flecken enthält oder einige Linien hat, die nicht korrekt sichtbar sind, führt zu Fehlern bei der Digitalisierung ihrer Vektormerkmale (insbesondere im Falle der automatischen Digitalisierung), unabhängig von der Qualität des Scan-Prozesses, der vorher benötigt wird. Unter den Fehlern, die auf den Digitalisierungsprozess selbst zurückzuführen sind und nicht mit den Dokumenteigenschaften zusammenhängen, sind nicht übereinstimmende Knoten in Vektorgeometrien am häufigsten (Abbildung 7.2).

![Digitalisierungsfehler a) Korrekte Version mit übereinstimmenden Knoten. b) und c) Falsche Versionen mit nicht übereinstimmenden Knoten verursachen falsche unterbrochene Leitungen](../media/img/Errors_digitization.png)
*Abbildung: Digitalisierungsfehler a) Korrekte Version mit übereinstimmenden Knoten. b) und c) Falsche Versionen mit nicht übereinstimmenden Knoten verursachen falsche unterbrochene Leitungen.*

Aus diesem Grund beinhalten die Editierfunktionen von GIS zusätzliche Funktionalitäten, um diese Fehler beim Digitalisieren zu vermeiden, dem Benutzer zu helfen und eine Genauigkeit und Qualität zu ermöglichen, die ohne solche Hilfsmittel nicht möglich wären. Unter diesen ist die automatische Anpassung von Geometrieknoten basierend auf vordefinierten Toleranzen (bekannt als Fangen) besonders relevant, da sie eine korrekte Beziehung zwischen den Knoten unterschiedlicher Geometrien garantieren kann, unabhängig davon, ob sie zu demselben Merkmal gehören oder nicht.

Dies ist besonders wichtig, wenn nicht nur die Geometrien digitalisiert werden, sondern auch die topologischen Informationen, die im Originaldokument enthalten sind (z. B. die Verbindung zwischen den Straßen in einem Kartenblatt). Beim Digitalisieren von Geometrien und ihrer Topologie müssen bestimmte zusätzliche Regeln beachtet werden, z. B. das einmalige Digitalisieren der gemeinsamen Seiten benachbarter Polygone. Zusätzliche Informationen müssen ebenfalls digitalisiert werden, z. B. die Definition von Knoten, wenn sich Linien kreuzen und eine Beziehung zwischen den Objekten besteht (z. B. eine Kreuzung zwischen zwei Straßenlinien, die einen Punkt darstellen, an dem Fahrzeuge von einer Straße zu das andere).

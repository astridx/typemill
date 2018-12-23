# Grundlegende Ideen zur Datenvisualisierung

Wenn wir irgendeine Art von geografischer Information visualisieren, 
ob auf einem Computerbildschirm oder auf einer gedruckten Karte, 
verwenden wir eine visuelle Sprache, um diese Information zu übermitteln.

Das Studium der Zeichen einer Sprache wird Semiologie[^1] genannt. 

> Semiologie ist die allgemeine Lehre von sprachlichen und außersprachlichen Zeichen und 
ihren Systemen.

Im Falle einer Bildsprache haben wir eine grafische Semiologie. 
Diese Semiologie arbeitet mit den Zeichen der Sprache, 
die wir verwenden, 
um geografische Daten zu visualisieren, 
und hilft uns zu verstehen, 
warum und wie visuelle Elemente ihren Zweck erfüllen. 
Wie sie also die Informationen, aus denen sie erzeugt werden, korrekt zu vermitteln.

## Visuelle Variablen

Visuelle Elemente haben mehrere Eigenschaften, 
die zum Übertragen von Informationen verwendet werden können. 
Je nach Fall könnten einige von ihnen geeigneter sein als andere.

![Visuelle Variablen Von links nach rechts: Position, Form, Größe, Farbton, Wert, Textur und Ausrichtung](../media/img/VisualVariables.png)
*Abbildung: Visuelle Variablen Von links nach rechts: Position, Form, Größe, Farbton, Wert, Textur und Ausrichtung.*

Diese Eigenschaften werden als visuelle Variablen bezeichnet und 
auf die geometrischen Elemente angewendet, 
die zur Visualisierung geografischer Informationen verwendet werden. 
Diese Elemente können anhand der folgenden visuellen Variablen unterschieden werden, 
die in Abbildung 11.1 dargestellt sind: 
- Position, 
- Form, 
- Größe, 
- Farbton, 
- Wert, 
- Textur und 
- Ausrichtung.

Die Verwendung von *Position* ist im Falle einer Karte eher eingeschränkt, 
da die tatsächliche Position des zu rendernden Elements respektiert werden sollte. 
Sie wird selten verwendet.

Die *Form* wird durch den Umfang des Objekts definiert. 
Diese Variable wird hauptsächlich im Fall von Punktdaten verwendet, 
wobei ein Symbol einer gegebenen Form verwendet wird, 
das sich an den exakten Koordinaten des zu rendernden Punktes befindet. 
Es ist schwierig, es auf lineare Symbole anzuwenden, 
und im Falle von Gebietssymbolen erfordert es die Änderung der Form des Symbols selbst.

*Größe* gibt die Abmessungen des Symbols an. 
Im Falle von Punkten kann es angewendet werden, 
indem die Größe des Symbols selbst geändert wird. 
Im Fall von Linien ist das Ändern ihrer Dicke die üblichste Art, 
diese visuelle Variable anzuwenden. 
Es wird nicht in Flächensymbolen verwendet, 
außer bei Verwendung einer Texturfüllung, 
bei der die Größenvariable auf die Textur und nicht auf das Symbol selbst angewendet wird.

Die *Größe* ändert, wie andere visuelle Variablen wahrgenommen werden, insbesondere bei kleinen Größen.
Textur bezieht sich auf das Muster, mit dem der Körper des Symbols gefüllt wird. Es kann auf Linien angewendet werden, die Strichmuster verwenden, aber es wird meistens auf Flächensymbole angewendet.
Farbe ist die wichtigste aller visuellen Variablen. Zwei seiner Komponenten können selbst als visuelle Variablen verwendet werden: Farbton und Wert.

*Farbton* ist, was wir normalerweise Farbe nennen. Das heißt, der Name der Farbe (blau, rot, grün usw.)
Der Farbton kann durch den Farbton der umgebenden Elemente, besonders in kleinen Symbolen, verändert werden. Obwohl die menschliche Wahrnehmung sehr sensibel ist, könnte es schwierig sein, sie in kleinen Symbolen zu identifizieren, und sie kann fälschlicherweise identifiziert werden, wenn das Symbol andere größere mit unterschiedlichen Farbtönen in seiner Umgebung aufweist.

*Wert* definiert die Dunkelheit der Farbe. Zum Beispiel haben hellblau und dunkelblau den gleichen Farbton, aber sie haben unterschiedliche Werte.

Die Unterscheidung zweier Symbole nach ihrem Wert kann je nach Symboltyp schwierig sein. Im Fall von Flächensymbolen ist dies einfacher, während es bei linearen und Punktsymbolen auf deren Größe ankommt. Kleinere Größen erschweren das Vergleichen von Werten und das Extrahieren der Informationen, die die visuelle Variable zu vermitteln versucht.

Die Orientierung wird auf Punktsymbole angewendet, es sei denn, sie haben eine Art von Symmetrie, die es schwierig macht, die Orientierung des Symbols zu identifizieren. Für Flächensymbole wird es auf ihre Textur angewendet. Bei linearen Symbolen wird es nicht angewendet.

## Eigenschaften von visuellen Variablen

Visuelle Variablen können vier grundlegende Eigenschaften haben.

- **Assoziativ**  
Eine visuelle Variable wird als assoziativ bezeichnet, wenn sie die Sichtbarkeit eines Elements nicht ändert. Das heißt, es ist nicht möglich, einem Element, das diese visuelle Variable verwendet, mehr Bedeutung zu geben.
- **Selektiv**  
Eine visuelle Variable wird als selektiv bezeichnet, wenn bei ihrer Anwendung verschiedene Kategorien von Symbolen erzeugt werden.
- **Bestellt  
Eine visuelle Variable wird als selektiv bezeichnet, wenn sie zur Darstellung einer gegebenen Ordnung verwendet werden kann.
- **quantitativ**  
Wenn es, abgesehen von der Bestellung, verwendet werden kann, um Verhältnisse auszudrücken.

In der obigen Liste sind Variablen nach den sogenannten Organisationsebenen geordnet. Die assoziative Eigenschaft ist auf der unteren Ebene, während die quantitative Eigenschaft am höchsten ist. Wie wir später sehen werden, ist die Organisation der visuellen Variablen relevant, wenn sie kombiniert werden. Die Organisationsebene einer Variablen definiert auch den Informationstyp, den die Variable übertragen kann.

Die nachfolgende Abbildung zeigt verschiedene Renderings einer Menge von Punktsymbolen, die jeweils eine visuelle Variable erklären.

![Visualisierung einer Menge von Punktsymbolen mit jeweils einer einzigen visuellen Variablen](../media/img/PropertiesVisualVariables.png)
*Abbildung: Visualisierung einer Menge von Punktsymbolen mit jeweils einer einzigen visuellen Variablen.*

Ausgehend von der assoziativen Eigenschaft sehen wir, dass alle anderen visuellen Variablen außer Größe und Wert kein Element gegenüber den anderen hervorheben. Mit anderen Worten, ein Element wird nicht als wichtiger angesehen als der Rest, wenn die visuelle Variable Textur, Farbe, Form oder Position ist.

Mit der Größe ist es jedoch klar, dass ein größeres Symbol eine wichtigere Rolle spielt. Auf die gleiche Weise zieht ein dunklerer Wert die Aufmerksamkeit des Betrachters viel mehr auf sich als eine Farbe mit einem helleren Wert.

In Bezug auf die selektive Eigenschaft können wir sagen, dass eine Variable eine selektive Qualität hat, wenn wir auf den ersten Blick leicht die Elemente identifizieren können, die zu einer bestimmten Gruppe gehören, die durch eine visuelle Variable definiert ist. Das deutlichste Beispiel dafür ist der Farbton. Wir können schnell von einer Reihe von Symbolen diejenigen trennen, die rot oder gelb sind. Alle visuellen Variablen, mit Ausnahme der Form, haben diese Eigenschaft, obwohl es möglicherweise nicht so ist wie im Falle des Farbtons. Form macht Elemente nicht spontan zu Gruppen.

Die geordnete Eigenschaft wird in den visuellen Variablen gefunden, die wir zum Definieren einer Reihenfolge verwenden können. Nur die Position, Textur, Größe und der Wert sind Bestelleigenschaften. Zum Beispiel können wir in dem Bild, das dem visuellen Variablen-Farbton entspricht, nicht sagen, welches Element wir am Anfang oder Ende einer durch den Farbton selbst definierten Skala platzieren würden. Mit Wert können wir jedoch, da diese Skala zwischen den helleren Tönen zu den dunkleren reichen würde, und wir können sie visuell unterscheiden und sortieren.

Schließlich wird die quantitative Eigenschaft in jenen visuellen Variablen gefunden, die verwendet werden können, um Mengen und Verhältnisse visuell zu schätzen. Nur Position und Größe haben es. Zum Beispiel können wir sehen, dass die großen Kreise in dem Bild, die der visuellen Größe der Größe entsprechen, mehr oder weniger doppelt so groß sind wie die kleineren.

Tabelle 1 enthält eine Zusammenfassung all dieser Ideen.

|Eigenschaft |Position |Größe |Form |Wert |Farbton |Textur |Ausrichtung|
|------------|---------|------|-----|-----|--------|-------|-----------|
|Assoziativ  |    ◊    |  -   |  ◊  |  -  |   ◊    |  ◊    |     ◊     |
|Selektive   |    ◊    |  ◊   |  -  |  ◊  |   ◊    |  ◊    |     ◊     |
|Bestellte   |    ◊    |  ◊   |  -  |  ◊  |   -    |  -    |     -     |
|Quantitativ |    ◊    |  ◊   |  -  |  -  |   -    |  -    |     -     |
Tabelle 1: Eigenschaften von visuellen Variablen.

Visuelle Variablen können kombiniert werden - 
beispielweise Objekte mit unterschiedlicher Größe und Farbton darstellen. 
Die Eigenschaften aller verwendeten visuellen Variablen müssen berücksichtigt werden, 
und wenn eine bestimmte Eigenschaft für die Informationen benötigt wird, 
die wir vermitteln möchten, sollten alle diese visuellen Variablen sie haben.

## Die Wahrnehmung von visuellen Variablen

Die Wahrnehmung von visuellen Variablen könnte durch die Umwelt verändert werden. 
Es ist wichtig, dies aus zwei Blickwinkeln zu betrachten: 
- Wahrnehmungskonstanz   
Wie sehr wir visuelle Elemente und ihre Umgebung verändern können, 
bevor sie nicht die gleichen Informationen vermitteln und falsch identifiziert werden können.
- Wahrnehmungshilfen   
Wie wir visuellen Elementen helfen können genau so wahrgenommen werden, 
wie wir es möchten.

Perzeptive Konstanz definiert, 
wie Objekte auf die gleiche Weise wahrgenommen werden, 
unabhängig von den Änderungen in der Umgebung. 
Zum Beispiel, wenn ein Objekt rund ist, 
wie ein Rad. Dann wird es auch eine runde Form haben,  
wenn wir es aus einer senkrechten Richtung betrachten. 
Wenn wir es jetzt aus einem anderen Blickwinkel betrachten, 
sehen wir statt eines Kreises eine Ellipse. 
Wir werden es jedoch als rund lesen und seine Form immer noch korrekt identifizieren. 
Das ist ein Beispiel für die Wahrnehmungskonstanz der Form.

Nicht alle visuellen Variablen haben eine solche Wahrnehmungskonstanz. 
Wenn sich die Wahrnehmung eines Elements ändert, 
selbst wenn das Objekt selbst dies nicht tut, 
wird gesagt, 
dass ein perzeptiver Kontrast existiert. 
Ein perzeptiver Kontrast kann dazu führen, 
dass ein visuelles Element falsch wahrgenommen wird und die Information, 
die es überträgt, falsch interpretiert wird.

Im Folgenden werden einige der Hauptideen über wahrnehmbare Kontraste aufgeführt, 
die beim Erstellen einer Karte berücksichtigt werden müssen:

- Die Größe ist die visuelle Variable, 
die stärker von Wahrnehmungskontrasten betroffen ist. 
Die scheinbare Größe eines Objekts kann sich ändern, 
wenn es von anderen Elementen unterschiedlicher Größe umgeben ist. 
Dies ist besonders relevant, wenn Punktsymbole in einer Karte verwendet werden.
- Werte werden auch geändert, 
wenn andere Elemente mit einem anderen Wert in der Nähe angezeigt werden, 
insbesondere wenn es eine große Anzahl von Elementen gibt.
- Der Farbton wird durch die Anwesenheit anderer Farbtöne verändert. 
In einer Karte sollten wir überlegen, 
wie sich die Hintergrundfarbe auf die Vordergrundsymbole auswirken könnte.
- Wenn komplementäre Farbtöne zusammengefügt werden, 
kann ein Vibrationsempfinden an der Grenze zwischen ihnen hervorrufen.

Hinsichtlich der Wahrnehmungshilfen ist der wichtigste Faktor 
beim Erstellen einer Karte die korrekte Trennung zwischen den 
Vordergrundobjekten und dem Hintergrund. 
Die Eigenschaften der visuellen Variablen müssen verwendet werden, 
um verschiedene Ebenen in der Visualisierung zu erzeugen, 
wobei einigen Elementen mehr Relevanz zugewiesen wird, 
um die Aufmerksamkeit auf die Informationen zu lenken, die sie übertragen.

Um bestimmte Layer - die relevantesten in Bezug auf das Thema der Karte - 
besser sichtbar zu machen, 
muss eine korrekte Hierarchie mit Hilfe visueller Variablen erstellt werden. 
Diese Hierarchie wird die in der Karte angezeigten Informationen vertiefen, 
und einige Elemente werden als wichtiger angesehen als andere. 
Die Ebenenordnung definiert bereits eine Struktur und eine Hierarchie, 
aber das reicht in den meisten Fällen nicht aus und 
visuelle Variablen sollten verwendet werden, um sie zu verstärken.

Die nachfolgende Abbildung zeigt, warum eine korrekte Hierarchie benötigt wird, 
um eine gute Karte zu erstellen.

![Vergleich zwischen einer Karte ohne Hierarchie (a) und einer Karte mit einer korrekten Hierarchie (b)](../media/img/HierarchyMap.png)
*Abbildung: Vergleich zwischen einer Karte ohne Hierarchie (a) und einer Karte mit einer korrekten Hierarchie (b).*


[^1]: https://de.wikipedia.org/w/index.php?title=Semiologie&oldid=180284573

*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute
*[DBMS]: Datenbankmanagementsystem
*[SQL]: Structured Query Language“ (auf Deutsch: „Strukturierte Abfrage-Sprache“)


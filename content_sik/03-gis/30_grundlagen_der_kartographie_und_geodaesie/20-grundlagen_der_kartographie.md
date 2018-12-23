# Grundlegende kartographische Konzepte

Unter den grundlegenden Konzepten der Kartographie, die jeder GIS-Benutzer kennen muss, ist die Skalierung die wichtigste. Der Maßstab einer Karte stellt das Größenverhältnis zwischen der "Karte" dar, die durch die Entwicklung der realen Oberfläche, die wir repräsentieren (die Erdoberfläche in diesem Fall), und dem Maßstab unserer kleineren Karte erhalten würde. Wenn wir dieses Verhältnis kennen, können wir die tatsächlichen Maße der Elemente kennen, die in der Karte enthalten sind, da wir die Messungen, die wir daran vornehmen, in reale Messwerte umwandeln können. Es ist wichtig, daran zu denken, dass diese Maße nicht so "real" sind, da die Projektion sie verzerrt haben könnte, aber sie sind nichtsdestoweniger Maße im ursprünglichen Maßstab des gemessenen Objekts.

Maßstab wird normalerweise als ein Quotient zwischen der in einer Karte gemessenen Entfernung und der Entfernung, die dieses Maß in der Realität darstellt, ausgedrückt. Zum Beispiel bedeutet ein Maßstab von 1: 50000, dass ein Zentimeter in einer Karte in Wirklichkeit 50000 Zentimeter entspricht, also 500 Meter. Dieser Wert wird als numerische Skalierung bezeichnet.

Unabhängig von der verwendeten Projektion ist der Maßstab nur an bestimmten Punkten der Karte vollständig wahr. In den anderen ändert sich die Skalierung. Die Beziehung zwischen der Skala in diesen Punkten und der numerischen Skala wird als Skalierungsfaktor bezeichnet.

Obwohl Skalierung traditionell als ein Konzept im Zusammenhang mit der Datendarstellung verstanden wird, haben geografische Daten eine inhärente Skalierung, die nicht mit ihrer Repräsentation in Beziehung steht, sondern mit der Detailebene, mit der die Daten auf dem Feld erfasst wurden. Es ist korrekter, Skalierung als etwas zu verstehen, das mit der Datenauflösung in Beziehung steht, das heißt mit der minimalen abgebildeten Größe.

Die Auflösung des menschlichen Auges beträgt 0,2 mm. Mit diesem Wert und der Skalierung, die wir für eine Karte verwenden möchten, können wir den Detaillierungsgrad ermitteln, den wir verwenden müssen, wenn Daten erfasst werden, die als Teil dieser Karte verwendet werden sollen.

Wie wir gesehen haben, enthalten Daten in GIS keine Visualisierung. Das bedeutet, dass wir es in jedem Maßstab visualisieren können (und das ist sehr einfach mit den Zoom-Tools, die in den meisten GIS-Software zu finden sind). Die Daten wurden jedoch auf einer bestimmten Detailebene erfasst. Die Daten wurden jedoch mit einer bestimmten Detailebene erfasst, die den zu verwendenden Maßstab definiert und eine Einschränkung dieser Daten darstellt. Es wird nicht korrekt sein, sie über diesen Maßstab hinaus darzustellen. Mit anderen Worten, um eine Karte in einem detaillierteren Maßstab zu erstellen, benötigen wir detailliertere Daten. Das kann man leicht vergessen, wenn man ein GIS benutzt.

Raster-Layer haben, wie wir gesehen haben, eine Zellengröße, die die Auflösung der Ebene definiert und mit der Skalierung zusammenhängt.

Im Zusammenhang mit dem Konzept der Skala finden wir die sogenannte kartographische Verallgemeinerung. Es bedeutet, eine Idee oder Information in einer prägnanteren Weise auszudrücken, so dass sie in einem gegebenen Kontext nützlicher sein kann. In einem GIS ist eine Verallgemeinerung erforderlich, um Daten in einem kleineren (weniger detaillierten) Maßstab darzustellen, als dies inhärent ist, hauptsächlich aufgrund der Beschränkungen, die von den Wiedergabegeräten auferlegt werden. Wenn wir beispielsweise eine Ebene mit den Straßen eines bestimmten Landes haben, macht es keinen Sinn, sie in einer Karte zu verwenden, die den gesamten Planeten darstellt. Wir werden eine Masse von Linien bekommen, und wer auch immer diese Karte benutzt, wird nicht in der Lage sein, zwischen ihnen zu unterscheiden. Außerdem wird das Rendern all dieser Zeilen eine Menge Verarbeitungsleistung verbrauchen. Eine viel interessantere Option wäre, nur die Hauptautobahnen und Autobahnen zu benutzen und den Rest von ihnen nicht zu malen. Die Karte wird klarer und nützlicher, und das Bildschirm-Rendering wird viel schneller sein.

![Generalisierung durch Aggregation Zwei Straßen, die fast parallel sind, werden als zwei separate Elemente in der Karte dargestellt, aber in der Übersichtskarte der oberen linken Ecke, mit einer kleineren Detailstufe, werden sie als ein einzelnes Element verallgemeinert. (Aus Yahoo Maps.)](../media/img/Generalization_aggregation.png)

*Abbildung: Generalisierung durch Aggregation Zwei Straßen, die fast parallel sind, werden als zwei separate Elemente in der Karte dargestellt, aber in der Übersichtskarte der oberen linken Ecke, mit einer kleineren Detailstufe, werden sie als ein einzelnes Element verallgemeinert. (Aus Yahoo Maps.)*

Die Verallgemeinerung im Kontext eines GIS umfasst auch andere Änderungen, die vorgenommen werden, um die Qualität der Karte zu verbessern und die Art der Übermittlung von Informationen zu verbessern. Dies bedeutet möglicherweise nicht, die Detailgenauigkeit zu reduzieren, sondern lediglich die Daten für rein kartografische Zwecke zu ändern.

Wenn wir beispielsweise die Straßenebene in einer Karte darstellen, die die gesamte Welt abdeckt, sollten wir die Straßen nicht in ihrer tatsächlichen Größe malen. Sie wären zu dünn und fast unsichtbar. Wir werden sie viel dicker bemalen und so eine Karte erstellen, die weniger korrekt ist (wir verzerren die tatsächliche Größe dieser Straßen), ist aber viel nützlicher.

Verallgemeinerung ist daher ein Prozess, dessen Hauptzweck darin besteht, ein kartographisches Bild lesbarer und expressiver zu machen, indem die Elemente ausgewählt und angepasst werden, die in der Karte enthalten sind. Es betont die wichtigen, während es die unwichtigsten weglässt.

Einige der wichtigsten Operationen in der kartographischen Verallgemeinerung sind die Vereinfachung (die ein weniger komplexes Element repräsentiert), die Aggregation (die mehrere Elemente repräsentiert, wie nur eine Abbildung 5.3), die Übertreibung (die Elemente mit einer größeren Größe repräsentiert) und die Verschiebung (die Elemente repräsentiert) ein anderer Ort, um die Lesbarkeit zu gewährleisten).

In GIS kann die Generalisierung als Teil des Visualisierungsmechanismus implementiert werden. Das heißt, wenn eine Schicht gerendert wird, wird sie gleichzeitig entsprechend der kartographischen Skala und anderen Faktoren modifiziert. Dies ist ein zeitaufwendiger Vorgang und führt normalerweise nicht zu guten Ergebnissen, hauptsächlich wegen der Komplexität des Prozesses, der schwer zu automatisieren ist.

![In einem GIS werden häufig Informationen in verschiedenen Maßstäben verwendet. Die aktuelle kartographische Skala wird definieren, welcher Teil davon gerendert wird und welcher nicht](../media/img/GIS_multi_scale.png)

*Abbildung: In einem GIS werden häufig Informationen in verschiedenen Maßstäben verwendet. Die aktuelle kartographische Skala wird definieren, welcher Teil davon gerendert wird und welcher nicht.*

Eine alternative Lösung besteht in der Verwendung eines Multiskalen-Ansatzes (Abbildung 5.4). Informationen für ein bestimmtes Untersuchungsgebiet werden in verschiedenen Maßstäben erstellt (mit Hilfe einer Generalisierung basierend auf einem einzelnen oder nur mit Schichten mit einem anderen Ursprung), und das jeweils günstigste wird in Abhängigkeit von der aktuellen Skala verwendet. Dies entspricht mehreren gedruckten Karten in verschiedenen Maßstäben.

Das Konzept der Schicht, das wir im nächsten Kapitel sehen werden, ist der Schlüssel für diesen multiskaligen Ansatz.

Im Falle von Bildern beinhaltet der Ansatz die Erzeugung sogenannter Pyramiden. Anstatt ein einzelnes Bild zu verwenden, haben wir eine Reihe von ihnen mit verschiedenen Zellgrößen. Um die Datenverarbeitung zu optimieren und die Menge der beim Rendern des Bildes zu verarbeitenden Daten zu minimieren, wird die Ebene in der Pyramide verwendet, die am besten zum aktuellen Maßstab passt.
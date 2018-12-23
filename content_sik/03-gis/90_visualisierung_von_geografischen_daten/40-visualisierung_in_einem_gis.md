# Visualisierung in einem GIS

Nachdem wir nun die grundlegenden Ideen zur Visualisierung und deren Anwendung auf Karten kennen, ist es an der Zeit zu sehen, wie diese im Zusammenhang mit einem GIS verwendet werden. Zwei Ideen sind in diesem Zusammenhang besonders relevant: Die Tatsache, dass wir mit mehreren Schichten arbeiten, um zusammen dargestellt zu werden, und die Besonderheiten des Bildschirm-Renderings und der Interaktivität, die es bietet.

## Mehrere Ebenen kombinieren

In den meisten Fällen ist die Visualisierung einer Ebene allein nicht die beste Möglichkeit, die darin enthaltenen Informationen zu visualisieren. In einer Karte finden wir normalerweise verschiedene Arten von Informationen, und zwar nicht nur aus Platzgründen, sondern weil sie dem Kartenbenutzer helfen, die Hauptinformationen zu verstehen und zu interpretieren. Zum Beispiel helfen Konturlinien, die Formen von Flüssen und Seen zu verstehen, was einen wertvollen Kontext darstellt.

Wenn wir Ebenen kombinieren, sollten wir versuchen, eine Synergie zwischen ihnen zu schaffen, so dass sie sich ergänzen. Dies geschieht meist durch korrekte Anordnung der Ebenen und Verwendung einer Symbologie für jede von ihnen, die die anderen nicht beeinträchtigt.

Wenn zwei Ebenen Informationen für denselben Ort haben, wird nur die Information der darüber liegenden Ebene angezeigt. Die Ebenenreihenfolge sollte die in der Karte angezeigten Informationen maximieren und die wichtigsten Ebenen gegenüber denen mit sekundären Informationen priorisieren.

Wir wissen, dass Raster-Layer den Raum ausfüllen und Werte in allen ihren Zellen enthalten (Pixel im Falle eines Bildes). Aus diesem Grund werden sie alles abdecken, was darunter ist, und es ist keine gute Idee, sie an der Spitze der Renderreihenfolge zu platzieren. Stattdessen sollten sie als Basisschichten betrachtet werden, auf denen die verbleibenden Schichten platziert werden.

Mit einer ähnlichen Argumentation können wir den besten Weg für die Anordnung von Vektorebenen definieren, indem wir zuerst Polygone, dann Linien und dann Punkte am oberen Rand der Renderreihenfolge platzieren.

Manchmal wird die Darstellungsreihenfolge durch die Bedeutung von Ebenen bestimmt. Wenn wir beispielsweise eine Karte mit einer Ebene erstellen, die Streams enthält, und einer anderen, die Straßen enthält, sollte diese letzte über die erste gehen, da Straßen normalerweise über Streams verlaufen und nicht umgekehrt.

Eine gängige Funktionalität der meisten GIS ist die Verwendung von Transparenz für Ebenen. Sie kann sowohl auf Raster- als auch auf Vektorlayer angewendet werden. Abbildung 11.9 wurde mit dieser Technik erstellt. Das Polygon, das die Grenze der Wasserscheide definiert, hat eine halbtransparente Füllung, die es ermöglicht, die darunter liegende schattierte Reliefschicht zu sehen. Das Ergebnis ist eine Karte, in der die hydrogische Bedeutung der Wasserscheide viel klarer und leichter zu verstehen ist.

![Kombination zweier Ebenen mit Transparenz](../media/img/Transparency.png)
*Abbildung: Kombination zweier Ebenen mit Transparenz.*

Im Fall von Raster-Layern kann Transparenz teilweise angewendet werden, indem nur die Zellen gerendert werden, die sich innerhalb eines bestimmten Wertebereichs befinden.

Wenn eine Variable in viele separate Ebenen unterteilt ist (horizontale Teilung), muss auf alle dieselbe Symbologie angewendet werden, um eine zusammenhängende Karte zu erhalten.

## Besonderheiten des Renderns auf dem Bildschirm

Abgesehen von den Ideen, die auf gedruckte Karten angewendet werden, müssen zusätzliche berücksichtigt werden, wenn die Visualisierung stattdessen auf einem Computerbildschirm stattfindet. Eine gedruckte Karte sollte nicht wie eine Karte entworfen werden, die auf dem Bildschirm gerendert werden soll.

Die wichtigsten zu berücksichtigenden Elemente sind die geringe Auflösung des Bildschirms im Vergleich zu einem Druckgerät und die Interaktivität der Visualisierung selbst.

Beim Erstellen einer gedruckten Karte ist die Auflösung kein Problem, da Druckgeräte eine Detailgenauigkeit bieten, die über das hinausgeht, was der Kartograf benötigt. Die Bildschirmauflösung ist jedoch viel niedriger und bestimmte Elemente werden möglicherweise nicht mit ausreichender Klarheit wiedergegeben. Obwohl diese Elemente in gedruckten Karten verwendet werden können, sollten sie für Bildschirmkarten ersetzt werden. Unter diesen problematischen Elementen finden wir Schriftarten mit Ornamenten wie Schattierungen, Schriftarten mit Serifen (kleine Linien am Ende des Strichs, um die Lesbarkeit zu erhöhen) oder Texturfüllungen mit kleiner Größe.

In Bezug auf Interaktivität müssen wir berücksichtigen, dass eine On-Screen-Karte im Gegensatz zu einer gedruckten Karte kein statisches, sondern ein dynamisches Element ist. Das bedeutet nicht, dass sich die Karte von selbst ändert, sondern dass der Benutzer sie mit den Werkzeugen ändern kann, die wir bereits gesehen haben (zoomen, schwenken usw.).

Da die Skalierung vom Benutzer geändert werden kann, kann dies bei bestimmten Elementen wie Symbolen und Textbeschriftungen zu Problemen führen. Wenn alle Elemente proportional skaliert werden, werden die Beschriftungen durch das Reduzieren der Skalierung zu klein und nicht lesbar. Wenn die Skala dagegen vergrößert wird, können Beschriftungen zu groß sein, wie in Abbildung 11.10 zu sehen ist.

![Eine Maßstabsänderung ändert die Größe von Symbolen und Textbeschriftungen und kann sie zu klein (a) oder zu groß (b) machen](../media/img/ProblemsChangeScale.png)
*Abbildung: Eine Maßstabsänderung ändert die Größe von Symbolen und Textbeschriftungen und kann sie zu klein (a) oder zu groß (b) machen.*

Eine Lösung hierfür ist die Verwendung einer absoluten Größe für diese Elemente, sodass sie unabhängig von der Skalierung immer die gleiche Größe haben. Bei niedrigeren Skalen kann dies jedoch zu gesättigten Karten führen, wie in Abbildung 11.11 zu sehen ist.

![Gesättigte Karte, die durch das Rendern von Elementen mit einer festen Größe in einem niedrigen Maßstab verursacht wird](../media/img/SaturatedMap.png)
*Abbildung: Gesättigte Karte, die durch das Rendern von Elementen mit einer festen Größe in einem niedrigen Maßstab verursacht wird.*

Die Fähigkeit von GIS, Ebenen in unterschiedlichen Maßstäben zu rendern, kann ebenfalls Leistungsprobleme verursachen. Bei niedrigen Skalen kann die Anzahl der zu rendernden Elemente zu groß sein und das Malen auf dem Bildschirm kann zu lange dauern. Um diese Probleme zu vermeiden, kann ein multiskalarer Ansatz gewählt werden, bei dem abhängig von der Skalierung verschiedene Schichten und Elemente gerendert werden. Für die gleiche Information können verschiedene Versionen mit unterschiedlichen Detailgraden verwendet werden, wobei jeder von ihnen nur in einem bestimmten Maßstabsbereich verwendet wird.

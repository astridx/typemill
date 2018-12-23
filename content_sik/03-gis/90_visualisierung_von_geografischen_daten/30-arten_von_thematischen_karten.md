# Arten von thematischen Karten

Es gibt viele verschiedene Möglichkeiten, eine bestimmte Variable in einer Karte zu visualisieren. Mehrere von ihnen können in einer einzigen Karte kombiniert werden, insbesondere wenn sie mehr als eine Variable enthält. In diesem Fall sollte die Kombination danach streben, die größtmögliche Klarheit für alle von ihnen zu erhalten, so dass die Wiedergabe einer Variablen die übrigen nicht überschattet.

In diesem Abschnitt werden die folgenden Arten von thematischen Karten beschrieben: Proportionale Symbolkarten, Punktdichtekarten, Isolinienkarten und Choroplethenkarten.

## Proportionale Symbolkarten

Eine proportionale Symbolkarte repräsentiert quantitative Variablen unter Verwendung von Symbolen, deren Größen proportional zum Wert der Variablen sind. Das heißt, die Karte verwendet die Größe der visuellen Variablen (die einzige mit der quantitativen Eigenschaft), um den Wert der dargestellten Variablen zu übertragen. Wenn das verwendete Symbol linear ist (z. B. ein Balken), wird seine Länge verwendet, um die zu rendernden Werte zu skalieren. Wenn es flächenhaft ist, wird Fläche verwendet. Das bedeutet, dass im Fall der Verwendung von Kreisen ein Wert, der drei Mal größer ist als ein Referenzwert, nicht mit einem Kreis mit einem dreimal längeren Radius gerendert wird, sondern mit einem Kreis mit einer Fläche, die dreimal so groß ist wie der Referenzkreis.

Die Symbolskalierung kann kontinuierlich durchgeführt werden, aber normalerweise ist es einfacher, einen diskreten Ansatz zu verwenden, indem Sie Werte in Klassen gruppieren und allen Werten in jeder Klasse eine einzige Größe zuweisen, normalerweise die Größe, die dem Mittelpunkt der Klasse entspricht .

Um Probleme zu vermeiden, wenn die Größe jedes Symbols erkannt wird, ist es wichtig, in der Legende die Beziehung zwischen den verschiedenen Größen und ihren entsprechenden Werten zu zeigen, wie in Abbildung 11.6 zu sehen ist

![Zwei Arten von Legenden für proportionale Symbolkarten](../media/img/LegendProportionalSymbols.png)
*Abbildung: Zwei Arten von Legenden für proportionale Symbolkarten.*

## Punktdichte Karten

Punktdichtekarten eignen sich besonders für zählbare Variablen wie Population oder Ernteerträge. Diese Größen werden durch wiederholte Punkte dargestellt, deren Anzahl proportional zur Menge selbst ist. Jeder Punkt repräsentiert einen Einheitswert, und alle Punkte innerhalb eines Bereichs addieren sich zum Gesamtwert der darin enthaltenen Variablen. Alle Punkte haben die gleiche Größe und Form, im Gegensatz zu dem, was wir bei proportionalen Symbolen gesehen haben.

Beim Erstellen einer Punktdichtekarte müssen drei Parameter definiert werden: der Wert jedes Punkts (dh wie viele Einheiten der Variablen der Punkt darstellt), seine Größe und seine Position.

Der Wert jedes Punkts sollte basierend auf dem Bereich der Werte definiert werden, die durch die Variable abgedeckt werden, so dass Punkte in der resultierenden Karte nicht zu knapp oder zu zahlreich sind. Dieser Wert wird in der Legende enthalten, normalerweise in Textform, zum Beispiel, dass "ein Punkt 1000 Einwohner repräsentiert".

Die Größe muss garantieren, dass Punkte sichtbar sind und gleichzeitig nicht zu viel Platz in der Karte einnehmen. Die optimale Größe wird mit dem ausgewählten Wert jedes Punktes verknüpft, und beide Parameter sollten zusammen betrachtet werden, um die beste Kombination davon zu finden.

Die Position der Punkte ist von großer Bedeutung, da sie keine falschen Informationen vermitteln oder den Benutzer dazu verleiten sollte, ihre Bedeutung falsch zu interpretieren. Wenn wir keine zusätzlichen Informationen haben, sollten Punkte regelmäßig verteilt werden, die das gesamte Gebiet abdecken, das dem Variablenwert entspricht. Wenn wir andererseits mehr Informationen über die Verteilung der Variablen haben, sollten wir sie verwenden, um den Punkten eine realistischere Position zu geben. Wenn wir beispielsweise eine Dichtekarte mit Bevölkerungswerten für Regionen erstellen, sollten in der Umgebung der Städte innerhalb der Region mehr Punkte vorhanden sein, da in diesen Gebieten mehr Einwohner leben.

Eine andere Sache, die man beachten sollte, ist die Bedeutung der Variablen und ob das Phänomen, das sie repräsentiert, an einem bestimmten Punkt auftreten kann oder nicht. Wenn zum Beispiel die Variable, die wir repräsentieren, die Anzahl der Wasservögel ist, die in jeder Region nisten, ist es falsch, die Dichtepunkte in Waldgebiete oder Stadtgebiete zu platzieren, da daraus geschlossen werden kann, dass Vögel dort gefunden werden. was wahrscheinlich nicht wahr ist.

Bild 11.7 zeigt ein Beispiel für eine Punktdichtekarte.

![Punktdichtekarte](../media/img/MapPoints.png)
*Abbildung: Punktdichtekarte.*

## Karte mit Intensitätswertlinie (Isoline maps)

Isolinienkarten werden häufig verwendet, um kontinuierliche Variablen darzustellen. Da sie nur Linien enthalten, vermischen sie sich gut mit anderen Arten von Karten, ohne aufdringlich zu sein.

Eine Isolinien-Map wird durch eine Menge von Linien gebildet, von denen jede Punkte verbindet, die denselben Wert der dargestellten Variablen haben. Diese Linien können sich nicht kreuzen, da ein Punkt nicht zwei Werte gleichzeitig haben kann. Die häufigste Verwendung von Isolinien sind Höhenlinien in topographischen Karten, die Punkte mit der gleichen Höhe darstellen.

Isolinien werden durch ihre Äquidistanz definiert, die den Unterschied zwischen den Werten zweier benachbarter Isolinien angibt. Eine niedrigere Äquidistanz bedeutet mehr Isolinien und eine dichtere Karte.

Größe ist die einzige visuelle Variable, die mit Isolinien verwendet wird. Es wird verwendet, um diejenigen hervorzuheben, die einen Wert darstellen, der ein Vielfaches einer gegebenen Zahl ist, um die Karte leichter lesbar zu machen. Diese Zeilen sind als Indexzeilen bekannt.

![Karte mit Intensitätswertlinie (Isolinien) und hypsometrischen Tönungen](../media/img/Isolines.png)
*Abbildung: Karte mit Intensitätswertlinie (Isolinien) und hypsometrischen Tönungen.*

Linien werden mit ihrem Wert über der Linie selbst gekennzeichnet, normalerweise nur auf den Indexlinien (der Wert von anderen Linien zwischen den Indexen kann leicht mit der Äquidistanz herausgefunden werden).

Ein spezieller Fall von Isolinien sind die sogenannten hypsometrischen Tönungen. Abgesehen davon, dass die Linien selbst gezeichnet werden, sind die Bereiche zwischen ihnen gefärbt, jede mit einer anderen Farbe (normalerweise mit einem abgestuften Schema).

Die Abbildung zeigt ein Beispiel dafür.

## Choroplethenkarten

Choropleth Karten sind eine sehr häufige Art von Karten in GIS. Zum Beispiel waren Karten in Abbildung 11.4 alle Choroplethenkarten.

In einer Choropleth-Map gibt es eine Reihe von Bereichen, von denen jeder einen einzelnen Wert einer Variablen darstellt. Dieser Wert gilt für den gesamten Bereich und wird normalerweise mithilfe des Farbtons dargestellt, der auf das Flächensymbol angewendet wird.

Choropleth Karten haben einige wichtige Einschränkungen. Eine davon ist die scharfe Änderung der Grenzen zwischen den Bereichen, was als abrupte Änderung des Variablenwerts in dieser Grenze interpretiert werden könnte. Dies könnte die Kontinuität der Variablenverteilung verbergen, falls diese existiert. Ein weiteres Problem ist die Homogenität in jedem Bereich, was zu der Annahme führen könnte, dass die Variable eine gleichmäßige Verteilung aufweist, auch wenn dies falsch ist.

In vielen Fällen und um die in der Variablen enthaltene Information korrekt zu übertragen, müssen ihre Werte unter Verwendung der Fläche jeder Region normalisiert werden.
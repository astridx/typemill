# Besonderheiten räumlicher Daten für ihre Analyse

Räumliche Daten haben aufgrund ihrer besonderen Eigenschaften ein großes Potenzial, aber gleichzeitig können diese Eigenschaften die Arbeit mit ihnen einschränken oder bedingen. In einigen Fällen können sie Probleme darstellen, die bei der Analyse der Daten berücksichtigt werden müssen. in anderen sind sie nur etwas, das jeder, der mit räumlichen Daten arbeitet, wissen sollte, aber das ist per se nicht problematisch.

## Rahmen (Scale)

Wir können geographische Informationen in verschiedenen Maßstäben studieren und je nachdem, welche wir verwenden, werden die Ergebnisse unterschiedlich sein. Aus diesem Grund sollte neben der Skalierung beim Rendern und Visualisieren geographischer Daten auch der Analyseskala bei jeder Analyse berücksichtigt werden.

Die Analyseskala sollte von den Dateneigenschaften (Genauigkeit, Datentyp usw.) und der mit ihnen durchzuführenden Analyse abhängen.

Dies kann mit Hilfe der Abbildung leicht verstanden werden. Wenn wir die Form des Geländes an einem bestimmten Punkt kategorisieren wollen, müssen wir die Höhe des Punktes und auch die Höhe in seiner Umgebung analysieren. Abhängig von der Größe des Analysefensters um den Mittelpunkt (was den Analyseskala definiert) können die Ergebnisse sehr unterschiedlich sein. In dem Bild wird das Gelände für einen kleinen Wert des Analyse-Radius als ein Peak kategorisiert. Für eine größere Region wird es jedoch als Talboden betrachtet.

![Je nach Analyseskala kann die Form des Geländes als Peak (a) oder Talsohle (b) klassifiziert werden](../media/img/Scales.png)
*Abbildung: Je nach Analyseskala kann die Form des Geländes als Peak (a) oder Talsohle (b) klassifiziert werden.*

Daher müssen wir das Gelände in der richtigen Entfernung betrachten, für die die Informationen, die es uns gibt, für die Art der Analyse, die wir durchführen, am interessantesten und richtigsten sind. Abgesehen von der Tatsache, dass es für jede Art von Analyse eine optimale Analyseskala gibt, ist es auch interessant, auf mehreren Skalen zu arbeiten, da dies uns mehr Informationen liefert als das, was wir erhalten können, wenn wir nur in einer einzigen Skala arbeiten.

Ein weiteres Beispiel, wie der Analyseskala das Analyseergebnis beeinflusst, findet sich bei Messungen. Wie in Abbildung 10.4 zu sehen ist, verursacht die verwendete Maßeinheit (die implizit durch den Detaillierungsgrad der Daten definiert wird), dass die Ergebnisse unterschiedlich sind.

![Maßeinheit beeinflusst den Wert der Messung](../media/img/Fractal_line.png)
*Abbildung 10.4: Maßeinheit beeinflusst den Wert der Messung.*

Ein Wert an sich hat möglicherweise keine Bedeutung, wenn er nicht von der Skala begleitet wird, mit der er erhalten wurde.

Das Konzept des Fraktalen steht in direktem Zusammenhang damit.

## Das Problem der modifizierbaren Flächeneinheit

Viele der Variablen, mit denen wir in GIS arbeiten, können nicht an einem einzigen Punkt gemessen werden, und sie müssen für einen bestimmten Bereich um diesen Punkt herum aggregiert werden. Beispiele dafür sind der Anteil der Bevölkerung innerhalb einer bestimmten Altersgruppe oder die Bevölkerungsdichte.

Bereiche, die definiert sind, um mit diesen Variablen zu arbeiten, sind im Wesentlichen willkürlich, wie beispielsweise Länder, Bezirke, Bezirke usw., und sie werden definiert, ohne irgendwelche Kriterien in Bezug auf räumliche Analyse zu berücksichtigen. Die Verwendung verschiedener Bereiche (unterschiedliche Einheiten zur Berechnung der Werte der Variablen) führt zu unterschiedlichen Ergebnissen.

Dieses Problem wird als modifizierbares Flächeneinheitsproblem (MAUP) bezeichnet. Die Lösung oder Reduzierung ihrer Auswirkungen ist komplex und es gibt keine Lösung, die in allen Fällen angewendet werden kann. Wenn wir jedoch mit dieser Art von geografischen Daten arbeiten, ist es wichtig zu beachten, dass es eine Quelle statistischer Verzerrung gibt, die nicht vernachlässigt werden kann .

Ein anderes Problem, das mit dem MAUP zusammenhängt, ist der sogenannte ökologische Fehlschluss, der sich aus der (falschen) Annahme ergibt, dass die für ein bestimmtes Gebiet berechneten Werte den Individuen der Population innerhalb dieses Gebiets zugeordnet werden können. Dies wäre nur bei vollständiger Homogenität der Fall.

## Räumliche Autokorrelation

Räumliche Autokorrelation ist die Korrelation einer Variablen mit sich selbst, so dass Werte der Variablen an jedem Punkt mit Werten derselben Variablen in nahegelegenen Punkten korreliert sind. Zum Beispiel haben im Falle der Temperatur Punkte in der Nähe einer Wärmequelle eine höhere Temperatur als diejenigen, die weit davon entfernt sind oder näher an einer kalten Stelle liegen. Wenn wir die Verbreitung einer Infektionskrankheit untersuchen, erscheinen die gemeldeten Fälle wahrscheinlich gruppiert, und eine große Anzahl von ihnen führt normalerweise dazu, dass die nahe gelegenen Populationen ebenfalls signifikant von der Krankheit betroffen sind.

Eine andere Art, dies auszudrücken, ist die Verwendung des bekannten ersten Toblerschen Geographiesetzes, das besagt, dass "alles mit allem zusammenhängt, aber nahe Dinge mehr miteinander verbunden sind als entfernte Dinge".

In den obigen Fällen wird die räumliche Autokorrelation als positiv bezeichnet. Es kann jedoch auch negativ sein, wenn höhere Werte von niedrigeren umgeben sind oder gar keine Korrelation vorhanden ist, wenn Werte in separaten Punkten unabhängig voneinander sind und sich unabhängig von der Entfernung nicht gegenseitig beeinflussen.

Die nachfolgende Abbildung zeigt drei Raster-Layer, die die obigen Arten der räumlichen Autokorrelation zeigen.

![a) Positive räumliche Autokorrelation. b) Negative räumliche Autokorrelation. c) Keine räumliche Autokorrelation (Unabhängigkeit)](../media/img/Autocorrelation.png)
*Abbildung: a) Positive räumliche Autokorrelation. b) Negative räumliche Autokorrelation. c) Keine räumliche Autokorrelation (Unabhängigkeit).*

Die Existenz von räumlicher Autokorrelation hat mehrere wichtige Konsequenzen.

Erstens nehmen viele der häufigsten statistischen Analysen die Unabhängigkeit der Variablen an, die untersucht wird. Da es eine Abhängigkeit von der räumlichen Komponente gibt, muss diese Komponente als eine andere zu berücksichtigende Variable eingeführt werden, um sicherzustellen, dass die Ergebnisse solide sind.

Etwas Ähnliches passiert, wenn Daten einen räumlichen Trend haben (Werte einer Variablen hängen von der Position ab; zum Beispiel Temperaturwerte, die einen klaren Trend zeigen, wenn sich der Breitengrad ändert), da dies auch die Annahme außer Kraft setzt, dass Daten unabhängig sind.

Wenn eine positive Korrelation besteht, ist die statistische Inferenz weniger effektiv. Die gleiche Anzahl an Beobachtungen enthält weniger Informationen über die von der Variablen dargestellten Phänomene.

Die Folgen der räumlichen Autokorrelation sind jedoch nicht nur negativ. Wenn Punkte, die in der Nähe eines bestimmten Punktes liegen, mit ihm in Beziehung stehen und der Wert einer Variablen durch diese Nähe beeinflusst wird, kann dies verwendet werden, um Werte an einem beliebigen Punkt zu schätzen, wobei die Werte in einem Satz nahegelegener Punkte bekannt sein müssen. Das ist der Grundgedanke hinter den Interpolationsmethoden.

## Struktur

Sowohl die Daten selbst als auch die Eigenschaften des von ihnen repräsentierten Phänomens (wie die oben erwähnte räumliche Korrelation) haben eine gewisse Struktur. Diese Struktur kann relevante Auswirkungen auf die Analyseergebnisse haben und sollte berücksichtigt werden.

Die zwei grundlegenden statistischen Konzepte, die sich auf die räumliche Struktur eines Prozesses beziehen, sind Stationarität und Isotropie. Die Stationarität zeigt an, dass der Prozess translationsinvariant ist. Das heißt, seine Eigenschaften sind über den gesamten Raum konstant und es gibt keinen räumlichen Trend. Isotropie bedeutet, dass der Prozess rotationsinvariant ist und in allen Richtungen auf die gleiche Weise stattfindet.

## Grenzeffekte

Die Bereiche, in denen wir räumliche Analysen durchführen, haben Grenzen. Diese können künstlich sein, zum Beispiel die Grenze der Luftaufnahme, mit der wir arbeiten, oder natürlich. Wenn wir einen Wald in der Nähe eines Sees untersuchen, ist die Küste die Grenze des Waldes. Grenzen verfälschen das Ergebnis der Analyse, speziell für diejenigen Variablen, die aggregiert werden müssen (Dichte, etc., wie wir es für den Fall der MAUP gesehen haben)

In einigen Fällen kann sich der Grenzeffekt nur für die Grenzpunkte auswirken. In anderen können jedoch alle Punkte, die mit der Grenze verbunden sind oder irgendwie damit verbunden sind, beeinflusst werden, unabhängig von der Entfernung zu ihr.
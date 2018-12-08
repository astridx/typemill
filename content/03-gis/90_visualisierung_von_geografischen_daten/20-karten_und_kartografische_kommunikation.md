# Karten und kartografische Kommunikation

Theoretisch kann man Karten wir folgt beschreiben: Karten sind eine Kommunikationsmethode, 
die eine Sprache mit einem bestimmten Zweck verwendet: Karten möchten 
räumliche Beziehungen beschreiben. 
Eine Karte ist nichts anderes als eine symbolische Abstraktion eines realen Phänomens und 
weist daher ein gewisses Maß an Vereinfachung und Verallgemeinerung auf.

Diese visuelle Sprache wird zu einer kartographischen Sprache, 
wenn sie an den speziellen Fall der Erstellung von Karten angepasst wird und 
ihre Regeln benötigt werden, um Kartografie zu erstellen, 
die später für den Kartenbenutzer nützlich ist. 
All diese Ideen zur Kartenproduktion bilden das sogenannte kartographische Design.

Beim kartografischen Design müssen Entscheidungen getroffen werden. 
In unserem Fall müssen diese Entscheidungen vom GIS-Benutzer, 
der die Rolle des Kartographen übernimmt, getroffen werden. 
Diese Entscheidungen müssen sich am Ziel der Karte und der Zielgruppe orientieren. 
Abhängig von diesen Faktoren muss der Kartograph unter anderem folgende 
Punkte festlegen:
- die Projektion - die nicht immer die ursprüngliche der Daten sein muss 
- die Skala, der Maßstab oder der Zoom - abhängig hiervon ist 
die Anzeige der Details und der mögliche anzeigbare Bereich, 
- die Art der Karte - auf die Art der Karte werden wir später in diesem Kapitel 
noch einmal zurückkommen
- die zu verwendenden Symbole.

Es gibt zwei Hauptarten der Kartographie: 
- Basiskartographie (auch als fundamental oder topographisch bezeichnet) und 
- thematische Kartographie.

Historisch gesehen stellt die Basiskartographie die klassischen Karten dar.  
Also die Karte, die ursprünglich von Kartographen erstellt wurde. 
Vereinfacht ausgedrückt dient dieser Kartentyp dazu, 
genau zu beschreiben, was sich wo auf der Erdoberfläche befindet.

Die thematische Kartographie konzentriert sich auf die Darstellung von Informationen 
über ein bestimmtes Thema. 
Dieses Thema kann sehr vielfältig sein. Beispielsweise 
- physisch, 
- sozial, 
- politisch, 
- kulturell 
- ...
 
Nur rein topografische Themen bilden keine thematische Karte. 
Topografische Karten zählen zum Bereich der Basiskartographie.

Anderes ausgedrückt kann man kann auch sagen, 
dass die Basiskartographie physikalische Elemente wie 
einen Strommast, eine Küstenlinie, eine Straße oder ein Tal darstellt. 
Die thematische Kartographie hingegen konzentriert sich eher auf die Darstellung von 
Werten und Attributen.

Die thematische Kartografie verwendet eine Basiskarte, 
um dem Kartenbenutzer zu helfen, 
das räumliche Verhalten der dargestellten Variablen zu verstehen.
Außerdem wird so der der geografischen Kontext bereitgestellt. 
Eine Basiskarte ist also normalerweise in thematischen Karten enthalten.

## Arten von Informationen und deren Visualisierung

Wir wissen bereits, 
dass die thematische Komponente geografischer Informationen 
- numerisch oder 
- alphanumerisch sein kann.

Außderm wissen wir, dass numerische Variablen 
- nominal, 
- ordinal, 
- Intervalle oder 
- Verhältnisse sein können. 

Die Auswahl einer korrekten Symbologie entsprechend der Art der Informationen, 
mit denen wir arbeiten, ist der Schlüssel zum Erstellen einer effektiven Karte. 
Insbesondere müssen wir eine visuelle Variable verwenden, 
die die richtigen Eigenschaften (Organisationsebenen) für die Variable hat, 
die wir visualisieren möchten.

Zum Beispiel sind die assoziative Eigenschaft und die selektive Eigenschaft 
nur für qualitative Informationen von Interesse. 
Größe ist die einzige visuelle Variable, die wir verwenden können, 
die die quantitative Eigenschaft besitzt. Größe ist daher die einzige Eigenschaft, 
die verwendet werden sollte, um Verhältnisse darzustellen.

Im Folgenden sind einige der wichtigeren Ideen dazu, 
bezogen auf die oben genannten Arten von Informationen.

- **Numerisch**  
Numerische Informationen werden korrekt unter Verwendung der visuellen Variablenform dargestellt. 
Diese Information zeigt, was an den verschiedenen Orten einer Karte zu finden ist, 
und nicht wie viel gefunden wird, 
und sie ist eher mit der Basiskartographie als mit der thematischen Kartographie verbunden. 
Die Verwendung verschiedener Symbole für Punktelemente und Linienelemente 
ist eine übliche und sehr effektive Lösung. 
Für den Fall von Flächensymbolen sind Farbton und Textur die gebräuchlichsten Lösungen.  
Alphanumerische Informationen haben ähnliche Eigenschaften und die gleichen Ideen 
gelten für sie.

- **Ordinal**  
Da Werte der Variablen eine Reihenfolge definieren, 
wird eine visuelle Variable mit der geordneten Eigenschaft benötigt, 
um diese Art von Informationen korrekt zu visualisieren

- **Intervall und Verhältnis**  
Visuelle Variablen mit der geordneten Eigenschaft können in diesem Fall verwendet werden. 
Größe ist jedoch eine bessere Wahl, da es die einzige ist, 
die die quantitative Eigenschaft hat.
Werte werden normalerweise in Klassen gruppiert, 
sodass der gleiche Wert der visuellen Variablen 
(z. B. die gleiche Größe der Symbole oder der gleiche Farbwert) 
für verschiedene Werte der Variablen verwendet wird, 
die wir visualisieren. 
Dafür gibt es verschiedene Strategien, die versuchen, 
die Informationen zu maximieren, 
die die Karte überträgt. 
Die meisten Commons sind gleiche Intervalle, Intervalle, die Perzentile oder 
natürliche Intervalle verwenden 
(Intervalle, die versuchen, die Varianz innerhalb jeder Klasse zu minimieren).
Die Verwendung der einen oder anderen dieser Methoden kann sich in der Visualisierung 
bemerkbar machen, wie in Abbildung 11.4 gezeigt.

![Vergleich zwischen verschiedenen Methoden zur Definition von Intervallen](../media/img/IntervalClasses.png)
*Abbildung: Vergleich zwischen verschiedenen Methoden zur Definition von Intervallen.*

Es ist wichtig anzumerken, dass, 
obwohl Organisationsstufen ein erhöhtes Potenzial anzeigen 
(das heißt, mit einer Variablen wie Größe oder Wert können wir alle Informationen, 
die mit Farbton übermittelt werden können, übermitteln, 
da sie Eigenschaften mit einem höheren Niveau haben) 
ist es nicht immer besser, 
visuelle Variablen mit einem höheren Organisationsgrad zu verwenden, 
und es ist nicht wahr, 
dass sie immer besser sein werden als die mit einem niedrigeren. 
Zum Beispiel ist die Verwendung des visuellen Variablenwerts für eine Karte 
mit qualitativen Informationen 
(wie die Verwendung einer Rampe mit verschiedenen Blau-Tönen 
für eine Karte mit Informationen zum Bodentyp) 
möglicherweise keine gute Idee, 
da sie die geordnete Eigenschaft hat und dies verursachen könnte der Kartenbenutzer denkt, 
dass es eine Hierarchie gibt (dass einige Bodentypen "besser" sind als andere), 
was falsch ist.

## Kartenelemente Kartenkomposition

Eine Karte ist nicht nur der Teil, 
der die geografische Information darstellt. Eine Karte ist viel mehr. 
Sie beinhaltet auch eine Menge von Elemente, 
beispielswiese diejenige, die selbst geografischen Informationen beinhalten.

Ein korrektes Layout der Kartenelemente ist ebenso wichtig 
wie eine korrekte Symbologie, da diese, 
wie die Symbologie selbst, dem Kartenbenutzer helfen sollen, 
die enthaltenen Informationen besser zu interpretieren.

Die folgenden Elemente können zum Erstellen einer Karte verwendet werden (Abbildung):

![Karte mit den gebräuchlichsten Elementen](../media/img/MapElements.png)
*Abbildung: Karte mit den gebräuchlichsten Elementen*

- **Name oder Titel**  
Wird benötigt um zu wissen, welche Informationen in der Karte enthalten sind.
- **Autor**  
Der Ersteller der Karte.
- **Zusätzliche Informationen zur Karte**  
Zum Beispiel das verwendete Koordinatenreferenzsystem oder seine Erstellungsdaten.
- **Datenrahmen**  
Der Rahmen, der die gerenderten geografischen Informationen enthält. 
Es ist das zentrale Element und wird den größten Teil des Kartenraums nutzen.
- **Gradnetz**  
Über dem Datenrahmen wird der Inhalt der Karte auf der Erde lokalisiert und 
eine geografische Referenz bereitgestellt. 
Es dient dem gleichen Zweck wie die Skala und hilft, 
Entfernungen zu schätzen. 
Es wird normalerweise auf allen Skalen hinzugefügt, 
aber es ist bei kleinen Skalen relevanter.
- **Legende**  
Beim Entwurf einer Karte sollten wir versuchen, 
eine möglichst ausdrucksstarke Symbologie zu verwenden. 
Manchmal ist es jedoch nicht möglich, 
alle Informationen nur mit der Symbologie selbst zu versehen, 
und es wird eine Legende benötigt. 
Die Legende muss klar und einfach zu interpretieren sein. 
Eine Legende, die zu groß oder schwer zu verstehen ist, 
sagt uns wahrscheinlich, dass die von uns gewählte Symbologie verbessert werden kann. 
Die Legende und der Datenrahmen bilden eine Einheit und sollten zusammen sein 
(Legende innerhalb des Datenrahmens), 
nicht getrennt in verschiedenen Rahmen oder mit Grenzen zwischen ihnen, 
außer der Datenrahmen nutzt den gesamten Platz der Karte und 
es ist nicht möglich Beide Elemente optisch deutlich voneinander trennen.

- **Nordpfeil**  
Obwohl die Karten nach Konvention eine Süd-Nord-Ausrichtung haben 
(Norden ist oben auf der Karte), muss das nicht immer so sein. 
Ein nach Norden weisender Pfeil oder eine Kompassrose helfen dabei, 
die Kartenausrichtung zu verdeutlichen.
- **Rahmen**  
Der Kartenmaßstab sollte sowohl numerisch als auch grafisch angezeigt werden 
(Maßstabsleiste).
- **Locator-Karte**  
Ermöglicht dem Benutzer, 
die Karte in einem größeren geografischen Kontext zu finden. 
Es ist besonders wichtig im Fall von Kartenserien, 
die Beziehung zwischen der aktuellen Karte und 
dem Rest von ihnen als eine Indexkarte zu zeigen.
- **Detailkarten**  
Wird verwendet, wenn es einen Bereich gibt, 
den wir detaillierter anzeigen können. 
Das Gebiet, dem es entspricht, sollte auch in der Hauptkarte angegeben werden.

Es ist auch wichtig, 
dass die Karte ihren Zweck betont und den Elementen, 
die ihr besser dienen, mehr Bedeutung beimisst.
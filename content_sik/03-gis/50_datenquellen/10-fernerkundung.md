# Fernerkundung

Fernerkundung ist die Erfassung von Informationen über ein Objekt oder 
Phänomen ohne physischen Kontakt damit. Anstatt das Objekt selbst zu messen, 
misst es die Störungen - hauptsächlich die elektromagnetischen -, die es an 
seiner Umgebung verursacht. In unserem Fall wird es auf Objekte auf der 
Erdoberfläche angewendet.

Ein Fernerkundungssystem enthält die folgenden Elemente (Abbildung):

![Elemente in einem Fernerkundungssystem](../media/img/Elements_remote_sensing.png)
*Abbildung: Elemente in einem Fernerkundungssystem.*

- Eine Strahlungsquelle (A). Es kann natürlich oder künstlich sein. Die von der Quelle emittierte Strahlung erreicht die Erdoberfläche und wird durch die Anwesenheit der Objekte auf dieser Oberfläche verändert. Fernerkundung studiert diese Veränderung. Objekte selbst können ebenfalls Strahlung emittieren.
- Objekte (B), die mit Strahlung wechselwirken oder diese abgeben können, wie oben erwähnt.
- Eine Atmosphäre (C), durch die sich Strahlung von der Quelle zu den Objekten bewegt. Die Atmosphäre interagiert auch mit der Strahlung und verändert sie.
- Ein Empfänger (D), der die Strahlung empfängt, sobald sie von den Objekten emittiert oder verändert wurde. Der Empfänger misst die Intensität der Strahlung, die von verschiedenen Punkten in dem zu untersuchenden Bereich kommt, und erzeugt damit sein Endprodukt (in den meisten Fällen und das Bild).

In diesem Kapitel werden wir diese Elemente im Detail beschreiben. Um die ersten beiden zu untersuchen, werden wir auch einige Grundlagen über Strahlung und ihre Wechselwirkung mit Materie untersuchen. Um die Empfänger zu beschreiben, die Teil eines Fernerkundungssystems sind, werden wir sie in zwei Komponenten aufteilen: Sensoren und Plattformen.

Die Interaktion mit der Atmosphäre muss gesteuert werden, um ihren Einfluss zu eliminieren, da wir uns in den meisten Fällen für das Objekt auf der Erdoberfläche interessieren, nicht für die Atmosphäre selbst. Das Entfernen dieses Einflusses ist Teil der Nachbearbeitung der Daten. Diese Prozesse sind jedoch sehr komplex und gehen über den Rahmen dieses Buches hinaus, weshalb sie hier nicht erläutert werden.

## Elektromagnetische Strahlung

Elektromagnetische Strahlung wird durch Veränderungen der elektrischen und magnetischen Felder verursacht, die Wellen erzeugen, die jedem von ihnen entsprechen. Diese Wellen bewegen sich mit Lichtgeschwindigkeit und können mit den üblichen Parametern wie Wellenlänge und Frequenz beschrieben werden. Der Bereich von Frequenzen (und entsprechenden Wellenlängen) von elektromagnetischer Strahlung wird als elektromagnetisches Spektrum bezeichnet.

Das Spektrum ist in Bereiche unterteilt, die von der Wellenlänge abhängig sind, wie Gammastrahlen, Röntgenstrahlen, Ultraviolettbereich, sichtbarer Bereich, Infrarotbereich oder Mikrowellen (von kürzerer zu größerer Wellenlänge).

Die von einer Strahlungsquelle emittierte Strahlung wird durch das Vorhandensein von Objekten verändert, die sie absorbieren, übertragen oder reflektieren.

Diese drei Phänomene treten in Abhängigkeit von den Eigenschaften des Objekts und der Strahlung in einem anderen Verhältnis auf. Für die Fernerkundung ist die Strahlung, die reflektiert wird, von Interesse, da sie später gesammelt und zur Erzeugung der Datenausgabe verwendet werden kann.

Da jedes Objekt Strahlung mit unterschiedlichen Wellenlängen auf eine andere Weise reflektiert, kann dies als eine Eigenschaft eines Objekts betrachtet werden. Die besondere Antwort eines gegebenen Objekts und die Art und Weise, wie es eine gegebene Strahlung ändert (was von seiner Form, seinem Material usw. abhängt), wird als seine spektrale Signatur bezeichnet und kann verwendet werden, um das Objekt zu identifizieren.

## Sensoren und Plattformen

Die zwei wichtigsten technologischen Elemente in einem Fernerkundungssystem, die beide mit dem Empfänger zusammenhängen, sind der Sensor und die Plattform.

Der Sensor ist das Element, das die elektromagnetische Strahlung lesen und ihre Intensität für eine bestimmte Zone des Spektrums registrieren kann. Es kann eine einfache Fotokamera oder ein spezieller Sensor sein.

Passive Sensoren verwenden natürliche Strahlungsquellen (in den meisten Fällen Sonnenlicht) und messen diese Strahlung, wenn sie auf der Erdoberfläche reflektiert wird. Aktive Sensoren emittieren ihre eigene Strahlung und sammeln sie dann zurück, nachdem sie reflektiert wurden. Hier ist ein einfaches Beispiel, um dies besser zu verstehen: Eine Fotokamera ist ein passiver Sensor, während eine Fotokamera, die ein Blitzgerät verwendet, aktiv ist. Die von einem aktiven Sensor emittierte Strahlung muss kein sichtbares Licht sein (wie beim Blitz); der Sensor kann in anderen Bereichen des Spektrums emittieren.

Technologien wie Radar oder LiDAR (ähnlich wie Radar, aber mit Lichtpulsen anstelle von Radiowellen) basieren auf aktiven Sensoren.

Der Sensor ist auf einer Plattform montiert und führt seine Datenerfassung aus. Mehrere Sensoren können auf einer einzigen Plattform montiert werden.

Die zwei wichtigsten Arten von Plattformen sind diejenigen, die sich innerhalb der Erdatmosphäre befinden (hauptsächlich in Flugzeugen) und außerhalb (auf Satelliten).

Der Vorteil von Flugzeugen ist ihre Verfügbarkeit, da sie gesteuert werden können und jederzeit an jedem Ort der Erde eingesetzt werden können. Satelliten dagegen können nicht geführt werden, und ihre Bewegung wird durch einen Satz von Parametern, die als Umlaufbahnparameter bezeichnet werden und die die Umlaufbahn des Satelliten um die Erde definieren, festgelegt und definiert.

Umlaufbahnen können nach ihrer Rotationsachse oder ihren Bewegungen klassifiziert werden. Zwei besondere Fälle sind die geosynchronen Umlaufbahnen (der Satellit befindet sich an einem festen Punkt und seine Bewegung folgt der Erdrotation) und der heliosynchrone Umlauf (der Satellit passiert einen beliebigen Punkt auf seinem Weg, immer zur selben lokalen Sonnenzeit).

### Auflösungen

Die wichtigsten Parameter, die die Eigenschaften eines Fernerkundungssystems definieren, 
sind seine Auflösungen. Diese definieren den Detaillierungsgrad der Produkte, 
die es erstellt. Entscheidungen hängen sowohl vom Sensor als auch von der 
Plattform als einer einzelnen operativen Einheit und von den individuellen 
Eigenschaften jedes einzelnen ab.  

Allgemein werden vier Auflösungen unterschieden:

- Räumliche Auflösung. Sie gibt die Größe des kleineren Objekts an, das unterschieden werden kann. Wenn die Ausgabe ein Bild ist, ist die räumliche Auflösung die tatsächliche Größe des Bereichs, der durch ein einzelnes Pixel dargestellt wird.
- Die spektrale Auflösung zeigt die Amplitude jedes der Bereiche des registrierten Spektrums an. Es wird durch die Gesamtamplitude, die abgedeckt wird, und die Anzahl der Abschnitte definiert, in die es unterteilt ist. Die Messung, die jedem dieser Abschnitte entspricht, wird normalerweise in einem separaten Band in dem resultierenden Bild gespeichert.
- Die radiometrische Auflösung zeigt den Detaillierungsgrad der Intensitätsmessung für jeden der registrierten Spektralbereiche an.
- Die zeitliche Auflösung gibt die Zeit an, die der Sensor benötigt, um zu einem bestimmten Ort zurückzukehren. Dies ist nur für Orbitalsensoren sinnvoll und hängt von den Plattformeigenschaften wie Höhe und auch von den Sensoreigenschaften ab.

Aus technischen und theoretischen Gründen ist es nicht möglich, einen Sensor zu verwenden, bei dem alle oben genannten Auflösungen gleichzeitig maximiert sind. Einige Sensoren bevorzugen bestimmte Auflösungen, andere bevorzugen andere.

Bei der Verwendung von Bildern aus der Fernerkundung in einem GIS sollten wir überlegen, welche Auflösung wichtiger ist (um z. B. Elemente mit einer geringen Größe zu finden, ist eine hohe räumliche Auflösung erforderlich). Die Verwendung von Daten von verschiedenen Sensoren ist eine gute Strategie, um diese Einschränkungen zu überwinden.

## Photogrammetrie od fotogrammetrische Vermessung

Photogrammetrie ist die Technik, die benutzt wird, um die Form, die Größe und die Position im Raum irgendeines Gegenstandes zu studieren und genau zu bestimmen, unter Verwendung der Maße von den Fotographien. Von besonderem Interesse für GIS ist der Bereich der Photogrammetrie, bekannt als Luftfotogrammetrie, der Luftbilder verwendet und hauptsächlich zur Erzeugung von Höhendaten durch einen als Restitution bekannten Prozess verwendet wird.

Anstelle von Einzelbildern verwendet der als Stereofotogrammetrie bekannte Zweig der Photogrammetrie Bilderpaare, die jeweils von einem anderen Punkt aus aufgenommen wurden. Diese Bilder bilden ein Stereopaar und mit ihnen kann eine dreidimensionale Rekonstruktion der Originalszene erzeugt werden. Dies kann von einem Bediener verwendet werden, um die Szene mit Tiefe und Volumen zu sehen, so dass Geländeformen identifiziert und Höheninformationen erhalten werden können.

Wenn Satellitenbilder verwendet werden, können Stereopaare von diesen Plattformen und Sensoren erhalten werden, die eine Änderung des Blickwinkels erlauben, so dass im selben Satellitenpass Bilder eines gegebenen Bereichs von verschiedenen Punkten aufgenommen werden können.

Die Photogrammetrie kann analog oder digital sein, wobei die letztere mehr mit dem Gebiet des GIS verwandt ist.

Stereoplotter werden verwendet, um die Bilder, die das Stereopaar bilden, zu kombinieren und auszurichten. Aktuelle Stereoplotter werden analytische Stereoplotter genannt und enthalten Elemente aus GIS zusammen mit spezifischeren Elementen. Unter diesen finden wir spezifische Visualisierungssoftware und Peripheriegeräte wie 3D-Mäuse oder andere mechanische Elemente, die in analogen photogrammetrischen Geräten zu finden sind, so dass sich der Bediener leicht an diese neue Art von Werkzeugen anpassen kann.
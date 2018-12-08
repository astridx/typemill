# Webbasierte Geografische Informationssysteme

Einer der relevantesten Fortschritte in der Geschichte von GIS ist 
das Aufkommen des Geodatenmanagements im Internet[^1], also des Web-Mappings. 
Web-Mapping-Technologien werden verwendet, 
um GIS-Elemente als Teil von Websites zu integrieren. 
Hierbei kann der  Internet-Browser dann die Basisplattform sein, 
auf der die GIS-Funktionalität ausgeführt wird. 
Diese Technologien umfassen nicht nur die Elemente, 
die im Browser ausgeführt werden, 
sondern sind auch maßgeblich für die Gestaltung und Entwicklung anderer Elemente 
wie Remote-Datendienste, die nicht nur von Web Mapping-Anwendungen, 
sondern auch von Desktop-GIS verwendet werden. 
Desktop-GIS war Thema im vorherigen Kapitel.

Hier geht es also in erste Linie um Clients und Servers[^2]. 
Deshalb sehen wir uns das *Client-Server-Modell* als nächstes 
etwas ausführlicher an.

Ein **Server** ist das Element, 
das einen bestimmten Inhalt über das Netzwerk bereitstellt. Er dient. 
In unserem GIS-Kontext bedeutet dieser Inhalt im Wesentlichen geografische Daten. 
Der **Client** ist das Element, das die Daten anfordert, empfängt und damit arbeitet.

Ein Webbrowser ist ein Client, da er eine Anfrage stellt, 
um den Inhalt einer Website abzurufen und dem Benutzer zu zeigen. 
Wenn wir eine Webadresse in die Adressleiste eines Webbrowsers eingeben, 
stellen wir die Informationen bereit, 
die zum Herstellen der Verbindung zwischen dem Server und dem Client 
und zum Übertragen der Daten von einem zum anderen erforderlich sind.

Angenommen, Sie möchten die folgende Website besuchen:

https://astrid-guenther.de/texte

Die Anfragen werden basierend auf der Webadresse - 
technisch gesehen, einem Uniform Resource Locator (URL) - 
ausgeführt. 
Die Webadresse ist eine Referenz auf eine Web-Ressource, 
die ihren Speicherort in einem Computernetzwerk 
und eine Regel zum Abrufen angibt. Wir können es in folgende Teile teilen:

1. https: Das zu verwendende Protokoll, das definiert oder regelt, 
wie Client und Server miteinander kommunizieren.
2. astrid-guenther.de: Der Hostname. 
Dieser Teil identifiziert den Computer der als Server dient 
und der mit dem Netzwerk verbunden ist. 
Auf diesem Server ist die Seite gespeichert, die wir lesen möchten. 
Es ist eine lesbare Version eines numerischen Codes - der IP-Adresse[^3] -, 
der die Adresse angibt.
3. texte: texte ist nun die Webseite, die wir lesen möchten. 
Genau die unter allen, die der Server bereitstellt.

Der Prozess, der es uns ermöglicht, diese Seite in unserem Webbrowser zu lesen, 
umfasst die folgenden Schritte:

1. Der Client stellt die Anfrage.
2. Der Server-Computer wird identifiziert und die Anfrage wird an ihn gesendet.
3. Der Server bereitet die angeforderte Seite vor und sendet sie zurück 
an den Client (oder er sendet eine Fehlermeldung, 
falls die Seite nicht gefunden oder vorbereitet werden kann).
4. Der Client empfängt die Seite und rendert sie so, 
dass der Client sie lesen kann.

Abbildung 8.3 zeigt eine Zusammenfassung davon.

![Client-Server-Interaktionsmechanismus beim Besuch einer Website](../media/img/How_internet_works.png)
*Abbildung 8.3: Client-Server-Interaktionsmechanismus beim Besuch einer Website.*

Es wird also eine Verbindung zwischen Clients und Servern hergestellt. 
Eine beliebige Anzahl von Clients kann sich mit einem Server verbinden. 
Der Client erhält vom Server Daten, wenn er eine Anfrage stellt. 
In dieser Client-Server-Architektur verfügt der Server über die Daten, 
die über einen Dienst freigegeben werden.
Der Clients stellt nur Informationen über sich selbst bereit, 
die zum Validieren und Durchführen der gemeinsamen Datennutzung erforderlich sind.

Übertragen wir dies nun auf den Bereich GIS!

In Bezug auf Server können wir folgende Hauptfunktionen unterscheiden:

- **Server bietet gerenderte geografische Daten**   
Diese Server werden allgemein als Kartenserver bezeichnet - sie stellen Karten bereit. 
Das heißt: Sie erzeugen aus geografischen Daten Bilder und stellen diese zur Verfügung. 
Diese Bilder werden auch Kacheln genannt, da wie Kacheln an der Hauswand 
um die ganze Erde verteilt sind.
Wenn die Daten bereits ein Bild sind - beispielsweise eine Luft- oder eine 
Satellitenaufnahme - sendet der Server das Bild so wie es ist - allerdings (todo link) georeferenziert. 
Wenn es sich nicht um kein direkt anzeigbares Bildformat handelt erstellt der Server 
zunächst basierend auf den geografischen Daten ein Bild und stellt diese zur Verfügung.  
Die verwendeten grafischen Elemente oder Symbole werden oft für alle 
Anfragen gleich verwendet. Manchmal kann der Client die Darstellung beeinlussen. 
Der Client bestimmt immer die Dimensionen des angeforderten 
Kartenbildes - also den anzuzeigenden Bereich. Der Server bereitet das Kartenbild genau 
auf die gewünschte Größe vor.
- **Server bietet rohe geografische Daten**   
Eine flexiblere Option besteht darin, 
die geografischen Daten selbst unbearbeitet anzubieten. 
Der Client fordert die Daten an und kann sie, 
sobald sie über das Netzwerk übertragen wurden, beliebig verwenden. 
Für den Fall, dass die Daten visualisiert werden sollen, 
muss die Symbologie auf der Client-Seite eingestellt werden, 
da sich der Server nicht darum kümmert und die Rohdaten zur Verfügung stellt.
- **Server bietet das Ergebnis von Abfragen oder Queries**   
Eine andere Funktionalität, die der Server haben kann, 
ist, nicht nur den gesamten Satz von geographischen Daten auszuliefern, 
sondern nur einen Teil davon. Dies ist sinnvoll, wenn der Client ein bestimmtes 
Thema darstellen will.
Der Client kann einen Filter angeben und der Server erstellt aufgrund dieses Filters  
seine Antwort. 
Außerdem kann der Server beschreibende Werte über die Daten bereitstellen, die er hat. 
Der Client, der mit mehreren Diensten verbunden sein und die Werte abrufen kann, 
kann diese Werte verwenden, um zu filtern, welche Dienste verwendet werden 
sollen (z. B. nach dem Umfang ihrer Daten fragen und dann nur diejenigen 
auswählen, die Daten zu einem bestimmten Untersuchungsgebiet haben). 
Wie wir bereits gesehen haben, haben Metadaten in diesem Kontext eine 
große Relevanz, da sie es ermöglichen, dass diese Art von Abfragen 
effizient ausgeführt wird (und die entsprechenden Anfragen beantwortet werden).
- **Server führen Prozesse aus und erstellen neue Daten**.  
Schließlich kann ein Server neue Daten bereitstellen.  
Egal ob geografisch oder nicht. 
Die neuene Daten werden  aus geografischen Daten berechnet werden. 
Der Server stellt also einen Verarbeitungsservice bereit und 
verarbeitet die Daten, die als Teil der Anforderung an ihn übergeben werden. 
Die Anfrage kann die Daten selbst oder einen Verweis darauf enthalten. 
Wenn eine Referenz übergeben wird, befinden sich die Daten möglicherweise 
bereits auf dem Server oder oder auf einem anderen Server. 
Wenn sich die Daten bereits auf einem Server befinden 
wird der erste Server ein Client des zweiten Servers. 
Der erste Server, also der Client des zweiten Servers, 
die Daten vom zweiten Server ab, verarbeitet diese und sendet das Ergebnis an den 
ursprünglichen Client zurück. (Abbildung 8.4).

![Fernverarbeitungsdienst, der Daten von einem zweiten Server verwendet](../media/img/Remote_data_and_Services.png)
*Abbildung 8.4: Fernverarbeitungsdienst, der Daten von einem zweiten Server verwendet.*

Die Clients können in zwei Klassen unterteilt werden:

- **Heavy Clients** 
Heavy Clients sind unabhängige Anwendungen, die nicht auf einem anderen wie einem Webbrowser ausgeführt werden. Sie haben normalerweise eine größere Größe, da die Anwendung sich um die gesamte Programmlogik kümmern muss.  
Heavy Clients verarbeiten und verwenden Daten, die nicht von Webdiensten stammen, z. B. lokale Datendateien. Sie sind nicht nur Clients, sondern vollwertige Anwendungen, die auch ohne ihren Client-Teil funktionieren.  
Heutzutage sind die meisten Desktop-GIS selbst Heavy-Clients, da sie die Funktionalität eines klassischen GIS besitzen, aber auch Web-Services nutzen können.
- **Light Clients**  
Die Fähigkeiten von Light clients sind begrenzter. 
Sie laufen auf Web-Browsern und sind meist auf Daten von Servern angewiesen.
Ursprünglich konzentrierten sie sich auf die Visualisierung von Daten. 
Meist fügten sie Kartenansichte zu Websites hinzu. 
Heutzutage bieten sie erweiterte Funktionen wie Analysefunktionen oder die Möglichkeit 
Daten zu bearbeiten.  
Der Begriff Web-Mapping steht meist in Zusammenhang mit Light Clients.
während der Begriff Web-GIS für diejenigen mit mehr Funktionalität verwendet wird, die einige der traditionell in Desktop-GIS verwendeten Tools enthalten.


> **Heavy Client oder Fat Client**[^4] ist ein Begriff aus der elektronischen 
Datenverarbeitung und bezeichnet vollwertig ausgestattete, 
leistungsfähige Desktop-Computer mit ausreichender Rechenkapazität, 
Plattenspeicher, Disketten- und CD-ROM-Laufwerken sowie leistungsstarken Grafikkarten. 
Das Gegenstück dazu ist, je nach applikationsspezifischer Funktionalität, 
der Thin Client.  
Ein **Light client oder Thin Client** [^5] ist ein Client, 
das heißt ein Computer oder Programm, das auf die Hilfe eines Servers angewiesen ist, 
um seine Aufgaben zu erfüllen.




## Techniken mit Bezug zu Geografische Informationssystemen und deren Diensten

Zwei wichtige Techniken, die im Kontext der Client - Server - Architektur 
für geografische Daten verwendet werden, sind Tiling und Caching. 
Diese Techniken, ob auf einem Light-Client oder einem Heavy-Client implementiert, 
ermöglichen reaktionsschnellere Schnittstellen und reduzieren die Menge der 
über das Netzwerk gesendeten Daten. 
Dadurch werden die Probleme, die ein langsames Netzwerk verursachen kann, 
bis zu einem gewissen Grad überwunden. 
Beide werden hauptsächlich mit Kartenservern, also  
Servern, die gerenderte Bilder bereitstellen, verwendet.

> **Tiling oder Kacheln**[^6] bezeichnet im Gebiet der grafischen Benutzeroberflächen die 
kachelartige Anordnung von Fenstern nebeneinander, frei von Überdeckungen.  
**HTTP Caching oder Zwischenspeichern**[^7] ist eine Technik um Ressourcen 
(Dokumente, Bilder, Dateien allgemein) anhand bestimmter Kriterien 
in einem Cache zwischenzuspeichern, um unnötige Datenübertragungen, 
Serveranfragen zu vermeiden und Zugriffszeiten zu verringern. 


### Tiling
Tiling[^6] unterteilt die Bilder, mit denen der Client arbeitet, 
in kleinere, die ein Art Mosaik bilden. Durch die korrekte Verwaltung 
der Kacheln in diesem Mosaik kann die Menge der übertragenen Daten reduziert werden. 
Wenn die Anforderung an den Server gesendet wird, wird anstelle 
eines einzelnen Bildes eine Gruppe von ihnen angefordert. 
Obwohl dies die Datenmenge nicht reduziert, ermöglicht die gekachelte Struktur einen 
flexibleren und optimierten Umgang mit den Daten. todo link auf später

### HTTP Caching
HTTP Caching[^7] ist eine Technik, die nicht nur für Web-GIS verwendet wird, 
sondern als allgemeines Werkzeug im Kontext des Internets. 
Webbrowser speichern frühere Antworten von Webservern wie Webseiten 
und Bildern in einem so genannten Cache. 
Wenn Daten, die zuvor angefordert wurden, erneut angefordert werden, 
können diese aus dem Cache statt aus dem entsprechenden Server entnommen werden - 
was ist normalerweise schneller und effizienter.

### Kombination von Tiling und HTTP Caching
Die Kombination von Tiling[^6] und Caching[^7] erhöht die Reaktionsfähigkeit 
und führt zu einem optimierten Datenmanagement. 
Sehen wir uns in Abbildung 8.5 genauer an, wie das funktioniert. 

![Kombination von Tiling- und Caching-Techniken zur Optimierung der Datenverarbeitung in einer Web-GIS-Anwendung](../media/img/Tiling.png)
*Abbildung 8.5: Kombination von Tiling- und Caching-Techniken zur Optimierung der Datenverarbeitung in einer Web-GIS-Anwendung.*

Zu Beginn zeigt die Anwendung einen Bereich mit 20 Elementen oder Kacheln an. 
Alle diese Kacheln wurden bereits vom Server heruntergeladen und im 
Anwendungscache gespeichert. 
Dies bedeutet, dass bei erneuter Verwendung keine neuen Anforderungen an den 
Server gestellt werden müssen. 
Wenn der Anwendungsbenutzer den anzuzeigenden Bereich wie in der 
Abbildung dargestellt ändert, 
muss ein neues Bild mit genau der gleichen Größe wie das auf dem Bildschirm 
zu rendernde Bild, angefordert werden. 
Wenn jedoch Tiling und Caching angewendet werden, 
müssen wir nur das gesamte neue Bild in Kacheln unterteilen. 
Im Beispiel besteht der anzuzeigende Bereich aus 20 Kacheln.
Einige Kacheln, nämlich 12, wurden in einer früheren Anfrage gespeichert. 
Deshalb müssen wir bei der Änderung des Anzeigebereiches nur eine kleine Anzahl 
von neuen Kachelln anfordern - in unserm Fall 8. 
Die Menge an Daten, die für den Server angefordert und über das Netzwerk 
übertragen wird, ist viel kleiner.

Caching kann auch serverseitig implementiert werden. 
Wir haben gesehen, dass Kartenserver bereits gerenderte Bilder basierend 
auf einigen Daten bereitstellen. 
Das Rendern dieser Daten, 
also das Erstellen des Kartenbildes aus den geografischen Daten, 
kann zeitaufwendig sein.
Wenn das Rendern für jede Anforderung durchgeführt werden muss, 
bedeutet dies eine Menge Rechenaufwand für den Server. 
Stattdessen werden mit Caching Bilder in unterschiedlichen Skalierungen vorgerendert 
und zwischen gespeichert. 
Wenn nun eine Clientanforderung vom Server empfangen wird, 
muss das Bild nicht neu erstellt werden - das vorgerenderte Bild kann aus dem Cache 
abgerufen und ausgeliefert werden.

Eine neue Technik, die an Popularität gewinnt, ist der Vektor-Tiling[^8]. 
Mit dem gleichen Ansatz wie im Falle der Kachelung, 
die wir gerade gesehen haben (das heißt, die Daten in Stücke schneiden), 
werden Vektorschichten geteilt und nur die erforderlichen Daten werden 
an den Client gesendet.

Dadurch kann der Client Vektorebenen anfordern und verwenden 
und gleichzeitig reagieren. 
Ohne Vektorkacheln wäre dies für große Schichten unmöglich. 
Der Vorteil ist in diesem Fall, dass die Darstellung vom Client definiert werden kann. 
Auch wird die Benutzerfreundlichkeit verbessert, 
da zum Beispiel Übergänge aufgrund der Skalierbarkeit von Vektordaten 
fließender werden, wenn der Kartenmaßstab geändert wird.




## Standards

Um sicherzustellen, dass das Client-Server-System korrekt funktioniert, 
ist es wichtig zu definieren, 
wie die Kommunikation zwischen Servern und Clients stattfindet. 
Eine gewisse Normalisierung ist erforderlich, 
und es müssen gemeinsame und wohldefinierte Elemente 
sowohl vom Client als auch vom Server implementiert werden. 
Diese Verkehrssprache oder Lingua Franca[^9], 
die es Clients und Servern ermöglicht zu kommunizieren, nennen wir einen Standard.

Im Idealfall würde eine vollständige Einhaltung gemeinsamer Standards, also eine 
vollständige **Interoperabilität**, 
unabhängig von den verwendeten Formaten und Anwendungen bestehen. 
Clients und Server können sich unabhängig von ihren eigenen Eigenschaften 
miteinander verbinden. 
Standards sind das Element, das dies ermöglicht, 
da sie einen gemeinsames Rahmen definieren, 
in dem Clients und Server kommunizieren. 
Solange ein Client oder ein Server dem Standard folgt, 
kann er mit allen anderen kommunizieren, die diesem Standard auch folgen. 
Normen bieten **technologische Homogenität**.

Interoperabilität[^10] bedeutet, dass jedes Element des Client-Server-Systems 
durch ein anderes ersetzt werden kann und die Interaktion zwischen allen 
Teilen des Systems nicht beeinträchtigt wird. 
Ein Client oder Server kann verschiedene Funktionalitäten haben, 
aber unabhängig von seinem Ursprung (dem Hersteller) kann er mit den 
anderen Elementen interagieren, wenn alle denselben Standard implementieren.

Eine Norm[^11] gilt als solche, 
wenn sie von einer Gruppe oder Gemeinschaft verwendet wird, 
die sie akzeptiert, 
um die Merkmale eines Produkts oder einer Dienstleistung darin zu definieren. 
Standards können durch öffentliche Akzeptanz und Gewohnheit (de facto-Standards[^12]) 
festgelegt werden oder sie können rechtliche Anerkennung haben 
und von einer offiziellen Organisation vorgeschlagen werden (de jure-Standards[^12]).

Ein Standard[^13] ist **offen**[^14], wenn seine Definition **für jeden verfügbar ist**, 
der mehr darüber wissen und ihn für jede damit zusammenhängende Aktivität 
verwenden möchte.

Im Folgenden einige der grundlegenden Prinzipien, 
auf denen offene Standards basieren:

- **Verfügbarkeit**  
Offene Standards sind für jeden verfügbar, zu lesen und zu verwenden.
- **Maximales Wahlrecht des Endbenutzers**  
Offene Standards schaffen einen fairen, wettbewerbsfähigen Markt 
und sperren Benutzer nicht in der geschlossenen Umgebung eines bestimmten Anbieters.
- **Keine Lizenzgebühr**  
Die Implementierung eines Standards ist freiwillig und im Gegensatz zu 
einem Patent kostenlos.
- **Keine Diskriminierung**  
Offene Standards und die dahinter stehenden Organisationen behandeln alle Nutzer gleich - 
niemand wird bevorzugt.
- **Erweiterbarkeit oder Erstellung von Teilmengen**  
Standards können um zusätzliche Elemente erweitert oder auf weniger 
detaillierte Teilmengen reduziert werden.

Um die Auswirkungen eines Standards im Zusammenhang mit GIS zu verstehen, 
werfen wir einen Blick auf Abbildung 8.6, 
die eine nicht interoperable Architektur darstellt, die keine Standards verwendet.

![Nicht interoperable Architektur](../media/img/Non_interoperable.png)
*Abbildung 8.6: Nicht interoperable Architektur*

Daten, die in jeder Datenbank gespeichert sind, sind nur mit einem Client verfügbar, der dem Server entspricht, der diese Daten bereitstellt. Die übrigen Daten sind für diesen Client nicht verfügbar. Jede Client-Server-Datenbankgruppe ist eine unabhängige Insel, die technologisch von den anderen isoliert ist.

Zu den Nachteilen einer solchen nicht interoperablen Architektur gehören:

- **Verschwendung von Ressourcen**  
Jeder Dienst muss seine eigenen Daten verwalten. 
Das ist komplex und verursacht höhere Kosten als das Teilen von 
Daten mit anderen kompatiblen Diensten.
- **Wissen zu mehrere Clients muss vorliegen**  
Da wir für jeden Dienst einen anderen Client benötigen, 
muss der Benutzer mit allen vertraut sein. 
Die Möglichkeit, nur einen Client zu verwenden, 
reicht nicht aus, um alle verfügbaren Daten zu verwenden, 
da dieser Client nur auf einen kleinen Teil all dieser Daten zugreifen kann.
- **Die Kombination von Daten ist nicht möglich**  
Zwei Datensätze, die über zwei verschiedene Dienste verfügbar sind, 
können nicht im selben Client verwendet werden, 
da sie nicht mit den entsprechenden Servern kommunizieren können.
- **Die Kombination von Funktionalitäten ist nicht möglich**  
Wenn Daten nur für einen bestimmten Client verfügbar sind, 
kann die Funktionalität in einem anderen Client nicht für diese Daten verwendet werden. 
Wenn Sie mit diesen Daten arbeiten, beschränken sich die Möglichkeiten 
des Benutzers auf das, was der entsprechende eine Client tun kann.

Sehen wir uns nun eine vollständig interoperable Architektur an, 
die auf offenen Standards basiert (siehe Abbildung 8.7).

![Interoperable Architektur](../media/img/Interoperable.png)
*Abbildung 8.7: Interoperable Architektur*

In diesem Fall gibt es einen Server, 
der die Dienste für jede Datenbank verwaltet und anbietet. 
Aber: Alle Clients können auf alle Server zugreifen, 
da sie auf offenen Standards basieren und die Kommunikation 
zwischen zweien möglich ist.

## Relevante Standards in GIS

Die häufigsten Standards für geografische Informationen werden vom 
Open Geospatial Consortium (OGC) erstellt und gefördert. 
Das OGC ist eine internationale Non-Profit-Organisation, 
die es sich zur Aufgabe gemacht hat, offene Standards für die globale 
Geodatengemeinschaft zu schaffen.

Einige der wichtigsten OGC-Standards sind die folgenden:

- WMS  
Um Karten (Bilder) zu bedienen
- WCS  
Um Coverages zu bedienen (derzeit nur Raster-Layer).
- WFS  
Um geographische Merkmale und Attribute (Vektorschichten) zu dienen. Es kann auch die Bearbeitung von Funktionen vom Client aus ermöglichen.
- WPS  
Um Remote-Verarbeitungsdienste zu bedienen.
- GML  
Um geografische Informationen zu speichern.
- CSW  
Abfragen an einen Katalog erstellen, der geografische Daten enthält

Jeder dieser Standards wird in einer entsprechenden Spezifikation beschrieben, 
die Änderungen und Verbesserungen unterliegt. 
Für jede von ihnen existieren mehrere Versionen.

Zu diesen Standards gehören auch solche, die von Organisationen wie 
ISO oder W3C mit einem allgemeineren Umfang, 
aber auch im Zusammenhang mit GIS wichtig sind. 
Zu den wichtigsten Standards gehören die **ISO-Standards** und die **W3C-Standards**.
Die ISO-Standards legen fest **wie Metadaten gespeichert werden**. 
Die W3C-Standards **regeln die Kommunikation über das Internet**.




[^1]: https://de.wikipedia.org/w/index.php?title=Geodatenmanagement&oldid=178920482
[^2]: https://de.wikipedia.org/w/index.php?title=Client-Server-Modell&oldid=180615857
[^3]: https://de.wikipedia.org/w/index.php?title=IP-Adresse&oldid=180307356
[^4]: https://de.wikipedia.org/w/index.php?title=Fat_Client&oldid=168762301
[^5]: https://de.wikipedia.org/w/index.php?title=Thin_Client&oldid=177785603
[^6]: https://de.wikipedia.org/w/index.php?title=Tiling_(Computer)&oldid=167093744
[^7]: https://de.wikipedia.org/w/index.php?title=HTTP_Caching&oldid=177036286
[^8]: http://doc.arcgis.com/de/arcgis-online/reference/tile-layers.htm#ESRI_SECTION1_8F68399EB47B48FF9EF46719FCC96978
[^9]: https://de.wikipedia.org/wiki/Verkehrssprache
[^10]: https://de.wikipedia.org/w/index.php?title=Interoperabilit%C3%A4t&oldid=174308275
[^11]: https://de.wikipedia.org/w/index.php?title=Normung&oldid=180706546
[^12]: https://de.wikipedia.org/w/index.php?title=De_jure/de_facto&oldid=178765180
[^13]: https://de.wikipedia.org/w/index.php?title=Standard&oldid=177624274
[^14]: https://de.wikipedia.org/w/index.php?title=Offener_Standard&oldid=162881849


*[GIS]: Geografisches Informationssystem / Geografische Informationssysteme
*[GRASS]: Geographic Resources Analysis Support System
*[ESRI]: Environmental Systems Research Institute


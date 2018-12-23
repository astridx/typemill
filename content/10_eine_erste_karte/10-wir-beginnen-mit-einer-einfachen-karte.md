# Eine Karte mit Leaflet erstellen
[](#){#EineKarteMitLeafletErstellen}

## Wir beginnen mit einer einfachen Karte

Um eine Karte mit Leaflet auf einer Internetseite anzuzeigen, 
reichen wenige Schritte aus:

1. Integrieren Sie die notwendigen JavaScript und Cascading Style Sheet Dateien (CSS). 
2. Erstellen Sie ein HTML-Element – üblicherweise ein `<div>`-Element – in dem Ihre Karte angezeigt werden soll. 
3. Erstellen Sie das JavaScript Karten-Objekt. 
4. Fügen Sie eine Schicht mit Kacheln – einen Tile-Layer – zum Karten-Objekt hinzu. 
 
Noch vor Schritt 1 erstellen wir eine einfache HTML-Datei. 
Diese Datei ist die Grundlage für die Beispiele hier im Buch. 
Den Programmcode für die einfache HTML-Datei sehen Sie im nachfolgenden 
Programmcodebeispiel. Fügen Sie diesen Programmcode in eine Datei ein und 
speichern diese Datei ab.

```
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8"/>
<title>Eine OSM Karte mit Leaflet</title>
</head>
<body>
</body>
</html>
<!--999.html-->
```

Ein Aufruf dieser Datei in Ihrem Browser öffnet zunächst nur ein 
leeres Browser-Fenster. Nur der Titel der Seite ist in der Titelleiste des 
Browsers abzulesen. In den nächsten vier Kapiteln erfahren Sie, wie Sie die 
digitale Landkarte in das Fenster bekommen. Vier Kapitel hört sich aufwendiger 
an. Das ist es aber nicht. Fangen Sie an und Sie werden sehen, dass Sie schon 
in wenigen Minuten die Karte präsentieren können.

[](#){#IntegrierenSiedienotwendigenJavaScriptundCascadingStyleSheet}
### Integrieren Sie die notwendigen JavaScript und Cascading Style Sheet Dateien

Sie haben zwei Möglichkeiten die notwendigen Dateien in Ihr HTML-Dokument zu integrieren.

1. Binden Sie die Dateien über ein CDN in Ihr HTML-Dokument ein. 
2. Kopieren Sie die Dateien und binden Sie die lokale Kopie in Ihr HTML-Dokument ein. 

> Ein [Content Delivery Network](https://de.wikipedia.org/wiki/Content_Delivery_Network) 
oder Content *Distribution* Network (CDN) ist ein
Netz von Servern, das über das Internet verbundenen ist. Die
Server in diesem Netzwerk bieten Inhalte zum Download an.

#### Leaflet über ein Content Delivery Network einbinden

Sie können Leaflet mithilfe eines CDN nutzen. So müssen Sie die Dateien 
nicht selbst herunterladen. Es ist lediglich eine Verlinkung nötig. 
Mit der richtigen Verlinkung wird Leaflet automatisch über das CDN heruntergeladen, 
wenn ein Website Besucher Ihre Website aufruft. Im nachfolgenden Programmcodebeispiel 
sehen Sie den Text für die Verlinkung zum Aufruf der Leaflet-Version 1.2.0 in 
fett formatiert.

```
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8"/>
<title>Eine OSM Karte mit Leaflet</title>
* <link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css" />
* <script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js"></script>
</head>
<body>
</body>
</html>
<!--index_998.html-->
```

> Welche Leaflet-Versionen Ihnen über das CDN zur Verfügung stehen, können
Sie jederzeit unter der Adresse http://leafletjs.com/download.html
nachlesen.

Auch wenn die Dateien der Leaflet Bibliothek nun automatisch über das CDN heruntergeladen werden: 
Ein Aufruf Ihrer Datei in Ihrem Browser öffnet immer noch ein leeres Browser-Fenster. 
Erst im letzten Schritt, im Kapitel *[Fügen Sie eine Schicht mit Kacheln – einen Tile-Layer – zum Karten-Objekt hinzu](#FuegenSieEineSchichtMitKachelnHinzu),* wird die Karte sichtbar.

> Fast alle modernen Browser unterstützen Subresource Integrity[^1] (SRI) und auch 
Leaflet verwendet diese
Sicherheitsfunktion. SRI steht für die Überprüfung der Integrität
von Dateien die im Internet verwendet werden. Mithilfe dieser
Funktion können Sie sich davor schützen, dass nachträglich veränderte Dateien auf Ihrem
Server ausgeführt werden. Die Dateien könnten beispielsweise bei der Übertragung im Internet verändert werden. Wenn Sie SRI nutzen, erhalten Sie immer exakt die Version, die
Ihnen auch ausgeliefert werden sollte – oder eine
Fehlermeldung. Dabei wird auf eine Prüfsumme – also einen
Hash-Wert – zurückgegriffen. Diese Prüfsumme macht die Datei eindeutig erkennbar. Um potenzielle Sicherheitsprobleme zu vermeiden, empfehle ich
Ihnen SRI zu nutzen, wenn Sie Leaflet über ein CDN einbinden. Wie
Sie dies genau handhaben, finden Sie unter der Adresse http://leafletjs.com/download.html .

#### Eine lokale Leaflet-Kopie einbinden
[](#){#EineKarteMitLeafletErstellenEinelokaleLeafletKopieeinbinden}

Eine zweite – vielleicht etwas kompliziertere – Möglichkeit ist, die 
Leaflet-Dateien selbst herunterzuladen. Die aktuellen Versionen finden Sie unter 
der Adresse http://leafletjs.com/download.html . Diese müssen Sie anschließend auf 
dem eigenen Server verfügbar machen und in Ihre Website einbinden.  
Diese Variante hat den *Vorteil*, dass Sie nicht von einem CDN Server abhängig sind. 
Somit haben Sie mehr Sicherheit. Sie wissen genau, welche Datei Sie auf Ihrem Server 
abgelegt haben und haben Einfluss auf die Konfiguration Ihres Servers.  
*Nachteilig* ist dabei allerdings, dass Sie sich selbst um alles kümmern müssen. 
Sie müssen selbst die Dateien kopieren und sicherstellen, dass Sie die passende 
Version von Leaflet nutzen. Aktualisierungen müssen Sie selbst vornehmen.

Im nachfolgenden Codebeispiel sehen Sie – fett hervorgehoben – das Einbinden von 
Leaflet unter der Annahme, dass Sie die heruntergeladenen Dateien - relativ 
zu Ihrem HTML-Dokument ein Verzeichnis höher - im Unterverzeichnis `/leaflet` auf 
Ihrem Webserver abgelegt haben.

>  Wenn Sie mit relativen Pfadangaben[^2] arbeiten, 
setzen Sie die Links innerhalb eines
Projektes mit Hilfe von Punkten. Der große Vorteil von relativen
Pfadangaben ist, dass Sie ein Projekt jederzeit in ein anderes
Verzeichnis kopieren können ohne Pfadangaben korrigieren zu müssen.
Bei einer relativen Pfadangabe bedeuten die Punkte folgendes:  
Ein Punkt gefolgt von einem Schrägstrich (`./datei.html`) zeigt auf
eine Datei, die sich im gleichen Verzeichnis befindet.  
Zwei Punkte gefolgt von einem Schrägstrich (`../datei.html`)
zeigen auf eine Datei, die sich ein Verzeichnis höher
befindet.  
Zweimal zwei Punkte gefolgt von einem Schrägstrich
hintereinander (`../../datei.html`) 
zeigen auf eine Datei, die sich zwei Verzeichnisse höher befindet.

`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<meta charset="utf-8"/>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
**`<link rel="stylesheet" href="../leaflet/leaflet.css" />`**  
**`<script src="../leaflet/leaflet.js"></script>`**  
`</head>`  
`<body>`  
`</body>`  
`</html>`  
`<!--index_998a.html-->`  


Auch wenn Leaflet nun lokal geladen wird, zeigt ein Aufruf dieser Datei in Ihrem Browser 
immer noch ein leeres Browser-Fenster. Erst im letzten Schritt - 
im Kapitel *[Fügen Sie eine Schicht mit Kacheln – einen Tile-Layer – zum Karten-Objekt hinzu](#FuegenSieEineSchichtMitKachelnHinzu)*  wird die Karte sichtbar.

> Vielleicht fragen Sie sich, warum ich den Link zur CSS-Datei mithilfe 
eines selbst-schließenden Tags – also einem *unary* Tag – geschrieben habe, 
aber für das Tag, in dem das Skript eingebunden wird, zwei separate 
Tags – also ein *binary*
Tag – verwendet habe.  
**`<link`** `rel="stylesheet" href="../leaflet/leaflet.css"`**`/>`**  
**`<script`**`src="../leaflet/leaflet.js"`**`></script>`**  
HTML unterscheidet zwischen Tags, die nie
Inhalt enthalten können – nämlich den *void*-Tags –, und
solchen, die prinzipiell Inhalt enthalten können. Im ersten Fall
muss ein selbst-schließendes *unary* Tag verwendet werden.
Hierzu gehört das <link>-Tag[^3] .
Im zweiten Fall darf kein selbst-schließendes *unary* Tag
benutzt werden – auch dann nicht, wenn das Tag tatsächlich leer
ist. Hierzu gehört das <script>-Tag[^4] .


#### Leaflet performant einbinden – defer oder async

In diesem Kapitel erkläre ich Ihnen, wie Sie Leaflet in Ihre Website einbinden 
können, ohne den Ladeprozess der Webseite zu unterbrechen. Falls Sie noch unsicher 
in der Anwendung von JavaScript sind, überspringen Sie dieses Kapitel am 
besten erst einmal. Das Beachten der Performance sollten Sie erst angehen, 
wenn Sie die ersten Karten selbst erstellt haben.

##### Was passiert genau, wenn eine Website geladen wird die im Kopfbereich ein Skript einbindet?

Sehen wir uns zunächst einmal an, was genau passiert, wenn ein Browser eine 
Website mit einem `<script>`-Tag lädt.

1. Als erstes lädt der Browser den Text der HTML-Seite. 
2. Als nächstes beginnt er, den HTML-Code zu analysieren, also zu parsen. 
3. Nun trifft der Parser auf das `<script>`-Tag, welches auf eine externe Skript-Datei verweist. 
4. Der Browser fordert die Skript-Datei an. Einstweilen blockiert und stoppt der Parser seine Arbeit. 
5. Je nach Größe der Datei ist das Skript nach einiger Zeit vollständig heruntergeladen und wird anschließend ausgeführt. 
6. Nun endlich kann der Parser seine Arbeit fortsetzten und den Rest des 
HTML-Dokuments analysieren und am Ende im Browser anzeigen. 

Wenn Sie sich diese Abfolge ansehen, können Sie sich vorstellen, dass Punkt vier 
das performante Laden der Website negativ beeinflusst. Der Ladevorgang der Website 
macht praktisch eine Pause. Solange bis alle Skripte heruntergeladen sind, passiert 
nichts mehr. Und wenn es eine Sache gibt, die Website-Besucher und Suchmaschinen nicht 
mögen, dann ist dies die Wartezeit beim Aufbau der Website.

##### Wie können Sie die Ladezeit positiv beeinflussen?

Um das im vorherigen Abschnitt beschriebene Problem zu umgehen wurde früher oft empfohlen, den JavaScript-Code möglichst nah am schließenden `<body>`-Tag in die Website zu integrieren. Zu dieser Empfehlung gibt es mit HTML5 zwei gute Alternativen – nämlich die Attribute `defer` und `async`.

Sofern Sie das Attribut `defer`[^5] verwenden, wird das Skript ausgeführt, wenn das HTML-Dokument geladen und für die Ansicht umgewandelt - also geparst - ist. Zum anderen können Sie das Attribut `async`[^6] einsetzten. Mit `async` wird Ihr Skript asynchron mit dem HTML-Dokument ausgeführt. Wenn Sie keines dieser Attribute explizit angegeben, wird erst das vollständige Skript geladen und ausgeführt und erst dann wird das Laden und Parsen des HTML-Dokuments fortgesetzt.

##### Was sollten Sie beim Einsatz von defer oder async mit Leaflet beachten?

Wenn Sie Ihre Karte auf Ihrer Website anzeigen, werden Sie nicht nur das 
Leaflet-Skript laden. Sie werden später noch eigenen JavaSript-Code schreiben. 
Dieser eigene Code setzt das Laden des Leaflet-Skripts voraus. 
Aus diesem Grund müssen Sie sicherstellen, dass die Leaflet Bibliothek vollständig 
geladen ist, bevor Ihr eigener Code ausgeführt wird. Dies können Sie mithilfe 
des *Eventhandlers*[^7]: `load`[^8].  

Obwohl Ihr eigenes Skript voraussetzt, dass Leaflet vollständig geladen ist, 
können Sie das Attribut `async` verwenden. Sehen Sie selbst: Das folgende einfache 
Beispiel zeigt es Ihnen.

`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.3/dist/leaflet.css"/>`  
`</head>`  
`<body>`  
`<div id="map" style="width: 600px; height: 400px"></div>`  
`<script src="mymap_99.js" **async**></script>`  
`<script src="https://unpkg.com/leaflet@1.3.3/dist/leaflet.js" **async**></script>`  
`</body>`  
`</html>`  
`<!--mymap_99.html-->`  

In ihrem eigenen Skript `mymap_99.js` müssen Sie mithilfe 
von `window.addEventListener('load', function() ... )` das Laden des 
vollständigen HTML-Dokuments abwarte.

**`window.addEventListener('load', function()`**
`{`  
`var map = L.map('map',`  
`{`  
`center: [50.27264, 7.26469],`  
`zoom: 10`  
`});`  
`L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(map);`  
`},`  
`false);`  
`<!--mymap_99.js-->`  

Alle weiteren Beispiele hier im Buch habe ich ohne das Attribut `async` 
erstellt, weil ich den Schwerpunkt auf die Verwendung von Leaflet 
selbst setzen wollte.

### Erstellen Sie ein Element in dem Ihre Karte angezeigt werden soll

Das Einfügen eines HTML-Elements in unser Grundgerüst dürfte für Sie kein Problem 
darstellen. Der Vollständigkeit halber habe ich diesen Schritt hier trotzdem eingefügt.

Setzen Sie ein `<div>`-Element mit einer bestimmten `ID` an die Stelle in Ihrem 
HTML-Dokument, an der Sie Ihre Karte anzeigen möchten. 
Stellen Sie dabei sicher, dass das `<div>`-Element, also der Kartencontainer, 
eine definierte Höhe hat.

> Der einfachste Weg einem HTML-Element eine feste Höhe zuzuordnen, ist das `style`-Attribut
– also direkt im HTML-Element selbst. Weil hier im Buch *Leaflet* das
Hauptthema ist, verwende ich für das Einbinden von Stylesheets in
den Beispielen diese einfache Methode. Durch das direkte Festlegen von
Formaten gehen allerdings im praktischen Einsatz viele Vorteile
verloren. Alternative Varianten zum Einbinden von Stylesheets finden
Sie unter anderem unter der Adresse https://wiki.selfhtml.org/wiki/CSS/alternative_Stylesheets .

Im nachfolgenden Programmcodeausschnitt sehen Sie die relevante Zeile fett formatiert.

`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="../leaflet/leaflet.css"/>`  
`<script src="../leaflet/leaflet.js"></script>`  
`</head>`  
`<body>`  
**`<div style="height: 180px;" id="mapid"></div>`**  
`</body>`   
`</html>`  
`<!--index_997.html-->`  

So, nun ist das HTML-Dokument bereit ein Leaflet Kartenobjekt zu initialisieren 
und interessante Dinge mit ihm anzustellen.

### Erstellen Sie das Karten-Objekt

Nun wird es spannend. Wir erstellen das erste Skript. Dabei beginnen wir mit dem 
Erstellen des Karten-Objektes. Im nachfolgenden Programmcodeausschnitt sehen Sie die erste Zeile des Skripts fett formatiert.

`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="../leaflet/leaflet.css"/>`  
`<script src="../leaflet/leaflet.js"></script>`  
`</head>`  
`<body>`  
`<div style="height: 180px;" id="mapid"></div>`  
**`<script>`**  
**`var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);`**  
**`</script>`**  
`</body>`  
`</html>`  
`<!--index_996.html-->`  


Was haben wir genau gemacht? Wir haben mit dem Befehl `var mymap = L.map('mapid')` 
ein neues Objekt – oder eine neue Instanz – der Klasse `map` erstellt und 
dieser den Namen `mymap` gegeben.

[](#){#Fabrikmethode1}
> Sie frage sich nun vielleicht, wie wir 
eine neue Instanz ohne die Verwendung des Schlüsselwortes **`new`** 
erstellen konnten? Die Antwort ist einfach: Die Leaflet-Klassen sind mit 
einem Großbuchstaben – beispielsweise **`L.Map`**–benannt und diese 
müssen mit `new` erstellt werden. Es gibt aber Shortcuts mit Kleinbuchstaben
 – **`L.map`** – die aus Bequemlichkeitsgründen von den Leaflet-Programmierern
für Sie erstellt wurden. Leaflet setzt hier das Entwurfsmuster Fabrikmethode[^9] 
(englisch factory method) ein. Das Muster beschreibt, wie ein Objekt
durch Aufruf einer Methode anstatt durch direkten Aufruf eines Konstruktors erzeugt wird.  
Wollen Sie sich dies selbst ansehen? Die Funktion `L.map()` der Klasse `L.Map` 
finden Sie auf Github ganz am Ende in der Datei `map.js`[^10]. Ein weiteres Beispiel 
finden Sie zu Beginn des Kapitels [Custom Markers](#Fabrikmethode2).

Das Festlegen des Kartenmittelpunktes mithilfe der Koordinaten `[50.27264, 7.26469]` 
und der Methode `setView()  `und die Angabe der Zoomstufe 13 ist optional. 
Ich empfehle Ihnen, diese Werte immer mitzugeben. 
Denn: Es ist für jeden ärgerlich eine Karte zu sehen, die die ganze Welt anzeigt – 
die relevanten Daten befinden sich aber alle in Gering, einem kleinen Dorf 
in der deutschen Eifel.

> Sagen Ihnen die  *Koordinaten*  in der Form [50.27264, 7.26469] nichts und möchten 
Sie gerne mehr zum Thema geografische Koordinaten erfahren? Dann lesen den Exkurs 
im Kapitel [Exkurs: Geographische Koordinaten](./exkurs-geografische-koordinaten#ExkursGeografischeKoordinaten).

Sie verfügen nun über ein Leaflet Karten-Objekt, mit dem Sie eine Karte anzeigen können. Sie müssen dem  *Karten-Objekt* noch mitteilen, welches  *Kartenbild* - also welche Grafiken - es anzeigen soll. Dies tun Sie, indem Sie eine Schicht mit Kacheln, also einen *Tile-Layer*, zum Karten-Objekt hinzufügen. Wie Sie dies genau tun, zeige ich Ihnen im nächsten Kapitel.

[](#){#FuegenSieEineSchichtMitKachelnHinzu}
### Fügen Sie eine Schicht mit Kacheln – einen Tile-Layer – zum Karten-Objekt hinzu

Der letzte Schritt beim Erstellen der Karte ist das Hinzufügen der Kachel-Schicht. Diese Schicht – oder dieser Layer – kann als eine Art Basiskarte angesehen werden. Es handelt sich um die Grafiken, auf der die Geoobjekte, die wir hier im Buch erarbeiten, dargestellt werden. Also die Imagedateien.

Kacheln zum Anzeigen in einem digitalen Kartenobjekt werden als Service von unterschiedlichen Providern angeboten. Im nächsten Kapitel werde ich Ihnen genauer erläutert, dass diese Kacheln normalerweise als 256 Pixel x 256 Pixel Images angeboten werden und warum die URL zum Aufruf der Kacheln die etwas kryptisch wirkenden Zeichen  `/{z}/{x}/{y}.png`  enthält.

Ich verwende hier das Angebot von http://www.openstreetmap.org zur Darstellung der Karte. Den Programmcode zum Einbinden der Imagedateien vom OpenStreetMap Tile-Server habe ich für Sie im nachfolgenden Programmcodebeispiel fett hervorgehoben. Die rechtlichen Voraussetzungen zur Verwendung der Kacheln des Openstreetmap-Servers finden Sie unter der Adresse https://operations.osmfoundation.org/policies/tiles.

`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="https://unpkg.com/leaflet@1.1.0/dist/leaflet.css"/>`  
`<script src="https://unpkg.com/leaflet@1.1.0/dist/leaflet.js"></script>`  
`</head>`  
`<body>`  
`<div style="height: 180px;" id="mapid"></div>`  
`<script>`  
`var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);`  
**`L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);`**  
`</script>`  
`</body>`  
`</html>`  
`<!--index_995.html-->`  

Was haben wir genau gemacht? Wir haben ein `TileLayer`-Objekt erstellt und diesem 
die URL des OpenStreetMap-Servers übergeben. Außerdem haben wir die 
Methode  `addTo()`  aufgerufen und dieser Methode unser Karten-Objekt  `mymap`  
als Parameter übergeben. So weiß Leaflet nun genau, welche Bilder es wo abrufen 
soll und kann die Kartenschicht zeichnen.

> Leaflet ist so programmiert, dass Sie die
verschiedenen Methoden verketten können. Dies ist möglich, weil die
unterschiedlichen Methoden Objekte zurückgeben, die wieder
Funktionen enthalten.
So konnten wir `.addTo(mymap)` einfach an `L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')` anhängen.
Alternativ hätten wir zuerst ein TileLayer Objekt erstellen müssen und 
hätten erst im nächsten Schritt die Methode `addTo()` aufrufen können.  
`var x = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png');`  
`x.addTo(mymap);`

Fertig! Sie haben nun eine vollständige Karte erstellt. Zählen Sie nach: 
In diesen vier Schritten haben Sie gerade einmal fünf Zeilen Programmcode eingegeben.

Standardmäßig – wir haben ja bisher noch keine Optionen übergeben –  sind alle 
Maus- und Touch-Interaktionen auf der Karte aktiviert. Sie können die Karte 
vergrößern und verkleinern und in der rechten unteren Ecke befindet sich ein 
Hinweis darauf, dass die Karte mit Leaflet erstellt wurde.
Sie können nun die ganze Welt auf dieser Karte erkunden.
In der nachfolgenden Abbildung sehen Sie diese Karte – so sollte diese bei Ihnen aussehen, wenn Sie meinem Beispiel gefolgt sind.

![Screenshot der eine Landkarte mit Leaflet anzeigt](../media/images/997.png)
*Abbildung: Screenshot der eine Landkarte mit Leaflet anzeigt.*

Bevor wir die Karte nun weiter bearbeiten, sehen wir uns ein bisschen Theorie an. 
Falls Sie keine Theorie mögen, können sie sofort praktisch 
im Kapitel [Die Karte mit Daten bestücken](../die-karte-mit-daten#DieKarteMitDatenBestuecken)  
weitermachen.

[^1]: https://en.wikipedia.org/wiki/Subresource_Integrity
[^2]: http://wiki.selfhtml.org/wiki/HTML/Regeln/Referenzieren_in_HTML#Mit_relativen_Pfadangaben_relativ_zum_Basis-URI_referenzieren
[^3]: https://dev.w3.org/html5/html-author/#the-link-element (engl.)
[^4]: https://dev.w3.org/html5/html-author/#scripting (engl.)
[^5]: https://wiki.selfhtml.org/wiki/Referenz:HTML/Attribute/defer
[^6]: https://wiki.selfhtml.org/wiki/Referenz:HTML/Attribute/async
[^7]: https://wiki.selfhtml.org/wiki/HTML/Eventhandler
[^8]: http://wiki.selfhtml.org/wiki/JavaScript/DOM/Event/load
[^9]: https://de.wikipedia.org/wiki/Fabrikmethode
[^10]: https://github.com/Leaflet/Leaflet/blob/master/src/map/Map.js

*[CSS]: Cascading Style Sheet
*[CDN]: Delivery Network
*[DOM]: Document Object ModelOM
*[HTML]: Hypertext Markup Language
*[W3C]: World Wide Web Consortium
*[WHATWG]: Web Hypertext Application Technology Working Group
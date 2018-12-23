# Custom Markers

Sie <a class="sigil_index_marker" title="Custom Markers" id="sigil_index_id_1">wissen</a> nun wie Sie die unterschiedlichsten Geodaten auf Ihrer Karte anzeigen können und auch wie Sie mit den Geodaten ein Thema visualisieren können.

<h2 id="sigil_toc_id_73">In diesem Kapitel werden wir …</h2>

In diesem Kapitel werden wir über die reine Anzeige hinaus noch einen Schritt weiter gehen. Nun geht es darum, der Karte eine individuelle Note zu geben. Wir sehen uns an, wie Sie Marker beliebig gestalten können. Außerdem sehen wir uns Plugins an, die Sie bei dieser Arbeit unterstützen.

<h2 id="inEinindividuellerMarkeraufIhrerKarte">Ein individueller Marker auf Ihrer Karte</h2>

Wenn Leaflet einen Marker auf einer Karte anzeigt, werden gleich zwei Bilddateien angezeigt. Zunächst wird das eigentliche Bild an die passende Stelle auf die Karte gelegt. Danach wird ein Schatten zu diesem Bild hinzugefügt. Mit einem passenden Schatten fallen die Marker eher ins Auge. Der Schatten verleiht einem Marker eine Tiefe. So hebt dieser sich besser von der Karte ab.

Wenn Sie die Dateien zu Leaflet, wie im Kapitel <a href="../Text/EineErsteKarte.html#sigil_toc_id_8">*Eine lokale Leaflet-Kopie einbinden*</a> beschrieben, auf Ihren Rechner kopiert haben, sehen Sie unter den kopierten Daten einen Unterordner mit dem Namen  `images`. Dieser Ordner enthält die Imagedateien die angezeigt werden, wenn kein individuelles Image angegeben ist. Ich habe die Bilder hier nachfolgend abgedruckt. Wenn Sie dieses Buch bisher durchgearbeitet haben, kommen Ihnen die Bilder sicher teilweise bekannt vor.

<img alt="" src="../Images/data-url-image71.png" id="Bild53"/>

Oft ist es so, dass das Bekannte vertraut ist und man sich deshalb damit sicher und wohl fühlt. Manchmal möchte man aber aus der Reihen tanzen. Wenn Sie auf Ihrer Karte außergewöhnliche Stellen mit einem Marker markieren möchten, dann sollten diese Marker vielleicht aus der Reihe tanzen. Wenn Sie an einer besonderen Stelle keine blaue Einheitsgrafik anzeigen möchten, dann zeigen Sie doch Ihre eigene Grafik an!  
  
Haben Sie schon eine schöne Grafik für Ihren Marker und den passenden Schatten dazu? Wie Sie ein eigenes Image mit einem Grafikprogramm erstellen, gehört nicht zum Thema dieses Buches. Hier möchte ich Ihnen nur ein paar Punkte aufzählen, die Sie beim Erstellen des Images für einen Leaflet Marker beachten sollten.  
Falls Sie keine Grafiken besitzen und auch nicht selbst Hand anlegen möchten, dann können Sie entweder die Übungen mit den Beispielbildern des  <a href="http://leafletjs.com/examples/custom-icons/">Leaflet Tutorials</a>  durcharbeiten – oder Sie blättern direkt weiter zum nächsten Kapitel. Das Kapitel <a href="#inEinMarkerPlugin">*Ein Marker Plugin*</a> bietet Ihnen einen Kompromiss. Sie benötigen keine eigenen Grafiken, können einem Marker aber trotzdem ein anderes Aussehen verleihen.

> Sie möchten gerne selbst die Grafiken erstellen, wissen aber noch nicht genau wie und womit? Dann sehen Sie
sich doch das Programm  <a href="https://www.gimp.org/">GIMP</a> an. GIMP
(GNU Image Manipulation Program) ist eine gute kostenlose Alternative
zum Bildbearbeitungsprogramm  <a href="http://www.adobe.com/de/products/photoshop.html">Photoshop von Adobe</a> und kommt mit zahlreichen professionellen
Bearbeitungsfunktionen.
  
Wenn Sie zwei Bilder haben – also ein Bild, das Ihren Marker selbst darstellt und eines, das den Schatten zeigt – dann können wir diese beiden Bilder als Marker in Ihre Karte einbinden. Ich habe hier zum Ausprobieren die Bild-Dateien aus dem Leaflet Tutorial <a href="http://leafletjs.com/examples/custom-icons/">Markers with Custom Icons</a> verwenden.

  <img alt="" src="../Images/data-url-image72.png" id="Bild63"/>

  Im nachfolgenden Beispiel habe ich den Text, der für die Anzeige des benutzerdefinierten Markers verantwortlich ist, fett formatiert.


<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 10);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);
**
var greenIcon = L.icon({**
**iconUrl: 'http://leafletjs.com/
  examples/custom-icons/leaf-green.png',**
**shadowUrl: 'http://leafletjs.com/
  examples/custom-icons/leaf-shadow.png',**
**iconSize: [38, 95],**
**shadowSize: [50, 64],**
**iconAnchor: [22, 94],**
**shadowAnchor: [4, 62],**
**popupAnchor: [-3, -76]**
**});**
**
L.marker(
[50.27264, 7.26469],
{icon: greenIcon}
).addTo(mymap)
.bindPopup(
"Ich bin ein Marker mit einem individuellen Image."
);
**
</script>
</body>
</html>
<!--index_955.html-->
`</pre>

  Sehen wir uns diese Zeilen genau an: Zunächst einmal sticht die Instanziierung des Bildes hervor.

<pre>`var greenIcon = L.icon({

iconUrl: 'http://leafletjs.com
/examples/custom-icons/leaf-green.png',

shadowUrl: 'http://leafletjs.com
/examples/custom-icons/leaf-shadow.png',

iconSize: [38, 95],
shadowSize: [50, 64],
iconAnchor: [22, 94],
shadowAnchor: [4, 62],
popupAnchor: [-3, -76]
});
`</pre>

  Die Bedeutung der einzelnen Optionen habe ich in der nachfolgenden Abbildung veranschaulicht. Aber zunächst einmal sehen wir uns das Problem genauer an: Die Schwierigkeit beim Positionieren des Bildest liegt darin, die Position des Icons mit der Stelle auf der Erde, die markiert werden soll, zu verbinden. Das Bild ist in der Regel größer als der zu markierende Punkt. Außerdem enthält das Bild oft eine Art Pfeil, dessen Spitze auf den zu markierenden Punkt zeigen sollte. Zudem gibt es meist noch ein Pop-up Fenster, dass relativ zum Bild geöffnet werden sollte. Wie also nutzen Sie die Optionen, um das Bild an der passende Stelle auf der Karte anzuzeigen?
Sie können mit der optionalen Option  `iconSize: [38, 95]`  die Größe des Bildes mitgeben. Mit der optionalen Option  `shadowSize: [50, 64]`  können Sie die Größe des Schattens beeinflussen. Wenn Sie die Werte für diese Option nicht setzten, wird die Originalgröße des Images verwendet.  
Die Option  `iconAnchor: [22, 94]`  gibt Ihnen nun die Möglichkeit, die Stelle, an der das Bild in die Karte eingefügt werden soll, zu definieren. Ohne ein Setzen dieser Option, würde die linke obere Ecke des Bildes an der Stelle, die markiert werden soll, beginnen. In der Regel ist es aber so, dass man das Bild mittig oder vielleicht sogar über dieser Stelle einfügen möchte.  `iconAnchor: [22, 94]`  fügt das Bild 22 Pixel weiter links und 94 Pixel oberhalb der zu markierenden Stelle ein.  
Wenn Sie sich die nachfolgende Abbildung ansehen, wird dies klar. Der rote Punkt stellt in der Abbildung die zu markierende Stelle dar. Für die Option  `shadowAnchor: [4, 62]`  gilt das gleiche wie für  `iconAnchor`. Das Schattenbild wird 4 Pixel links und 76 Pixel oberhalb des roten Punktes, also der zu markierenden Stelle, eingefügt.  
Die Belegung der Wert in der Option  `popupAnchor: [-3, -76]`  ist meiner Meinung nach etwas verwirrend, weil im Gegensatz zu den anderen Optionen für die gleiche Wirkung ein Minuszeichen vorangestellt werden muss. Wenn Sie das Pop-up Fenster links obenhalb der zu markierenden Position öffnen möchten, müssen Sie bei der Option  <span style="font-family: monospace;">popupAnchor  </span>also ein Minuszeichen voran stellen!  

<img alt="" src="../Images/data-url-image73.png" id="Bild57"/>

Im Kapitel *<a href="../Text/DieKarteMitDaten.html#sigil_toc_id_24">Die Karte mit Daten bestücken</a>*  –  genau im Unterkapitel  *<a href="../Text/DieKarteMitDaten.html#PunkteundMarker">Punkte und Marker</a>*  –  haben wir schon Marker mit Optionen angelegt. Im nächsten Codeschnipsel sehen Sie nun, dass Sie auch das Bild zum Marker – also das Icon – als Option angeben können. Im Programmcode geben Sie dazu einfach den Namen des eben erstellen `L.Icon` Objektes an.

`L.marker(`  
`[50.27264, 7.26469],`  
`{**icon: greenIcon**}`  
`).addTo(mymap).bindPopup("Ich bin ein Marker mit einem individuellen Image");`

Wenn Sie das HTML Dokument dieses Beispiels im Browser öffnen, sehen Sie eine Karte auf der das grüne Icon als Marker an der festgelegten Koordinate – passend positioniert – erscheint.

<img alt="" src="../Images/data-url-image74.png" id="Bild54"/>

### Eigenschaften eines individuellen Marker

Einen eigenes Marker Bild erstellen Sie in Leaflet mithilfe der Kasse <a href="http://leafletjs.com/reference-1.1.0.html#icon">L.icon</a>. Das haben Sie eben praktisch gesehen. Diese Klasse bietet Ihnen zehn Optionen.

- `iconUrl:`  
Die `iconUrl`  müssen Sie auf alle Fälle angeben. Diese Option muss die Adresse zur Bilddatei enthalten – absolut oder relativ zu Ihrem Skript-Pfad. 
- `iconRetinaUrl:`  
Die `iconRetinaUrl`  bietet Ihnen optional die Möglichkeit, die Adresse einer für Retina Bildschirme optimierten Version des Bildes – absolut oder relativ zum Skript-Pfad – anzugeben. 
- `iconSize:`  
Die optionale   `iconSize`  beeinflusst die Größe, in der das Bild angezeigt wird. 
- `IconAnchor:`
Die Option  `IconAnchor  `beschreibt die Pixel Koordinate, an der das Bild eingefügt werden soll. Die Koordinate gibt die Pixelwerte relativ zur zu markierenden Stelle an. 
- `PopupAnchor:`
Die Option `PopupAnchor` beschreibt den Punkte, an dem ein Pop-up Fenster geöffent werden soll. Die Koordinate gibt die Pixelwerte relativ zur zu markierenden Stelle an. Wenn Sie das Pop-up Fenster links obenhalb der zu markierenden Position öffnen möchten, müssen Sie bei den Werten der Option  <span style="font-family: monospace;">popupAnchor  </span>ein Minuszeichen voran stellen! 
- `ShadowUrl:`
Die Option `ShadowUrl` enthält die Adresse zur Imagedatei, die den Schatten darstellen soll. Wenn nichts angegeben ist, wird kein Schattenbild erstellt. 
- `ShadowRetinaUrl:`
Mit der Option `ShadowRetinaUrl` können Sie ein Bild angeben, dass speziell für Retina Displays optimiert ist. Wie Leaflet dieses Bild genau optimiert, erkläre ich Ihnen im Anschluss an die Auflistung dieser Optionen. 
- `shadowSize:`
`shadowSize` beschreibt die Höhe und Breite des Bildes, dass den Schatten darstellen soll, in Pixeln. 
- `shadowAnchor:`
Die Pixel Koordinaten an der das Schattenbild eingefügt werden soll, können Sie mit der Option `ShadowAnchor` übergeben. Ansonsten gilt für diese Option das Gleiche, was ich bei der Option `iconAnchor` geschrieben habe. 
- `className:`
Mit der Option `className` können Sie den Namen einer CSS-Klasse, die beiden Bildern - also dem Schattenbild und dem eigentlichen Marker Bild - hinzugefügt wird, definieren. 


> Hochauflösende Displays haben eine höhere Pixeldichte als gewöhnliche Monitore.
Auf der gleichen Fläche werden etwa viermal so viele Pixel
dargestellt. Der Vorteil dieser Technologie liegt darin, dass die
Pixel nun so klein sind, dass das menschliche Auge sie nicht mehr
auflösen kann. Das Ergebnis sind sehr scharfe Grafiken und Texte.
Damit das Bild nun auf einem HiDPI (High Dots Per Inch) Bildschirm,
also einem Retina Display, scharf dargestellt wird, muss es mit
mindestens zweifacher Breite und Höhe zur Verfügung gestellt werden. Denn: Eine Pixelgrafik, die bei gewöhnlicher Auflösung das ganze Display
ausfüllt, würde auf einem Retina Display der gleichen
Größe nur ein Viertel des Displays einnehmen. Ein Pixel der Grafik
entspricht auch auf dem Retina-Display einem Pixel. Es werden aber auf der gleichen Fläche viermal so viele Pixel kleiner abgebildet. Damit
die Pixelgrafiken nicht plötzlich alle zu klein dargestellt werden,
rechnen die Geräte die Grafiken um. Dadurch geht Qualität verloren. Pixelgrafiken sehen auf dem
Retina-Display daher unscharf aus. Um dieses Problem zu umgehen,
prüft Leaflet die Auflösung des Anzeigegerätes. Anschließend
werden die Marker Bilder – sofern eine Grafik mit hohere Auflösung vorhanden ist – in hoher Auflösung
angezeigt.

### Die Klasse `L.Icon` erweitern

So, nun haben Sie einen benutzerdefinierten Marker erstellt und möchten weitere Marker kreiere. Schön, dass Leaflet objektorientiertes Arbeiten unterstützt. So können Sie sich das Erstellen von neuen Marker Objekten sehr einfach machen. Erweitern Sie einfach die Klasse `L.Icon` und geben alle gemeinsamen Eigenschaften hier nur einmal an. Nur die besonderen Eigenschaften des Markers müssen Sie separat für jeden Marker angeben. Das nachfolgende Codebeispiel zeigt Ihnen, wie Sie drei unterschiedliche Marker, die aber gemeinsame Eigenschaften haben, mithilfe von einer Eltern-Klasse erstellen können. So können die drei Marker von dem Elternteil die gemeinsamen Eigenschaften erben.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 9);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

**var LeafIcon = L.Icon.extend({**
**options: {**
**shadowUrl: 'leaf-shadow.png',**
**iconSize: [38, 95],**
**shadowSize: [50, 64],**
**iconAnchor: [22, 94],****shadowAnchor: [4, 62],**
**popupAnchor: [-3, -76]**
**}**
**});
**
**var greenIcon = new LeafIcon(
{iconUrl: 'http://leafletjs.com
/examples/custom-icons/leaf-green.png'}
);
****var redIcon = new LeafIcon(
{iconUrl: 'http://leafletjs.com
/examples/custom-icons/leaf-red.png'}
);**
**var orangeIcon = new LeafIcon(
{iconUrl: 'http://leafletjs.com
/examples/custom-icons/leaf-orange.png'}
);**
**
L.marker(
[50.27264, 7.26469], {icon: greenIcon}
).addTo(mymap).bindPopup(
"Ich bin ein grüner Marker."
);**
**L.marker(
[50.27264, 6.26469], {icon: redIcon}
).addTo(mymap).bindPopup(
"Ich bin ein roter Marker."
);**
**L.marker(
[50.27264, 8.26469], {icon: orangeIcon}
).addTo(mymap).bindPopup(
"Ich bin ein oranger Marker."
);**

</script>
</body>
</html>
<!--index_954.html-->
`</pre>

Dieser Programmcodeabschnitt hat Ähnlichkeit mit dem vorherigen Beispiel. Wenn Sie genau hinsehen, finden Sie aber Unterschiede. Wir erstellen im ersten Schritt kein neues  `Icon`  Objekt   um dieses Anzuzeigen, sondern erweitern die Klasse  `L:Icon`. mit der Klasse  `LeafIcon`. Wir legen nur die gemeinsamen Optionen für das Objekt  <span style="font-family: monospace;">LeafIcon  </span>fest. Die URL des Bildes ist die Option, die von Marker zu Marker unterschiedlich ist. Deshalb geben wir diese beim Erweitern der Klasse in den Optionen noch nicht an.

`var **LeafIcon** = L.Icon.extend({  
options: {  
shadowUrl: 'leaf-shadow.png',  
iconSize: [38, 95],  
shadowSize: [50, 64],  
iconAnchor: [22, 94],  
shadowAnchor: [4, 62],  
popupAnchor: [-3, -76]  
}  
});`

Im zweiten Schritt erstellen wir drei Instanzen des `LeafIcon`, also des erweiterten L.Icon

`var **greenIcon** = new **LeafIcon**(`  
`{iconUrl: 'http://leafletjs.com`  
`/examples/custom-icons/leaf-green.png'}`  
`);`  
`var **redIcon** = new **LeafIcon**(`  
`{iconUrl: 'http://leafletjs.com`  
`/examples/custom-icons/leaf-red.png'}`  
`);`  
`var **orangeIcon** = new **LeafIcon**(`  
`{iconUrl: 'http://leafletjs.com`  
`/examples/custom-icons/leaf-orange.png'}`  
`);`

Und zu guter Letzt fügen wir die Marker mit dem zugehörigen Icon an die passende Stelle auf der Karte zum Kartenobjekt hinzu.

`L.marker(  [50.27264, 7.26469],`  
`{icon: greenIcon}).addTo(mymap)`  
`.bindPopup("Ich bin ein grüner Marker."`  
`);`  
`L.marker(`  
`[50.27264, 6.26469],`  
`{icon: redIcon}).addTo(mymap)`  
`.bindPopup("Ich bin ein roter Marker."`  
`);`  
`L.marker(`  
`[50.27264, 8.26469],`  
`{icon: orangeIcon}).addTo(mymap)`  
`.bindPopup("Ich bin ein oranger Marker."`  
`);`

> Sie haben vielleicht bemerkt, dass wir das Schlüsselwort  `new`  für die Erstellung von  `LeafIcon`  Instanzen verwendet haben. Warum haben wir vorher alle Leafelt Objekte ohne das Schlüsselwort  `new`  erstellt? Die Antwort ist einfach: Die echten Leaflet Klassen sind
mit einem Großbuchstaben – beispielsweise  `**L**.Icon`  – benannt und diese
müssen mit  `new`  erstellt
werden. Es gibt aber Shortcuts mit Kleinbuchstaben –  `L.icon`  – die aus Bequemlichkeitsgründen von den Leaflet-Programmierern
für Sie erstellt wurden:  
`**L.icon** = function icon(options) {`  
`return new L.Icon(options);`  
` };`  
Die Funktion `L.icon` können Sie sich auf Github in der Datei <a href="https://github.com/Leaflet/Leaflet/blob/master/src/layer/marker/Icon.js#L145">icon.js</a> ansehen.  
Leaflet setzt hier das Entwurfsmuster <a href="https://de.wikipedia.org/wiki/Fabrikmethode">Fabrikmethode</a>
(englisch factory method) ein. Das Muster beschreibt, wie ein Objekt
durch Aufruf einer Methode, anstatt durch direkten Aufruf eines
Konstruktors, erzeugt wird.

Im nachfolgenden Bild sehen Sie das Ergebnis. Jeder Marker wird nun mit einem individuellen Icon erstellt. Die meisten Optionen sind gleich – allerdings hat jeder Marker seine eigene Farbe.

<img alt="" src="../Images/data-url-image75.png" id="Bild55"/>

<h2 id="inEinMarkerPlugin">Ein Marker Plugin</h2>

Sie wissen nun, wie Sie einen Marker mit einem standardisierten Aussehen einfügen und können einen Marker mit einem eigenen Image belegen. Leider haben Sie aber kein eigenes Image und haben auch nicht viel Erfahrung mit einem Grafikprogramm. Sie können kein professionell aussehendes individuelles Image hervor zaubern oder haben einfach nicht die Zeit dazu. Trotzdem möchten Sie Ihrer Karte ein besonderes Aussehen verleihen. In diesem Fall bietet Ihnen dieses Kapitel eine Lösung. Ich stelle Ihnen zwei Plugins vor, die Sie bei der Erstellung von individuellen Marker Objekten unterstützen.

### BeautifyIcon

<a href="https://github.com/marslan390/BeautifyMarker">Leaflet.BeautifyIcon</a>, ist ein einfaches Plugin, das bunte Marker ganz ohne eigene Grafik zu Leaflet hinzufügt. Trotzdem behalten Sie die volle Kontrolle über den Stil der Marker. Konkret heißt das: Sie können über unbegrenzte Farben und viele Eigenschaften verfügen. Das Plugin Leaflet.BeautifyIcon bietet auch die Möglichkeit, Schriftart und Glyphen, also die grafische Darstellung von Schriftzeichen, anzupassen.

<img alt="" src="../Images/data-url-image76.png" id="Bild64"/>

Damit Sie sich dieses besser vorstellen können, habe ich ein Beispiel erstellt.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**
<link rel="stylesheet"
href="https://maxcdn.bootstrapcdn.com/
font-awesome/4.5.0/css/font-awesome.min.css"
>
****<link rel="stylesheet"
href="http://netdna.bootstrapcdn.com/
bootstrap/3.0.0/css/bootstrap.min.css"
>
****<link rel="stylesheet"
href="leaflet-beautify-marker-icon.css">
****<script src="leaflet-beautify-marker-icon.js"
></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 8);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);
**
L.marker(
[50.27264, 7.26469],
{****icon: L.BeautifyIcon.icon(****{iconSize: [50, 50]}****),****draggable: true****}
).addTo(mymap).bindPopup("Ich bin ein beautify Marker");
****
options = {
****icon: 'spinner',
****spin: 'true',
****borderColor: '#8A90B4',
****textColor: 'white',
****backgroundColor: '#8A90B4'
****};
****L.marker(
[50.27264, 6.26469],
{****icon: L.BeautifyIcon.icon(options),****draggable: true****}
).addTo(mymap).bindPopup("Ich bin ein beautify Marker");
****
options = {
****icon: 'plane',
****iconShape: 'marker',
****borderColor: '#8D208B',
****textColor: '#8D208B',
****backgroundColor: 'transparent'
****};
****L.marker(
[50.27264, 8.26469],
{
****icon: L.BeautifyIcon.icon(options),
****draggable: true
****}
).addTo(mymap).bindPopup("Ich bin ein beautify Marker");
**
</script>
</body>
</html>
<!--index_953.html-->
`</pre>

  Was müssen Sie tun, wenn Sie das Plugin  <a class="sigil_index_marker" title="Plugin Leaflet.BeautifyIcon" id="sigil_index_id_3">Leaflet.BeautifyIcon</a>  verwenden möchten? Zunächst einmal müssen Sie die notwendigen Skripte und Stylesheet Dateien einbinden. Das ist zum einen das Skript und die CSS-Datei zum Plugin selbst. Zum anderen können Sie über Leaflet.BeautifyIcon Drittdienste nutzen. Sie können  <a class="sigil_index_marker" title="Font Awesome CSS" id="sigil_index_id_4">Font Awesome CSS</a>  und  <a class="sigil_index_marker" title="Bootstrap CSS " id="sigil_index_id_5">Bootstrap CSS  </a>einbinden. Ich habe im Beispiel die CSS-Dateien von Font Awesome und von Boostrap eingebunden, um Ihnen dies zu demonstrieren. Für dieses Beispiel wäre nur die CSS-Datei von Font Awesome CSS notwendig gewesen.

  Mehr müssen Sie nicht tun. Sie können sofort einen Marker mit der Option  `icon: L.BeautifyIcon.icon(options)`  kreieren.

`L.marker([50.27264, 8.26469], {`  
`**icon: L.BeautifyIcon.icon(options),**`  
`draggable: true`  
`}).addTo(mymap).bindPopup("Ich bin ein beautify Marker");`  

Sehen Sie sich die Optionen des Plugin Leaflet.BeautifyIcon an. Es macht Spaß diese zu erkunden. Wie die Optionen wirken, die ich verwendet haben, können Sie sich im nächsten Bild teilweise ansehen. Das sich eines der Icons dreht, erkennen Sie nur, wenn Sie die Datei selbst im Browser öffne.

<img alt="" src="../Images/data-url-image77.png" id="Bild65"/>

> Ich hatte Ihnen ja schon geschrieben,
dass es jede Menge Plugins für Leaflet gibt und dies gilt für den
Bereich Marker besonders. Die meisten sind auf der Website von
Leaflet aufgelistet. Diese Liste finden Sie unter der Adresse
    <a href="http://leafletjs.com/plugins.html#markers--renderers">http://leafletjs.com/plugins.html#markers—renderers</a>.
 
<h2 id="inCluster">Cluster</h2>

Je nachdem welche Informationen Sie mit Ihrer Karte weitergeben möchten, kann es vorkommen, dass Sie sehr viele Marker benötigen. Wenn Sie mit vielen Marker Objekten arbeiten, sollten Sie beachten, dass diese das Laden der Karte verlangsamen. Außerdem kann es vorkommen, dass Marker nahe nebeneinander liegen und sich beim Zoomen überschneiden. Dies ist nicht benutzerfreundlich. Schön wäre es, wenn bei einer vergrößerten Ansicht alle Marker zu sehen sind – diese aber beim Hineinzoomen in die Karte zu  <a class="sigil_index_marker" title="Clustern (Marker)" id="sigil_index_id_6">Clustern</a>  zusammengefasst werden. So hat der Benutzer alle Informationen passend zur Kartenanzeige.

In diesem Kapitel erfahren Sie, wie Sie <a class="sigil_index_marker" title="Plugin Leaflet.markercluster " id="sigil_index_id_7">das</a> Plugin <a href="https://github.com/Leaflet/Leaflet.markercluster">Leaflet.markercluster</a> zum Clustern von Marker Objekten verwenden und so eine große Anzahl von Marker Objekten auf einer Karte benutzerfreundlich und übersichtlich darstellen können. Sehen Sie sich das nachfolgende Beispiel an, um zu verstehen, wie das Clustern von Marker Objekten funktioniert.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<link rel="stylesheet" href="MarkerCluster.css"/>
****<link rel="stylesheet" href="MarkerCluster.Default.css"/>
****<script src="leaflet.markercluster-src.js">
</script>****<script src="points.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid',
{doubleClickZoom:false})
.setView([50.219264, 7.19469], 13);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

**var markers = L.markerClusterGroup(**
**{showCoverageOnHover : false}**
**);
**
for (var i = 0; i < points.length; i++) {
var a = points[i];
var title = a[2];

var marker = L.marker(new L.LatLng(a[0], a[1]),
{ title: title });

marker.bindPopup(title);
**markers.addLayer(marker);**
}

mymap.addLayer(markers);
</script>
</body>
</html>
<!--index_952.html-->
`</pre>

  Das haben wir gemacht? Als erstes haben wir die notwendigen Dateien zum Plugin  <a href="https://github.com/Leaflet/Leaflet.markercluster">Leaflet.markercluster</a>  eingebunden. Damit wir auch genug Marker zum Clustern zur Verfügung haben, habe wir dann Punkte über eine externe Datei eingebunden. Die Datei  `points.js`   enthält 380 Punkte und sieht auszugsweise wie folgt aus:  


`var points = [`  
`[50.2210922667, 7.2209316333, "2"],`  
`[50.2210819833, 7.2213903167, "3"],`  
`...`  
`];`  

Zu guter Letzt mussten wir mit  
`var markers = L.markerClusterGroup(`  
`{showCoverageOnHover : false}`  
`);`  

ein Objekt vom Typ  `markerClusterGroup`  erzeugen und diesem Objekt jeden einzelnen Marker hinzufügen. Das Objekt  `markerClusterGroup`  übernimmt nun die ganze Arbeit für uns.


So wie in der nachfolgenden Abbildung zu sehen ist, könnte Ihre Karte aussehen.

<img alt="" src="../Images/data-url-image78.png" id="Bild67"/>

### Optionen, Methoden und Ereignisse

Sie können einem Cluster jede Menge Optionen mitgeben und sehr viele Methoden und Ereignisse nutzen. Zum Beispiel können sie die standardmäßig aktivierte Option `showCoverageOnHover` mit
  
`var markers = L.markerClusterGroup(`  
`{**showCoverageOnHover : false**}`  
`);`  

ausschalten. Aktiviert bewirkt diese Option folgendes: Wenn Sie die Maus über einen Cluster bewegen, blendet sich ein Polygon ein, dass die Grenzen des Bereichs in dem die Marker sich befinden, anzeigt.
Alle Optionen, Methoden und Ereignisse finden Sie in der  <a href="https://github.com/Leaflet/Leaflet.markercluster">Dokumentation</a>  zum Plugin auf Github.

<h2 id="inMarkeranimieren">Marker animieren</h2>

### Hüpfende Marker

Wenn Sie einen Marker animieren möchten, unterstützt Sie das Plugin <a href="https://github.com/maximeh/leaflet.bouncemarker">https://github.com/maximeh/leaflet.bouncemarker</a>. Wie Sie den hüpfenden Marker in Ihre Karte einbinden, zeigte ich Ihnen wieder anhand eines Beispiels.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="bouncemarker.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 12);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**L.marker([50.27264, 7.26469],
{
bounceOnAdd: true,
bounceOnAddOptions: {duration: 5000, height: 100},
bounceOnAddCallback: function() {alert("Gelandet");}
}
).addTo(mymap);
**
</script>
</body>
</html>
<!--index_951.html-->
`</pre>

Als Erebnis sehen Sie einen Marker, der in die Karte spring. Nach dem der Marker gelandet ist, öffnet sich ein Pop-up-Fenster mit der Meldung: Gelandet!.

### Animierte Marker

#### Ein Marker bewegt sich

Es gibt sehr viele spannende Ideen, die man mit einer Karte umsetzen kann. Möchten Sie vielleicht mit Ihrem Marker einen Weg beschreiten? Dann ist das Plugin <a href="https://github.com/openplans/Leaflet.AnimatedMarker">https://github.com/openplans/Leaflet.AnimatedMarker</a> vielleicht etwas für Sie. Mit diesem Plugin können Sie einen Marker so animieren, dass er einer Linie folgt. Vielleicht möchten Sie einen Marker in Form eines Autos darstellen, dass auf einer Straße fährt?

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="AnimatedMarker.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 9);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

**var line = L.polyline(
[[50.68510, 7.94136],
[50.68576, 6.94149],[51.68649, 6.94165]
]);

animatedMarker = L.animatedMarker(line.getLatLngs(), {
distance: 2000,
interval: 1000,
});**

mymap.addLayer(animatedMarker);
</script>
</body>
</html>
<!--index_950.html-->
`</pre>

#### Einen Marker in Bewegung setzen und wieder stoppen

Und auch wenn Sie die Bewegung des Markers beeinflussen möchten, unterstützt Sie das Plugin <a href="https://github.com/openplans/Leaflet.AnimatedMarker">https://github.com/openplans/Leaflet.AnimatedMarker</a>. Bauen Sie in diesem Falle doch einfach zwei Schaltenflächen ein, über die Sie den Maker anhalten oder starten können. Das nächste Beispiel will Ihnen eine Idee zur Umsetzung dieser Aufabenstellung geben.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="AnimatedMarker.js"></script>
</head>
<body>

**<button onclick="start()">Start</button>
<button onclick="stop()">Stop</button>
**
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 9);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var line = L.polyline(
[[50.68510, 7.94136],[50.68510, 7.84136],
[50.68510, 7.74136],[50.68510, 7.64136],
[50.68510, 7.5136],[50.68510, 7.44136],
[50.68510, 7.34136],[50.68510, 7.24136]]);

animatedMarker = L.animatedMarker(line.getLatLngs(), {
autoStart: false,
distance: 200,
interval: 100
});

mymap.addLayer(animatedMarker);
**
function start(){
animatedMarker.start();
}

function stop(){
animatedMarker.stop();
}**

</script>
</body>
</html>
<!--index_949.html-->
`</pre>

Wie Sie sehen, können Sie die Funktionen  `start()`  und  `stop()`, die Ihnen das Plugin  <a href="https://github.com/openplans/Leaflet.AnimatedMarker">https://github.com/openplans/Leaflet.AnimatedMarker</a> zur Verfügung stellt, nutzen.

#### Plugins kombinieren

Und natürlich können Sie Plugins auch kombinieren. Ihrer Kreativität sind keine Grenzen gesteckt. Schon allein mit den beiden gerade gezeigten Plugins <a href="https://github.com/openplans/Leaflet.AnimatedMarker">Leaflet.AnimatedMarker</a> und <a href="https://github.com/maximeh/leaflet.bouncemarker">Leaflet.bouncemarker</a> können Sie einen Marker auf der Karte Aktionen ausführen lassen und ihn am Schluss gekonnt  aus dem Bild hüpfen lassen. Sehen Sie selbst, probieren Sie das nächste Beispiel aus!

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="AnimatedMarker.js"></script>
<script src="bouncemarker.js"></script>**
</head>
<body>
<button onclick="start()">Start</button>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 7);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

b = new L.Marker([51.68649, 6.94165],
{bounceOnAdd: true});
var line = L.polyline(
[[50.68510, 7.94136],[50.68576, 6.94149],
[51.68649, 6.94165]]),
animatedMarker = L.animatedMarker(line.getLatLngs(), {
autoStart: false,
distance: 2000,
interval: 10,
onEnd: function() {
b.addTo(mymap);
b.bounce({duration: 100, height: 50});
mymap.removeLayer(animatedMarker);
setTimeout('mymap.removeLayer(b)', 900);
}
});
mymap.addLayer(animatedMarker);
function start(){animatedMarker.start();}
</script>
</body>
</html>
<!--index_948.html-->`</pre>

<h2 id="inLeafletDataVisualizationFramework">Leaflet Data Visualization Framework (DVF)</h2>

Möchten Sie gerne mit Ihrer Karte Daten visualisieren. <a href="../Text/Heatmap.html#inHeatmapundChoropletenjkarten">Heatmaps und Choroplethenkarten</a> sind aber nicht das Richtige für Sie? Sie können Daten mithilfe von Markern in überzeugende Karten verwandeln. Hierbei unterstützt Sie das Plugin <a href="https://github.com/humangeo/leaflet-dvf">Leaflet Data Visualization Framework (DVF)</a>. Leider ist dieses Plugin zu dem Zeitpunkt, zu dem ich dieses Kapitel geschrieben haben, nicht mit der neuesten Leaflet Version <a href="https://github.com/humangeo/leaflet-dvf/wiki/1.0-Compatibility">kompatibel</a>. Deshalb verwende ich im Beispiel eine ältere Leaflet Version.

### Das Plugin Data Visualization Framework

Das erste Beispiel zeigt Ihnen, wie Sie Formen als Marker darstellen können. Hier geht es noch nicht um das Visualisieren von Daten, sondern eher darum, die Möglichkeiten diese Plugins zu sehen und ein Gefühl für die Anwendung zu bekommen. 

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet"
href="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.css" />

<script src="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.js">
</script>

<link rel="stylesheet" href="dvf.css" />
<script src="leaflet-dvf.js"></script>
<script src="leaflet-dvf.markers.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 7);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var **marker** = new L.MapMarker([50.27264, 7.26469],
{
radius: 30,
fillOpacity:0.5,
fillColor:'orange',
color:'purple',
innerRadius:7,
numberOfSides:4,
rotation:10
});
mymap.addLayer(marker);

var **polygonmarker** = new L.RegularPolygonMarker(
[50.27264, 6.26469],
{
numberOfSides: 3,
rotation: 10,
radius: 10,
fillColor:'green',
fillOpacity:1,
opacity:1,
weight:1,
radius:30
});
mymap.addLayer(polygonmarker);

var **star** = new L.StarMarker([50.27264, 8.26469],
{
numberOfPoints:8,
opacity:1,
weight:2,
fillOpacity:0,
radius:30});
mymap.addLayer(star);
</script>
</body>
</html>
<!--index_947.html-->
`</pre>

Die nächste Abbildung zeigt Ihnen die drei im vorherigen Beispiel erstellen Marker.

<img alt="Leaflet" src="../Images/Leaflet.png"/>

### Diagrammen als Marker

Das außergewöhnlichste an diesem Plugin ist meiner Meinung nach die Einfachheit, mit der Diagramme als Marker dargestellt werden können. Sehen sich dies im nachfolgenden Beispiel an.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet"
href="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.css" />

<script src="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.js">
</script>
<link rel="stylesheet" href="dvf.css" />
<script src="leaflet-dvf.js"></script>
<script src="leaflet-dvf.markers.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 7);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var options = {
data: {
'data1': 20,
'data2': 50,
'data3': 10,
'data4': 20
},

**chartOptions**: {
'**data1**': {
fillColor: 'blue',
minValue: 0,
maxValue: 50,
maxHeight: 30,
displayText: function (value) {
//return value.toFixed(2);
return 'Mein Text';
}
},
'**data2**': {
fillColor: 'red',
minValue: 0,
maxValue: 50,
maxHeight: 30,
},
'**data3**': {
fillColor: 'green',
minValue: 0,
maxValue: 50,
maxHeight: 30,
},
'**data4**': {
fillColor: 'yellow',
minValue: 0,
maxValue: 50,
maxHeight: 30,
}
},
weight: 1,
color: '#000000',
radius:30,
fillOpacity:1
};

var bar = new L.BarChartMarker(
[50.27264, 7.26469], options);
mymap.addLayer(bar);

var radial = new L.RadialBarChartMarker(
[50.27264, 8.26469], options);
mymap.addLayer(radial);

var pie= new L.PieChartMarker(
[50.27264, 6.26469], options);
mymap.addLayer(pie);

var cox = new L.CoxcombChartMarker(
[50.97264, 7.26469], options);
mymap.addLayer(cox);

var stack = new L.StackedRegularPolygonMarker(
[50.97264, 8.26469], options);
mymap.addLayer(stack);

var radialmeter= new L.RadialMeterMarker(
[50.97264, 6.26469], options);
mymap.addLayer(radialmeter);

</script>
</body>
</html>
<!--index_946.html-->
`</pre>

Ich habe die Daten für dieses Beispiel künstlich erstellt. Das Prinzip wird so klar. Das Beispiel zeigt Ihnen, wie Sie Daten in Form eines Diagramms mithilfe des Leaflet Data Visualization Framework auf Ihrer Leaflet Karte einblenden können. Und das nachfolgende Bild zeigt Ihnen das Ergebnis.
<img alt="" src="../Images/data-url-image79.png" id="Bild68"/>

<h2 id="sigil_toc_id_77">In diesem Kapitel haben wir …</h2>

In diesem Kapitel haben wir der Leaflet Karte eine individuelle Note gegeben. Wir haben uns angesehen, wie Sie Marker beliebig gestalten können. Dabei haben wir einen Ausflug in die objektorientierte Programmierung gemacht. Insbesondere bei der Erstellung von vielen individuellen Marker Objekten kann man sich durch eine mögliche Vererbung viel Arbeit und viele Programmcodezeilen sparen. Außerdem haben wir uns verschiedene Plugins angesehen – man muss ja nicht immer das Rad selbst neu erfinden.  
  
Sie haben Ihre digitale Karte bereits im Griff. Sie können diese gestalten und Daten auf ihr visualisieren. Nun kann es sein, dass Sie selbst keine großen Datenbestände zum Anzeigen haben. Vielleicht bietet das ESRI Inc. (Environmental Systems Research Institute) Daten, die zum Thema Ihrer Website passen? Im nächsten Kapitel erfahren Sie, wie Sie Daten und Anwendungen dieses Institutes verwenden können.  


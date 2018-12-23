# Die Karte mit Daten bestücken
[](#){#DieKarteMitDatenBestuecken}

Sie können nun eine digitale Karte mit Leaflet in ein HTML Dokument einbinden, 
Sie wissen was geografische Koordinaten sind und wie die Imagedateien für digitale Karten erstellt werden. Darauf aufbauend können wir nun im nächsten Kapitel Ihre digitale Karte mit Geodaten füllen.

## In diesem Kapitel werden wir …

Bisher haben wir ausschließlich Layer zur Karte hinzugefügt. Wie das Beispiel mit den    <a href="../Text/EineErsteKarte.html#uPopcgokgNR6doW5vo3ziL4">Warnhinweisen vom Deutschen Wetterdienst</a>im vorherigen Kapitel zeigt, können diese Layer dynamisch mit Daten bestückt werden.
In diesem Kapitel zeige ich Ihnen nun, wie Sie selbst Layer mit Daten erstellen und als Schicht auf Ihrer Karte anzeigen können. Dabei verwenden wir einfache geometrische Objekte. Konkret sind dies Punkte, Linien und Polygone.

- <a class="sigil_index_marker" title="Punkt" id="sigil_index_id_1">Punkte</a>/<a class="sigil_index_marker" title="Marker" id="sigil_index_id_2">Marker</a>:  
Das einfachste Objekt ist ein Punkt. Auf einer Landkarte wird ein Punkt mit Zahlen – den Koordinaten – beschrieben. In Leaflet gibt es neben dem Punkt noch ein komfortableres Element – nämlich den Marker.  
Auf einer realen Karte könnte ein Marker zum Beispiel einen interessanten Ort, also einen<a class="sigil_index_marker" title="Point of Interest (POI)" href="https://de.wikipedia.org/wiki/Point_of_Interest">Point of Interest (POI)</a>darstellen. 
- <a class="sigil_index_marker" title="Linie" id="sigil_index_id_3">Linien</a>:  
Eine Linie besteht aus mindestens zwei Punkten die miteinander verbunden sind.  
Auf einer Landkarte könnte eine Linie zum Beispiel eine Straße darstellen. 
- <a class="sigil_index_marker" title="Polygon" id="sigil_index_id_4">Polygone</a>:  
Ähnlich wie eine Linie besteht ein Polygon aus mehreren miteinander verbundenen Punkten. Zusätzlich ist beim Polygon auch der erste Punkt mit dem letzten Punkte verbunden. Somit stellt ein Polygon eine geschlossene Form dar.  
Auf einer realen Karte könnte ein Polygon zum Beispiel die Fläche eines Landes oder einer Stadt darstellen. 

Wie können Sie nun Punkte, Marker, Linien und Polygone auf Ihre Karte zeichnen? 
Das ist Thema dieses Kapitels. Außerdem erkläre ich Ihnen wie Sie die Objekte in 
Layer-Gruppen und Feature-Gruppen gruppieren können und welche Vorteile dies bringt. 
Nebenbei sehen wir uns an, wie Sie die Karte auch auf kleinen Displays passend anzeigen 
und wie Sie auf Ereignisse reagieren können.

<h2 id="sigil_toc_id_26">Punkte, Marker, Linien, Polygone, Rechtecke und Kreise als Leaflet Objekte</h2>

Leaflet biete Ihnen jede Menge verschiedene Objekte. Beginnen wir mit den einfachsten – den Punkten und Markern.

### Punkte und Marker
[](#){#DieKarteMitDatenBestueckenPunkteundMarker}

Ich gehen noch einmal von unserer Basiskarte aus. Zur besseren Übersicht habe ich Ihnen das HTML-Grundgerüst dazu nachfolgend noch einmal abgedruckt.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
</script>
</body>
</html>
<!--index_989.html-->
`</pre>
  In der nächsten Abbildung sehen Sie die Karte, die angezeigt werden sollte, wenn Sie die vorhergehende HTML-Datei in einem Browser öffnen.

  <img alt="" src="../Images/data-url-image23.png" id="Bild30"/>

  Diese Karte ist bisher nicht sehr spannend. Landkarten, die Straßen und Orte anzeigen, findet man wie Sand am Meer. Auf Ihrer Website geht es sicher um etwas Besonderes und so möchten Sie sicher auch einen besonderen Ort hervorheben oder ein besonderes Thema beschreiben. Beginnen wir mit einem besonderen Ort – beziehungsweise einem besonderen Punkt.

#### Punkte

  Die Leaflet Klasse <a href="http://leafletjs.com/reference-1.1.0.html#point">`Point`</a> stellt einen Punkt mit X- und Y-Koordinaten in *Pixeln* dar<a class="sigil_index_marker" title="Punkt (Leaflet)" id="sigil_index_id_5">.</a>

> Sie haben richtig gelesen. Bei einem Punkt arbeitet Leaflet nicht mit *geografischen* Koordinaten<a class="sigil_index_marker" title="Point (Leaflet)" id="sigil_index_id_6">.</a> Hier müssen Sie tatsächlich die *Pixel* der Grafik, mit die Karte angezeigt wird, angeben.

  Objekte vom Typ `Point` sind in Leaflet nicht zur Anzeige gedacht. Vielmehr wird mit Ihnen gearbeitet. Zum Beispiel gibt es die Methode <a href="http://leafletjs.com/reference-1.1.0.html#map-methods-for-modifying-map-state">`panBy`()</a> <a class="sigil_index_marker" title="panBy()" id="sigil_index_id_7">mit</a> der die Karte um eine gegebene Anzahl von Pixeln verschoben werden kann.

  Sie merken schon. Ein Objekt vom Typ `Point` ist nicht das, was wir möchten, wenn wir eine geografische Stelle auf der Karte hervorheben möchten. Um einen Punkt als besonders zu markieren, möchten Sie sicher eher einen Marker mit Informationen an dieser Stelle – also an den *geografischen* Koordinaten – anzeigen. Und für diesen Zweck bietet Leaflet ein spezielles Objekt – das`Marker`Objekt<a class="sigil_index_marker" title="Marker (Leaflet)" id="sigil_index_id_8">.</a>

  Im nachfolgenden Programmcode-Beispiel sehen wir uns zunächst kurz an, was Sie mit einem Punkt anstellen können.


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

**var point = L.point(400, 600);**
**mymap.panBy(point);**
</script>
</body>
</html>
<!--index_988.html-->
`</pre>

Wenn Sie das vorhergehende HTML-Dokument in Ihrem Browser öffnen, müssen Sie ganz schnell gucken. Nur dann können Sie erkennen, dass die Karte unmittelbar nach dem Öffnen um 400 Pixel nach rechts und 600 Pixel nach unten geschoben wird.

> Anstelle von  
`var point = L.point(400, 600);`  
`mymap.panBy(point);`  
hätten Sie auch ganz einfach  
`mymap.panBy([400, 600]);`  
oder  
`mymap.panBy(L.point(400, 600));`  
schreiben können.  

An dieser Stelle füge ich kein Bild ein, auf dem das Ergebnis dargestellt ist. Das Verschieben der Karte wäre auf diesem nicht zu erkennen.

#### Marker

Die Leaflet Klasse <a href="http://leafletjs.com/reference-1.1.0.html#marker">`Marker`</a> wird verwendet, um anklickbare und/oder verschiebbare *Symbole* auf einer Karte anzuzeigen. Die Klasse erweitert die Klasse <a href="http://leafletjs.com/reference-1.1.0.html#layer">`Layer`</a>. In der Regel wird dieses *Symbol* mit einem Pop-up Fenster erweitert, auf dem weitere Informationen zu der entsprechenden Stelle auf der Erde enthalten sind.

Machen wir mit einem einfachen Beispiel weiter und fügen einen Marker zu unserer bisher noch langweiligen Karte hinzu.


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.1.0/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet@1.1.0/dist/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**var myMarker = L.marker([50.27264, 7.26469],**
**{**
**title:"Gering",**
**alt:"Ein schönes kleines Dorf auf dem Maifeld in der Eifel",**
**draggable:true**
**}**
**).addTo(mymap);**
</script>
</body>
</html>
<!--index_987.html-->
`</pre>
  Was haben wir genau gemacht? Mit dem Text`var` `myMarker = L.marker([50.27264, 7.26469])`haben wir ein`Marker`Objekt, das an den Koordinaten`[50.27264, 7.26469]`angezeigt wird, instanziiert. Im Weiteren haben wir die Optionen`title`,`alt`und`draggable`mit Werten belegt. Dabei setzen Sie mit der Option`title`den Tooltip der erscheint, wenn Sie die Maus über den Marker bewegen, mit der Option`alt`setzen Sie den Text für das`alt`Attribut des Marker Bildes und mit der Option`draggable`legen Sie fest, ob der Marker mithilfe der Maus auf der Karte bewegt werden kann – oder nicht.

  Das `<img>`-Tag des Markers fügt Leaflet zur Anzeige wie folgt ins HTML-Dokument ein:

`<img  
src="file:///images/marker-icon.png"  
class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive leaflet-marker-draggable"  
style="margin-left: -12px; margin-top: -41px; width: 25px; height: 41px; transform: translate3d(637px, 350px, 0px); z-index: 350;"  
**title**="Gering"  
**alt**="Ein schones kleines Dorf auf dem Maifeld in der Eifel" tabindex="0"  
>`

Alle Optionen und Methoden, die Ihnen die Leaflet Klasse`Marker`bietet, können Sie in der <a href="http://leafletjs.com/reference#marker">Leaflet Dokumentation</a> nachlesen.

Im nächsten Bild sehen Sie den Marker in die Karte integriert. Als Bild wurde ein <a href="http://leafletjs.com/reference#icon-default">Standardbild</a> verwendet, da die Option `icon` nicht gesetzt wurde. Wie Sie ein benutzerdefiniertes Icon verwenden können, sehen wir uns in Kapitel <a href="../Text/CustomMarkers.html#inCustomMarkers">*Custom Markers*</a> genauer an.
In der Karte des vorhergehenden Beispiels können Sie den Marker im Browser mit der Maus bewegen, da die Option `draggable` auf `true` gesetzt wurde. Probieren Sie es aus!

  <img alt="" src="../Images/data-url-image24.png" id="Bild31"/>

> Sie müssen für
einen Marker keine Variable instanziieren. Sie können den Marker
auch ganz einfach so zur Karte hinzufügen:  
`L.marker([50.27264, 7.26469],  
{ title:"Gering", alt:"Ein schönes kleines Dorf auf dem Maifeld in der Eifel", draggable:true }  
).addTo(mymap);`  
Beachten Sie dabei aber folgendes: Falls Sie den Marker später einmal
modifizieren möchten, benötigen Sie einen Namen. Andernfalls können
Sie den Marker nicht identifizieren und somit auch nicht zum Ändern
auswählen.


### Objekte, die aus mehr als einem Punkte bestehen

#### Linien

Linien können Sie in Leaflet mit der Klasse 
[Polyline](https://leafletjs.com/reference-1.3.2.html#polyline) erstellen. 
Die Klasse `Polyline` erweitert die abstrakte Klasse 
[Path](http://leafletjs.com/reference-1.3.2.html#path). 
Diese Klasse ermöglicht es Ihnen eine einfache Linie oder mehrere 
aneinandergereihte Liniensegmente zu erstellen.

Im nachfolgenden Programmcodebeispiel habe ich den Text, der für die Erstellung des `Polyline` Objektes verantwortlich ist, fett formatiert.

`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="../leaflet/leaflet.css" />`  
`<script src="../leaflet/leaflet.js"></script>`  
`</head>`  
`<body>`  
`<div style="height: 700px;" id="mapid"></div>`  
`<script>`  
`var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);`  
`L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);`  
**`var polyline = L.polyline(`**  
**`[`**  
**`[50.27264, 7.26469],`**  
**`[51.27264, 7.26469],`**  
**`[51.27264, 6.26469]`**  
**`],`**  
**`{color: 'red', weight:8})`**  
**`.addTo(mymap);`**  
`</script>`  
`</body>`  
`</html>`  
`<!--index_986.html-->`  


Im Beispiel wird ein`Polyline`Objekt instanziiert, das aus drei Punkten besteht. Außerdem werden die Optionen`color`und`weigth`verwendet. Diese Optionen erbt die Klasse`Polyline`von der Klasse`Path`. Konkret legen wir im Beispiel mit`color = 'red'`die Farbe der Linie fest – diese soll rot sein. Mit`weight:8`bestimmen wir, dass die Linie 8 Pixel dick sein soll.

In der nächsten Abbildung sehen Sie genau diese Linie.

<img alt="" src="../Images/data-url-image25.png" id="Bild32"/>

#### Polygone
[](#){#DieKarteMitDatenBestueckenPolygone}

Ein Polygon<a class="sigil_index_marker" title="Polygon (Leaflet)" id="sigil_index_id_11">e</a>ist eine geschlossene Linie – also eine Linie die einen *Innenbereich* von einem *Außenbereich* abtrennt. Mit der Klasse <a href="http://leafletjs.com/reference-1.1.0.html#polygon">`Polygone`</a> können Sie, wie der Name schon sagt,`Polygone`Objekte auf Ihre Karte zeichnen. Die Klasse`Polygone`erweiterte die Klasse`Polyline`und somit auch die Klasse`Path`. Alle Methoden und Optionen dieser Klassen können Sie also auch mit einem`Polygone` Objekt nutzen.

> Die Punkte, die Sie
beim Erstellen eines Polygons übergeben, sollten als letzten Punkt
keinen Punkt enthalten, der dem ersten Punkt entspricht. Es ist besser,
solche Punkte herauszufiltern.  
Warum sollen der erste und der letzte Punkt nicht identisch sein? Leaflet schließt Ihr Polygon
automatisch. Wenn der erste Punkt mit dem letzten Punkt
übereinstimmt, kann dies zu Problemen führen.  

Wie Sie ein Polygon in Leaflet erstellen, zeigt Ihnen der nachfolgende Programmcode und das konkrete Polygon sehen im darauf folgenden Bild. Alle Methoden und Optionen, die Sie auf ein`Polygon`Objekt anwenden könne, finden Sie in der<a href="http://leafletjs.com/reference#marker">Leaflet Dokumentation</a>.


`<!DOCTYPE HTML>`  
`<html>`  
`<head>`  
`<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
`<link rel="stylesheet" href="../leaflet/leaflet.css" />`  
`<script src="../leaflet/leaflet.js"></script>`  
`</head>`  
`<body>`  
`<div style="height: 700px;" id="mapid"></div>`  
`<script>`  
`var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);`  
`L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);`  
**`var polygon = L.polygon(`**  
**`[`**  
**`[50.27264, 7.26469],`**  
**`[51.27264, 7.26469],`**  
**`[51.27264, 6.26469]`**  
**`],`**  
**`{color: 'red', weight:2, fillColor:'green', fillOpacity:0.5}`**  
**`).addTo(mymap);`**  
`</script>`  
`</body>`  
`</html>`  
`<!--index_985.html-->`  

<img alt="" src="../Images/data-url-image26.png" id="Bild33"/>

### Rechtecke und Kreise

Um einen<a class="sigil_index_marker" title="Kreis (Leaflet)" id="sigil_index_id_12">Kreis</a>oder ein<a class="sigil_index_marker" title="Rechteck (Leaflet)" id="sigil_index_id_13">Rechteck</a>zu erstellen benötigt man eigentlich keine eigene Klasse. Man könnten diese Formen mit der Klasse`Polygon`erzeugen. Beim Kreis wäre dies allerdings sehr mühselig und auch für ein Rechteck gibt es einfacherer Verfahrensweisen. Leaflet bietet deshalb für diese beiden Formen spezielle Klassen an.

Das Zeichnen von Rechtecken und Kreisen ist kein Hexenwerk. Der Vollständigkeit halber finden Sie in den nächsten beiden Kapiteln jeweils ein Beispiel für beide Formen.

#### Rechtecke

Der nachfolgende Programmcode zeigt Ihnen an einem Beispiel, wie Sie ein<a class="sigil_index_marker" title="Rectangle  (Leaflet)" id="sigil_index_id_14">Rechteck</a>– also ein Objekt vom Typ <a href="http://leafletjs.com/reference-1.1.0.html#rectangle">`Rectangle`</a> – in eine Leaflet Karte einfügen.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**var myRectangle = L.rectangle(
[
[50.27264, 7.26469],
[51.27264, 6.26469]],
{color: "yellow", weight: 8, fillColor:"purple"}
).addTo(mymap);**
</script>
</body>
</html>
`<!--index_984.html-->`

Als Parameter geben Sie für das Rechteck immer die diagonal versetzten beiden Ecken an. Dabei ist es egal, in welcher Reihenfolge Sie diese angeben.
Das Rechteck

`var myRectangle = L.rectangle([`  
**`[50.27264, 7.26469],`**  
**`[51.27264, 6.26469]`**  
`])`  

sieht auf der Karte genauso aus, wie das Rechteck

`var myRectangle = L.rectangle([`  
**`[51.27264, 6.26469],`**  
**`[50.27264, 7.26469]`**  
`])`

Und wie das Rechteck des Beispiels aussieht, zeigt Ihnen die nachfolgende Abbildung.

<img alt="" src="../Images/data-url-image27.png" id="Bild34"/>

In diesem Zusammenhang ist vielleicht ganz interessant wie Leaflet das<a class="sigil_index_marker" title="Koordinatensystem" id="sigil_index_id_15">Koordinatensystem</a>der Erde verarbeitet. Dieses Koordinatensystem ist ja kein gewöhnliches Koordinatensystem, sondern ein<a class="sigil_index_marker" title="sphärisches Koordinatensystem" id="sigil_index_id_16">sphärisches</a>. Unter einer Sphäre versteht man in der Mathematik ganz vereinfacht ausgedrückt die Oberfläche einer Kugel. Und auf einer Kugel führen, im Gegensatz zu einer Ebene, immer zwei Linien auf direktem Wege zu einem anderen Punkt. Die nachfolgenden Abbildungen zeigen Ihnen, dass Leaflet dieses Problem vereinfacht. Es behandelt das sphärische Koordinatensystem als normales Koordinatensystem. Dies hatten wir uns im Exkurs<a href="../Text/EineErsteKarte.html#ui4EqCDOvbKdNQ6JO9P6WeC">*Das Koordinagensystem der Erde*</a>schon einmal angesehen.
Um von der Koordinate`[50, -180]`zur Koordinate`[51, 180]`zu gelangen, muss man mit Leaflet einmal um die ganze Erde laufen. Und analog wird auch ein Rechteck mit diesen Eckpunkten um die ganze Erde gezeichnet. Und das, obwohl die Ecken hier ganz nah beieinander liegen.

  <table>
    <colgroup>
      <col/>
      <col/>
    </colgroup>

    <tbody>
      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image28.png" id="Bild88"/>
        </td>
      </tr>

      <tr valign="top">
       <td>
          <img alt="" src="../Images/data-url-image29.png" id="Bild89"/>
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image30.png" id="Bild90"/>
        </td>
       </tr>

      <tr valign="top">
      <td>
          <img alt="" src="../Images/data-url-image31.png" id="Bild91"/>
        </td>
      </tr>
    </tbody>
  </table>

#### Kreise

Anhand des nachfolgenden Programmcode können Sie erkennen, wie ein Kreis – also ein Objekt vom Ty<a class="sigil_index_marker" title="Circle (Leaflet)" id="sigil_index_id_17">p</a><a href="http://leafletjs.com/reference-1.1.0.html#circle">`Circle`</a> – in eine Leaflet Karte eingefügt wird.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**L.circle(
[50.27264, 7.26469],100000,
{color: "red", weight: 8, fillColor:"green"}
).addTo(mymap);**
</script>
</body>
</html>
<!--index_983.html-->
`</pre>

Ein Kreis wird anhand seines Mittelpunktes und seines Radius definiert. Der Radius muss dabei in Metern angegeben werden. In den Beispielen habe ich den Rand mit 8 Pixel festgelegt. Diese Breite passt für die Zoom-Stufe 7. Probieren Sie doch einmal aus, wie der Rand aussieht, wenn Sie die Karte vergrößern. Sie werden feststellen, dass man irgendwann nur noch den Rand sieht und es wichtig sein könnte, dessen Größe immer relativ zur Zoom-Stufe zu setzen.

<img alt="" src="../Images/data-url-image32.png" id="Bild35"/>

<h2 id="sigil_toc_id_33">Mehrere Poly- Objekte auf einer Ebene</h2>

In den vorhergehenden Beispielen haben wir jedes Element auf einem separaten Layer – also einer separaten Ebenen – abgebildet. Spätestens, wenn Sie selbst unterschiedliche Geodaten auf einer Karte darstellen möchten werden Sie sich wünschen, Objekte mit gleichen Eigenschaften auf einem Layer<a class="sigil_index_marker" title="gruppieren (Objekte in Leaflet)" id="sigil_index_id_18">gruppieren</a>zu können. Denn nur so können sie alle Elemente zusammen ansprechen.
Stellen Sie sich vor, Sie möchten auf Ihrer Website Touren für Aktivurlauber beschreiben. Diese Touren sind unterteilt in Wanderer, Bergsteiger, Gipfelstürmer und Freikletterer. Auf der Karte kann ein Kunde Angebote für eine bestimmte Region heraus filtern. Hierzu muss er nur die Karte passend positionieren. Wenn Sie pro Touren-Typen einen <a href="https://de.wikipedia.org/wiki/Layertechnik">Layer</a> anlegen und die Touren entsprechend ihres Typs auf diesen Layern ablegen, können Sie es dem Kunden zusätzlich ermöglichen, nur die für ihn relevanten Touren einzublenden. Warum erkläre ich Ihnen dies an dieser Stelle? Alle Polyline Objekte und alle Polygone Objekte die zusammen definiert wurden, liegen automatisch zusammen auf einem eigenen separaten Layer.

Das Setzen von Klammern beim Arbeiten mit Polygon Objekten und Polyline Objekten, die mehrere Objekte gleichzeitig auf einem Layer erstellen, kann sehr herausfordernd sein.

<ul>
<li>Sie müssen zum einen alle Objekte – Polygon Objekte oder Polyline Objekte – zusammen mit einer äußeren Klammer versehen.`  
 **[**  
[[50.17264, -7.26469], [49.27264, -6.26469]],  
[[50.37264, -7.26469], [51.27264, -8.26469]]  
**]**` 
<li>Außerdem müssen Sie alles Punkte jedes einzelnen Objekts – Polyline oder Polygon – mit einer Klammer umgeben.  
`[  
**[**[50.17264, -7.26469], [49.27264, -6.26469]**]**,  
**[**[50.37264, -7.26469], [51.27264, -8.26469]**]**  
]` 
<li>Und zuletzt werden auch die Koordinaten selbst noch eingeklammert.  
`[  
[**[**50.17264, -7.26469**]**, **[**49.27264, -6.26469**]**],  
[**[**50.37264, -7.26469], **[**51.27264, -8.26469**]**]  
]` 
</ul>

### Mehrere Polyline Objekte auf einer Ebene

In diesem Kapitel gibt es nun ein praktisches Beispiel. Der nachfolgende Programmcodeausschnitt zeigt Ihnen, wie Sie mit dem instanziieren eines Objekts mehrerer Polyline Objekte auf eine Ebene zeichnen können. Und das die Polyline Objekte alle auf einer Ebene liegen, beweise ich Ihnen gleichzeitig.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**var multipolyline = L.polyline(**
**[**
**[
[50.17264, -7.26469],**
**[49.27264, -7.26469],**
**[49.27264, -6.26469]
],**
**[
[50.37264, -7.26469],**
**[51.27264, -7.26469],**
**[51.27264, -8.26469]
]**
**],**
**{color: 'black'}).addTo(mymap);**
**mymap.fitBounds(multipolyline.getBounds());**
</script>
</body>
</html>
<!--index_981.html-->
`</pre>

  Was zeigt Ihnen dieses Beispiel? Zunächst einmal können Sie erkennen, dass das Erstellen mehrerer Polyline Objekte zusammen möglich ist. Und das es auch einfacher ist erkennen Sie daran, dass Sie Optionen nur einmal zuweisen müssen. Beide Linien werden gleichzeitig schwarz gefärbt.

  Am meisten Vorteile bringt aber die Tatsache, dass beide Linien eine Ebene darstellen. Dies bedeutet, dass die Methode`fitBounds()`die beiden Linien als ein Objekt sieht und die Abgenzungen dieses einen Objektes berechnet. Die Methode <a href="http://leafletjs.com/reference-1.1.0.html#map-fitbounds">`fitBounds()`</a> verschiebt eine Karte an die Stelle, an der die übergebenen Koordinaten sich befinden, und setzt die Zoom-Stufe so, dass die Karte für die übergebenen Abgenzungen ideal angezeigt wird. Würden die beiden Linien nicht auf einer Ebenen liegen, wäre es komplizierter beide Linien gleichzeitig vollständig mit optimaler Zoom-Stufe anzuzeigen.

> Noch einmal zur Erinnerung:
Ein Objekt vom Typ`Polygon`und auch ein`Polyline`Objekt ist eine Ebene – die beiden Klassen erweitern die Leaflet
Klasse <a href="http://leafletjs.com/reference-1.1.0.html#layer">Layer</a>.  

  <img alt="" src="../Images/data-url-image33.png" id="Bild36"/>

### Mehrere Polygon Objekte auf einer Ebene

In diesem Kapitel zeige ich Ihnen ein Beispiel, bei dem mehrere Polygone zusammen erstellt werden.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**var multipolygone = L.polygon(
[
[
[50.17264, 7.26469],
[49.27264, 7.26469],
[49.27264, 6.26469]],
[
[50.37264, 7.26469],
[51.27264, 7.26469],
[51.27264, 8.26469]
]
],
{color: 'black'}).addTo(mymap).bindPopup("Wir sind auf einer Ebene");**
</script>
</body>
</html>
<!--index_982.html-->
`</pre>

In diesem Beispiel sehen Sie, wie Sie mit der<a class="sigil_index_marker" title="Methode  bindPopup()" id="sigil_index_id_19">Methode</a>`bindPopup()`ein Pop-up Fenster zu einem Element hinzufügen können. Später im Buch werden Pop-up Fenster noch einmal Thema sein. An dieser Stelle habe ich die Methode gewählt, weil ich der Meinung bin, das diese hier gut passt.
Es gibt viele unzusammenhängende Flächen auf der Erde, für die die gleichen Informationen zutreffend sind. Zum Beispiel haben viele Länder Kolonien. Wenn nun alle zu einem Land gehörenden Gebiete als Polygon auf einem Layer zusammengefasst sind, dann ist es ein Leichtes, allen Gebieten eines Landes das gleiche Pop-up Fenster zuzuweisen. Und wenn Sie nun die ganze Welt auf Ihrer Karte abdecken möchten, dann können Sie sich den Vorteil dieser <a href="https://de.wikipedia.org/wiki/Layertechnik" class="sigil_index_marker" title="Layer-Technik" id="sigil_index_id_20">Layer-Technik</a> sicherlich gut vorstellen.

Auf der nächsten Abbildung sehen sie keine Ländergrenzen. Der Einfachheit halber habe ich mich auf zwei Dreiecke beschränkt.

<img alt="" src="../Images/data-url-image34.png" id="Bild37"/>

#### Mehrere sich überschneidende Polygon Objekte auf einer Ebene

Die Besonderheit bei einem Polygon ist, dass es einen Außen- und einen Innenbereich gibt. Das lesen Sie hier im Buch des Öfteren. Wenn Sie mehrere Polygone auf einem Layer zusammen erstellen, dann beeinflussen diese sich gegenseitig, wenn Flächen übereinander liegen. In der nachfolgenden Tabelle habe ich verschiedene Konstellationen mit Bild und Text aufgenommen. Anhand von Beispielen ist das Zusammenspiel der verschiedenen Bereiche meiner Meinung nach am leichtesten nachzuvollziehen.

<table>
<colgroup>
<col/>
<col/>
</colgroup>

<tbody>
<tr valign="top">
<td>
Beginnen wir mit einem einfachen Polygone:  
`L.polygon([  
[ [1, 1], [1, 10], [10, 10], [10, 1] ]  
])`
</td>
</tr>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image35.png" id="Bild92"/>
</td>
</tr>
<tr valign="top">
<td>
Wenn Sie innerhalb dieses Polygons ein weiteres Polygon zeichnen, dann wird der Innenbereich des ersten Polygon um die Fläche des zweiten Polygon verringert. Das zweite Polygon wird praktisch aus dem ersten Polygone ausgeschnitten.
`L.polygon([  
[ [1, 1], [1, 10], [10, 10], [10, 1] ],  
**[ [2, 2], [2, 5], [5, 5], [5, 2] ] **  
])`
</td>
</tr>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image36.png" id="Bild93"/>
</td>
</tr>
<tr valign="top">
<td>
In dieses zweite Polygon können Sie nun wiederum ein Polygon zeichnen. Nun wird diese Fläche wieder voll als Innenbereich gezeichnet.  
`L.polygon([  
[ [1, 1], [1, 10], [10, 10], [10, 1] ],  
[ [2, 2], [2, 5], [5, 5], [5, 2] ],  
**[ [3, 3], [3, 4], [4, 4], [4, 3] ] **  
])`
</td>
</tr>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image37.png" id="Bild94"/>
</td>
</tr>
<tr valign="top">
<td>
Zeichnen Sie nun ein weiteres Polygon, dass Innenbereich und Außenbereich gleichzeitig abdeckt, dann wird der abgedeckte Innenbereich zum Außenbereich und umgekehrt.  
`L.polygon([  
[ [1, 1], [1, 10], [10, 10], [10, 1] ],  
[ [2, 2], [2, 5], [5, 5], [5, 2] ],  
[ [3, 3], [3, 4], [4, 4], [4, 3] ],  
**[ [9, 9], [11, 9], [11, 11], [9, 11] ] **  
])`
</td>
</tr>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image38.png" id="Bild95"/>
</td>
</tr>
</tbody>
</table>

<h2 id="sigil_toc_id_35">Daten mit Layern gruppieren</h2>

  Im vorherigen Kapitel haben Sie gesehen, dass Sie mehrere Polygone Objekte oder mehrere Polyline Objekte zusammen auf einem Layer positionieren können. Es wird sicher einmal vorkommen, dass Sie Elemente unterschiedlicher Typen auf einem Layer zusammen gruppieren möchten.

### Layergruppen

Die Leaflet Klasse <a href="http://leafletjs.com/reference-1.1.0.html#layergroup">`LayerGroup`</a> wird verwendet, um mehrere Layer oder Ebenen zu gruppieren. So können Sie diese Ebenen wie eine Ebene behandeln. Wenn Sie ein Objekt vom Typ `<a class="sigil_index_marker" title="LayerGroup (Leaflet)" id="sigil_index_id_21">LayerGroup</a>` zur Karte hinzufügen, werden alle zur Gruppe gehörenden Layer zum Karten Objekt hinzugefügt.

Der nachfolgende Programmcodeausschnitt zeigt Ihnen, wie Sie ein Objekt vom Typ`LayerGroup`erstellen und zu Ihrem Karten Objekt hinzufügen können.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

var **marker1** = L.marker([50.27264, 7.26469],
{
title:"Marker1",
alt:"Ich bin ein Marker"
}
).bindPopup('Marker1');

var **polyline** = L.polyline([
[50.27264, 7.26469],
[51.27264, 7.26469],
[51.27264, 6.26469]],
{color: 'red', weight:8});

**var myLayerGroup = L.layerGroup([marker1, polyline]).addTo(mymap);**

</script>
</body>
</html>
<!--index_980.html-->
`</pre>
  Im vorherigen Beispiel habe ich ein`Marker`Objekt und ein Objekt vom Typ`Polyline`erstellt und beide zusammen auf dem Layer`myLayerGroup`gruppiert.


> Sie können auch
später noch Objekt zum`LayerGroup`Objekt hinzufügen. Zum Beispiel so:  
`var marker2 = L.marker([51.27264, 6.26469],`  
`{`  
`title:"Marker2",`  
`alt:"Ich bin ein anderer Marker"`  
`}`  
`).bindPopup('Marker2');`  
`myLayerGroup.addLayer(marker2);`  

Entfernen können sie das`LayerGroup`Objekt – und somit alle zu ihr gehörenden Objekt auf einen Schlag – mit der<a class="sigil_index_marker" title="Methode  removeLayer()" id="sigil_index_id_22">Methode</a>`removeLayer()`. Im vohergehenden vollständigen Beispiel konkret mit der Zeile  
`myLayerGroup.removeLayer(polyline);`.

### Featuregruppen

Die<a class="sigil_index_marker" title="FeatureGroup (Leaflet)" id="sigil_index_id_23">Klasse</a>`FeatureGroup`erweitert die Klasse`LayerGroup`. Während die Klasse`LayerGroup`eher Methoden zum Gruppieren von Layern bereit stellt, geht es in der`FeatureGroup`hauptsächlich um das gemeinsame Verarbeiten von Ereignissen und das Hinzufügen von Stylen.


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

var **marker1** = L.marker([50.27264, 7.26469],
{
title:"Marker1",
alt:"Ich bin ein Marker"
}
);

var **polyline** = L.polyline([
[50.27264, 7.26469],
[51.27264, 7.26469],
[51.27264, 6.26469]],
);
**
var myfeatureGroup=L.featureGroup(
[marker1, polyline]
).addTo(mymap);

myfeatureGroup.bindPopup('Wir haben alle das gleiche Popup!');**

</script>
</body>
</html>
<!--index_979.html-->
`</pre>


  Analog zum Beispiel im Kapitel Layergruppen sehen Sie im vorhergehenden Programmcodeausschnitt, wie zwei Elemente erstellt und einem Objekt vom Typ`FeatureGroup`zugeordnet werden. Die FeatureGroup, wird dann zum Karten Objekt hinzugefügt und ein Aufruf der Methode`bindPopup()`beim`FeatureGroup`Objekt fügt das Pop-up zu allen Objekten des FeatureGroup Objektes hinzu.

  Wenn Sie alle Elemente des FeatureGroup Objektes rot färben möchten, reicht die Zeile


`myfeatureGroup.setStyle({color:'red'})
`


aus.

  Der Eintrag

`myfeatureGroup.on('click', function()`  
`{`  
`alert('Ein Gruppenmitglied wurde angeklickt!');`  
`}`  
`)`

würde bewirken, dass sich immer, wenn ein Element des`FeatureGroup`Objektes angeklickt wird, ein Hinweisfenster öffnet.

Wenn Sie das`FeatureGroup`Objekt mit Inhalt mit einem Mausklick entfernen möchten, können Sie folgenden Text zu Ihrem Skript hinzufügen:

`myfeatureGroup.on('click', function()`  
`{`  
`myfeatureGroup.removeLayer(polyline);`  
`}  
)`  


<h2 id="sigil_toc_id_36">Popups</h2>

In diesem Kapitel geht es um Leaflet Objekte vom Typ <a href="http://leafletjs.com/reference-1.1.0.html#popup">`Popup`</a>. Mithilfe dieses Objekts können Sie <a class="sigil_index_marker" title="Pop-up Fenster " id="sigil_index_id_24">Pop-up Fenster</a> an bestimmten Stellen auf Ihrem Karten Objekt öffnen. Wenn Sie die Methode <a href="http://leafletjs.com/reference-1.1.0.html#map-openpopup" class="sigil_index_marker" title="Methode openPopup()">`openPopup()`</a> einsetzten, um das Pop-up Fenster zu öffnen, stellt Leaflet sicher, dass gleichzeitig nur ein Pop-up geöffnet ist. Ich empfehle Ihnen diese Methode einzusetzen, weil ich der Meinung bin, das das gleichzeitige Öffnen von mehreren Pop-up Fenstern nicht benutzerfreundlich ist. Nichtsdestotrotz kann es aber sein, dass Sie gerne mehrere Pop-up Fenster gleichzeitig anzeigen möchten. In diesem Fall müssen Sie das Pop-up Fenster mit der Methode <a href="http://leafletjs.com/reference-1.1.0.html#map-addlayer" class="sigil_index_marker" title="Methode addLayer()">`addLayer()`</a> auf einem eigenen Layer einbinden.

  So nun aber genug der Theorie. Sehen Sie sich das alles anhand des nachfolgenden Programmcodes – am besten auf praktische Weise – an.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {**closePopupOnClick: false**})
.setView([50.27264, 7.26469], 7);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var **marker1** = L.marker([50.27264, 7.26469],
{
title:"Marker1",
alt:"Ich bin Marker 1"
}
).addTo(mymap);

var **marker2** = L.marker([51.27264, 6.26469],
{
title:"Marker2",
alt:"Ich bin Marker 2"
}
).addTo(mymap);

**marker1.bindPopup("<h1>Gering</h1>
<p>Ein kleines <a href='https://de.wikipedia.org/wiki/Dorf'>Dorf</a></p>
<ul><li>auf dem Maifeld</li><li>in der Eifel</li><li>an der Elz</li></ul>"
);

marker2.bindPopup("<h1>Boisheim</h1>
<p>Ein kleines Dorf</p>
<ul><li>irgendwo</li><li>nordwestlich</li><li>von Gering</li></ul>"
);**

</script>
</body>
</html>
<!--index_978.html-->
`</pre>










  Was zeigt Ihnen dieses Beispiel genau? Sie sehen, wie Sie zwei Marker erstellen und diesen mit der Methode`bindPopup()`ein Pop-up Fenster hinzufügen könne. Wenn Sie den ersten Marker anklicken, dann öffnet sich das Pop-up Fenster dieses Markers. Wenn Sie danach den zweiten Marker anklicken, schließt sich das Pop-up Fenster des ersten Markers und das Pop-up Fenster des zweiten Markers wird aktiv.
Vielleicht ist Ihnen aufgefallen, dass wir beim Karten Objekt die Option`closePopupOnClick`<a class="sigil_index_marker" title="Option closePopupOnClick" id="sigil_index_id_25">auf</a>`false`gesetzt haben. Diese Option ist standardmäßig mit`true`belegt, was bedeutet, dass auch beim Klick auf eine beliebige Position auf der Karte ein eventuell offenes Pop-up Fenster von Leaflet automatisch geschlossen wird.

> Möchten Sie, dass das Pop-up Fenster zum Marker mit dem Namen`marker1`schon beim Öffnen der Karte angezeigt wird? Dann schreiben Sie einfach den Text`marker1.openPopup();`in Ihr Skript.


  Wie die Karte zum vorhergehenden Programmcodeausschnitt im Browser aussieht, sehen Sie in der nachfolgenden Abbildung.

  <img alt="" src="../Images/data-url-image39.png" id="Bild38"/>

> Ich hatte Ihnen zu Beginn dieses Kapitels schon erklärt, dass Leaflet standardmäßig
nur ein Pop-up Fenster gleichzeitig offen anzeigt. Dies ist so, wenn Sie das
Pop-up Fenster mithilfe der Methode`openOn()`<a class="sigil_index_marker" title="Methode openOn()" id="sigil_index_id_26">zu</a>Karte hinzufügen:  
`var popup1 = L.popup({**keepInView**:true})  
.setLatLng([49.27264, 6.26469])  
.setContent('<p>Hallo Welt<br />Ich bin ein Popup.</p>')  
.**openOn**(mymap);`  
Falls Sie mehrere Pop-up Fenster
gleichzeitig anbieten möchte, dann können Sie dies mithilfe der
Methode `addTo()`<a class="sigil_index_marker" title="Methode addTo()" id="sigil_index_id_27">bew</a>erkstelligen.
`var popup1 = L.popup()  
.setLatLng([49.27264, 6.26469])  
.setContent('<p>Hallo Welt<br />Ich bin ein Popup.</p>')  
.**addTo**(mymap);`


Die Eigenschaft `keepInView:true` bewirkt hier übrigens, dass die Karte nur so weit verschoben werden kann, wie der Marker sichtbar ist.

  <h2 id="sigil_toc_id_37">Mobil</h2>

  Ein großer Vorteil von JavaScript ist es, das Landkarten in jedem aktuellen Standardbrowser ohne notwendige externe Applikationen oder Plugins angezeigt werden können.

> Genaue Informationen zu den unterstützten
Browsern finden Sie auf der Website von <a href="http://leafletjs.com/">Leaflet</a>
im Bereich *Features*.


  Jede Website, die eine Leaflet Karte anzeigt, kann vom Entwickler auf die gleiche Art und Weise programmiert werden. Der Entwickler muss im Normalfall nichts Spezielles für ein Gerät beachtet. Ein paar erwähnenswerte Punkte gibt es aber trotzdem und das, was meiner Meinung nach erwähnenswert ist, finden Sie in diesem Kapitel.

  Das Spannendste bei der Arbeit mit mobilen Anwendungen ist sicherlich die Funktio<a class="sigil_index_marker" title="Methode locate()" id="sigil_index_id_28">n</a><a href="http://leafletjs.com/reference-1.1.0.html#map-locate">locate()</a>. Diese Funktion versucht, den Benutzer mit der<a class="sigil_index_marker" title="W3C Geolocation API " id="sigil_index_id_29">W3C Geolocation API</a>zu lokalisieren. Die <a href="https://www.w3.org/TR/geolocation-API/">W3C Geolocation API </a>ist eine einheitliche Webbrowser-Programmierschnittstelle zum Ermitteln des geografischen Standorts des zugehörigen Endgeräts. Aber beginnen wir von vorne mit dem Bereich HTML und CSS.

### HTML und CSS

Sie möchten Ihre Leaflet Karte auch für<a class="sigil_index_marker" title="mobile Geräte" id="sigil_index_id_30">mobile Geräte</a>optimal konfigurieren? Dann sollten Sie als Erstes sicherstellen, dass die Karte passend angezeigt wird. Sie möchten sicher nicht, dass jemand der die Karte über ein Gerät mit einem kleinen Display aufruft, nur einen Teil der Karte sieht und er diese erst verschieben muss, um auch die Randbereiche zu erkennen. Oder, dass die Karte so klein dargestellt wird, dass der Inhalt auf einem kleinen Display nicht lesbar ist. Ideal ist es, wenn die vollständige Karte im Display lesbar angezeigt wird. In diesem Punkt stimmen Sie mir sicher zu. Das nächste Beispiel zeigt Ihnen, wie Sie die vollständige Karte im Display lesbar angezeigen können.


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<meta name="viewport" content="width=device-width, initial-scale=1.0,
maximum-scale=1.0, user-scalable=no" />
<style>body {padding: 0;margin: 0;}html, body, #mapid {height: 100vh;width: 100vw;}
</style>**
</head>
<body>
<div id="mapid"></div>
<script>
var mymap = L.map('mapid', {closePopupOnClick: false})
.setView([50.27264, 7.26469], 18);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**mymap.locate({setView: true, maxZoom: 18});**

mymap.on('**locationfound**', onLocationFound);
mymap.on('**locationerror**', onLocationError);

function **onLocationFound**(e) {
var radius = e.accuracy / 2;
L.marker(e.latlng).addTo(mymap)
.bindPopup("Sie sind etwa" + radius + " Meter von diesem Punkt entfernt.")
.openPopup();
L.circle(e.latlng, radius).addTo(mymap);
}

function **onLocationError**(e) {
alert(e.message);
}

</script>
</body>
</html>
<!--index_977.html-->
`</pre>









> Wissen Sie, dass Sie zum Debuggen die Methode`console.log()`verwenden können? Der Eintrag  
`<script>`   
`...`  
`console.log(e);`  
`...`  
`</script>`  
gibt an einer Stelle, an der das Objekt `e` instanziiert ist, den Inhalt dieses Objektes in der Konsole aus.  
Die Konsole können Sie im Browser <a href="https://www.mozilla.org/de/firefox/new/">Mozilla Firefox</a> über das Menü  
`Extras | Web Entwickler | Web Konsole öffnen`.  
Im Browser <a href="https://www.google.de/chrome/browser/desktop/index.html">Google Chrome</a> finden Sie die Konsole über das Menü  
`Tools | Javascipt-Konsole`.

Dieses Beispiel enthält zusätzlich zu den vorhergehenden Beispielen ein `<style>`-Element. In diesem`<style>`-Element sind die Abstände, also`padding`und`margin`, auf`0`gesetzt. So passt die Karte sich genau an das Dispay an und es wird kein Platz mit Rändern verschwendet. Außerdem haben wir die Höhe mit`height: 100vh`auf 100 % gesetzt, damit diese voll ausgenutzt wird.

Die Einheiten <a href="https://www.w3.org/TR/css3-values/#viewport-relative-lengths">vw</a><a href="https://www.w3.org/TR/css3-values/#viewport-relative-lengths"> und </a><a href="https://www.w3.org/TR/css3-values/#viewport-relative-lengths">vh</a>
definieren eine Breite - beziehungsweise Höhe - in Relation zur Größe
des Browser-Fensters. Dabei steht`vw`für die Breite und` vh`für
die Höhe des Viewport. Diese Viewport Units ermöglichen es, Größen
in Relation zur jeweils aktuellen Größe des Browser-Fensters zu
definieren.

  Den fixen Wert für die Höhe, der im `<div>`-Element des Karten-Objektes enthalten war, habe ich entfernt. So verschwindet auch die Bildlaufleiste am rechten Rand.

  Außerdem ist in diesem Beispiel das Meta-Element`viewport`hinzu gekommen. Somit kann die Seite für mobile Geräte nicht künstlich verkleinert oder vergrößert werden – zoomen ist aber immer noch möglich!

> Bei die Anzeige auf mobilen Geräten spielt das<a class="sigil_index_marker" title="viewport (Meta-Element)" id="sigil_index_id_31">Meta-Element</a>`viewport`eine große Rolle. In unserm Beispiel haben wir die Attribute`initial-scale=1.0`,`maximum-scale=1.0`, und`user-scalable=no`verwendet.  
Das Attribut`initial-scale`legt die anfängliche Zoom-Stufe fest.`1.0`führt dazu, dass die Inhalte in ihrer Originalgröße
dargestellt werden. Das bedeutet, dass auf einem Display mit 320
Pixel Breite, eine 320 Pixel breite Grafik die volle Breite
ausfüllt. Im Gegensatz dazu würde der Wert`2.0`zu einer 2-fachen Vergrößerung führen – das Bild wäre dann nur noch
halb zu sehen.  
Das Attribut`user-scalable`bestimmt, ob der Nutzer die Anzeige der Website vergrößern oder
verkleinern kann.  
Die Attribute`minimum-scale`und`maximum-scale`ermöglichen es die Zoom-Stufe einzuschränken. Die Vorgabe`maximum-scale=1.0`,
bewirkt, dass der Inhalt nicht vergrößert werden kann.
  
### JavaScript

Die Karte wird nun passend auf der Website angezeigt. Soweit so gut! Wir können die Karte aber noch benutzerfreundlicher machen. Jemand der mit einem mobilen Gerät im Internet unterwegs ist, nutzt sein Gerät in der Regel an verschiedenen Standorten. Und meistens ist es so, dass das, was in der Nähe ist, am interessantesten ist. Ideal wäre es also, wenn die Karte sich sofort so öffnet, dass der aktuelle Standort in der Mitte der Karte dargestellt wird. Und das ist möglich. Leaflet bietet Ihnen Funktionen, die Sie nutzen können.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<meta name="viewport" content="width=device-width, initial-scale=1.0,
maximum-scale=1.0, user-scalable=no" />
<style>body {padding: 0;margin: 0;}html, body, #mapid {height: 100vh;width: 100vw;}
</style>**
body {
padding: 0;
margin: 0;
}
html, body, #mapid {
height: 100vh;
width: 100vw;
}
</style>
</head>
<body>
<div id="mapid"></div>
<script>
var mymap = L.map('mapid', {closePopupOnClick: false}).setView([50.27264, 7.26469], 18);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**mymap.locate({setView: true, maxZoom: 18});
mymap.on('locationfound', onLocationFound);
mymap.on('locationerror', onLocationError);

function onLocationFound(e) {
var radius = e.accuracy / 2;
L.marker(e.latlng).addTo(mymap)
.bindPopup("Sie sind etwa" + radius + " Meter von diesem Punkt entfernt.")
.openPopup();
L.circle(e.latlng, radius).addTo(mymap);**
**}
**
function onLocationError(e) {
alert(e.message);
}
</script>
</body>
</html>
<!--index_977.html-->
`</pre>








Wenn Sie eine Website besuchen, die standortbezogenes Surfen unterstützt – zum Beispiel die Leaflet Karte im Beispielcode – prüft der Browser, ob Sie Ihren Aufenthaltsort bekannt geben möchten. Wenn Sie zustimmen, berechnet der Browser Ihren Standort über nahe gelegene Funkzugangsknoten oder die IP-Adresse Ihres Computers. Diese ungefähre Ortsangabe wird dann an die anfragende Website weitergegeben.  

Wenn Sie Ihren Standort freigegeben haben, dann sehen beim Aufruf der Karte einen Kreis, der Ihren ungefähren Standort wiedergibt und ein Pop-up Fenster, dass Ihnen erklärt wo Sie sich gerade befinden. Möchten Sie Ihren Standort nicht mit anderen teilen, dann sehen Sie eine Fehlermeldung beim Öffnen der Karte. Diese Fehlermeldung erklärt Ihnen, warum Sie nicht geortet werden können.  

Damit Sie sich auch Bild davon machen könne, wenn Sie das Beispiel gerade nicht praktisch nachvollziehen können, habe ich Ihnen Bilder eingefügt.

<img alt="" src="../Images/data-url-image40.png" id="Bild39"/>

<img alt="" src="../Images/data-url-image41.png" id="Bild40"/>

<img alt="" src="../Images/data-url-image42.png" id="Bild41"/>

Leaflet bietet Ihnen noch weitere <a href="http://leafletjs.com/reference-1.1.0.html#locate-options">Geolokalisierungsmethoden</a> und <a href="http://leafletjs.com/reference-1.1.0.html#locationevent">Geolokalisierungsereignisse</a> an.

<h2 id="sigil_toc_id_38">Ereignisse in Leaflet</h2>

Bisher haben wir ausschließlich mit statischen Daten gearbeitet. In der Welt passiert aber fortwährend ganz schön viel und Sie möchten sicherlich mit Ihrer Karte auf das ein oder andere Ereignis reagieren. Vielleicht möchten Sie je nach Standort einen Pop-up Text ändern. Oder Sie möchten auf ein anderes Ereignis reagieren. Vielleicht wissen Sie auch noch gar nicht so genau auf welche Ereignisse Sie reagieren können. Dann shen Sie sich zur Inspiration doch einfach einmal an, was Leaflet Ihnen bietet. Insgesamt bietet Leaflet Ihnen 34 verschiedene Ereignisse, die die sie nutzen können. Alle Ereignisse sind in der <a href="http://leafletjs.com/reference-1.1.0.html#events">Dokumentation</a> gut erklärt.

Exemplarisch sehen wir uns mit dem folgenden Programmcode – wieder anhand eines ganz einfache Beispiels – die Vorgehensweise genauer an. Konkret reagieren wir auf einen Mausklick.


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid', {closePopupOnClick: false}).setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**mymap.on('click',
function(){
alert('Sie haben auf die Karte geklickt.')
}
);
**
</script>
</body>
</html>
<!--index_976.html-->
`</pre>

  Leaflet bietet die Methode <a href="http://leafletjs.com/reference-1.1.0.html#evented-on">`on()`</a> um auf ein Ereignis zu reagieren. Der erste Parameter, der mit dieser Methode übergeben wird, steht für den Ereignistyp. In unserem Falle ist dies`click`. Der zweite Wert erwartet eine Funktion, die beim Eintreten des Ereignisses ausgeführt werden soll.

> In unserem Beispiel haben wir die Funktion sofort in den Methodenaufruf eingefügt:  
`mymap.on('click',  
function(){  
alert('Sie haben auf die Karte geklickt.')  
}  
);`  
Diese Schreibweise wird auch als <a class="sigil_index_marker" title="anonymer Funktionsausdruck" id="sigil_index_id_32">anonymer Funktionsausdruck</a>bezeichnet,
weil die Funktion keinen Namen hat.


  Wenn Sie die Karte des vorhergehenden Beispiels im Browser aufrufen und anklicken, sehen Sie die in der nachfolgenden Abbildung dargestellte Meldung.

  <img alt="" src="../Images/data-url-image43.png" id="Bild42"/>

> Vielleicht möchten sie selbst eigene Beispiele ausprobieren und diese anderen zeigen.  
Insbesondere bei der Fehlersuche ist dies oft hilfreich.  
Dies können Sie mithilfe des <a href="http://playground-leaflet.rhcloud.com/fixo/edit?html,console,output">Leaflet Playgrounds</a> tun.

### Eine benutzerdefinierte Funktionen

Die Methoden, die Leaflet Ihnen bietet, kennen Sie nun. Bisher haben Sie immer die Variable`e`in den Funktionen übergeben. Mit JavaScript können Sie aber auch eigene Variablen übergeben. Außerdem können Sie eigene Funktionen an beliebigen Stellen im Programmcode aufrufen.

Probieren wir das doch sofort einmal aus. Im nächsten Beispiel erstellen wir einen Marker und verbinden diesen mit einem Pop-up Fenster – und das mithilfe einer selbst erstellten Funktion.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid', {closePopupOnClick: false}).setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

var marker1 = L.marker([50.27264, 7.26469]).addTo(mymap)
.bindPopup(**createPopup**("Text als Parameter"));

var marker2 = L.marker([51.27264, 6.26469]).addTo(mymap)
.bindPopup(**createPopup**("Anderer Text als Parameter"));

**function createPopup(popuptext){
return L.popup({autoClose:false, keepInView:true, closeButton:false})
.setContent(popuptext);
}
**
</script>
</body>
</html>
<!--index_975.html-->
`</pre>

  In diesem Beispiel ging es nur um das Grundsätzliche und die Mächtigkeit von eigenen Funktionen wird mit nur zwei Markern noch nicht klar. Vielleicht können Sie sich aber vorstellen, wie viel Text mithilfe einer benutzerdefinierten Funktion eingespart werden kann.

> Achtung: Wenn Sie bei einem Pop-up Fenster die Eigenschaften`autoClose:false`und`closeButton:false`gleichzeitig setzten, kann dieses Pop-up Fenster tatsächlich nicht
mehr geschlossen werden.

  <img alt="" src="../Images/data-url-image44.png" id="Bild43"/>

### Ein interaktives Beispiel

  Und zu guter Letzt möchte ich Ihnen noch ein interaktives Beispiel zeigen.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<p>Bitte geben Sie eine Koordinte an:</p><br>
Geographische Breite:<input type="text" id="lat"><br>
Geographische Länge:<input type="text" id="long"><br>
Name:<input type="text" id="name"><br>
**<button onclick="save()">Speichern</button>**
<div style="height: 700px;" id="mapid"></div>

<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 7);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**function save(){
var p1 = parseFloat(document.getElementById("lat").value);**
**var p2 = parseFloat(document.getElementById("long").value);
L.marker([p1,p2]).bindPopup(document.getElementById("name").value).addTo(mymap);**
**}**
</script>
</body>
</html>
<!--index_974.html-->
`</pre>



  Im vorhergehenden Beispiel ist eine Schaltfläche integriert, die – wenn sie angeklickt wird – eine benutzerdefinierte Funktion ausführt. Mit der Funktion wird ein Marker mit einem Pop-up Fenster in die Karte eingesetzt. Dies ist nur als Beispiel gedacht. Die können in der benutzerdefinierten Funktion alles Mögliche ausführen – lassen Sie Ihrer Fantasie freien Lauf. Ein weiterer Anwendungsfall könnte eine Art Heiß-Kalt Spiel sein. Sie kennen sicher das einfache Suchspiel.

 > Möchten die interaktiv eingefügten Daten in einem Objekt speichern, um einen Überblick über diese zu haben und eventuell weitere Aktionen von dem Datenbestand abhängig zu machen?  
Das vorhergehende Beispiel könnten Sie in diesem Falle wie folgt erweitern. Sie könnten mithilfe der Zeile  
`var myStorage = localStorage;`  
ein <a href="https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage">localStorage</a> Objekt instanziieren. Mit  
`myStorage.setItem(`  
`document.getElementById("name").value,`  
`document.getElementById("lat").value+ "," + document.getElementById("long").value`  
`);`  
konnten Sie daraufhin alle eingefügten Objekte speichern und mit diesen arbeiten.  
Die`sessionStorage`-Eigenschaft
erlaubt den Zugriff auf ein, nur während der aktuellen Sitzung,
verfügbares Storage-Objekt.`sessionStorage`ist mit einer Ausnahme identisch zu`Window.localStorage`:
In`localStorage`gespeicherte Daten besitzen kein Verfallsdatum, während Sie im`sessionStorage`mit Ablauf
der Sitzung gelöscht werden.  
Eine Sitzung endet mit dem
Schließen des Browsers, sie übersteht das Neuladen und
Wiederherstellen einer Webseite. Das Öffnen einer Webseite in einem
neuen Tabulator oder Browser-Fenster erzeugt jedoch eine neue
Sitzung. Dies unterscheide ein`sessionStorage`Objekt von einem`Session-Cookie:`<a href="https://developer.mozilla.org/de/docs/Web/API/Window/sessionStorage">https://developer.mozilla.org/de/docs/Web/API/Window/sessionStorage</a>
  
<h2 id="sigil_toc_id_39">In diesem Kapitel haben wir …</h2>

  In diesem Kapitel haben Sie Punkte, Marker, Linien und Polygone kennen gelernt. Sie können diese nun auf eine Leaflet-Karte zeichnen und wissen, wann welches Objekt das Richtige ist. Sie können Layer-Gruppen und Featur-Gruppen voneinander unterscheiden und wissen die Grundlagen zur Anzeige von mobilen Leaflet Karten. Und auf einen Mausklick oder ein anderes Ereignis können Sie entsprechend reagieren.  
Im nächsten Kapitel geht es um das Format GeoJson und darum, wie Sie Daten auch in großen Mengen gut Handhaben können.

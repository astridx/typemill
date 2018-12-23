# Custom Markers

Wenn Sie intensiver mit digitalen Landkarten arbeiten, möchten Sie sicherlich auch einmal Daten eines Geoinformationssystems (GIS) auf Ihrer Karte anzeigen.

> Ein <a href="https://de.wikipedia.org/wiki/Geoinformationssystem">Geoinformationssystem (https://de.wikipedia.org/wiki/Geoinformationssystem)</a>
ist ein Informationssystem zur Erfassung, Bearbeitung, Organisation,
Analyse und Präsentation von Daten, die einen Bezug zu einer Stelle
auf unserer Erde haben. Zu einem Geoinformationssystem gehören dabei
die notwendige Hardware, die notwendige Software, die Daten und die
Anwendungen selbst.
 
Wenn Sie Daten eines Geoinformationssystems nutzen möchten, werden Sie früher oder später über den Begriff <a href="https://de.wikipedia.org/wiki/Shapefile">Shapefile (https://de.wikipedia.org/wiki/Shapefile)</a> oder Shape Datei stolpern. Aber auch wenn Sie nie auf den Begriff  <a class="sigil_index_marker" title="Shape Datei" id="sigil_index_id_1">Shape Datei</a>  stoßen werden Sie vielleicht einmal einen Webservice nutzen, der Endpunkt eines ARCServers ist. Außerdem werden Sie sicher auch das ESRI Inc., also das Environmental Systems Research Institute, kennenlernen. Dieses Institut ist ein US-amerikanischer Softwarehersteller.  <a href="https://de.wikipedia.org/wiki/ESRI">ESRI (https://de.wikipedia.org/wiki/ESRI)</a>  hat sich auf Geoinformationssysteme spezialisiert. Das Unternehmen hat unter anderem die Anwendung <a href="https://de.wikipedia.org/wiki/ArcGIS">ArcGIS (https://de.wikipedia.org/wiki/ArcGIS)</a> erstellt und das Dateiformat Shapefiles eingeführt.

> Die wesentlichen Produkte des ESRI sind
Geoinformationssysteme. Die Namen der verschiedenen
Geoinformationssysteme des ESRI enthalten in der Regel den Namensteil
ArcGIS. Es gibt ArcGIS Anwendungen für Server und für Clients.

Bitte lassen Sie sich durch die vielen neuen Begriffe nicht verunsichern. Natürlich gibt es Leaflet Plugins, die Ihnen beim Integrieren dieser Services zur Hand geht. Außerdem sehen wir uns alles Schritt für Schritt und nacheinander an.

<h2 id="sigil_toc_id_78">In diesem Kapitel werden wir …</h2>

In diesem Teil werden wir uns als Erstes die Karten, die das <a href="https://www.esri.de/">ESRI (https://www.esri.de)</a> anbietet, ansehen. Danach schauen wir, was sich hinter dem Begriff Shapefile versteckt. Außerdem werden wir ESRI Webservices kennen lernen. Unter anderem einen L.esri.DynamicMapLayer, Geocoding und einen L.esri.FeatureLayer – hier konkret einen Query Layer. Mit letztgenanntem können Sie Daten, die Sie nicht benötigen, einfach aus der gegebenen Datenmenge herausfiltern.

<h2 id="sigil_toc_id_79">`L.esri.BasemapLayer` erweitert `L.TileLayer`</h2>

Mit der Klasse  `L.esri.BasemapLayer`  können Sie Karten, die das Esri anbietet, auf Ihrer Website als Leaflet Karte anzeigen.

> Die <a href="https://github.com/esri/esri-leaflet#terms">Nutzungsbedingungen</a>
für ESRI Dienste gelten für Leaflet Anwendungen. Diese können Sie
auf der Website <a href="https://github.com/esri/esri-leaflet#terms">https://github.com/esri/esri-leaflet#terms</a>
nachlesen.

### Basemaps und optionale Layer von ESRI

Sie möchten Basemaps von ESRI verwenden. Wir haben im Kapitel *<a href="../Text/EineErsteKarte.html#sigil_toc_id_21">Schöne Kartenlayer</a>* schon Karten von anderen Kartenanbietern eingebunden. Dieses Kapitel erweitert die Erklärungen im Kapitel *Schöne Kartenlayer *um ein weiteres Beispiel – nämlich die Karten des ESRI Instituts.

#### Basemaps

Basemaps von ESRI bieten eine weltweite Abdeckung bei einer Vielzahl von Zoom Stufen. Dabei können die folgenden Themenbereiche wählen.

- Streets 
- Topographic 
- NationalGeographic 
- Oceans 
- Gray 
- DarkGray 
- Imagery 
- ShadedRelief 
- Terrain 
- USATopo (Diese Karte wird nur für die USA angeboten) 

Wenn Ihnen eine der Basiskarten grundsätzlich gut gefällt, diese Ihnen aber zu wenig Informationen bietet, können Sie weitere optionale Ebenen über diese Basisebene einblenden. ESRI bietet speziell für jede Basisebene eine optionale Ebene mit weiteren Informationen.

#### Optionale Label Layer

Label Layer sind optionale Ebenen, die zusätzliche Textbeschriftungen zu den Basiskarten hinzufügen. ESRI biete Ihnen sieben verschiedene optionale Schichten. Jede Ebene ist speziell für eine Basiskarte kreiert worden. Wenn Sie möchten, können Sie diese aber auch quer Beet kombinieren. Konkret bietet ESRI die Layer

- OceansLabels:
- GrayLabels:
- DarkGrayLabels:
- ImageryLabels:
- ImageryTransportation:
- ShadedReliefLabels
- TerrainLabels

Alle möglichen Basiskarten mit optionalen Ebenen können Sie auch in der Dokumentation des Leaflet Plugins nachlesen. Genau finden Sie diese Informationen unter der Adresse <a href="https://esri.github.io/esri-leaflet/api-reference/layers/basemap-layer.html">https://esri.github.io/esri-leaflet/api-reference/layers/basemap-layer.html</a>

> Wenn Sie möchten, können Sie die Anzeige von
Basemaps bei höheren Auflösungen auf Retina-Geräten mit der Option  `detectRetina`  optimal einstellen. Im nachfolgenden Programmcodeausschnitt wird die
Basemap auf einem Retina Display in Retina-Auflösungen ausgegeben.
Was ein Retina Display ist, habe ich Ihnen im Kapitel  <a href="../Text/CustomMarkers.html#retina">Custom Markers</a>*  *schon in einem Hinweis erklärt. Die Option  `detectRetina`  ist eine <a href="http://leafletjs.com/reference-1.2.0.html#tilelayer-detectretina">Leaflet Funktion</a>  

…  
L.esri.basemapLayer('DarkGray', {  
**detectRetina: true**  
}).addTo(map);  
 …  
  
Wenn Sie die Option  `detectRetina`  mit  `true`  belegt haben und ein Website-Besucher Ihre Karte auf einem Geräte mit einem Retina-Display öffnet, wird Leaflet anstelle der Bilddateien zur aktuellen Zoom-Stufe die vierfache Anzahl der Bildkacheln der nächsthöheren Zoom-Stufe anfordern und anzeigen. Wie die Bilddateien für eine Zoom-Stufe berechnet werden, können Sie im Kapitel *<a href="../Text/EineErsteKarte.html#uFWDKZaFtU7YxdvHCSQTPY6">Wie weiß Leaflet welche Kacheln angezeigt werden sollen?</a>* nachlesen.

### Ein erstes Beispiel

Das nachfolgende Beispiel zeigt Ihnen, wie Sie eine ESRI Basiskarte in Leaflet anzeigen können.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="esri-leaflet-debug.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 7);
**
var gray = L.esri.basemapLayer('Gray').addTo(mymap);

****var graylabels = L.esri.basemapLayer('GrayLabels')
.addTo(mymap);
****gray.setOpacity(0.5);
****gray.on('load', alertme);
****
function alertme(){
****alert("Fertig!");
****}**
</script>
</body>
</html>
<!--index_945.html-->
`</pre>







Das haben wir gemacht? Fangen wir mit dem wichtigen an: Wichtig ist, dass wir das Skript zum ESRI Leaflet Plugin einbinden. Ich habe dies mit der Zeile `<script src="esri-leaflet-debug.js"></script>` getan. Im Echtsystem können Sie die komprimierte Version verwenden, also `<script src="esri-leaflet.js"></script>`. Die aktuellste Version dieses Skripts können Sie von der Adresse <a href="http://esri.github.io/esri-leaflet/download/">http://esri.github.io/esri-leaflet/download/</a> kopieren. Nach dem Einbinden des Plugins haben wir mit der Zeile `var gray = L.esri.basemapLayer('Gray').addTo(mymap);` das `L.esri.basemapLayer` Objekt erstellt und es auch sofort zur Karte hinzugefügt. Zusätzlich haben wir die Karte mit `gray.setOpacity(0.5);` transparent dargestellt und dem Ereignis `on('load')` die Funktion `alertme()` zugeordnet. Immer dann, wenn die Karte fertig geladen ist, soll die Funktion `alertme()` ausgeführt werden. Genau bedeutet das, dass immer, wenn die Karte fertig geladen ist, ein Hinweisfenster erscheint. Verschieben Sie die Karte einmal. Dabei werden Sie sehen, dass das Ereignis `on('load')` auch immer dann, wenn die Karte neu geladen wird, eintritt.

Die beiden nachfolgenden Abbildungen zeigen Ihnen die Basiskarte mit dem Namen gray – einmal mit und einmal ohne optionale Ebene.

<table cellpadding="4" width="100%" cellspacing="0">
<colgroup>
<col width="128*"/>
<col width="128*"/>
</colgroup>
<tbody>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image80.png" id="Bild99"/>  
*Die Basiskarte Gray mit optionaler Ebene*
</td>
</tr>
<tr valign="top">
<td>
<img alt="" src="../Images/data-url-image81.png" id="Bild100"/>  
*Die Basiskarte Gray ohne optionale Ebene*
</td>
</tr>
</tbody>
</table>

### Switch Basemaps

Im nächsten Beispiel habe ich eine Auswahllist im HTML-Dokument über der Karte eingefügt. So können Sie zwischen den verschiedenen ESRI Karten schnell hin und her wechseln und sich so einen Überblick über das Kartenangebot verschaffen.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="esri-leaflet-debug.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>

<select
style ="position: absolute;top: 10px;right:10px;z-index: 400;"
id="basemaps"
onChange="changeBasemap(basemaps)"
>
<option value="Topographic">Topographic</option>
<option value="Streets">Streets</option>
<option value="NationalGeographic">National Geographic
</option>
<option value="Oceans">Oceans</option>
<option value="Gray">Gray</option>
<option value="DarkGray">Dark Gray</option>
<option value="Imagery">Imagery</option>
<option value="ShadedRelief">Shaded Relief</option>
<option value="Terrain">Terrain</option>
<option value="USATopo">USATopo </option>
</select>

<script>
var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 7);

var layer = L.esri.basemapLayer('Gray').addTo(mymap);
**
function changeBasemap(basemaps){
**** var basemap = basemaps.value;
****
 if (layer){
**** mymap.removeLayer(layer);
**** }
****
 layer = L.esri.basemapLayer(basemap);
**** mymap.addLayer(layer);
****}**

</script>
</body>
</html>
<!--index_944.html-->
`</pre>

Was haben wir genau gemacht? Hier gibt es nichts weltbewegend Neues. Eine Auswahlliste haben wir schon oft im Buch verwendet, deshalb ist diese im Programmcodebeispiel auch nicht fett hervorgehoben. Wenn ein Website-Besucher den aktiven Listeneintrag der Auswahlliste ändert, wird die aktuelle Kartenebene mit `mymap.removeLayer(layer)` entfernt. Danach wird eine neue Ebene mit der gewünschten Option erstellt – `layer = L.esri.basemapLayer(basemap)` – und diese wird dann zum Kartenobjekt hinzugefügt `mymap.addLayer(layer)`.

Im Ergebnis können Sie sich mithilfe der Auswahlliste alle ESRI Karten ansehen. Oder Sie können es einem Website-Besucher ermöglichen die Karte, die dieser am besten findet, für seine Ansicht zu aktivieren.

<img alt="" src="../Images/data-url-image82.png" id="Bild69"/>

<h2 id="inShapefiles">Shapefiles</h2>

Das Dateiformat Shapefile wurde von der Firma ESRI für die Software ArcView entwickelt. Shape Dateien sind speziell für die Verarbeitung von Geodaten entwickelt worden.

### Was genau verbirgt sich hinter dem Begriff Shapefile

Ein <a class="sigil_index_marker" title="Shapefile" id="sigil_index_id_2">Shapefile</a>  ist keine einzelne Datei. In der Regel handelt es sich um mehrere Dateien, die zu einem Zip-Archiv zusammengefasst sind. In diesem Zip-Archiv müssen mindestens die drei nachfolgend genannten Dateitypen vorhanden sein:

- Eine Datei mit der Endung  `.shp`  dient zur Speicherung der Geometriedaten. 
- Eine Datei mit der Endung  `.dbf`  enthält Attribute oder Eigenschaften. 
- Eine Datei mit der Endung  `.shx`  dient als eine Art Index. Mithilfe dieser Datei sind die Geometriedaten in der Datei  `.shp`  mit den Eigenschaften in der  `.dbf`-Datei verknüpft. 

Weitere Informationen zu Shapefiles und wie Sie diese selbst erstellen können, finden Sie auf der Website <a href="http://desktop.arcgis.com/de/arcmap/10.3/">http://desktop.arcgis.com/de/arcmap/10.3/</a><a href="http://desktop.arcgis.com/de/arcmap/10.3/manage-data/shapefiles/creating-a-new-shapefile.htm">manage-data/shapefiles/creating-a-new-shapefile.htm</a>.

### Wie kommen Sie an ein Shapefiles

Natürlich können Sie selbst ein Shapefile erstellen. Das ist aber gar nicht einfach und außerdem nicht Thema dieses Buches. Einfach ist es aber, an Shapefiles von anderen zu kommen. Insbesondere Daten, die von öffentlichem Interesse sind, werden oft zum Download als Shapefile angeboten. Suchen einfach einmal in einer Suchmaschine nach Websites, die den Text *Open Data* enthalten.

Bei einer Suche <a class="sigil_index_marker" title="Open Data" id="sigil_index_id_3">nach</a>  *Open Data* in einer Suchmaschine im Internet habe ich unter anderem das Schienennetz der Deutschen Bahn als Shapefile gefunden:  <a href="http://data.deutschebahn.com/dataset/geo-strecke">http://data.deutschebahn.com/dataset/geo-strecke</a>. Höchstwahrscheinlich interessieren Sie sich für Daten in der Nähe Ihres Wohnortes. Dann geben Sie zum Suchbegriff *Open Dat**a* einfach den Namen einer Stadt in der Nähe Ihres Wohnortes ein. Eine Suche nach *Open Data* in der Nähe von *Koblenz* hat mich zu einer Website des Landesvermessungsamtes Koblenz geführt. Die Website <a href="https://lvermgeo.rlp.de/">https://lvermgeo.rlp.de/</a><a href="https://lvermgeo.rlp.de/fileadmin/"> fileadmin/</a><a href="https://lvermgeo.rlp.de/fileadmin/lvermgeo/pdf/open-data/Download_von_Verwaltungsgrenzen.pdf">lvermgeo/pdf/open-data/Download_von_Verwaltungsgrenzen.pdf</a> informiert über das Angebot des Landesvermessungsamtes - insbesondere über das Angebot an offenen Daten. Einige dieser Daten, zum Beispiel die Flurgrenzen, stehen als Shapefile zur Verfügung.

Wenn Sie per Internetsuche keine passenden Daten finden, können Sie auf der Website von Openstreetmap, insbesondere auf der Unterseite <a href="http://wiki.openstreetmap.org/wiki/Shapefiles">http://wiki.openstreetmap.org/wiki/Shapefiles</a> nach weiteren Anbietern suchen. Neben weiteren Informationen zum Shapefile Format gibt es hier auch eine Liste mit Anbietern von Shapefiles.

> Es muss nicht an Ihnen liegen, wenn Sie bei der Arbeit mit Geodaten auf
einen Fehler stoßen.
Insbesondere dann nicht, wenn Sie Daten von anderen in Ihre Arbeit
einbinden. Da das Shapefile Format kompliziert ist, ist es gut, dass
es im Internet Websites gibt, auf denen man eine Shapefile Datei
testen kann. Eine dieser Websites ist <a href="http://leaflet.calvinmetcalf.com/">calvinmetcalf.com</a>.
<img alt="" src="../Images/data-url-image83.png" id="Bild70"/>

### Wie binden Sie Shapefiles in Ihre Leaflet Karte ein?

#### Deutsche Verwaltungsgrenzen als Shapefile in der Leaflet Karte

Die *<a class="sigil_index_marker" title="Shape Datei" id="sigil_index_id_4">Shape Datei</a>*, die ich im nächsten Beispiel verwende, habe ich von der Website <a href="https://www.arcgis.com/home/item.html?id=ae25571c60d94ce5b7fcbf74e27c00e0">https://www.arcgis.com/home/item.html?id=ae25571c60d94ce5b7fcbf74e27c00e0</a> kopiert. Die Firma ESRI bietet auf dieser Website mit ArcGIS ein Geoinformationssystem, dass die Verwendung, Erstellung und Freigabe von Geodaten einfach macht. Ich habe mir den oben verlinkten Datensatz mit den Verwaltungsgrenzen von Deutschland kopiert. Die Datei landet unter dem Namen  `vg2500_geo84.zip`  bei mir auf dem Computer.

<img alt="" src="../Images/data-url-image84.png" id="Bild72"/>

Wie ich die Shape Datei mit Leaflet in eine Karte integriere, zeigt Ihnen das nachfolgende Beispiel. Natürlich gibt es dafür auch wieder ein Leaflet Plugin. Die Website zum Plugin `Leaflet.Shapefile` finden Sie auf Github unter der Adresse <a href="https://github.com/calvinmetcalf/leaflet.shapefile">https://github.com/calvinmetcalf/leaflet.shapefile</a>. Die Datei zum Plugin heißt `leaflet.shpfile.js`. Der gleiche Entwickler bietet auch ein Skript zum Analysieren der Shape Datei unter der Adresse <a href="https://github.com/calvinmetcalf/shapefile-js">https://github.com/calvinmetcalf/shapefile-js</a> an. Diese Datei heißt  `shp.js`. Diese beiden Dateien müssen Sie in Ihre HTML-Datei einbinden.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**
<script src="shp.js"></script>**
**<script src="leaflet.shpfile.js"></script>**

</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 6);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);
**
var shpfile = new L.Shapefile('vg2500_geo84.zip');
****shpfile.addTo(mymap);**

</script>
</body>
</html>
<!--index_943.html-->
`</pre>

Die vier fett formatierten Zeilen zeigen schon alles Notwendige. Und was haben wir genau gemacht? Im Kopfbereich unserer Beispiel HTML-Datei haben wir zwei Skripte eingebunden. Einmal das Skript  `leaflet.shpfile.js`  zum Leaflet Plugin und dann das Skript  `shp.js  `zum Analysieren der Shape Datei. Danach haben wir mit der Zeile  `var shpfile = new L.Shapefile('vg2500_geo84.zip')  `eine Ebene mit den Daten der Shape Datei erstellt. Zum Schluss haben wir diese Ebene zum Kartenobjekt hinzugefügt:  `shpfile.addTo(mymap)`.

Als Ergebnis sehen Sie nun alle Verwaltungsgrenzen, also die reinen Geometrien. Eigenschaften, die in der Shape Datei enthalten sind, werden in diesem Beispiel noch nicht angezeigt. Das Anzeigen von Eigenschaften und das Zuordnen anderer Stile habe ich für das nächste Beispiel aufgehoben.

<img alt="" src="../Images/data-url-image85.png" id="Bild75"/>

#### Deutsche Verwaltungsgrenzen mit Optionen

Im nächsten Beispiel sehen Sie, wie Sie das Aussehen der Formen in der Shape Datei beeinflussen könne.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="shp.js">
</script>****<script src="leaflet.shpfile.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 6);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);

**var shpfile = new L.Shapefile(
'vg2500_geo84.zip',
****{style:function(feature){return {
color:"black",fillColor:"red",fillOpacity:.75}}}
****);
****shpfile.addTo(mymap);**

</script>
</body>
</html>
<!--index_942.html-->
`</pre>

Das vorhergehende Beispiel manipuliert die Option  `style`. Die Belegung der Option  `style`  mit  `color:"black",fillColor:"red",fillOpacity:.75  `färbt die Grenzen der Shape Datei schwarz und füllt die Formen mit der Farbe Rot – bei einer Transparenz von 75 Prozent.

Das rot gefärbte Deutschland können Sie sich in der nächsten Abbildung ansehen.

<img alt="" src="../Images/data-url-image86.png" id="Bild75a"/>

#### Ein Pop-up-Fenster

Schön wäre es, wenn man für jede Verwaltungseinheit den Namen in einem Pop-up Fenster angezeigt bekommen würde – und zwar genau dann, wenn man die Fläche auf der Karte anklickt. Im nächsten Beispiel sehen Sie, wie Sie dies umsetzen können.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="shp.js"></script>
****<script src="leaflet.shpfile.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 5);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

**var shpfile = new L.Shapefile(
****'vg2500_geo84.zip',
****{****onEachFeature:function(feature, layer)
****{****layer.bindPopup(feature.properties.GEN);****}****}
);
****shpfile.addTo(mymap);**

</script>
</body>
</html>
<-- index_941.html -->
`</pre>

In diesem Beispiel haben wir die Option  `onEachFeature`  verwendet. Wir haben dieser Option eine anonyme Funktion zugeordnet in der wir jedem Feature in der Shape Datei mithilfe von  `layer.bindPopup(feature.properties.GEN)`  ein Pop-up Fenster zugewiesen haben. Im Pop-up Fenster erscheint der Text, der bei dem Feature im Attribut  `GEN`  als Eigenschaft eingetragen ist. Wenn Sie sich nun fragen, woher Sie wissen können, dass es als Eigenschaft ein Attribut  `GEN`  gibt, dann warten Sie bis zum nächsten Beispiel. Dort werde ich Ihnen zeigen, wie Sie alle Optionen auslesen können.

Probieren Sie aber zunächst dieses Beispiel selbst aus. Öffnen Sie die Karte und klicken Sie einen Landkreis an. Wie in der nachfolgenden Abbildung zu sehen ist, sollte sich auch auf Ihrer Karte ein Pop-up Fenster öffnen.

Auf diese Art und Weise können Sie auch
das Aussehen einer Form, abhängig vom Wert eines Attributes
gestalten.

<img alt="" src="../Images/data-url-image87.png" id="Bild78"/>

#### Ein Pop-up-Fenster mit allen Informationen des Features

Sie wissen nicht, welche Eigenschaften in der Shape Datei genau für die Geometrien enthalten sind – Sie möchten sich aber gerne einen Überblick über diese Eigenschaften verschaffen. Das nächste Beispiel zeigt Ihnen, wie Sie die Informationen nur mit JavaScript in Erfahrung bringen können.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="shp.js"></script>
<script src="leaflet.shpfile.js"></script>
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.27264, 7.26469], 5);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);
**
var shpfile = new L.Shapefile(**
**'vg2500_geo84.zip',**
**{**
**onEachFeature:function(feature, layer)**
**{****var holder=[];****for (var key in feature.properties){**
**holder.push(key+": "+feature.properties[key]+"<br>");**
**popupContent=holder.join("");**
**}**
**
layer.bindPopup(popupContent);**
**}});**

shpfile.addTo(mymap);
</script>
</body>
</html>
<!--index_940.html-->
`</pre>

Für die Beantwortung dieser Fragestellung nutzen wir auch wieder die Option  `onEachFeature`. In dieser Option erstellen wir eine Variable, genau ein Array, mit dem Namen  `holder`  ** **Als nächstes durchlaufen wir in einer Schleife alle Schlüssel, die in den Eigenschaften der Shape Datei, also in  `feature.properties  `enthalten sind. Wir fügen mit <a href="https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array/push">`push()`</a> jeden Eintrag in den Array  `holder  `ein und separieren diesen von dem nächsten Eintrag mit <a href="https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array/join">`join()`</a>. Den Text mit allen Schlüssel-Wert-Paaren fügen wir am Schluss als Pop-up Text zum Layer hinzu.

Als Ergebnis sehen Sie alle möglichen Schlüssel-Wert-Paare in einem Pop-up Fenster über Ihrer Karte, sobald Sie eine Fläche anklicken.

<img alt="" src="../Images/data-url-image88.png" id="Bild79"/>

<h2 id="inEsriServives">ESRI Services</h2>

Sie wissen nun wie Sie eine ESRI Basiskarte laden, wie Sie mit dem Plugin ESRI-Leaflet grundsätzlich umgehen und wie Sie Dateien im Format Shapefile nutzen können.

ESRI bietet aber noch eine ganze Menge mehr. Sie können ArcGIS Server-Web-Services nutzen. Das ESRI Plugin unterstützt Sie auch bei der Verbindung mit einem Web Service, der sich auf einer ArcGIS Server-Website befindet und für Client-Anwendungen zur Verfügung gestellt wird. Mit einem ArcGIS Web Service kann entweder eine weitere <a href="http://esri.github.io/esri-leaflet/api-reference/#layers">Ebene</a> für eine Karte zur Verfügung gestellt oder eine bestimmte <a href="http://esri.github.io/esri-leaflet/api-reference/#tasks">Aufgabe</a> bearbeitet werden.

Eine Ebene kann dabei neben dem  `L.esri.BasemapLayer`, den Sie ja schon kennengelernt haben, ein  `L.esri.DynamicMapLayer,`  ein  `L.esri.ImageMapLayer`, ein  `L.esri.RasterLayer`, ein` L.esri.TiledMapLayer`, ein  `L.esri.FeatureLayer`, ein  `L.esri.Cluster.FeatureLayer`  oder ein  `L.esri.Heat.FeatureLayer  `sein. Eine Aufgabe könnte das Einschränken der Anzeige auf bestimmte Objekte mit  `L.esri.Query  `sein oder das Zuordnen von Adressen zu Koordinaten mit  `L.esri.Geocoding`.

Im nächsten Kapitel beginnen wir damit, das wir eine Ebene, nämlich einen  `L.esri.DynamicMapLayer`, mithilfe eines Web Services nutzen. Wenn Sie dieses Beispiel durchgearbeitet haben, können Sie alle anderen Layer ebenfalls verwenden. Die Vorgehensweise ist bei jedem einheitlich. Der einzige Unterschied besteht im Angebot der möglichen Methoden und Optionen. Da aber die Dokumentation zum Plugin sehr gut ist, dürfte dies keine Schwierigkeit darstellen. Die Dokumentation zu den Layern finden Sie unter der Adresse <a href="http://esri.github.io/esri-leaflet/api-reference/#layers">http://esri.github.io/esri-leaflet/api-reference/#layers</a>.

### L.esri.DynamicMapLayer

  Für  <a class="sigil_index_marker" title="L.esri.DynamicMapLayer" id="sigil_index_id_5">das</a>  nachfolgende Beispiel habe ich Daten des <a href="http://www.stadt-koeln.de/politik-und-verwaltung/geoportal/">Geoportals Köln</a> genutzt. Dieses Portal bietet den Zugriff auf offene Daten, Dienste und Anwendungen verschiedener Herkunft. Das Geoportal Köln zentralisieren nach eigenen Angaben Informationen aus den Bereichen Umwelt, Verkehr, Vermessung und Planung. Jeder hat die Möglichkeit die Geodaten des Geoportal Köln zu nutzen, anzusehen und zu analysieren. Informationen zum Geoportal Köln finden Sie auf der Website der Stadt Köln, genau unter der Adresse <a href="http://www.stadt-koeln.de/politik-und-verwaltung/geoportal/">http://www.stadt-koeln.de/politik-und-verwaltung/geoportal/</a>. Die Dokumentation zur Schnittstelle des Web Services finden Sie unter der Adresse <a href="https://geoportal.stadt-koeln.de/arcgis/">https://geoportal.stadt-koeln.de/arcgis/</a>. Wenn Sie dann auf den Eintrag *Behindertenparkplätze* klicken sehen Sie die Angaben, die speziell unser nachfolgendes Beispiel betreffen.


<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**
<script src="esri-leaflet.js"></script>**

</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.97264, 7.00469], 12);

//L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);
L.esri.basemapLayer('Gray').addTo(mymap);
**
var url = "https://geoportal.stadt-koeln.de/arcgis
/rest/services/Behindertenparkplaetze/MapServer";**

**var dMap = L.esri.dynamicMapLayer({**
**url: url,**
**opacity : 0.25,**
**useCors: false**
**}).addTo(mymap);**

**dMap.bindPopup(**
**function(err, featureCollection, response){**
**return featureCollection.features[0]
.properties.Bezeichnung +**
**'<br>Anzahl: ' +**
**featureCollection.features[0].properties.Anzahl;**
**});**

</script>
</body>
</html>
<!--index_939.html-->
`</pre>

Als Erstes haben wir im vorherigen Beispiel das Skript zum Esri Leaflet Plugin eingebunden. Als Nächstes haben wir die URL, unter welcher der betreffende Service angeboten wird, in die Variabel` url`  gespeichert. Danach haben wir mit dem Code

`var dMap = L.esri.dynamicMapLayer({`  
`url: url,`    
`opacity : 0.25,`  
`useCors: false`  
`}).addTo(mymap);`

ein `L.esri.dynamicMapLayer`-Objekt erstellt und diesem gleichzeitig Optionen übergeben. Unter anderem die URL. Zuletzt haben wir dann mit dem Code

`dMap.bindPopup(  
function(err, featureCollection, response){  
return featureCollection.features[0].properties.Bezeichnung +  
'<br>Anzahl: ' +  
featureCollection.features[0].properties.Anzahl;  
});`

jedem Feature ein Pop-up hinzugefügt und in dieses Pop-up die Eigenschaften  `Bezeichnung`  und  `Anzahl`  als Text eingetragen. Welche Eigenschaften Ihnen ein Web Service zur Verfügung stellt, finden Sie in der Dokumentation zum jeweiligen Service. Die Adresse zur Dokumentation des hier verwendeten Services hatte ich Ihnen weiter oben schon genannt.

Die nachfolgende Abbildung zeigt Ihnen alle – im Web Service Behindertenparkplätze des Geoportals Köln eingetragenen – Parkplätze.

<img alt="" src="../Images/data-url-image89.png" id="Bild80"/>

### Geocoding

Was ist <a href="https://de.wikipedia.org/wiki/Georeferenzierung">Geocoding</a>?  <a class="sigil_index_marker" title="Geocoding" id="sigil_index_id_6">Geocoding</a>  bezeichnet die Umwandlung von Adressen wie *Kirchstraße 13, 56571 Muster* in geografische Koordinaten wie *50**.423021 Breite und **7**.083739 Länge.* Nur so können Sie nämlich einen Marker auf einer Karte platzieren oder die Karte an einer bestimmten Adresse zentriert öffnen.

> Nicht nur ESRI bietet Geocoding Dienste an. Auch OpenStreetMap bietet Ihnen diesen Service. <a href="https://nominatim.openstreetmap.org/">Nominatim</a> ist eine Anwendung, mithilfe derer OpenStreetMap Daten anhand von
Texten durchsucht werden können. Diese Texte sind in der Regel eine
Adresse oder ein Teil einer Adresse. Falls der Suchtext mit einer Eigenschaften eines OpenStreetMap-Objektes, übereinstimmt, wird die Koordinate zu
diesem Objekt auf eine Suchanfrage hin zurückgegeben. Sie finden die Anwendung Nominatim unter der Adresse
    <a href="https://nominatim.openstreetmap.org/">https://nominatim.openstreetmap.org/</a>
im Internet.
    Da Nominatim auf OpenStreetMap Daten beruht,
können Sie sich nicht darauf verlassen, dass alle Adressen
eingetragen sind. OSM ist keine kommerzielle Firma, sondern ein
Projekt das auf der Mitarbeit von Freiwilligen beruht. Dafür können
Sie aber selbst Einfluss auf den Datenbestand nehmen. Bei
OpenStreetMap kann jeder <a href="http://wiki.openstreetmap.org/wiki/DE:Getting_Involved">mitmachen</a>
und korrekte Daten zu dem aktuellen Datenband hinzufügen.  
  
Ein Pluign, dass Nominatim als Service nutze, ist das Plugin <a href="https://github.com/perliedman/leaflet-control-geocoder">Leaflet Control Geocoder.</a>


Ich zeige Ihnen in diesem Kapitel anhand des <a href="https://github.com/Esri/esri-leaflet-geocoder">ESRI Leaflet Geocoder Plugins</a> folgendes:

- Ich zeige Ihnen, wie Sie eine Adresse in eine Koordinate umwandeln können. 
- Ich zeige Ihnen, wie Sie eine Koordinate in eine Adresse umwandeln können. 
- Ich zeige Ihnen, wie Sie eine Karte so öffnen können, dass eine bestimmte Adresse zentriert angezeigt wird. 

#### Nach Eingabe einer Adresse den passenden Ort auf der Karte finden

Sie zeigen eine Karte auf Ihrer Website an und möchten es anderen ermöglichen, zu einer bestimmten Adresse auf der Karte zu navigieren, nachdem Sie diese Adresse in einem Textfeld eingetragen haben. Dann integrieren Sie doch einfach ein ESRI Leaflet Geocoder Control in Ihre Karte. Wie Sie dies tun können zeigt Ihnen das nächste Beispiel.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="esri-leaflet.js"></script>
****<link rel="stylesheet" href="esri-leaflet-geocoder.css">
****<script src="esri-leaflet-geocoder.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.97264, 7.00469], 12);
L.esri.basemapLayer('Gray').addTo(mymap);

**var searchControl = L.esri.Geocoding.geosearch()
.addTo(mymap);**
**var results = L.layerGroup().addTo(mymap);**
**searchControl.on("results", function(data) {****results.clearLayers();**
**for (var i = data.results.length - 1; i >= 0; i--){
****results.addLayer(L.marker(data.results[i].latlng));**
**}**
**});
**
</script>
</body>
</html>
<!--index_938.html-->
`</pre>

  Zur Darstellung des Textfeldes für die Eingabe der Adresse ist es notwendig zwei weitere Skripte einzubinden. Neben dem Skript  `esri-leaflet.js`  sollten Sie auch noch die Dateien  `esri-leaflet-geocoder.css`  und  `esri-leaflet-geocoder.js`  in Ihr HTML-Dokument einbinden. Die notwendigen Dateien hierfür finden Sie unter der Adresse <a href="https://github.com/Esri/esri-leaflet-geocoder/">https://github.com/Esri/esri-leaflet-geocoder/</a>. Als Nächstes wird dann mit  `var searchControl = L.esri.Geocoding.geosearch().addTo(mymap);`  das Eingabefeld für die zu suchende Adresse erstellt und zur Karte hinzugefügt. Dieses Eingabefeld nennt Leaflet auch Control. Wir brauchen eine Ebene, die die Suchergebnisse richtig verarbeitet. Diese erstellen wir mit der Zeile  `var results = L.layerGroup().addTo(mymap);`. Zum Schluss können wir dann das Ereignis  `on("results")`  des Objektes  `searchControl`  mit einer Funktion belegen.

  `searchControl.on("results", **function(data) {**  


  **results.clearLayers();**  

  **for (var i = data.results.length - 1; i >= 0; i--) {**  


  **results.addLayer(L.marker(data.results[i].latlng));**  


  **}**  


  });`

  Wenn es neue Suchergebnisse gibt, dann werden alle alten Suchergebnisse von der Ebene entfernt und die neuen Suchergebnisse als Marker auf der Ebene platziert.

> Ihre Adresse wird
nicht auf der Karte gefunden? Das ESRI Leaflet Geocoder Control
findet mithilfe der Methode <a href="http://esri.github.io/esri-leaflet/api-reference/controls/geosearch.html">`geosearch()`</a>
standardmäßig nur Adressen, die aktuell auch sichtbar auf der Karte
sind. Erst wenn Ihre sicher vorhandene Adresse auch bei einer Zoom-Stufe von 0 nicht
gefunden wird, stimmt etwas nicht. Falls Sie lieber sofort die ganz
Welt durchsuchen möchten, dann sollten Sie die Option  `useMapBounds`  des Objektes, das Ihnen die Funktion** ****`L.esri.Geocoding.geosearch()`**** **liefert, mit  `false`  belegen.

Die erste Ansicht der Karte nach dem Hinzufügen des ESRI Leaflet Geocoder Control Plugins ist nicht spektakulär. Sie sehen in der linken oberen Ecke eine kleine Lupe. Wenn Sie diese anklicken, öffnet sich ein Textfeld. In dieses Textfeld können Sie nun die Adresse eingeben, nach der Sie suchen möchten. Standardmäßig werden Ihnen alternative Eingaben vorgeschlagen. Sie können das Verhalten des Plugins mit vielen Optionen beeinflussen. Sehen sich die Dokumentation unter Adresse <a href="http://esri.github.io/esri-leaflet/api-reference/controls/geosearch.html">http://esri.github.io/esri-leaflet/api-reference/controls/geosearch.html</a> an. Vielleicht ist da sogar eine Option dabei, auf die Sie selbst nicht gekommen wären.

<img alt="" src="../Images/data-url-image90.png" id="Bild83"/>

#### Mithilfe eines Parameters in der URL den passenden Ort finden

Manchmal kommt es vor, dass Sie eine Karte schon an einer bestimmten Adresse zentriert öffnen möchten. Wie Sie so etwas umsetzten können, zeigt Ihnen das nächste Beispiel.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="esri-leaflet.js"></script>
**<script src="esri-leaflet-geocoder.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
**
var x = location.search;****var y = x.split("=");****var temp=y[1];**
**var address = decodeURIComponent(temp);**

var mymap = L.map('mapid', {doubleClickZoom:false})
.setView([50.97264, 7.00469], 3);

L.esri.basemapLayer('Gray').addTo(mymap);

**L.esri.Geocoding.geocode().text(address)
.run(function(err, result, response){**
**L.marker(result.results[0].latlng).addTo(mymap);
****mymap.setView(result.results[0].latlng, 13);**
**});**

</script>
</body>
</html>
<!--index_937.html-->

`</pre>

Was haben wir genau gemacht? Angenommen, wir haben in der Adresszeile des Browsers den Text  `?test=56751 Gering`  an die URL angefügt. Dieser Text würde im Beispiel als Erstes in der Variablen  `x`  gespeichert. Hierzu wird die Eigenschaft <a href="https://wiki.selfhtml.org/wiki/JavaScript/Location/search">`location.search`</a> zu Hilfe genommen. Diese Eigenschaft speichert eine Zeichenkette die, durch ein Fragezeichen getrennt, zur aktuellen URL gehört. Die Variable  `x`  enthält also nun den Text  `test=56751 Gering`. Diesen Text haben wir dann mithilfe von  `x.split("=")`  an der Position des Gleichheitszeichens getrennt und die beiden Teile als Array in der Variablen  `y`  gespeichert. Den Adressteil können wir nun über  `y[1]` abrufen. Wir müssen die Adresse vor der Eingabe in eine Suchfunktion aber noch dekodieren. In der URL wurde diese nämlich kodiert. `var address = <a href="https://wiki.selfhtml.org/wiki/JavaScript/decodeURIComponent">decodeURIComponent</a>(temp)` macht aus `56751**%**20Gering` wieder `56751 Gering` und speichert den dekodierten Text in der Variablen `address` ab. Und diesen Text können wir nun als Suchtext in die Methode `text()` des Geocode Objektes eingeben und auf dem Ergebnis die Methode `run()` ausführen.

`L.esri.Geocoding.geocode().text(**address**)  
.run(function(err, result, response){  
L.marker(result.results[0].latlng)  
.addTo(mymap);  
< br />

mymap.setView(result.results[0].latlng,13);  
});`

  Die Rückruffunktion, die daraufhin ausgeführt wird, erstellt einen Marker für das erste Ergebnis und zentriert diesen Marker, bei einer Zoom-Stufe von 13, in der Karte. Eine <a href="https://de.wikipedia.org/wiki/R%C3%BCckruffunktion">Rückruffunktion</a> ist eine Funktion, die einer anderen Funktion als Parameter übergeben und von dieser erst später, unter definierten Bedingungen mit definierten Argumenten, aufgerufen wird. Eine solche Funktion kennen Sie sicher auch unter dem englischen Namen  <a class="sigil_index_marker" title="callback function" id="sigil_index_id_7">callback function</a>.

> Möchten Sie die Suchanfrage genauer formulieren? Dann ersetzen Sie den Text  
`L.esri.Geocoding.geocode()  
.**text**('Amselweg 7, Koblenz, Rheinland Pfalz, 65065')  
.run(function(err, results, response){  
 ...  
 });`  
  
mit  
  
`L.esri.Geocoding.geocode()  
.**address**('Amselweg 7')  
.**city**('Koblenz').**region**('Rheinland Pfalz')  
.**postal**(65065)  
.run(function(err, results, response){  
...  
});`  
Welche Funktionen Sie genau verwenden können, ist in der Dokumentation beschrieben: <a href="https://esri.github.io/esri-leaflet/api-reference/tasks/geocode.html">https://esri.github.io/esri-leaflet/api-reference/tasks/geocode.html</a>.

Voilà! Wenn sie an die URL, unter der Sie Ihre Leaflet Karte abegelegt haben, den Text  `?test=56751 Gering  `anhängen, wird Ihnen die in der nachfolgenden Abbildung dargestellte Karte angezeigt.

<img alt="" src="../Images/data-url-image91.png" id="Bild82"/>

#### Nach Klick auf die Karte die passende Adresse ausgeben

Umgekehrtes Geocoding ist die Bezeichnung für die Umwandlung geografischer Koordinaten in, für Menschen gut lesbare, Adressen.
Sie wissen ja schon, dass Leaflet bei einem Klick mit der Maus auf die Karte die Koordinaten in einem Objekt speichert. Nun möchten Sie aber gerne anstelle der Koordinaten wissen, welche Adresse Sie gerade angeklickt haben. Das nächste Beispiel zeigt ihnen, wie Sie dies erreichen können.

<pre>`<!DOCTYPE HTML>
<html lang="de">
<head>
<meta charset="utf-8"/>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="esri-leaflet.js"></script>
**<script src="esri-leaflet-geocoder.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid',
{doubleClickZoom:false}).setView([50.97264, 7.00469], 12);

L.esri.basemapLayer('Gray').addTo(mymap);**

mymap.on('click', function(e){

var r = L.marker();

L.esri.Geocoding.reverseGeocode()
.latlng(e.latlng)
.run(function(error, result, response){
r = L.marker(result.latlng).addTo(mymap)
.bindPopup(result.address.Match_addr)
.openPopup();
});

});
**
</script>
</body>
</html>
<!--index_936.html-->
`</pre>

Das haben wir gemacht? Wir haben veranlasst, dass immer dann, wenn jemand auf die Karte klickt, eine umgekehrte Geocoding Suche gestartet wird. Genau habe wir dies mit dem Programmcode, der in der Funktion  `mymap.on('click', function(e){}`  ausgeführt wird, erreicht. Gleichzeitig wird ein Marker an der Position, die angeklickt wurde, erstellt. Das Ergebnis der Suche – also die gefundene Adresse – wird schlussendlich als Text in einem Pop-up zum Marker angezeigt.

Wie diese Karte aussieht, können Sie sich in der nächsten Abbildung ansehen.

<img alt="" src="../Images/data-url-image92.png" id="Bild81"/>

Die Dokumentation zum ESRI Reverse Geocoding finden Sie unter der Internetadresse <a href="http://esri.github.io/esri-leaflet/api-reference/tasks/reverse-geocode.html">http://esri.github.io/esri-leaflet/api-reference/tasks/reverse-geocode.html</a>

### Feature Services

Im vorletzten Kapitel haben wir mit dem  `L.esri.dynamicMapLayer`  Daten über einen Webservice geladen. Dabei wurden alle zur Verfügung stehenden Daten auf der Karte angezeigt. Das kann sehr unübersichtlich werden. Meist bietet ein Webservice große Datenmengen an. Sie möchten sicherlich nur die für Sie und Ihre Anwender relevanten Daten auf Ihrer Karte anzeigen. Eine Lösung für diese Aufgabe erarbeiten wir in diesem Kapitel.

In diesem Beispiel werden wir die Klasse <a href="https://esri.github.io/esri-leaflet/api-reference/layers/feature-layer.html">`L.esri.featureLayer`</a> instanziieren. Vorher haben wir mit der Klasse <a href="https://esri.github.io/esri-leaflet/api-reference/layers/dynamic-map-layer.html">`L.esri.dynamicMapLayer`</a> gearbeitet. Vielleicht fragen Sie sich nun, wie die beiden Klassen sich genau unterscheiden. ESRI erklärt dies wie folgt: Mit einem <a href="http://resources.arcgis.com/de/help/main/10.2/index.html#//0154000002w8000000">Feature-Service</a> können Sie Funktionen über das Internet bereitstellen. Mit dem <a href="http://resources.arcgis.com/de/help/main/10.2/index.html#//0154000002m7000000">Karten-Service</a> können Sie Karten im Web bereitstellen. Meiner Meinung nach ist ein *Feature Service *ein spezieller *Karten-Service* – denn ein Feature Service setzt eine Karte voraus.

> Interessieren Sie sich für die
technologische Entwicklung beim ESRI? Die wichtigsten Informationen
zur ArcGIS Plattform und zu ergänzenden Technologien können Sie auf
dem Blog GIS IQ – <a href="https://gis-iq.esri.de/">https://gis-iq.esri.de/</a>
– mitverfolgen.
 
#### Attribute

So, nun kommen wir zum praktischen Beispiel. Wir konfigurieren eine Abfrage zum Filtern von Daten. Konkret verwenden wir Sicherheitseinrichtungen, deren Daten über die Adresse <a href="http://www.arcgis.com/home/item.html?id=59711f4ee839438299c90164115f129b">http://www.arcgis.com/home/item.html?id=59711f4ee839438299c90164115f129b</a> bereit gestellt werden.


`<!DOCTYPE HTML>`  
<html lang="de">`  
<head>`  
<meta charset="utf-8"/>`  
<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
<link rel="stylesheet" href="../leaflet/leaflet.css" />`  
<script src="../leaflet/leaflet.js"></script>`  
<script src="esri-leaflet.js"></script>`  
</head>`  
<body>`  
<select id="sicherheitseinrichtungenID">`  
<option value="">Reset</option>`  
<option value="Untertyp='pt_Notrufsaeule'">`  
Notrufsaeule</option>`  
<option value="Untertyp='pt_Feuerwache'">`  
Feuerwache</option>`  
<option value="Untertyp='pt_Rettungspunkt'">`  
Rettungspunkt</option>`  
<option value="Untertyp='pt_Polizeistation'">`  
Polizeistation</option>`  
<option value="Untertyp='pt_Sirene'">`  
Sirene</option>`  
<option value="Untertyp='pt_Rettungswache'">`  
Rettungswache</option>`  
</select>`  
<div style="height: 700px" id="mapid"></div>`  
<script>`  
  
var mymap = L.map('mapid', {doubleClickZoom:false})`  
.setView([50.27264, 7.26469], 12);`  
  
L.esri.basemapLayer('Gray').addTo(mymap);`  
**var url = 'http://services.arcgis.com/OLiydejKCZTGhvWg`  
/arcgis/rest/services/OSM_DE_Sicherheitseinrichtungen`  
/FeatureServer/0';`**  
  
`var sicherheitseinrichtungen = document`  
`.getElementById('sicherheitseinrichtungenID');`  
  
`var sicherheitseinrichtungenLayer =`  
`L.esri.featureLayer({
`url: `**`url`**  
`}).addTo(mymap);`  
`var popupTemplate = "<h3>Details:</h3>\n\`  
`Land: {Land}<br>\n\`  
`Kreis: {Kreis}<br>\n\`  
`Gemeinde: {Gemeinde}<br>\n\`  
`Stadt: {Stadt} <br>\n\`  
`Typ: {Typ}, {Untertyp}";`  
`sicherheitseinrichtungenLayer`  
`.bindPopup(function (layer){`  
`return L.Util`  
`.template(popupTemplate, layer.feature.properties)`  
`});`  
`sicherheitseinrichtungen`  
`.addEventListener('change', function(){`  
` sicherheitseinrichtungenLayer`  
**`.setWhere`**`(sicherheitseinrichtungen.value);`  
`});`  
`</script>`  
`</body>`  
`</html>`  
`<!--index_935.html-->`  

Was macht der Programmcode in diesem Beispiel konkret. Zunächst wird mit dem Befehl  `var sicherheitseinrichtungenLayer = L.esri.featureLayer({ url: url }).addTo(mymap);`  ein  `L.esri.featureLayer` Objekt erstellt und dieses zur Karte hinzugefügt. Der nächste Schritt ist das Filtern der Daten. Dies erreichen wir mit der Zeile `sicherheitseinrichtungenLayer.**setWhere**(sicherheitseinrichtungen.value);`.

Das Ergebnis sehen Sie in der nächsten Abbildung. Wenn Sie in der Auswahlliste den Eintrag *Feuerwachen* auswählen, werden nur die Feuerwachen auf der Karte als Marker angezeigt.

<img alt="" src="../Images/data-url-image93.png" id="Bild85"/>

> Möchten Sie selbst einen Feature-Service
nutzen? Das Thema Sicherheitseinrichtungen passt aber nicht zum Thema
Ihrer Website. Das Team von Esri Deutschland hat verschiedene
Datensätze aus OpenStreetMap als Feature-Services veröffentlicht. Vielleicht ist auf der Website   <a href="http://www.arcgis.com/home/group.html?id=0ef29288545f43e29d9a90581f8f5b20#overview">http://www.arcgis.com/home/group.html?id=0ef29288545f43e29d9a90581f8f5b20#overview</a>  ein Thema dabei, dass Sie gerne auf Ihrer Website
mit einer Leaflet-Karte visualisieren möchten.

#### Abstand visualisieren

Ein weiteres Merkmal, das auf Landkarten oft wichtig ist, ist die Entfernung zu einem Punkt. Oft möchte man gerne wissen, welche Objekte sich innerhalb eines bestimmten Abstands zu einer bestimmten Koordinate befinden. Diese Fragestellung beantwortet das nächste Beispiel.

<pre>`<!DOCTYPE HTML>`  
<html lang="de">`  
<head>`  
<meta charset="utf-8"/>`  
<title>Eine OpenStreetMap Karte mit Leaflet</title>`  
<link rel="stylesheet" href="../leaflet/leaflet.css" />`  
<script src="../leaflet/leaflet.js"></script>`  
<script src="esri-leaflet.js"></script>`  
</head>`  
<body>`  
<div style="height: 700px" id="mapid"></div>`  
<script>`  
  
var mymap = L.map('mapid', {doubleClickZoom:false})`  
.setView([50.27264, 7.26469], 12);`  
  
L.esri.basemapLayer('Gray').addTo(mymap);`  
var url = 'http://services.arcgis.com/OLiydejKCZTGhvWg`  
/arcgis/rest/services/OSM_DE_Sicherheitseinrichtungen`  
/FeatureServer/0 ';`  
var sicherheitseinrichtungen =`  
document.getElementById('sicherheitseinrichtungenID');`  
var sicherheitseinrichtungenLayer = L.esri.featureLayer({`  
url: url,`  
pointToLayer: function (geojson, latlng) {`  
**`return L.circleMarker(latlng);`**  
},`  
style:{`  
color: '#5B7CBA',`  
}`  
}).addTo(mymap);`  
var popupTemplate = "<h3>Details:</h3>\n\`  
Land: {Land}<br>\n\`  
Kreis: {Kreis}<br>\n\`  
Gemeinde: {Gemeinde}<br>\n\` 
Stadt: {Stadt} <br>\n\`  
Typ: {Typ}, {Untertyp}";`  
sicherheitseinrichtungenLayer.bindPopup(function (layer){`  
return L.Util.template(`  
popupTemplate, layer.feature.properties)`  
});`  
var nearbyIds = [];`  
  
**`mymap.on('click', function(e){`**  
  
**`sicherheitseinrichtungenLayer.query()`**  
**`.nearby(e.latlng, 5000).ids(function(error, ids){`**
  
`for (var j = 0; j < nearbyIds.length; j++) {`**  
**`  sicherheitseinrichtungenLayer.resetStyle(nearbyIds[j]);`**  
**` }`**  
**` nearbyIds = ids;`**  
**` for (var i = 0; i < ids.length; i++) {`**  
**`  sicherheitseinrichtungenLayer.setFeatureStyle(ids[i], {`**  
**`  color: '#BA454E',`**  
**`  });
 `}`  
  
`});`  
  
`});`  
`</script>`  
`</body>`  
`</html>`  
`<!--index_934.html-->`  

Das haben wir gemacht? Zunächst werden im Beispiel Sicherheitseinrichtungen mithilfe des Objektes  `L.esri.featureLayer`  zur Karte hinzugefügt. Soweit gibt es keine Unterschied zum vorherigen Beispiel. Zur Abwechslung habe ich hier einen kreisförmigen Marker verwendet. Danach rufen wir die Funktion  `nearby()`  des Objektes <a href="https://esri.github.io/esri-leaflet/api-reference/tasks/query.html">`L.esri.Query()`</a> für jeden Marker auf. Alle die Marker, die sich in einem Abstand von 5000 Metern befinden, werden im Anschluss rot gefärbt.

Das Ergebnis sehen Sie im nächsten Bild. Sobald Sie einen Punkt auf der Karte anklicken, werden alle Marker im Abstand von 5000 Metern um die angeklickte Stelle rot hervorgehoben.

<img alt="" src="../Images/data-url-image94.png" id="Bild84"/>

<h2 id="sigil_toc_id_91">In diesem Kapitel haben wir …</h2>

In diesem Teil haben wir uns als Erstes die Karten, die <a href="https://de.wikipedia.org/wiki/ESRI">ESRI</a> anbietet, angesehen. Danach haben wir mit einem Shapefile gearbeitet und ESRI Webservices genutzt. Sie wissen nun was ein  `L.esri.DynamicMapLayer,`  was Geocoding und was ein  `L.esri.FeatureLayer  `ist. Mit letztgenanntem können Sie unter anderem Daten, die Sie nicht benötigen, einfach aus der gegebenen Datenmenge herausfiltern.

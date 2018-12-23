# Routing

Last, but not least möchte ich Ihnen ein <a class="sigil_index_marker" title="Routing" id="sigil_index_id_1">Routing</a>  Plugin vorstellen, nämlich die <a href="https://github.com/perliedman/leaflet-routing-machine">Leaflet Routing Machine (https://github.com/perliedman/leaflet-routing-machine)</a> von <a href="http://www.liedman.net/leaflet-routing-machine/">Per Liedmann</a>.

Falls Sie lieber die Version des
Environmental Systems Research Institute ESRI einsetzen möchten,
finden Sie alle Informationen hierfür unter der Adresse
<a href="https://github.com/jgravois/lrm-esri">https://github.com/jgravois/lrm-esri (https://github.com/jgravois/lrm-esri)</a>.

<h2 id="sigil_toc_id_92">In diesem Kapitel werden wir …</h2>

Als Erstes sehen wir uns kurz an, was sich hinter dem Begriff Routing versteckt. Danach werden wir das Plugin Leaflet Routing Machine in unsere Leaflet Karte integrieren. Dieses Plugin stellt zwei Textfelder zur Eingabe von Adressen zur Verfügung und berechnet auf Anforderung eine Route zwischen diesen beiden Adressen. Im weiteren Verlauf nutzen wir Optionen, um die Routenberechnung flexibler und benutzerfreundlicher zu machen.

<h2 id="sigil_toc_id_93">Allgemeines zum Thema Routing…</h2>

Fangen wir von vorne an. Es ist nämlich meiner Meinung nach auch spannend, einmal etwas über den Tellerrand zu blicken. Reicht es Ihnen, wenn sie zwei Adressen eingeben könnten und einen Weg zwischen diesen beiden Adressen als Ergebnis ausgegeben bekommen? Oder, möchten Sie etwas genauer wissen, was sich hinter dem Begriff Routing verbirgt? Wenn ersteres auf Sie zutrifft, dann lesen Sie am besten im nächsten Kapitel weiter. Ansonsten ist meine kurze Zusammenfassung hier im Kapitel vielleicht interessant für Sie.

Das Berechnen einer Route kann von einer Software oder einem Dienst effizient durchgeführt werden. Dazu müssen die Daten der Karte, auf der die Berechnung ausgeführt werden soll, bestimmte Informationen enthalten. Die Daten von OpenStreetMap beinhalten Informationen, um Routen für verschiedene Profile berechnen zu können. Eine Route kann zum Beispiel für die Nutzung eines Autos oder eines Fahrrads unterschiedlich berechnet werden. Auch Optionen wie  `zu Fuß`  oder  `mit dem Pferd`  sind mit OpenStreetMap Daten möglich.

Damit die Software zur Routenberechnung fehlerfrei funktioniert, müssen diese Daten qualitativ gut sein. Das bedeutet, dass Linien – also zum Beispiel Straßen – die verbunden sein sollen, auch wirklich verbunden sind. Umgekehrt dürfen Straßen, die sich auf verschieden Ebenen mithilfe von Brücken kreuzen, nicht verbunden sein. Das bedeutet auch, dass Poller oder Absperrpfosten, an denen kein Auto vorbeikommt, auch als solche eingezeichnet sind. Ganz wichtig ist es, dass Abbiegeverbote an Kreuzungen auf der Karte klar gekennzeichnet sind. Wie OpenStreetMap das macht, können Sie unter anderem auf der Website <a href="http://wiki.openstreetmap.org/wiki/OSM_tags_for_routing">http://wiki.openstreetmap.org/wiki/OSM_tags_for_routing</a> nachlesen.

Um bei der Routen-Berechnung die schnellste Route bestimmen zu können, sind Geschwindigkeitsangaben notwendig. OpenStreetMap speichert für jede Straße den Standardhöchstwert für deutsche Straßen. Dieser Standardwerte kann jedoch für bestimmte Straßen anders sein. In diesem Fall ist es notwendig, dass beim Erstellung des Straßen-Objektes die zulässige Höchstgeschwindigkeit hinzufügt wird. Dies geschieht mit einer speziellen Eigenschaft oder mit einem speziellen Tag. Nebenbei haben auch andere Faktoren, wie Kurven, Steigungen oder Straßenbelag einen Einfluss auf die Geschwindigkeit – und dieser ist je nach Profil noch einmal unterschiedlich. Eine Steigung verringert die Geschwindigkeit eines Fahrrades stärker, als die eines Autos. Dafür wird der Fußgänger in Kurven nicht so viel an Geschwindigkeit verlieren wie ein Fahrrad.

Aber auch dann, wenn die Kartendaten sehr gut und fehlerfrei sind, ist es nicht trivial die ideale Software zur Routen-Berechnung zu erstellen. Hinzu kommen nämlich noch die Besonderheiten des Personenkreises, für den die Route erstellt werden soll. Welche Wege sollen für Radfahrer berücksichtigt werden? Es gibt Radfahrer, die nicht gerne durch die Stadt fahren sondern lieber im Wald unterwegs ist. Andere ziehen eine asphaltierte Straße mitten durch die Stadt einem matschigen Feldweg vor. Wie wählen wir die beste Strecke für einen Radfahrer, der überwiegend in der Nacht trainiert? Oft kommt es sicher auch vor, dass eine Radtour geplant wird, bei der so viele Sehenswürdigkeiten wie möglich unmittelbar am Weg liegen sollten. Sie sehen: Die Berechnung einer optimalen Route ist etwas sehr Individuelles!

Sehen wir uns also an, inwieweit das Plugin Leaflet Routing Machine diese Anforderungen erfüllt.

<h2 id="inleafletroutingmachine">Leaflet Routing Maching</h2>

Nachfolgende finden Sie das erste Beispiel für diesen Themenbereich.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script src="leaflet-routing-machine.js"></script>**
**<link rel="stylesheet" href="leaflet-routing-machine.css"/>**
</head> <body> <div style="height: 700px;" id="mapid">
</div>
<script> var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);
**
var control = L.Routing.control({** **waypoints: [**
**L.latLng(50.273543, 7.262993),** **L.latLng(50.281168, 7.276211)**
**],** **router: L.Routing.mapbox('pk.ihrkey')**
**}).addTo(mymap);**

</script>
</body>
</html>
<!--index_932.html-->
`</pre>

Was haben wir genau gemacht? Zunächst einmal haben wir die für die Verwendung der <a href="http://www.liedman.net/leaflet-routing-machine/">Leaflet Routing Machine</a>  erforderlichen Dateien eingebunden. Verantwortlich hierfür sind die Zeilen

`<script src="leaflet-routing-machine.js"></script>`

`<link rel="stylesheet" href="leaflet-routing-machine.css"/>.`

Die aktuellen Dateien zum Plugin finden Sie unter der Adresse <a href="https://github.com/perliedman/leaflet-routing-machine/releases">https://github.com/perliedman/leaflet-routing-machine/releases</a>. Als Nächstes haben wir mit dem Textblock

`var control = L.Routing.control({`  
`waypoints: [`  
`L.latLng(50.273543, 7.262993),`  
`L.latLng(50.281168, 7.276211)`  
`],  `
`router: L.Routing.mapbox('pk.ihrkey')`  
`}).addTo(mymap);`  

ein `L.Routing.control` erstellt und dieses zur Karte hinzugefügt. Die Koordinaten, zwischen denen eine Route berechnet werden soll, haben wir mit der Option  `waypoints`  an das Control übergeben. Außerdem haben wir einen Router, also eine Software, die die Route berechnen soll, mit dem Eintrag  `router: L.Routing.mapbox('pk.ihrkey')`  festgelegt. Für die Nutzung des Mapbox Routers benötigen Sie ein Zugriffstoken. Dieses können Sie unter der Adresse <a href="https://www.mapbox.com/api-documentation/#access-tokens">https://www.mapbox.com/api-documentation/#access-tokens</a> anfordern. In dieser Dokumentation finden Sie auch weitere Informationen zum Router und zu den Lizenzbedingungen.

> Wenn Sie die Option  `router`  nicht belegen, wird standardmäßig die Open Source Routing Machine –
    <a href="http://project-osrm.org/">http://project-osrm.org/</a> –
genutzt. Für diesen freien Router benötigen Sie kein Zugriffstoken.
Leider ist dieser aber nicht so zuverlässig wie Mapbox.
  
Die nächste Abbildung zeigt Ihnen unseren bisherigen Stand. Die Route wird berechnet und im rechten oberen Teil angezeigt. Leider werden Sie aber über eine Straße, auf der viele Autos fahren, geführt. Dabei möchten Sie gerne wandern. Außerdem sind die Texte in englischer Sprache. Das geht sicher besser!

<img alt="" src="../Images/data-url-image95.png" id="Bild66"/>

<h2 id="leafletroutingmachineoptions">Options</h2>

Das nächste Beispiel zeigt Ihnen, wie Sie die Sprache und das Routing Profil verändern können.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="leaflet-routing-machine.js"></script>
<link rel="stylesheet" href="leaflet-routing-machine.css" />
</head> <body> <div style="height: 700px;" id="mapid">
</div>
<script>
var mymap = L.map('mapid')
.setView([50.27264, 7.26469], 13);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var control = L.Routing.control({
waypoints: [ L.latLng(50.273543, 7.262993),
L.latLng(50.281168, 7.276211) ],
router: L.Routing.mapbox('pk.ihrkey'),
{ **profile: 'mapbox/walking',** **language: 'de'** }), }
).addTo(mymap);

</script>
</body> </html>
<!--index_931.html-->
`</pre>

  Der Mapbox Router bietet Ihnen unter anderem die Optionen  `profil`  und  `language`. Die Namen sagen es schon aus. Als <a href="https://www.mapbox.com/api-documentation/#retrieve-directions">Profil</a> können Sie einstellen, ob Sie wandern oder lieber mit dem Auto fahren möchten. Die Option <a href="https://www.mapbox.com/api-documentation/#instructions-languages">language</a> bietet Ihnen eine Menge unterschiedlicher Sprachen. Möchten Sie noch etwas anderes ändern? Die Dokumentation zum Router von Mapbox finden Sie unter der Adresse <a href="https://www.mapbox.com/api-documentation/#introduction">https://www.mapbox.com/api-documentation/#introduction</a>.

> Wenn Sie lieber eine andere Software zur
Berechnung der Route nutzen möchten, können Sie dies tun. Die
Leaflet Routing Machine bietet Ihnen viele Möglichkeiten. Weitere
Informationen, Demos und Tutorials zur Leaflet Routing Machine finden
Sie auf der Website: <a href="http://www.liedman.net/leaflet-routing-machine/">http://www.liedman.net/leaflet-routing-machine/</a>.

Im nächsten Bild sehen Sie, dass das Routing nun eher zu einem Wanderer passt und die Texte sind auch in deutscher Sprache. Das ist schon einmal gut. Aber es geht ja meist noch besser. Wahrscheinlich möchten Sie, dass die Adressen, zwischen denen geroutet wird, variabel auf der Karte verändert werden können. Genau das wollte ich als Nächstes und deshalb habe ich dies im nächsten Beispiel umgesetzt.

<img alt="" src="../Images/data-url-image96.png" id="Bild71"/>

<h2 id="inleafletroutingmachninegeocoding">Geocoding und Routing</h2>

Bisher wurde die Route ausschließlich anhand von Koordinaten berechnet. Menschen nutzen aber lieber Texte in Form von Adressen. Das Geocoding Adressen in Koordinaten verwandelt – beziehungsweise Koordinaten in Adressen verwandelt – haben Sie im Kapitel *<a href="../Text/esri.html#ingeocoding">Geocoding</a>* im Kapitel *<a href="../Text/esri.html#inESRI">ESRI</a>* schon lesen können. Hier im Beispiel kombinieren wir nun Routing und Geocoding. Sehen Sie selbst:


<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
<script src="leaflet-routing-machine.js"></script>

**<script src="Control.Geocoder.js"></script>**
**<link rel="stylesheet" href="Control.Geocoder.css" />

**<link rel="stylesheet" href="leaflet-routing-machine.css" />
</head>
<body>
<div style="height: 700px;" id="mapid">
</div>
<script>
var mymap = L.map('mapid')
.setView([50.27264, 7.26469], 13);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')
.addTo(mymap);

var control = L.Routing.control({
waypoints: [ L.latLng(50.273543, 7.262993),
L.latLng(50.281168, 7.276211) ],
router: L.Routing.mapbox('pk.ihrkey'),
{ language: 'de' }),
**geocoder: L.Control.Geocoder.nominatim({})**
}).addTo(mymap);

</script>
</body>
</html>
<!--index_930.html-->
`</pre>

  In diesem Beispiel haben wir das vorhergehende Beispiel mit dem Plugin <a href="https://github.com/perliedman/leaflet-control-geocoder">Geocoder Control</a> erweitert. Konkret haben wir mithilfe der Zeilen

  `<script src="Control.Geocoder.js"></script>`

  `<link rel="stylesheet" href="Control.Geocoder.css"/> `

  die Skript-Datei und die CSS-Datei des <a href="https://github.com/perliedman/leaflet-control-geocoder">Geocoder Control</a> von Per Liedmann eingebunden. Die aktuellste Version dieses Plugins können Sie unter der Adresse <a href="https://github.com/perliedman/leaflet-control-geocoder/releases">https://github.com/perliedman/leaflet-control-geocoder/releases</a> herunter laden. Danach haben wir die Option  `geocoder`  des Plugins Leaflet Routing Machine mit dem Wert  `L.Control.Geocoder.nominatim({})`  belegt. Und das war es schon!

  Als Ergebnis sehen Sie nun zwei Textfelder im oberen rechten Bereich auf Ihrer Karte. In diese können Sie Adressen eingeben und so Ihre Route benutzerfreundlich abändern.

<img alt="" src="../Images/data-url-image97.png" id="Bild73"/>

<h2 id="sigil_toc_id_94">In diesem Kapitel haben wir …</h2>

Gegenstand dieses Kapitels war Routing. Wir haben uns kurz angesehen, was Kartendaten bieten müssen, um die Berechnung einer Route zu ermöglichen. Dass die Kartendaten aber nicht alles sind und eine Route etwas sehr Individuelles sein kann, wurde dabei auch klar. Danach haben wir das Plugin Leaflet Routing Machine in unsere Leaflet Karte integriert und mithilfe von Optionen und Geocoding flexibler und benutzerfreundlicher gemacht.


# Eine Karte mit Leaflet erstellen

Zunächst zeige ich Ihnen, wie Sie in vier einfachen Schritten eine 
*digitale Karte* mit Leaflet in ein HTML Dokument einbinden. 
Mit Leaflet müssen Sie dafür nicht wissen, was geografische Koordinaten sind 
und wie die Bilddateien für die Karten erstellt werden.  

Da dies aber als Hintergrundwissen bei einer eventuellen Fehlersuche hilfreich sein kann, 
habe ich einen Theorie-Teil in dieses Kapitel eingefügt. 
Hier erkläre ich Ihnen Wichtiges zum Thema geografische Koordinaten und die übliche 
Vorgehensweise beim Erstellen und Zuordnen der Imagedateien für diese Karten – 
die *Kachel-Technik*. Zum Abschluss lernen Sie dann noch eine Alternative zur 
Kachel-Technik kennen, den *Web-Map-Service*.

  
  
  
  




  <h2 id="sigil_toc_id_18">Exkurs: Wie werden Landkarten auf einer Website angezeigt?</h2>

  Eine Karte ist im Grunde genommen nichts anderes als die Darstellung einer <a href="https://de.wikipedia.org/wiki/Abbild">Abbildung</a> oder einer <a href="https://de.wikipedia.org/wiki/Grafik">Grafik</a>. Abbildungen oder Grafiken müssen, damit sie von Computern verarbeitet werden können, in einem <a href="https://de.wikipedia.org/wiki/Grafikformat">Grafikformat</a> gespeichert werden. Bevor wir uns genau ansehen, wie die Grafiken für Landkarten erstellt werden, erkläre ich Ihnen nachfolgend kurz die wesentlichen Unterschiede dieser beiden Formate.

### Grafikformate: Vektoren und Rastergrafiken

  Ein Grafikformat ist ein Dateiformat, das den Aufbau einer Bilddatei beschreibt. Bei den Grafikformaten können Sie alles in allem zwischen <a href="https://de.wikipedia.org/wiki/Vektorgrafik">Vektorgrafi</a><a href="https://de.wikipedia.org/wiki/Vektorgrafik">ken</a> und <a href="https://de.wikipedia.org/wiki/Rastergrafik">Rastergrafi</a><a href="https://de.wikipedia.org/wiki/Rastergrafik">ken</a> unterscheiden. Im nächsten Bild sehen Sie oben eine Vektorgrafik und unten eine Rastergrafik.

  <img alt="" src="../Images/data-url-image4.png" id="Bild87"/>

#### Vektoren

  <a class="sigil_index_marker" title="Vektorgrafiken" id="sigil_index_id_14">Vektorgrafiken</a>  basieren, im Gegensatz zu Rastergrafiken, nicht auf einem Pixelraster, indem jedem Bildpunkt ein Farbwert zugeordnet ist. Vektorgrafiken basieren auf einer Formel, die die Elemente, aus denen das Bild aufgebaut ist, genau beschreibt. Ein Kreis kann in einer Vektorgrafik anhand des Mittelpunktes, des Radiuses, der Linienstärke und der Farbe vollständig beschrieben werden. Deshalb müssen auch nur diese Parameter gespeichert werden. Je nach Bildgröße benötigen Vektorgrafiken daher oft weniger Speicherplatzbedarf als Rastergrafiken. Außerdem können sie im Gegensatz zur Rastergrafik stufenlos und verlustfrei skaliert, also vergrößert oder verkleinert werden.

#### Rastergrafiken

  <a class="sigil_index_marker" title="Rastergrafiken" id="sigil_index_id_15">Rastergrafiken</a>  kennen Sie sicherlich auch unter dem Namen  <a class="sigil_index_marker" title="Pixelgrafik" id="sigil_index_id_16">Pixelgrafik</a>  oder  <a class="sigil_index_marker" title="Bitmap" id="sigil_index_id_17">Bitmap</a>. Dieses Format beschreibt die Bilder in Form einer Anordnung von Pixeln als Raster. Pixel sind im Grunde genommen nichts anderes als Bildpunkten, denen eine Farbe zugeordnet ist. Anders als bei Vektorgrafiken ist die Bildgröße – die Breite und Höhe gemessen in Pixeln –  und die Farbtiefe – die maximale Anzahl an Farben – ein wesentliches Merkmal des Bildes. Eine Rastergrafik kann nicht stufenlos und verlustfrei vergrößert werden.

### Vektoren und Rastergrafiken für digitale Karten

Karten sollen intuitiv und einfach bedienbar sein. Idealerweise ist jeder Ausschnitt der Karte in jeder Auflösung schnell abrufbar.

Theoretisch ist dies für Vektorkarten möglich. Praktisch kostet es aber sehr viel Rechenzeit. Abgesehen von Satellitenaufnahmen oder Luftbildern, die nichts anderes als ein Foto sind, sind Karten in der Regel keine Rastergrafiken. Die Informationen anhand derer die Karte erstellt wird, werden als Daten gespeichert. Diese Daten entsprechen eher den Daten, mit denen Vektorgrafiken erstellt werden. Eine Straße wird beispielsweise mithilfe einer Anzahl von Punkten, die miteinander verbunden sind, dargestellt. Zusätzlich werden mit diesen Punkten Eigenschaften abgespeichert. Eine Eigenschaft kann der Straßenname sein –  eine andere Eigenschaft kann der Straßenbelag sein.

Leider ist die Darstellung dieser Informationen auf einer Webseite in einem Vektorformat aber schwierig. Nicht alle Browser können gut mit Vektorgrafiken umgehen. Außerdem gibt es viele Geodaten, die große Bereiche auf der Erde abdecken. Diese müssen bei der Verwendung eines Vektorformates auch dann verarbeitet werden, wenn Sie sich nur einen kleinen Bereich in Deutschland ansehen möchten. Mit Rastergrafiken hat kein Browser Probleme. So ziemlich jedem Browser kann eine Rasterkarte anstandslos auf einem Bildschirm anzeigen.

Das Problem bei der Bereitstellung von geographischen Informationen als Rastergrafik ist, dass eine gute Bildqualität eine hohe Auflösung voraussetzt. Dies hat zur Folge, das die Grafikdateien sehr groß werden. Bilddateien, die über das Internet geladen und im Browser angezeigt werden, sollten aber so klein wie möglich sein.

Aus diesem Grund wird die Karte für kleine Ausschnitte im Vorfeld berechnet und in einem Rasterformat gespeichert. Als Rasterformat wird <a href="https://de.wikipedia.org/wiki/Portable_Network_Graphics">PNG</a> verwendet. Wie dies genau gemacht wird, erkläre ich Ihnen im nächsten Kapitel.

### Wir unterteilen die Welt in Kacheln

  Um eine Karte anzuzeigen, wird die Welt also in Ausschnitte, genau genommen in Quadrate zerlegt. Die Quadrate werden  <a class="sigil_index_marker" title="Tile" id="sigil_index_id_18">Tiles</a>, das ist das englische Wort für  <a class="sigil_index_marker" title="Kachel" id="sigil_index_id_19">Kacheln</a>, genannt. Jedes Quadrat ist exakt 256 Pixel x 256 Pixel groß.

> Nicht nur OpenStreetMap, auch die Google
Maps API unterteilt ihr Kartenbilder in Kacheln. Wenn Sie die Website
    <a href="https://www.google.de/maps">https://www.google.de/maps</a>
aufrufen und eine andere Vergrößerungsstufe wählen, wird ermittelt,
welche Daten erforderlich sind. Diese Daten werden dann in einen Satz
mit Kacheln übersetzt und angezeigt.

Dabei bildet die  <a class="sigil_index_marker" title="Zoom-Stufe" id="sigil_index_id_20">Zoom-Stufe</a>  0 die ganze Welt auf ein Quadrat ab. Teilt man den Erdumfang von 40.038 Kilometern durch die 256 Pixel der Kachel sieht man im Ergebnis, dass ein Pixel 156,4 Kilometer darstellt. Das ist noch nicht sehr detailliert. Bis Zoom-Stufe 19 ändert sich eine ganze Menge. In der nachfolgenden Tabelle sehen Sie, dass bei Zoom-Stufe 19 ein Pixel einem Bereich von 0,3 Metern auf der Erde entspricht. Damit kann man schon etwas anfangen!

  <table>
    <colgroup>
      <col class="vier"/>

      <col class="vier"/>

      <col class="vier"/>

      <col class="vier"/>
    </colgroup>

    <tbody>
      <tr valign="top">
        <td>**
          Zoom-Stufe
        **</td>

        <td>**
          Kachel-Anzahl
        **</td>

        <td>**
          Kachel-Breite entpricht   **</td>

        <td>**
          Ein Pixel entspricht
        **</td>
      </tr>

      <tr valign="top">
        <td>
          0
        </td>

        <td>
         1
        </td>

        <td>
          40.038 Kilometer
        </td>

        <td>
          156 Kilometer
        </td>
      </tr>

      <tr valign="top">
        <td>
         1
        </td>

        <td>
          4
        </td>

        <td>
          20.019 Kilometer
        </td>

        <td>
          78 Kilometer
        </td>
      </tr>

      <tr valign="top">
        <td>
          2
        </td>

        <td>
          16
        </td>

        <td>
          10.009 Kilometer
        </td>

        <td>
          39 Kilometer
        </td>
      </tr>

      <tr valign="top">
        <td>
          3
        </td>

        <td>
          64
        </td>

        <td>
          5.004 Kilometer
        </td>

        <td>
          19,5 Kilometer
        </td>
      </tr>

      <tr valign="top">
        <td>
          4
        </td>

        <td>
          256
        </td>

        <td>
          2502 Kilometer
        </td>

        <td>
          9,8 Kilometer
        </td>
      </tr>

      <tr valign="top">
        <td>
          ..
        </td>

        <td>
          ..
        </td>

        <td>
         ..
        </td>

        <td>
          ..
        </td>
      </tr>

      <tr valign="top">
        <td>
          15
        </td>

        <td>
          1 Milliarde
        </td>

        <td>
          1224 Meter
        </td>

        <td>
          4,8 Meter
        </td>
      </tr>

      <tr valign="top">
        <td>
          16
        </td>

        <td>
          4 Milliarden
        </td>

        <td>
          612 Meter
        </td>

        <td>
          2,4 Meter
        </td>
      </tr>

      <tr valign="top">
        <td>
          17
        </td>

        <td>
          17 Milliarden
        </td>

        <td>
          306 Meter
        </td>

        <td>
          1,2 Meter
        </td>
      </tr>

      <tr valign="top">
        <td>
          18
        </td>

        <td>
          69 Milliarden
        </td>

        <td>
          153 Meter
        </td>

        <td>
          0,6 Meter
        </td>
      </tr>

      <tr valign="top">
        <td>
          19
        </td>

        <td>
          275 Milliarden
        </td>

        <td>
          76 Meter
        </td>

        <td>
          0,3 Meter
        </td>
      </tr>
    </tbody>
  </table>



  Die vollständige Tabelle können Sie unter der Adresse <a href="http://wiki.openstreetmap.org/wiki/Zoom_levels">http://wiki.openstreetmap.org/wiki/Zoom_levels</a> mit weiteren Angaben im Internet abrufen.

  Vielleicht probieren Sie nun das Zoomen im vorangegangene Beispiel aus und wundern sich, dass Sie die Karte nur bis zur Zoom-Stufe 18 vergrößern können. Das liegt daran, dass bei dieser OpenStreeMap Karte standardmäßig die Option `maxZoom` mit 18 gesetzt ist. Sie können diese Option jedoch überschreiben. Wie das geht sehen Sie im nachfolgenden Programmcodebeispiel fett formatiert. Weitere Informationen finden Sie im Kapitel zur Karte von  <a href="#maxnativzoom">Stamen</a>*.*

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
</head>
<body>
<div style="height: 180px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);
console.log(mymap);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', **{minZoom: 0, maxZoom: 19}**)
.addTo(mymap);

</script>
</body>
</html>
<!--index_995a.html-->
`</pre>

> Vielleicht sind Sie es gewohnt, bei der
Darstellung von Landkarten in den Zahlen eines Maßstabs zu denken?
Bei digitalen Karten gibt es keinen Maßstab im Sinne einer
Papierkarte, weil die Druckauflösung nicht bekannt ist und ein
Maßstab hiervon abhängt. Ein Maßstab kann immer nur relativ zur
Auflösung angegeben werden.


### Wie weiß Leaflet welche der vielen Kacheln angezeigt werden sollen?

Nun haben wir jede Menge Kacheln und möchten mit diesen eine digitale Karte auf unserer Website anzeigen. Woher weiß Leaflet, welche Kacheln es vom verlinkten Server laden und an welcher Stelle es diese anzeigen soll? Dazu sehen wir uns zunächst einmal an, wie die Kacheln genau erstellt werden.

Um ein Bild von einer Karte in kleine überschaubare Abschnitte zu teilen, unterscheidet der Server, der die Kacheln erzeugt, zwischen verschiedenen Zoom-Stufen und für jede Zoom-Stufe erstellt er ein eigenes Set von Kacheln – praktisch eine eigene Ebene.  
Da der Standard für die Größe der Kacheln 256 Pixel x 256 Pixel beträgt, ist bei der Zoom-Stufe 0 die gesamte Welt in einer einzigen 256 Pixel x 256 Pixel großen Kachel enthalten. In der Tabelle im vorherigen Kapitel konnten Sie ja schon erkennen, dass jede Erhöhung der Zoom-Stufe auch die Anzahl der anzuzeigenden Kacheln erhöht.

Um die Kacheln in der richtigen Weise zu benutzen, muss es ein Muster geben, das befolgt werden kann, um sicherzustellen, dass die richtige Kachel vom Server geladen werden und vom Browser des Clients an der richtigen Stelle angezeigt werden.

Im Kapitel  <a href="#inFuegenSieeineSchichtmitKache">Fügen Sie eine Schicht mit Kacheln – einen Tile-Layer – zum Karten-Objekt hinzu</a>  hatten wir die URL für den Tile Server mit  `http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png`  angegeben.

Der Teil  `{z}/{x}/{y}`  des Pfades zur PNG-Datei enthält Variablen aus denen der Namen der Bilddatei berechnet werden kann.

- `{z}`  bezeichnet die zu ladende Zoom-Stufe. 
- `{x}`  bezeichnet die Position auf der x-Achse der Kachel. 
- `{y}`   bezeichnet die Position auf der y-Achse. 
- `{s}`  steht für eine optionale Subdomain. 

Zum Beispiel wird das Bild für die niedrigste Zoom-Stufe – also das Bild welches den größten Bereich pro Pixel anzeigt – unter dem Dateinamen  `0/0/0.png` abgespeichert.

<img alt="" src="../Images/data-url-image5.png" id="Bild13"/>

Die vollständige URL dieses Kachelbildes auf dem Openstreetmap Server ist  `http://a.tile.openstreetmap.org/0/0/0.png`. Probieren Sie es, klicken Sie den Link an oder öffnen Sie selbst die Adresse  <a href="http://a.tile.openstreetmap.org/0/0/0.png">http://a.tile.openstreetmap.org/0/0/0.png</a>  in Ihrem Internetbrowser.

> Tiefer gehend können Sie das Thema auf
der Website von OpenStreetMap, genau unter der Adresse
    <a href="http://wiki.openstreetmap.org/wiki/Slippy_map_tilenames">http://wiki.openstreetmap.org/wiki/Slippy_map_tilenames</a>,
nachlesen.

  Bei der Zoom-Stufe 1 sind die Kacheln, wie in der nachfolgenden Grafik dargestellt, angeordnet.

  <img alt="" src="../Images/data-url-image6.png" id="Bild12"/>

  *Abbildung 7: Zoom Level 1. © OpenStreetMap contributors*

  Unter der Adresse <a href="http://a.tile.openstreetmap.org/1/0/0.png">http://a.tile.openstreetmap.org/</a><a href="http://a.tile.openstreetmap.org/1/0/0.png">1</a><a href="http://a.tile.openstreetmap.org/1/0/0.png">/0/0.png</a> finden sie die Grafik, die sich in der Abbildung links oben befindet.

  <h2 id="sigil_toc_id_21">Schöne Kartenlayer</h2>

  Nachdem das Erstellen der ersten Karte so einfach vonstatten ging fragen Sie sich sicher, ob es genauso einfach ist eine alternative Darstellung – also  <a class="sigil_index_marker" title="Kartenlayeralternativen" id="sigil_index_id_22">Kacheln eines anderen Providers  </a>– zu verwenden. Die Antwort ist: Ja, es ist genauso einfach!

  Ich zeige Ihnen dies hier anhand von zwei weiteren Providern, nämlich <a href="https://www.thunderforest.com/">Thunderforest</a><a class="sigil_index_marker" title="Thunderforest" id="sigil_index_id_23"> und</a> <a href="https://stamen.com/">Stamen</a><a class="sigil_index_marker" title="Stamen" id="sigil_index_id_24">.</a>

> Mögen Sie die Karten von  <a class="sigil_index_marker" title="GoogleMaps einbinden" id="sigil_index_id_25">GoogleMaps</a>  und möchten Sie gerne die Kacheln von Google für Ihre digitale Karte nutzen? Wenn
Sie dies zusammen mit Leaflet tun möchten, können Sie dies mithifle des Plugins  <a href="https://gitlab.com/IvanSanchez/Leaflet.GridLayer.GoogleMutant">L.GridLayer.GoogleMutant</a>.

### Thunderforest

Thunderforest bietet Ihnen gleich neun verschiedene Kachel-Varianten. Sie erreichen die Kacheln alle über die gleiche URL, lediglich das Unterverzeichnis muss angepasst werden.  

> Um Kacheln von Thunderforest zu
verwenden, müssen Sie ein Zugriffstoken anfordern. Dieses Token können Sie über die Adresse  <a href="https://www.thunderforest.com/docs/apikeys/">https://www.thunderforest.com/docs/apikeys/</a>  selbst erstellen. Wenn Sie ihre Karte erstellen, hängen Sie dieses Zugriffstoken einfach an das Ende der URL des Tile-Servers an. Zum
Beispiel
so:
`https://{s}.tile.thunderforest.com/cycle/{z}/{x}/{y}.png`**?apikey=YourApiKey**`

  Die Kacheln der OpenCyclemap finden Sie beispielsweise unter der Adresse `https://{s}.tile.thunderforest.com/`**cycle**`/{z}/{x}/{y}.png?apikey=YourApiKey` abgelegt. Die Transportvariante finden Sie unter der Adresse `https://{s}.tile.thunderforest.com/`**transport**`/{z}/{x}/{y}.png?apikey=YourApiKey.`

  Die nachfolgende Tabelle zeigt Ihnen eine Übersicht über die verschiedenen Kartenstile von Thunderforest.

  <table>
    <colgroup>
      <col width="128*"/>

      <col width="128*"/>
    </colgroup>

    <tbody>
      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image7.png" id="Bild17"/>cycle
        </td>
     </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image8.png" id="Bild18"/>transport
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image9.png" id="Bild19"/> landscape
        </td>

     </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image10.png" id="Bild20"/> outdoors
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image11.png" id="Bild21"/>transport-dark
        </td>

     </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image12.png" id="Bild22"/>spinal-map
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image13.png" id="Bild23"/> pioneer
        </td>

     </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image14.png" id="Bild24"/>mobile-atlas
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image15.png" id="Bild25"/>neigborhood
        </td>


      </tr>
    </tbody>
  </table>



  Wenn Sie Thunderforest verwenden möchten, müssen Sie unser bisheriges Beispiel nun in einer Zeile abändern. Sie müssen als Tile Layer nur die im Beispiel zu sehende URL angeben. Der nachfolgende Programmcode zeigt Ihnen ein vollständiges Beispiel.

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
var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);

**L.tileLayer('https://{s}.tile.thunderforest.com/landscape/{z}/{x}/{y}
.png?apikey=MeinZugriffstoken').addTo(mymap);
**
</script>
</body>
</html>
<!--index_994.html-->

`</pre>

### Stamen

  Stamen legt den Schwerpunkt auf gutes Design. Informationen zu den Karten von Stamen finden Sie auf der Website <a href="http://maps.stamen.com/">http://maps.stamen.com/</a>. Die nachfolgende Tabelle zeigt Ihnen drei Kartenstile von Stamen.

  <table>
    <colgroup>
      <col width="128*"/>

      <col width="128*"/>
    </colgroup>

    <tbody>
      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image16.png" id="Bild14"/>
toner
        </td>
     </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image17.png" id="Bild15"/>
 watercolor
        </td>
      </tr>

      <tr valign="top">
        <td>
          <img alt="" src="../Images/data-url-image18.png" id="Bild16"/>
terraint
        </td>

      </tr>
    </tbody>
  </table>



  Beim Einbinden einer Karte von Stamen müssen Sie zusätzlich eine JavaScript Datei einbinden. Wie Sie den `StamenTileLayer` genau nutzen, können Sie im nachfolgenden Programmcodebeispiel ablesen.

<pre>`<!DOCTYPE HTML>
<html>
<head>
<title>Eine OpenStreetMap Karte mit Leaflet</title>
<link rel="stylesheet" href="../leaflet/leaflet.css" />
<script src="../leaflet/leaflet.js"></script>
**<script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js"></script>**
</head>
<body>
<div style="height: 700px;" id="mapid"></div>
<script>
var mymap = L.map('mapid').setView([50.27264, 7.26469], 13);
**var layer = new L.StamenTileLayer("watercolor");**
**mymap.addLayer(layer);**
</script>
</body>
</html>
<!--index_993.html-->

`</pre>

> **Achtung:**  
Der `StamenTileLayer` unterstützt nicht alle Zoom-Stufen. Wenn Sie den Typ `watercolor` verwenden, sehen Sie zum Beispiel mit der Zoom-Stufe 19 eine leere graue Fläche. Um dies zu verhindern können Sie die Optionen des `StamenTileLayer` überschreiben.  
<ul><li>Setzten Sie dafür nach der Instanziierung die Options `maxZoom`<a class="sigil_index_marker" title="Option maxZoom" id="sigil_index_id_26">  </a>auf 19. So
bleibt die Zoom-Stufe 19 als Ebene auf der Karte erhalten.   
<li>Setzen Sie dann aber die Option `maxNativeZoom`<a class="sigil_index_marker" title="maxNativeZoom" id="sigil_index_id_27">  </a>auf 18.   
</ul>
Dies bewirkt, dass Leaflet nicht versucht, Kachel für eine Zoom-Stufe 19 zu laden. Stattdessen benutze Leaflet auch bei Zoom-Stufe 19 die Kacheln der Zoom-Stufe 18 – skaliert diese aber auf die Größe der Zoom-Stufe 19.  
...  
`var layer = new L.StamenTileLayer("watercolor");`   
`layer.options.maxZoom = 19;`  
`layer.options.maxNativeZoom = 18;`  
...  

ESRI ist ein weiterer Anbieter von Basiskarten. Was ESRI genau ist und wie Sie die Karten dieses Institius einbinden können erkläre ich Ihnen im Kapitel  <a href="../Text/esri.html#inESRI">ESRI</a>.

> Haben Sie noch nicht den Kartenstil gefunden, den Sie suchen oder sind Sie einfach nur
neugierig, welche Karten sonst noch angeboten werden? Verweise auf
weitere Tile-Server-Provider finden Sie unter der Adresse:
    <a href="http://wiki.openstreetmap.org/wiki/Tiles">http://wiki.openstreetmap.org/wiki/Tiles</a>


<h2 id="sigil_toc_id_22">Images als Layer – Web-Map-Service</h2>

Sie haben eine gute Satellitenaufnahme und möchten diese als Schicht in Ihrer Karte anzeigen. Vielleicht denken Sie auch an die Wetterwarnkarten des Deutschen Wetterdienstes, die im Grunde genommen nur aus eingefärbten Polygonen bestehen. Ein Umwandeln dieser Grafikdateien in 275 Milliarden Kacheln, wie es im vorherigen Kapitel beschriebenen wurde, wäre zwar möglich – Sie können sich aber vorstellen, dass es für diese Aufgabenstellungen adäquatere Techniken gibt.

### Eine einfache Leaflet-Karte mithilfe des Web-Map-Services erstellen

Eine Alternative zur schon beschriebenen Kachel-Technik ist der <a href="https://de.wikipedia.org/wiki/Web_Map_Service" class="sigil_index_marker" title="Web-Map-Service (WMS)" id="sigil_index_id_28">Web-Map-Service</a> (WMS). Der WMS ist ein Spezialfall eines <a href="https://de.wikipedia.org/wiki/Webservice">Web </a><a href="https://de.wikipedia.org/wiki/Webservice">Services</a>. Dieser Service bietet Ihnen eine Schnittstelle zum Abrufen von Landkartenausschnitten über das Internet.

Ein WMS bietet drei Funktionen, die von einem Benutzer angefragt werden können. Die Funktionen `GetCapabilities` und `GetFeatureInfo` können wir hier vernachlässigen. Diese sind für die Anzeige der Karte nicht relevant. Die Funktion `GetMap` ist die, die wir uns genauer ansehen und die von Leaflet angewendet wird. Bei einem Aufruf von `GetMap`<a class="sigil_index_marker" title="Funktion getMap (WMS)" id="sigil_index_id_29"> liefert</a> der WMS ein  <a class="sigil_index_marker" title="georeferenziert" id="sigil_index_id_30">georeferenziertes</a>  Rasterbild.

> Bei einem georeferenzierten Rasterbild handelt
es sich um eine Bilddatei, der raumbezogene Informationen hinzugefügt
wurden. Das hört sich zunächst einmal sehr theoretisch an.
Praktisch können Sie sich den Vorgang der Georeferenzierung so
veranschaulichen: Stellen Sie sich vor, dass das Bild auf einen Bereich auf der Erde gelegt wird. Gleichzeitig wird das
Gradnetz der Erde dieses Bereichs mit dem Bild verbunden. Im Ergebnis
wird also jedem Pixel des Bildes eine Koordinate – in Relation zum
Gradnetz der Erde – zugewiesen. Georeferenzierung kennen Sie
vielleicht auch unter dem Begriff Geokodierung, Geotagging oder
Verortung.

Innerhalb des `GetMap  `Aufrufs können Sie Optionen auswählen. Zum Beispiel können Sie angeben,  

<ul><li>welches Koordinatensystem zugrundelegt werden soll, 
<li>welchen Kartenausschnitt Sie sehen möchten, 
<li>wie groß der Kartenausschnitt sein soll oder 
<li>welches Ausgabeformat Sie gerne hätten. 
</ul>


Mit folgendem URL-Abruf erhalten Sie beispielsweise ein speziell zusammengestelltes Bild vom GeoWebservice des <a href="http://www.dwd.de/">Deutschen Wetterdienstes</a>.

`<a href="https://maps.dwd.de/geoserver/dwd/wms?service=WMS&amp;version=1.1.1&amp;request=GetMap&amp;layers=dwd:Warnungen_Landkreise&amp;bbox=6.15,51.76,14.90,55.01&amp;width=512&amp;height=418&amp;srs=EPSG:4326&amp;format=image%2Fjpeg&amp;CQL_FILTER=EC_II%20IN%20('51','52">https://maps.dwd.de/geoserver/dwd/wms`  
`?service=WMS&amp;version=1.1.1`  
`&amp;request=GetMap&amp;layers=dwd:Warnungen_Landkreise`  
`&amp;bbox=6.15,51.76,14.90,55.01`  
`&amp;width=512`  
`&amp;height=418`  
`&amp;srs=EPSG:4326`  
`&amp;format=image**%2Fjpeg**`  
`&amp;CQL_FILTER=EC_II%20IN%20**('51','52**</a>**')**`

  Probieren Sie es aus: Der Aufruf der URL im Browser produziert eine Karte mit allen momentan ausgegebenen gültigen Windwarnungen der Kategorie 51 (Windböen) und 52 (Sturmböen) für Norddeutschland. Ausgegeben im JPG-Format. Sie sehen allerdings nur dann ein Bild, wenn tatsächlich Wetterwarnungen vorhanden sind.

> Eine Anleitung zur Nutzung des GeoWebservices des Deutschen Wetterdienstes finden Sie unter der Adresse <a href="http://www.dwd.de/DE/wetter/warnungen_aktuell/objekt_einbindung/einbindung_karten_geowebservice.pdf?__blob=publicationFile&amp;v=2">http://www.dwd.de/DE/wetter/warnungen_aktuell/objekt_einbindung/einbindung_karten_geowebservice.pdf?__blob=publicationFile&amp;v=2</a>.
Detaillierte technische Informationen zum Web Mapping Service (WMS) allgemein finden Sie unter der Adresse
<a href="http://www.opengeospatial.org/standards/wms">http://www.opengeospatial.org/standards/wms</a>
im Internet. Ausführliche Informationen zu den möglichen Funktionen eines Geoservers finden Sie unter <a href="http://docs.geoserver.org">http://docs.geoserver.org</a>.

Ich möchte Sie hier an dieser Stelle nicht mit trockenen Dokumentationen von Web Services langweilen. Viel lieber zeige ich Ihnen ein praktisches Beispiel. Im nachfolgenden Programmcodeausschnitt sehen Sie die wesentlichen Zeilen fett hervorgehoben.

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
**var dwd = L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms", {**
**layers:'dwd:bluemarble',**
**}).addTo(mymap);**
</script>
</body>
</html>
<!--index_992.html-->

`</pre>

  Wenn Sie dieses Beispiel mit dem Laden eines `L.tileLayer` ohne WMS vergleichen, ist eigentlich nur eine Zeile anders.

  Anstelle der Zeile

  `**L.tileLayer**('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);`

  haben wir

  `**L.tileLayer.wms**("https://maps.dwd.de/geoserver/dwd/wms", {`

  `layers:'dwd:bluemarble',`

  `}).addTo(mymap);`

  eingefügt.

  Wichtig ist, dass Sie dem Aufruf `L.tileLayer.wms  `

<ul><li>die richtige Adresse zum WMS Service mitgeben und   
<li>die Option `layers ` passend setzen.   
</ul>


Für alle anderen Parameter setzt Leaflet, oder der Service selbst, Standardwerte ein – falls Sie nichts Spezielles angeben ...

> **Hinweis:**
Die Leaflet Klasse
`L.tileLayer.wms` können
Sie sich <a href="https://github.com/Leaflet/Leaflet/blob/79e8bf724c4da1d7a95f758026c974ae96dfbc5c/src/layer/tile/TileLayer.WMS.js#L31">hier</a>
auf Github ansehen.


Möchten Sie wissen, was vom WMS-Service geliefert wird? Dann öffnen Sie doch die HTML-Datei des vorherigen Beispiels in Ihrem Browser. Mit dem Layer `dwd:bluemarble ` können Sie ein Satellitenbild zu Ihrer Karte hinzufügen. Wie das genau aussieht, sehen Sie im nachfolgenden Bild.

<img alt="" src="../Images/data-url-image19.png" id="Bild26"/>

### L.tileLayer.wms über L.tileLayer.wms

Das Schöne an WMS-Layern ist, das Sie diese übereinander legen können. Das nachfolgende Beispiel enthält Programmcode, der im Ergebnis gleichzeitig drei WMS-Layer übereinander anzeigt.

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
**`L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms",`**  
**`{`**  
**`transparent: true,`**  
**`layers:'dwd:bluemarble',`**  
**`}).addTo(mymap);`**  
  
**`L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms",`**  
**`{`**    
**`format: 'image/png',`**  
**`transparent: true,`**  
**`layers:'dwd:Warngebiete_Kreise'`**  
**`}).addTo(mymap);`**  
  
**`L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms",`**  
**`{`**  
**`format: 'image/png',`**  
**`transparent: true,`**  
**`layers:'dwd:Warnungen_Gemeinden_vereinigt'`**  
**`}).addTo(mymap);`**  
`</script>`  
`</body>`  
`</html>`  
`<!--index_991.html-->`  

Dieses Beispiel ist meiner Meinung nach selbsterklärend. Wichtig ist, dass Sie die Option `transparent` mit `true` übergeben. Andernfalls sehen Sie nur einen – nämlich den obersten – Layer. Bereiche, die nicht mit Daten gefüllt sind, werden weiß gezeichnet. Außerdem müssen Sie die Option `format` mit `'image/png'` belegen. Leaflet lädt ansonsten automatisch das Format `'image/jpeg'` und dieses Format unterstützt keine Transparenz.

<img alt="" src="../Images/data-url-image20.png" id="Bild27"/>

<img alt="" src="../Images/data-url-image21.png" id="Bild28"/>

### L.tileLayer.wms und L.tileLayer zusammen auf einer Karte

  Das nachfolgende Beispiel zeigt Ihnen, wie Sie einen  `L.tileLayer` mit einem `L.tileLayer.wms` kombinieren können.


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

**L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(mymap);**

**L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms",**
**{**
**format: 'image/png',**
**transparent: true,**
**layers:'dwd:Warngebiete_Kreise'****}).addTo(mymap);**

**L.tileLayer.wms("https://maps.dwd.de/geoserver/dwd/wms",**
**{**
**transparent: true,**
**format: 'image/png',**
**layers:'dwd:Warnungen_Gemeinden_vereinigt'**
**}).addTo(mymap);**
</script>
</body>
</html>
<!--index_990.html-->  
`</pre>

  Für dieses Beispiel gilt das, was ich im vorherigen Beispiel bezüglich Transparenz und Format geschrieben habe. Zusätzlich müssen Sie darauf achten, dass Sie den `L.tileLayer` nicht über die  `L.tileLayer.wms.Layer`  Schicht legen. Der `L.tileLayer` ist nicht transparent. Er würde die `L.tileLayer.wms.Layer` Schicht vollständig abdecken.

  Die nachfolgende Abbildung zeigt Ihnen die zwei `L.tileLayer.wms`  Layer über dem `L.tileLayer` Layer.

  <img alt="" src="../Images/data-url-image22.png" id="Bild29"/>

> **Achtung:**
Wenn auf Ihrer Karte
der Layer  `dwd:Warnungen_Gemeinden_vereinigt`  nicht angezeigt wird, kann es daran 
liegen, dass es zur Zeit keine Warnungen gibt.  
Dieser Layer enthält nur Daten, wenn aktuell Wetterwarnungen vorliegen.   
Die grünen Polygone – im Layer `dwd:Warngebiete_Kreise`  – die 
die Landkreise darstellen, werden dahingegen immer eingeblendet.

# Das erste Leaflet Control-Plugin - Ein Tutorial für Anfänger

In diesem Beitrag erkläre ich Ihnen, wie Sie ein Plugin für 
[LeafletJs](http://leafletjs.com/) erstellen. Ganz genau 
zeige ich Ihnen, wie Sie ein Control-Plugin, also ein Steuerelement für Ihre Leaflet Karte 
programmieren.  

In diesem Text konzentriere ich mich darauf, die Struktur und den Lebenszyklus 
von Leaflet-Plugins 
zu erklären. Meine Vorlage für die Erstellung von Leaflet Control- und 
Layer-Plugins habe ich auf [Github](https://github.com/astridx/leafletjs-plugin-boilerplate) 
veröffentlicht.

## Leaflet Control-Plugins

Während Layer-Plugins(todo link) die Leaflet-Karte mit Inhalten erweitern, 
fügen Leaflet Control-Plugins Steuerelemente zur Oberfläche der Leaflet-Karte hinzu. 
Mithilfe dieser Steuerelement kann mit der Leaflet-Karte interagiert werden.
Beispiele für Steuerelemente einer Leaflet-Karte sind die 
- Zoomsteuerung und die 
- Ebenensteuerung,  

die links oben und rechts oben in der folgenden Abbildung angezeigt werden.

![Steuerelemente auf einer Leaflet Karte](media/controls_leaflet.png)

### So erstellen Sie ein Leaflet Control-Plugin

Bevor ich mit Ihnen praktisch ein Control erstelle, hier die recht langweilig 
klingende Definition: Leaflet Control-Plugins sind JavaScript-Klassen, die die 
[Leaflet Klasse](http://leafletjs.com/reference.html#class) 
[`L.Control`](https://leafletjs.com/reference-1.3.4.html#control) erweitern. 
Üblicherweise wird der Name des Control-Plugins 
zum Namensraum von Leaflet, also zu `L`, hinzugefügt.  

Im nächsten Beispiel zeige ich Ihnen, wie Sie 
ein Control-Plugin mit dem Namen `L.LeafletControlExample` erstellen. Hier zunächst der 
JavaScript Code.

```
L.LeafletControlExample = L.Control.extend({
  options: {
    position: 'topright'
  },
  ...
}
```

Die Erweiterungsmethode `extend` der Klasse `L.Control` verwendet 
einen einzigen Parameter, 
der alle *Eigenschaften* und *Methoden* enthält, die das Plugin 
der `L.Control`-Unterklasse hinzufügt. 
Viele Control-Plugins verfügen über eine Reihe von Standardeinstellungen. 
Im obigen Code-Snippet enthält das Optionsobjekt `options` eine Standardeinstellung 
für die Position `position` des Steuerelements auf der Leaflet-Karte.  

Das Standardmuster für die Erstellung eines Leaflet-Plugins, 
implementiert eine [Factory-Methode](https://de.wikipedia.org/wiki/Fabrikmethode), 
mit der die Erstellung des Plugins mit anderen Methodensaufrufen verkettet werden kann. 
Das ist ganz praktisch. Deshalb sollten jedes Leaflet-Plugin diese 
Factory-Methode enthalten.
Schreiben Sie dazu ganz ans Ende der Datei den folgenden Text.

```
L.leafletControlExample = function(options) {
  return new L.LeafletControlExample(options);
};
```
Nun können sie Ihr Plugin ganz einfach in einer Zeile erstellen und zur Karte hinzufügen. 
Im Beispiel würde das wie folgt aussehen:

```
L.leafletControlExample({ position: 'bottomright' }).addTo(map);
```

Üblicherweise wird die Factory-Methode nach der Klasse des Steuerelement-Plugins benannt. 
Nur der erste Buchstaben wird - anstelle eines große - mit einem kleinen Buchstaben geschrieben.

### Der Lebenszyklus des Leaflet Controll-Plugins

Leaflet ruft die folgenden Methoden eines Steuerelement-Plugins auf, 
wenn das Steuerelement zu einer Leaflet-Karte hinzugefügt wird.

1. `initialize()`
2. `onAdd ()`

Leaflet ruft die `initialize`-Methode auf, wenn eine neue Instanz 
eines Controll-Plugins erstellt wird, indem entweder `new` direkt aufgerufen wird 
oder wenn die Factory-Methode verwendet wird:

1. `L.leafletControlExample()`
2. `new L.LeafletControlExample()`

In der folgenden `initialize`-Methode wird `L.Util.setOptions` aufgerufen, 
um die Werte der Standardeinstellungen zu setzten. 

```
...
initialize: function(options) {
  L.Util.setOptions(this, options);
  // Initialisierung des Control-Plugins.
 }
...
```

Nach dem Aufruf der Methode `setOptions` kann der `initialize`-Methode weiterer 
Code zur Initialisierung des Steuerelements hinzugefügt werden.  

Leaflet ruft die `onAdd`-Methode auf, wenn das Steuerelement mit den folgenden 
Methodenaufrufen zur Karte hinzugefügt wird:

1. `control.addTo(Karte);` 
2. `map.addControl(Steuerelement);`

Ein Leaflet-Control-Plugins ist ein [DOM-Element](https://de.wikipedia.org/wiki/Document_Object_Model) 
Element - in der Regel ein 
[HTML-Element](https://de.wikipedia.org/wiki/Hypertext_Markup_Language)-, 
das auf der Karte angezeigt wird. Genauer ausgedrückt: Das Element 
wird auf einer Schicht oberhalb der eigentlichen 
Kartenschicht angezeigt.

Wichtig: Die `onAdd`-Methode muss das 
DOM-Element zurückgeben.  
 
In der folgenden `onAdd`-Methode erstellen wir ein `div`-Element. 
Diesem `div`-Element fügen wir danach die Klasse `leaflet-control-example` hinzu.
So können wir das Steuerelement später mit CSS problemlos formatieren.

```
...
onAdd: function(map) {
  var controlElementTag = 'div';
  var controlElementClass = 'leaflet-control-example';
  var controlElement = L.DomUtil.create(controlElementTag, controlElementClass);

  // Hier können noch weitere Elemente hinzugefügt werden.
  // Außerdem können Sie hier einem Element Events hinzufügen.

  return controlElement;
},
...
```

Wenn alles fertig ist geben Sie das DOM-Element mit `return controlElement` zurück.

Leaflet erwartet eine weitere Methode. 
Diese Methode heißt `onRemove`. 
Die Methode `onRemove` wird - wie der Name schon sagt - aufgerufen, 
wenn das Steuerelement von der Karte entfernt wird.

1. `control.removeFrom(Karte);` 
2. `map.removeControl(Steuerelement);` 

Die `onRemove`-Methode ist der Ort, an dem aufgeräumt wird. Entfernen Sie hier 
die DOM-Elemente und Ereignis-Listener.

```
...
onRemove: function(map) {
  // Tear down the control.
}
...
```

### Styling

Leaflet Steuerelemente können Sie wie jedes andere 
DOM-Element mit CSS gestalten. 
Hier füge ich der CSS-Klasse `leaflet-control-example` Stilregeln hinzu. Naja, bisher füge ich 
nur drei Punkte hinzu. Sie haben sicher etwas mehr Fantasie. Zur Erinnerung: 
Das `div`-Element mit der Klasse `leaflet-control-example` haben wir in der 
`onAdd`-Methode hinzugefügt.

```
...
.leaflet-control-example {
  ...
}
...
```

### Lesen Sie weiter

Die Leaflet-Dokumentation enthält einen 
[Plugin-Authoring-Leitfaden](https://leafletjs.com/2013/06/28/leaflet-plugin-authoring-guide.html), 
in dem bewährte Vorgehensweisen zum 
- Organisieren, 
- Präsentieren und 
- Demonstrieren  

von Leaflet-Plugin-Code erläutert werden. 

Auf der [Leaflet Website](https://leafletjs.com/plugins.html) werden 
verschiedene Plugins aufgelistet, 
die von der Leaflet-Community erstellt wurden. 
Die meisten Plugins sind 
[Open Source](https://de.wikipedia.org/wiki/Open_Source) und sind auf 
[GitHub](https://github.com/) verfügbar. 
Wer gerne mit Beispielen lernt, findet hier eine Fülle von Möglichkeiten, 
um das Erstellen eigener Plugins zu lernen.

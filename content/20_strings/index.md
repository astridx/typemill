# ECMAScript 6 - Arbeiten mit Strings
[](#){#ArbeitenMitStrings}


## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 
Todo Meldungen immer mit Firefox




## Besser Unicode-Unterstützung

### UTF-16

ECMAScript 5 entstand, als 16 Bit ausreichten, um alle vorhandene Unicode-Zeichen 
abzubilden. Später wurde Unicode um weitere Zeichen mit einem erweitert. 
Dies hat zur Folge, 
dass 16 Bit nicht mehr ausreichen, um alle möglichen Unicode-Zeichen darzustellen.

> Das Ziel von Unicode ist es, alle in Gebrauch befindlichen Schriftsysteme 
und Zeichen zu kodieren. Der Zeichenumfang ist dazu 
in 17 Ebenen (englisch planes) gegliedert. 
Sechs dieser Ebenen werden bereits verwendet, die restlichen sind für spätere Nutzung reserviert. 
Die ursprünglichen 16 Bit sind unter dem Namen *Basic Multilingual Plane* 
(BMP; deutsch Mehrsprachige Basis-Ebene, auch als Plane 0 bezeichnet) bekannt.

Damit die ursprünglichen 16 Bit auch weiterhin problemlos 
verwendet werden könne, speichert UTF-16 die ursprünglichen Unicode-Zeichen in der BMP 
weiterhin in 16 Bit. 
Alle neuen Unicode-Zeichen werden hingegen in 32 Bit 
gespeichert, also in zwei 16-Bit-Werten. 
Diese beiden 16-Bit-Werte werden als *Ersatzpaar* (englisch surrogate pair) bezeichnet. 
Streng genommen wird ein Unicode-Zeichen außerhalb der BMP in einer 
*UTF-16-Codeeinheit* anstelle eines *Unicode-Zeichens* gespeichert.

So können Sie alle Methoden die auf 16 Bit begrenzt sind weiterhin 
nutzen. Zumindest solange die Zeichen der BMP ausreichen - das heißt solange 
Sie keine der neuen Unicode-Zeichen verwenden.

Wenn Sie eine vollständige Unicode-Unterstützung benötigen, kann die Verwendung 
der alten Methoden zu versteckten Fehlern führen.

> Ein sehr populäres Beispiel für Unicode-Zeichen, die nicht im BMP 
enthalten sind sind Emojis: Das einfache lachende Gesicht 😀 
[U + 1F600](https://unicode-table.com/de/#1F600)
kann nicht in einem einzelnen Zeichen dargestellt werden.

Was ich genau mit versteckten Fehler meine, verdeutlicht der nachfolgende 
Programmcode. Als Beispiel habe ich das Leerzeichen und das Emoji mit dem 
lachenden Gesicht gegenübergestellt. 
Die Unicode-Nummer des Emoji mit dem 
lachenden Gesicht ist `U+1F600` und der HTML-Code dazu 
ist `&#128512;`. 
Die Unicode-Nummer das Ausrufezeichen ist `U+0021` und der HTML-Code dazu 
ist `&#33;`.

``` 
let text = "😀";
console.log(text.length); // Ausgabe: 2
console.log(/^.$/.test(text)); // Ausgabe: false
console.log(text.charAt(0)); // Ausgabe: �
console.log(text.charAt(1)); // Ausgabe: �
console.log(text.charCodeAt(0)); // Ausgabe: 55357
console.log(text.charCodeAt(1)); // Ausgabe: 56832

text = "!";
console.log(text.length); // Ausgabe: 1
console.log(/^.$/.test(text)); // Ausgabe: true
console.log(text.charAt(0)); // Ausgabe: "!"
console.log(text.charAt(1)); // Ausgabe: ""
console.log(text.charCodeAt(0)); // Ausgabe: 33
console.log(text.charCodeAt(1)); // Ausgabe: NaN
<!--index_980.html -->
```

Es wird kein Fehler angezeigt, aber anders als erwartet  
- gibt `text.length` für das lachende Gesicht den Wert 2 anstelle von 1 zurück.
- wird das lachende Gesicht beim der Prüfung eines Regulären Ausdrucks nicht 
als ein Zeichen erkannt.
- es der `charAt()`-Methode nicht möglich ein Zeichen zurückzugeben.
- gibt die `charCodeAt()`-Methode für jedes der beiden Zeichen in der UTF-16-Codeeinheit 
das Unicode-Zeichen für die BMP aus. 

Falls Sie mit Unicode-Zeichen oberhalb der BMP arbeiten sind die Methoden 
`charAt()` und `charCodeAt()` nicht die richtige Wahl für Sie. Diese arbeiten 
ausschließlich im BMP-Bereich korrekt. Und noch schlimmer: Bei Unicode-Zeichen 
außerhalb der BMP melden diese keinen Fehler.  

Mit ECMAScript 6 sind 
Methoden hinzugekommen, die den neuen Bereich korrekt unterstützen. 

> Die Unicode-Nummer ist ein hexadezimaler Wert. Der HTML-Code ist die 
ins Dezimalsystem umgerechnete Unicode-Nummer.
Möchten Sie das Umrechnen von einem Zahlenformat in ein anderes Zahlenformat 
gerne selbst 
nachvollziehen. Falls Sie hierzu Hilfe benötigen ist die Website  
https://www.arndt-bruenner.de/mathe/scripts/Zahlensysteme.htm vielleicht das 
Richtige für Sie.

### codePointAt()

Eine Methode, eine vollständige Unicode-Unterstützung bietet ist `codePointAt()`

``` 
let text = "😀";
console.log(text.codePointAt(0)); // Ausgabe: 128512
console.log(text.codePointAt(1)); // Ausgabe: 56832

text = "!";
console.log(text.codePointAt(0)); // Ausgabe: 33
console.log(text.codePointAt(1)); // Ausgabe: undefined
<!--index_979.html -->
```

Noch einmal zur Wiederholung: Die Unicode-Nummer des Emoji mit dem 
lachenden Gesicht ist `U+1F600` und der HTML-Code dazu 
ist `&#128512;`. 
Die Unicode-Nummer das Ausrufezeichen ist `U+0021` und der HTML-Code dazu 
ist `&#33;`. `codePointAt(0)` gibt nun also in beiden Fällen denn korrekten Wert 
zurück.

> Bei der verwendung der `codePointAt()`-Method ist allerdings noch wichtig 
darauf zu achten, das auch hier die UTF-16-Codeeinheit zürckgegeben wird - also 
zwei Unicode-Zeichen. Sehen sich zur verdeutlichung nachfolgenden Programmcode an.

```
let text = "😀!";
console.log(text.codePointAt(0)); // Ausgabe: 128512
console.log(text.codePointAt(1)); // Ausgabe: 56832
console.log(text.codePointAt(2)); // Ausgabe: 33
console.log(text.codePointAt(1)); // Ausgabe: undefined
<!--index_979a.html -->
```

> Wenn Sie herausfinden möchten, ob Sie es mit einem Unicode-Zeichen oder einer 
UTF-16-Codeeinheit zu tun haben, können Sie die Methode `codePointAt(0)` zu Hilfe 
nehmen. Eine Möglichkeit zeigt Ihnen das nächste Codebeispiel.
```
console.log(is32Bit("😅")); // Ausgabe: true
console.log(is32Bit("!"));  // Ausgabe: false
function is32Bit(c){
    return c.codePointAt(0) > 0xFFFF;
}
<!--index_978.html -->
```

### String.fromCodePoint()

Im vorhergehenden Kapitel haben wir HTML-Code eines Zeichens ermittelt. In 
diesem Kapitel machen wir das Gegenteil. Bisher war für die Errechnung eines 
Zeichens aus einem HTML-Code die Methode 
`fromCharCode()` das Mittel der Wahl. Genau wie `charCodeAt()` deckt `fromCharCode()` 
außschließlich den BMP-Bereich korrekt ab. Analog zu `codePointAt()` 
für `charCodeAt()` gibt es die fromCodePoint()-Methode als Pentant zu 
`fromCharCode()`. `fromCodePoint()` bietet das gleiche Ergebnis 
wie `fromCharCode()` bei einer vollständige Unicode-Unterstützung.



| BMP-Bereich   | vollständige Unicode-Unterstützung |
| ------------- | ------------- |
| fromCharCode()| fromCodePoint() |
| charCodeAt()| codePointAt() |



### normalize()
### u-Flag
## Andere String-Verbesserungen
### Identifizieren
### Ersetzen
## Andere Verbesserungen bei der Arbeite mit Regulären Ausdrücken
### y-Flag
### Duplizieren
### Flag-Eigenschaften 
## Templates
### Syntax
### Multiline
### Ersetzungen
### Tagged




```
console.log(window.RegExp); // Ausgabe: function RegExp()
let RegExp = "Neuer Wert für RegExp";
console.log(window.RegExp); // Ausgabe: function RegExp()
<!--index_981.html -->
```

> **Achtung:**


## In diesem Kapitel haben wir ...

xxx

[^1]: https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640 (https://bit.ly/2GT9nQS)

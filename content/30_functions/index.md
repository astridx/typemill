# ECMAScript 6 - Funktionen
[](#){#Funktionen}


## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 
Todo Meldungen immer mit Firefox

## Standardwerte
### ECMAScript 5


```
function standardwert(variable1, timeout){
timeout = timeout || 1000;
...
}
```

```

<!--index_963.html -->
```

### ECMAScript 6

ECMAScript 6 vereinfacht die die Zuweisung eines Standardwertes. Zusätzlich 
ist diese Art der Zuweisung übersichtlicher.

```

<!--index_962.html -->
```

Imn nächsten Beispiel wird Standardparameter gesetzt.

```

<!--index_961.html -->
```

### Auswirkungen auf Arguments Objekt



```

<!--index_960.html -->
```

> Mit ECMAScript 5 wurde der strict mode eingeführt, welcher inzwischen 
in allen gängigen Web-Browsern - inklusive dem  IE10 - implementiert wurde. 
Es ist einfach, im Web-Browser zum *Strict mode* zu 
wechseln - es genügt, die Zeile `"use strict";` am Anfang des 
Quellcodes hinzufügen. 
Der strikte Modus ist eine 
Möglichkeit, sich für eine eingeschränkte Variante von JavaScript 
zu entscheiden. Hierdurch wird der *Sloppy Mode (schlampige Modus)* 
deaktiviert. *Sloppy Mode* ist der inoffizielle Name des 
Standardmodus von ECMAScript 5.
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Strict_mode

```

<!--index_960a.html -->
```

Wenn ein Standardparameter gesetzt wird, wir automatisch in den strict mode 
geschaltet.


```

<!--index_959.html -->
```

### Expressions

Sie können mithilfe einer Funktion einen Standardwert 
setzen. Dies ist meiner Meinung nach eine der spannendsten neuen 
Möglichkeiten.

```

<!--index_958.html -->
```

So ist es möglich, einen Wert zu unterschiedliche Zeiten unterschiedlich 
zu setzten.

```

<!--index_958a.html -->
```

Dies ist die Überleitung zu einer anderen sinnvollen Fähigkeit. Sie können 
einen eine Variable standardmäßig mit dem aktuellen Wert einer anderen Variable 
belegen.

```

<!--index_958b.html -->
```

Weitergedacht
```

<!--index_958c.html -->
```


Das geht nicht 

```

<!--index_958d.html -->
```

### TDZ

Die TDZ war im ersten Kapitel im Zusammenhang mit `let` und `const` schon einmal 
Thema.

958c aus Sicht des JavaScript Compilers

```

<!--index_957.html -->
```

958d aus Sicht des JavaScript Compilers

```

<!--index_956.html -->
```

## Unnamed functions

In den bisherigen Beispielen sind nur Funktionsparameter vorgekommen, die 
mit einem Namen in der Funktions-Signatur eingefügt wurden.

> Typisch für eine Funktion ist die sogenannte Signatur oder Schnittstelle. 
Darunter versteht man die genaue Art und Weise, mit der die Funktion 
aufgerufen wird. 
`Todo funktion einfügen`
Die Signatur der Funktion ist die oberste Zeile. Früher sagte man auch 
*Funktionskopf*. Viele Informatiker bezeichnen die oberste Zeile auch 
als *Interface* oder auf Deutsch *Schnittstelle*.

Schon in ECMAScript 5 war es möglich mit optionalen Parametern zu arbeiten. 
ECMAScript 6 macht das Arbeiten mit optionalen Parametern einfacher.

### ECMAScript 5

Optionale Parameter in ECMAScript 5

```

<!--index_955.html -->
```

### Rest Parameter

Was ist Rest Parameter? 

```

<!--index_954.html -->
```


#### Beschränkungen
Es darf nur einen geben und er muss an letzter Stelle stehen.


```

<!--index_953a.html -->
```

In einer Setter Methode ist ein Rest Parameter nicht möglich.

```

<!--index_953b.html -->
```

#### Auswirkungen auf das arguments-Objekt

## Konstruktor

##Spread Operator

## Name Eigenschaft
### Passende Namen wählen
### Spezielle Fälle

## Gründe für Funktionen
### ECMAScript 5
### new.target

## Block Leven Funktionen
### Wann verwenden
### Non Strict Mode

## Arrow Funktions
### Syntax
### Erstelle IIFE
### No this Binding
### Arrays
### No arguments binding
### Identify Arrow Functions

## Tail Call Optimierung
### ECMAScript 6
### Wie verwenden













```

<!--index_964.html -->
```




> **Achtung:**


## In diesem Kapitel haben wir ...

xxx

[^1]: https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640 (https://bit.ly/2GT9nQS)

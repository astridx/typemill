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

> Der Operator ... besitzt zwei grundsätzlich verschiedene Bedeutungen. 
Abhängig davon, in welchem Kontext er notiert wird, dient er entweder als 
Rest-Operator oder als Spread-Operator. 
Der erstgenannte Rest-Operator kann zur Erstellung von Restparametern 
genutzt werden.
https://wiki.selfhtml.org/wiki/JavaScript/Operatoren/Rest-_oder_Spread-Operator
Mithilfe eines Restparameters kann man beliebig viele 
Parameter als Array empfangen.
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Functions/rest_parameter

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

> Das arguments-Objekt ist ein Array-ähnliches Objekt, das auf 
die übergebenen Parameter einer Funktion verweist. 
Das arguments-Objekt ist eine lokal verfügbare Variable in allen 
(Nicht-Pfeil-) Funktionen. Man kann auf die Parameter einer Funktion 
referenzieren, wenn man in einer Funktion das arguments-Objekt benutzt. 
Dieses Objekt enthält einen Eintrag für jeden übergebenen Parameter 
der Funktion. Der erste Eintrag beginnt beim Index 0. 
Wenn einer Funktion drei Parameter übergeben werden, kann wie folgt auf 
diese zugegriffen werden;

```
arguments[0]
arguments[1]
arguments[2]
```
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Functions/arguments

Das arguments-Objekt spiegelt das Rest Objekt wider.

```

<!--index_952.html -->
```

## Konstruktor

Der `Function`-Konstruktor erstellt ein neues Funktions-Objekt. 
Dieser Konstruktor wird in der Praxis selten verwendet. 
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Function

Der folgende Code erstellt ein Funktions-Objekt, mit zwei Parametern. 
Die Parameter `variable1` und `variable2` sind formale Parameternamen, 
welche im Funktionskörper genutzt werden, `return variable1 + variable2`.

```

<!--index_951.html -->
```

> Es gibt oft Verwirrung zwischen den Begriffen Parameter und Argumente. 
Dabei ist es ganz einfach: Die Werte, die man beim Aufruf an eine 
Funktion übergibt, sind die Argumente. Die Variablen, in denen 
die Argumente dann innerhalb der Funktion zur Verfügung stehen, sind 
die Parameter. https://wiki.selfhtml.org/index.php?title=JavaScript/Funktion&oldid=59542

Mit ECMAScript 6 ist es möglich, im `Function`-Konstruktor Standardwerte für 
einen Paramameter zu setzten.

```
ECMAScript 6 ünterstützt Rest Parameter

<!--index_951a.html -->
```


```

<!--index_951b.html -->
```

##Spread Operator

> Der Operator ... besitzt zwei grundsätzlich verschiedene Bedeutungen. 
Abhängig davon, in welchem Kontext er notiert wird, dient er entweder als 
Rest-Operator oder als Spread-Operator. Mit dem Spread-Operator 
ist es möglich, die Elemente eines iterierbaren Objektes in ein Array 
oder eine Liste mit Argumenten einzufügen. 
https://wiki.selfhtml.org/wiki/JavaScript/Operatoren/Rest-_oder_Spread-Operator

Ich bin ein großer Fan des Spread-Operators. Im Folgenden finden Sie 
eines meiner bevorzugten 
Verwendungen des Spread-Operators in JavaScript! Weitere Beispiel 
können Sie bei https://davidwalsh.name/spread-operator nachlesen.

Bis ECMAScript 5 haben wir die Function.prototype.apply aufgerufen, 
indem wir ein Array von Argumenten übergeben, um eine Funktion mit einem 
gegebenen Satz von Parametern in einem Array aufzurufen.

```

<!--index_950.html -->
```

Mithilfe des Spread-Operators können wir die Verwendung der Funktion 
apply() vermeiden und die eigentliche Funktion mit 
dem Array aufrufen. Wir fügen nur vor das Array den Spread-Operator ein - also die 
drei Punkte.

```

<!--index_950a.html -->
```

Der Spread-Operator kann mit anderen Parametern gemischt werden.
```

<!--index_950b.html -->
```

## Spezialfall: Die Eigenschaft Name

Es ist einfach Funktionen in JavaScript allen Funktionen einen guten Namen 
zu geben. ECMAScript 6 geht noch einen Schritt weiter. Seit ECMAScript 6 
ist sichergestellt, dass alle Funktionen einen Namen haben. 
 
### Passende Namen wählen

```

<!--index_949.html -->
```

### Spezielle Fälle

getter, funktion in Variable, ...
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Function/name

```

<!--index_949a.html -->  passt nicht zur Erklärgun
```

bind und anonym

```

<!--index_949b.html -->  passt nicht zur Erklärgun
```




> Jede Funktion besitzt eine bind() Methode. Mit dieser können wir unserer 
Funktion einen neuen Kontext zuweisen. 
Der erste Parameter fungiert als neuer Kontext "this". 
Zusätzlich können weitere Parameter übergeben werden diese werden an die 
Funktion weitergereicht. Sehr wichtig: Die bind() methode ruft die 
Funktion nicht auf, sondern erzeugt eine neue Funktion.
https://alexandernaumov.de/artikel/javascript-apply-call-bind-unterschied
```
<!--index_949b.html -->  exkurs bind
```

## Gründe für Funktionen
### ECMAScript 5
### new.target

## Block Level Funktionen
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

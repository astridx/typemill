# ECMAScript 6 - Destrukturierende Zuweisung
[](#){#DestrukturierendeZuweisung}


## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 
Todo Meldungen immer mit Firefox

## Warum Destrukturieren



Die destrukturierende Zuweisung ermöglicht es, Daten aus Arrays oder Objekten 
zu extrahieren, und zwar mit Hilfe einer Syntax, die der Konstruktion von 
Array- und Objekt-Literalen nachempfunden ist.
https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Operators/Destrukturierende_Zuweisung

Mit ECMAScript 5 musste oft viel doppelter Text geschrieben werden.

```
let farben = { 
rot: "#FF0000",
gruen: "#00FF00",
blau: "#0000FF"
};
let rot = farben.rot;
let gruen = farben.gruen;
let blau = farben.blau;

console.log(rot);
console.log(gruen);
console.log(blau);
<!--index_926.html -->
```

## Objekt Strukturierung

Anstelle von 

```
let rot = farben.rot;
let gruen = farben.gruen;
let blau = farben.blau;
```

reicht mit ECMAScript 6 die Zeile

```
let {rot, gruen, blau} = farben;
```

```
let farben = { 
rot: "#FF0000",
gruen: "#00FF00",
blau: "#0000FF"
};
let {rot, gruen, blau} = farben;

console.log(rot);
console.log(gruen);
console.log(blau);
<!--index_926a.html -->
```


> Initialisieren nicht vergessen!

```
...
let {rot, gruen, blau}; 
// Ausgabe: SyntaxError: missing = in destructuring declaration
<!--index_926b.html -->
```

### Zuweisung

Nicht nur bei der Initialisierung eines Objektes gibt es Verbesserungen. Auch 
die Zuweisung eines Wertes zu einer Eigenschaft ist mit 
ECMAScript 6 unkomplizierter. 

```
<!--index_925.html -->
```

Das geht auch in einer Funktion.

```
<!--index_925b.html -->
```

> Achtung: Es gibt einen Fehler, wenn die Zuweisung einmal `null` ist.

### Standardwerte

Manchmal kommt es vor, dass ein Wert nicht bestimmt ist. Deshalb ist es gut, 
dass bei auch bei destrukturierender Zuweisung mit Standardwerten arbeiten kann. 

Ohne einen Standardwert anzugeben würde eine Variable nicht definiert werden.

```

<!--index_924.html -->
```

Mit Standardwerten kann man dieses Problem umgehen - wie das geht zeigt das 
nächste Beispiel.

```
let farben = { 
rot: "#FF0000",
gruen: "#00FF00",
};

let {rot = "#FF1111", gruen = "#1111FF", blau = "#0000FF"} = farben;

console.log(rot); // Ausgabe: #FF0000
console.log(gruen); // Ausgabe: #00FF00
console.log(blau); // Ausgabe: undefined
<!--index_924a.html -->
```


### Lokale Variablen

Bisher waren beim destrukturieren die korrespondierenden 
Variablennamen immer gleich. Das kann aber auch einmal anders sein. Die 
Namen können abweichen. Deshalb ist es gut, dass es hierfür eine Lösung in der 
Syntax gibt.


```

<!--index_923.html -->
```

Und lokalen Variblen önnen Sie auch in Verbindung mit Standardvariablen 
einsetzen. Sehen Sie sich dazu das nachfolgende Beispiel an.


```

<!--index_923a.html -->

### Verschachtelungen

```

<!--index_922.html -->

## Array Strukturierung
### Zuweisung
### Standardwerte
### Lokale Variablen
### Rest Items
## Gemischte Strukturierung
## Parameter Strukturierung
### Notwendige Parameter
### Standardwerte



```

<!--index_963.html -->
```



```

<!--index_964.html -->
```




> **Achtung:**


## In diesem Kapitel haben wir ...

xxx

[^1]: https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640 (https://bit.ly/2GT9nQS)

todo https://github.com/woota/FE-training-examples/blob/master/es6/4.%20Arrow-Functions.md
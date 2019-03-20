# ECMAScript 6 - Strukturierung
[](#){#Strukturierung}


## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 
Todo Meldungen immer mit Firefox

## Warum Strukturieren

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


## Objekt Strukturierung
### Zuweisung
### Standardwerte
### Lokale Variablen
### Verschachtelungen
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
# ECMAScript 6 - Symbole
[](#){#Symbole}


## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 
Todo Meldungen immer mit Firefox

## Symbole erstellen

In JavaScript handelt es sich bei einem primitiven (skalares) Datenelement 
um Daten, die kein Objekt sind und keine Methoden haben. 
Es gibt 6 primitive Datentypen: String, Number, Boolean, Null, undefined, 
Symbol (neu in ECMAScript 2015). https://developer.mozilla.org/en-US/docs/Glossary/Primitive
Meistens wird ein primitiver Wert direkt auf der untersten Ebene der 
Sprachimplementierung dargestellt. 
Alle Grundelemente sind unveränderlich, d. H. Sie können nicht geändert werden. 
Es ist wichtig, ein Primitiv selbst nicht mit einer einen Primitivwert 
zugewiesenen Variablen zu verwechseln. 
Der Variablen kann ein neuer Wert zugewiesen werden, der vorhandene 
Wert kann jedoch nicht auf die Art und Weise geändert werden, 
auf die Objekte, Arrays und Funktionen geändert werden können.

> Ein primitives (skalares) Datenelement (einfacher Wert, einfacher Datentyp) 
ist ein Datenelement, das kein Objekt ist und keine Methoden besitzt.
In JavaScript gibt es 6 skalare Datentypen:
    String
    Number
    Boolean
    null
    undefined
    Symbol (neu in ECMAScript 6)
Meistens repräsentiert ein skalares Datenelement die einfachste Datenstruktur einer Programmiersprache.
Alle skalaren Datentypen sind unveränderbar (sie können nicht noch weiter vereinfacht werden).
https://developer.mozilla.org/de/docs/Glossary/einfache_datenelemente




```
let vorname = Symbol();
let person = {};
person[vorname] = "Astrid";
console.log(person[vorname]); //Ausgabe: Astrid
<!--index_913.html -->
```


## Symbole erstellen
## Symbole anwenden
## Symbole teilen
## Symbolezwand
## Eigenschaften von Symbolen
## Internen Operationen mit bekannten Symbolen
http://2ality.com/2015/09/well-known-symbols-es6.html




```
<!--index_912.html -->
```



> **Achtung:**


## In diesem Kapitel haben wir ...

xxx

[^1]: https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640 (https://bit.ly/2GT9nQS)

todo https://github.com/woota/FE-training-examples/blob/master/es6/4.%20Arrow-Functions.md
# ECMAScript 6 - Gültigkeitsbereiche von Variablen
[](#){#GueltigkeitsbereicheVonVariablen}

https://de.wikipedia.org/w/index.php?title=JavaScript&oldid=184218223#Versionsgeschichte_von_ECMAScript_(ECMA-262)  

## In diesem Kapitel werden wir …
Zunächst zeige ich Ihnen, wie Sie 

## var - Deklaration und Hoisting

https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/var#var_hoisting
todo was ist deklaration

Die Deklartion einer Variablen erfolgt immer 
- im globalen Kontekt falls die Variable außerhalb einer Funktion deklariert wurde oder 
- ganz am Anfang einer Funktion.  
 
Konkret bedeutet das, dass das Deklarieren einer Variable irgendwo im Programmcode 
das gleiche ist, als würde sie am Anfang deklariert werden. Eine Variable 
kann somit genutzt werden, bevor sie im Programmcode deklariert wurde. 
Dies nennt man `hoisting`.  

> Exkurs: Der Unterschied zwischen instanziieren, deklarieren und initialisieren  
Variable instanzieren:  
Der Begriff Instanziierung meint das Erzeugen eines neuen Objekts, 
also einer Instanz, aus einer Klasse.
``` 
Objekt value = new Objekt();
// value ist Instanz der Klasse Objekt
```
Variable deklarieren:  
Unter deklarieren einer Variable können Sie sich das erste *Erwähnen der Variable* 
vorstellen. So weiß der Compiler, dass es die Variable gibt und kann sie ansprechen. 
Der Wert selbst wird bei der Deklaration nicht festgelegt.
```
int value;
// value als Variable des Typs int deklariert
```
Variable initialisieren:  
Eine Initialisierung ist das erste Zuweisen eines Wertes zu einer Variablen.
```
value = 0;
// value mit Wert 0 initialisiert
```

Sehen wir uns `hoisting` an einem Beispiel genauer an.

### Beispiele

#### Beispiel 1

Sehen Sie sich die nachfolgende Funktion einmal kurz an. 

```
function getValue() {
    if (false) {
        var value = "Prima";
        return value;
    } else {
        return value; // gibt "undefined" oder "" aus, abhängig vom Browser.
    }
}
<!--index_999a.html-->
```

Wenn Sie noch nicht vertraut mit JavaScript sind, erwarten Sie vielleicht, dass die 
Variable `value` nur erstellt wird, wenn die Bedingung in der 
`if`-Anweisung `true` ist. In der Realtiät ist es aber so, dass die Variable 
auf alle Fälle erstellt wird.

Im Hintergrund verändert JavaScipt den Programmcode nämlich. Der 
[Interpreter](https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640) macht 
daraus konkret den folgenden Aufruf. 
Die wesentliche Zeile habe ich mit einem Stern markiert.

```
 function getValue() {
*    var value;
     if (false) {
         var value = "Prima";
         return value;
     } else {
         return value; // gibt "undefined" oder "" aus, abhängig vom Browser.
     }
     // die Variable value existiert auch hier
 }
<!--index_999a.html aus Sicht des Interpeters-->
```

Die Deklaration der Variablen `value` wird an den Anfang der Funktion verschoben. 
Und die Initialisierung erfolgt im gleichen Gültigkeitsbereich. Dadurch kann im 
`else`-Block auf die Variablen `value` zugegriffen werden. Da die Variablen `value` im 
`else`-Block mit keinem Wert belegt ist, gibt sie bei einem Zugriff `undefined` 
anstelle von `ReferenceError: myvalue is not defined` aus. 

```
 function getValue() {
     if (false) {
         var value = "Prima";
         return value;
     } else {
*        return myvalue; // gibt "ReferenceError: myvalue is not defined" aus
     }
 }
<!--index_999c.html -->
```

`Hoisting` führt sehr oft zu Missverständnissen. Für viele Entwickler ist es 
befremdend, dass eine Variable nicht an der Stelle erstellt wird, an der sie im 
Programmcode steht. Wahrscheinlich wurde deshalb mit ECMAScript 6 
die Möglichkeit eingeführt, 
Variablen im Gültigkeitsbereich des lokalen Blocks zu deklarieren.

https://www.mediaevent.de/javascript/globale-lokale-variablen.html

## Gültigkeitsbereich (Scope) im Block

In vielen Programmiersprachen gibt es den Block Scope – alle Variablen, 
die innerhalb eines Blocks deklariert werden, gelten nur innerhalb dieses Blocks. 
Diese Variablen sind lokale Variablen.

Was genau ist ein Block? Ein Block ist entweder 
- der Bereich innerhalb einer Funktion oder
- ein Bereich der mit geschweiften Klammern - `{` und `}` - umgeben ist. 

Variablen, die mit `let` oder `const` angelegt werden, gelten nur innerhalb 
ihres Blocks. Das klingt unbequem. Es verhindert aber viele schwer 
aufzudeckende Fehler. 

### Block Scope mit let

Mit ECMAScript 6 ist `let` für die Deklaration von Variablen hinzugekommen. 
Eine mit `let` deklarierte Variable hat einen eingeschränkten Gültigkeitsbereich. 
Sie ist nur innerhalb des Blocks, in dem sie deklariert wurden, gültig. 

Die Deklaration einer Variablen mit `let` erfolgt auf die gleiche Art 
wie die Deklaration einer Variablen mit `var`. Was wäre, wenn die Variable im 
vorherigen Beispiel anstelle von var mit let deklariert worden wäre? Genau dies 
zeigt Ihnend das nachfolgende Beispiel.

```
 function getValue() {
     if (true) {
         let value = "Prima";
     } else {
*        return value; // Würde "ReferenceError: value is not defined" ausgeben.
     }
*    return value; // Gibt "ReferenceError: value is not defined" aus.
}
<!--index_998d.html -->
```

todo innerhalb ist aber möglich


Wenn sie den Programmcode nachvollzogen haben, stimmen Sie sicher mit mir überein, 
das die Ausgabe der Datei `998d.html` eher den Erwartungen entspricht, als die Ausgabe 
der Datei `999a.html`. Weil wir die Variable `value` mit `let` deklariert haben, 
wird die Deklaration nicht im Hintergrund vom Interpeter an den Anfang der 
Funktion verschoben. Ein Zugriff auf die Variable `value` ist nun außerhalb 
der `if`-Anweisung nicht möglich. Da die Variable `value` nur deklariert wird, 
wenn die Bedingung der `if`-Anweisung erfüllt ist, kann auch im `else`-Block 
nicht auf diese zugegriffen werden.

### Keine Mehrfachverwendung

Die Mehrfachverwendung einer mit `let` deklarierten 
Variablen innerhalb eines Blocks ist nicht möglich. Falls Sie dies versehentlich 
doch tun, wird der JavaScript Interpreter Ihnen den Fehler 
`SyntaxError: redeclaration of let value` melden.

```
 function getValue() {
     var value = "Prima";
*    let value = "Prima";  // SyntaxError: redeclaration of let value
 }
<!--index_997.html -->
```

Im vorhergehenden Beispiel wurde die Variable `value` zweimal deklariert. Einmal 
mit `var` und einmal mit `let`. Weil diese beiden Variablen im selben 
Gültigkeitsbereich deklariert wurden, tritt ein Fehler auf. 

Im Umkehrschluss ist es möglich, eine Variable mit dem gleichen Namen in einem 
untergeordneten Gültigkeitsbereich zu deklarieren.

```
 function getValue() {
     var value = "Prima";
     if (true) {
*        let value = "Prima";
     return true;
 }
<!--index_997c.html -->
```

Im Beispiel der Datei `997c.html` tritt kein Fehler auf. Die Variable `value` 
wird in der `if`-Anweisung neu deklariert. Die Deklaration erfolgt genau 
an der Stelle, an der der Programmierer sie in den Programmcode einfügt. 
Die Deklaration wird also nicht wie 
im Falle von `var`, an den Beginn des umgebenden Blocks gesetzt. 

### Block Scope mit const

Die Deklaration einer Variablen mit `const` erstellt eine Konstante. 
Der Gültigkeitsbereich einer mit `const` deklarierten Variablen ist, 
genau wie bei einer mit `let` deklarierten Variable, auf den lokalen Block begrenzt. 
Der Wert einer Konstanten muss bei der Deklaration initialisiert werden und 
kann nicht verändert werden.

```
function getValue() {
    const value1 = "Prima";
    const value2; // SyntaxError: missing = in const declaration
}
<!--index_996.html -->
```

Im vorherigen Beispiel wird die Variable `value1` korrekt deklariert und initialisiert. 
Die Deklaration der Variable `value2` ist nicht möglich. Hier wird ein Fehler 
angezeigt, weil `value2` beim Anlegen nicht initialisiert wurde.

#### const versus let

Genau wie im Falle von `let` ist eine mit `const` deklarierte Variable ausschießlich 
innerhalb eines Blocks gültig. 

```
 function getValue() {
     if (true) {
*        const value = "Prima";
     }   
     return value; //ReferenceError: value is not defined
 }
<!--index_995.html -->
```

Eine weitere Gemeinsamkeit von `let` und `const` ist die nicht mögliche 
Mehrfachverwendung.

```
 function getValue() {
     var value1 = "Prima";
     let value2 = "Super";
*    const value1 = "Prima"; // SyntaxError: redeclaration of var value1
*    const value2 = "Super"; // SyntaxError: redeclaration of var value2
     return true;
 }
<!--index_994.html -->
```

Abgesehen von diesen Gemeinsamkeiten gibt es einen bedeutenden Unterschied. Anders 
als bei einer mit `let` deklarierten Variablen kann der Wert einer Konstanten 
im Nachhinein nicht geändert werden.

```
 function getValue() {
     let value1 = "Prima";
     const value2 = "Super";
     value1 = "Toll";
*    value2 = "Schön"; // TypeError: invalid assignment to const `value2'
     return true;
 }
<!--index_993.html -->
```
todo Ausgaben sidn vom Browser abhängig.

#### const und Objekte

Erklärungsbedürftig ist die Behandlung von Konstanten in JavaScript. Wenn ein 
Objekt als Konstante deklariert wurde, dann ist nur das Objekt selbst konstant. 
Die Eigenschaften des Objektes können verändert werden.

```
function getValue() {
    const stadt = {
        name: "Koblenz"
    }
    stadt.name = "Bonn"; // Mögliche Neuzuweisung
    stadt.fluss = "Rhein"; // Mögliche Neuzuweisung
    
    const stadt = { // SyntaxError: redeclaration of const stadt
        name: "Bonn" 
    } 
    return true;
}
<!--index_992.html -->
```

### Die vorübergehend tote Zone

Variablen, die mit `let` oder `const` angelegt werden, gelten nur innerhalb 
ihres Blocks. Dies führt in JavaScript zu einem Zustand der sich gefährlich 
anhört: *Der vorübergehend toten Zone*. Der englische Ausdruck dafür ist 
*Temporal Dead Zone (TDZ)*. In der *vorübergehend toten Zone* tritt beim Zugriff 
auf eine deklarierte Variable, ein Fehler auf. Verhängnisvoll ist, dass 
dieser Fehler auch dann auftritt, wenn eine vermeintlich sichere 
Methode wie `typeof` verwendet wird.

```
 function getValue() {
     console.log(typeof value1); // Ausgabe: undefined
*    console.log(typeof value2); // ReferenceError: can't access lexical declaration
                                 // `value2' before initialization
     let value2 = "Prima"; 
    return true;
}
<!--index_991.html -->
```

In vorhergehenden Beispiel wird auf die Variablen `value1` und 
`value2` mithilfe von `typeof` 
zugegriffen. Im Falle von `value1` ist dies auch kein Problem. Bei `value2` 
tritt hingegen ein Fehler auf, weil `value2` im später gleichen 
Gültigkeitsbereich mit `let` deklariert wird. Die gleiche Deklaration in einem 
anderen Gültigkeitsbereich 
wäre kein Problem.

> Die *Temporal Dead Zone (TDZ)* wurde in der Spezifikation *ECMAScript 6* 
nicht explizit erwähnt. Der Begriff wird aber häufig zur Erklärung eingesetzt. Die 
TDZ entsteht, weil der JavaScript Interpreter sich eine Block beim Einlesen vollständig 
ansieht. Wenn er eine mit `var` deklarierte Variable findet, dann setzt er die 
Deklaration an den Beginn der Funktion oder in den globalen Gültigkeitsbereich. Findet 
der Interpreter eine mit `let` oder `const` deklarierte Variable, dann setzt er diese 
in die TDZ - solange, bis die eigenliche Deklaration erfolgt.


> Die Beispiele zur TDZ verwenden hier mithilfe von `let` deklarierte Variablen. Das 
Gleiche gilt aber auch für Variablen, die mit `const` deklariert wurden.

```
function getValue() {
     console.log(typeof value); // Ausgabe: undefined
*    if (true) {
*        let value = "Prima";
*        console.log(typeof value); // Ausgabe: String
*    }
     console.log(typeof value); // Ausgabe: undefined
     return true;
 }
<!--index_991a.html -->
```

Die Variable `value2` befindet sich nicht in der TDZ wenn der Befehl 
`console.log(typeof value)` ausgeführt wird. Das bedeutet konkret, dass die Variable 
frei aber tatsächlich `undefinded` ist.

## Gültigkeitsbereich (Scope) in Schleifen

Eine weitere Besonderheit von JavaScript ist der Gültigkeitsbereich bei 
Schleifen. Beim Druchlaufen 
von Schleifen bringt es viele Vorteile wenn die Gültikeitesbereiche der Variablen 
übersichtlich und getrennt sind. In einer Schleife wird häufig ein Zähler 
verwendet. Das nächste Beispiel zeigt Ihnen, dass der Gültigkeitsbereich einer 
solchen Zählervariablen nicht übersichtlich und getrennt ist, wenn diese Variable 
mit `var` deklariert wurde. 

```
 function getValue() {
     for (var i = 0; i < 5; i++) {
         // tue etwas ...
     }
*    console.log(i); // Ausgabe: 5
     return true;
 }
<!--index_990.html -->
```

Auch nachdem der Schleifendurchlauf abgeschlossen ist und der Block verlassen wurde, 
ist die Variable `i` noch gültig. Der letzte Wert der Variablen wird mittels 
`console.log(i)` ausgegeben. Dies ist ein Verhalten, das nicht erwünscht ist. Die 
Variable `i` wird in der Regel nur lokal in der Schleife benötigt und sollte auch 
nur hier ihren Gültigkeitsbereich haben. Bei der Verwendung von `var` zur Deklaration 
wird diese Deklaration aufgrund von 
[Hoisting](https://de.wikipedia.org/w/index.php?title=Hoisting&oldid=166784898) 
nach oben geschoben.

Das nächste Beispiel nutzt anstelle von `var` eine mit `let` deklarierte Variabel als 
Zähler. Das Ergebnis ist das erwartete Verhalten.

```
 function getValue() {
     for (let i = 0; i < 5; i++) {
         console.log(i); // Ausgabe: 0 1 2 3 4
     }
*    console.log(i); // ReferenceError: i is not defined
     return true;
 }
<!--index_989.html -->
```

Das Beispiel der Datei `index_989.html` demonstriert das gewünschte Verhalten. Die 
Variable `i` existiert nur innerhalb der Schleife. Nachdem die Schleife abgearbeitet 
ist, kann auf die Variable `i` nicht mehr zugegriffen werden. Die Variable `i` kann  
keine Verwirrung mehr stiften.

### Funktionen in Schleifen

Hoisting und das Verhalten von `var` machend das Arbeiten mit Funktionen in Schleifen 
problematisch. Das nächste Beispiel zeigt Ihnen, was ich genau meine.

```
function getValue() {
    var funktionen = [];
    for (var i = 0; i < 5; i++) {
        funktionen.push(function() {
            console.log(i);
        });
    }
    funktionen.forEach(function(funktion){
        funktion(); // Ausgabe: Fünfmal die Nummer "5"
    });
    return true;
}
<!--index_988.html -->
```

Sicherlich haben Sie die Ausgabe `0 1 2 3 4` erwartet. Anstelle davon wurde aber
`5 5 5 5 5` ausgegeben. Der Grund hierfür ist, dass dieselbe Variable `i` über alle 
Iterationen der Schleife hinweg geteilt wird. Aufgrund von Hoisting wurde 
die Variable `i` außerhalb der Schleife deklariert. Alle Funktionen, die in der 
Schleife erstellt wurden, halten eine Referenz auf die selbe Variable `i`. 
Diese Variable `i` hat den Wert `5`, wenn alle Schleifendurchläufe beendet sind. 
Wenn `console.log(i)` aufgrund von 

```
funktionen.forEach(function(funktion){
    funktion(); 
});
```
fünfmal ausgeführt wird, wird Wert `5` fünfmal ausgegeben.  

Eine Lösung für dieses Problem ist *IIFE*. *IIFE* steht für *Immediately-invoked Function Expression*, 
also ein sofort ausgeführter Funktionsausdruck. Das hört sich sehr kompliziert an. Meiner Meinung nach 
ist es auch kompliziert. Ich habe *IIFE* hier nur der Vollständigkeithalber aufgenommen. 
Im nächsten Kapitel findes Sie ein einfachere Lösung.  

```
function getValue() {
    var funktionen = [];
    for (var i = 0; i < 5; i++) {
        funktionen.push((function(value) {
            return function (){
                console.log(value);
            }
        }(i)));
    }
    funktionen.forEach(function(funktion){
        funktion(); // Ausgabe: 0 1 2 3 4 
    });
    return true;
}
<!--index_987.html -->
```

Das Beispiel der Datei `index_987.html` verwendet eine IIFE.

### let in Schleifen

```
 function getValue() {
     var funktionen = [];
*    for (var i = 0; i < 5; i++) {
         funktionen.push(function() {
             console.log(i);
         });
     }
     funktionen.forEach(function(funktion){
         funktion(); // Ausgabe: 0 1 2 3 4
     });
     return true;
 }
<!--index_986.html -->
```

Das Beispiel der Datei `index_986.html` tut genau das, was das Beispiel 
der Datei `index_987.html` tat.

Mit dem Beispiel der Datei `index_985.html` können Sie sich davon überzeugen, dass das 
was gerade für eine forEach Schleife beschrieben habe auch für for in und for of Schleifen.

<!--index_985.html -->
<!--index_985a.html -->




### const in Schleifen

## Globaler Gültigkeitsbereich (Scope)

## Erfolgsmethode - best practice

> **Achtung:**


## In diesem Kapitel haben wir ...

In diesem Kapitel haben Sie auf unterschiedliche Arten eine Karte erstellt. 

In den nächsten Kapiteln werden wir diese Karte mit Elementen und Informationen füllen.

[^1]: https://de.wikipedia.org/w/index.php?title=Interpreter&oldid=182588640 (https://bit.ly/2GT9nQS)

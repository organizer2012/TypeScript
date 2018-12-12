# TypeScript Seminar

TypeScript ist eine Obermenge von ECMAScript 6 (ES6) und ist rückwärtskompatibel mit ECMAScript 5, d. h. JavaScript.  
Angular bietet somit auch die Vorzüge von ES6:  
- Lambdas
- Iteratoren
- for…of-Schleifen
- Generatoren im Stil von Python
- Reflexion


## Markdown (.md) Formatierungsregeln
* [Markdown Tutorial Git](http://agea.github.io/tutorial.md/)
* [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
* [Markdown Navigation](https://github.com/AlanWalk/markdown-navigation)


## Visual Studio Code
* Live Server als Extension installieren
** mit ALT + L + O wird der Server gestartet und die aktuelle Webseite geöffnet und bei jedem Speichern aktualisiert im Browser
* Formatierung des Texts mit ALT + Shift + F
* Zeilenumbruch aktivieren mit ALT + Z
* Aus-/Einkommentieren mit STRG + #
* Kommentar in JavaScript /**/ (Ein-/Mehrzeilig) oder // (Einzeilig)

## Git Hub
* auf git hub ein neues Repository anlegen
* https Link kopieren
* Laufwerk/Order im Explorer öffnen in der das Repository lokal abgelegt werden soll

### Git Bash
* mit Rechtsklick git bash öffnen
* git config --global user.name "username"
* git config --global user.email "eMail@host"
* Repository nach lokal kopieren:
    * git clone  https://github.com/grisham88/Javascript.git

### Visual Studio Code
* [Visual Studio Code: How to integrate Git](https://www.theregister.co.uk/2015/12/07/visual_studio_code_git_integration/)
* Den neuen Ordner öffnen
* mit Rechtsklick "Open with Code"
* Nun ist das Repository mit git verknüpft und alle Änderungen sind direkt commit und pushbar 
    * Über die Source control (Link in Visual Studio Code) sieht man alle offenen Dateien die geändert wurden
    * Mit Button "V" können diese direkt commited werden oder einzeln zum Commit freigegeben werden
    * Beim ... kann dann push ausgeführt werden -> Git wird nach Git Hub aktualisiert

## Hilfsfunktionen für VS Code
- https://code.visualstudio.com/docs/getstarted/tips-and-tricks
- https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
- https://code.visualstudio.com/docs/getstarted/keybindings
- Aufruf durch F1
    - Wenn > hinterlegt ist, werden Funktionen aufgeführt
    - Ohne > kann man nach Dateien suchen
- STRG + B für Explorer links zuklappen

## Seminarablauf

### Tag 1
ECMA 6
- Syntaxerweiterungen
    - Variablen
    - Spread- & Rest-Operationen
    - Destructuring
    - Objektliterale
    - Symbols
    - Arrays
    - Iterables -> Iterator
        - for ... of

### Tag 2
ECMA 6
- Funktionen vs. Arrow-Funktionen
- Promises -> Chains
- fetch-API
- Generatoren
- class-Keyword vs. Konstruktor
- Vererbung
- Module (Webpack und TypeScript)
- Observables

### Tag 3
Typescript
- Decorators
- Types
- Interfaces
- TS-Classes
- Generics

Tooling
- TSC (TypeScript Compiler)
- Webpack
- RxJs

## Installation TypeScript
Installation:  
- https://code.visualstudio.com/docs/languages/typescript
- The easiest way to install TypeScript is through npm, the Node.js Package Manager. If you have npm installed, you can install TypeScript globally (-g) on your computer by:

```html
npm install -g typescript
```
You can test your install by checking the version or help.
```html
tsc --version
tsc --help
```
Compilierung:  
Eingabe im Terminal tsc und name der Datei
```html
Beispiel: tcs "typescript - example.ts"
```
Dadurch wird eine ausführbare .js-Datei erzeugt

## Installation Webpack

## ECMA-6
- https://www.w3schools.com/js/js_es6.asp
- https://www.buschmais.de/2017/08/24/cleaner-code-mit-ecmascript-6/
- Implementierungsstand  
    - http://kangax.github.io/
    - http://kangax.github.io/compat-table/es6/
        - grün (implementiert)
        - rot (nicht unterstützt)

### Emmet Cheatsheets
- https://docs.emmet.io/cheat-sheet/

### Syntaxerweiterungen

#### Variablen

##### var
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/var
```javascript
<script>
    //linearer Codeablauf
    console.log("Wir betrachten die neuen Keywords für Deklarationen");

    //kein RefErr wg. Hoisting!
    console.log(test);

    var test = "var: Das ist ein Test.";

    console.log(test);

    for (var i = 0; i < 5; i++) {
        var temp = i + i;
        console.log(temp);
    }

    //Variablen existieren global, nicht lokal
    console.log('oops...:', i, temp);    
</script>
```

##### let 
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/let
```javascript
<script>
    // ECMA6: let, const

    // RefErr, Variable ist nur an der Stelle existent (TDZ -> Temporal dead Zone)
    console.log(test2);

    let test2 = "let: Auch ein Test...";
    console.log(test2);

    //im Block
    if (true) {
        let iftest = "Ich bin im Block!";
        console.log(iftest);
    }

    // RefErr, Variable ist nur im Block existent (TDZ -> Temporal dead Zone)
    console.log(iftest);

    // let und Schleife:
    for (let j = 0; j < 3; j++) {
        // temp2 wird immer wieder angelegt
        let temp2 = j * 2;
        console.log('let:', temp2);
    }

    // RefErr, Variable ist nur in der Schleife existent (TDZ -> Temporal dead Zone)
    console.log('oops...:', j, temp2);  
</script>
```

##### const
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/const
```javascript
<script>
    // ECMA 6: const
    const test3 = "Das ist wieder ein Test!";
    console.log('const: ', test3);

    //Uncaught TypeError: Assignment to constant variable. Änderungen nicht erlaubt
    test3 = "Was anderes?";
    
    //Uncaught SyntaxError: Missing initializer in const declaration. Initialisierung ist ein MUSS
    const weissnicht;

    const werte = [];
    werte.push(5);
    //Möglich durch Referenztyp
    console.log('const Array:', werte); // Ausgabe [5]
     
    // Funktion ist durch const nicht mehr änderbar
    const tool = function (){
        //tue was Wichtiges...
    };

    // Funktion ist durch var änderbar
    var tool2 = function tool2(){
        //tue was Wichtiges...
    };

    // const und Schleife
    for (let k = 0; k < 3; k++) {
        //Variable wird nicht immer wieder initialisiert
        const temp3 = k * 2;
        console.log('const: ', temp3);
    }
</script>
```

#### Spread- & Rest-Operationen
##### Spread
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Operators/Spread_syntax
- Verwandelt durch ... ein Array in eine Sequenz, also in einzelne Übergabewerte
- Arrays
    ```javascript
    <script>
        let zahlen = [2, 3, 4];
        let addiere = function (a, b, c) {
            return a + b + c;
        }

        let erg = addiere(5, 7, 8);
        console.log('erg:', erg); // erg: 20

        erg = addiere(zahlen);
        console.log('erg:', erg); // erg: 2,3,4undefinedundefined
            
        erg = addiere(...zahlen); // Spread: Array -> Sequenz (Verwandelt)
        console.log('erg:', erg); // erg: 9

        let mehrzahlen = [7, 3, 9, 3];
        // Neues Array allezahlen -> allezahlen: (7) [2, 3, 4, 7, 3, 9, 3]
        let allezahlen = zahlen.concat(mehrzahlen);
        console.log('allezahlen:', allezahlen);

        let allezahlen2 = [2, 3, 4, allezahlen];
        console.log('allezahlen2:', allezahlen2); // allezahlen2: (4) [2, 3, 4, Array(7)]
            
        allezahlen2 = [...zahlen, ...allezahlen]; // Spread: Array -> Sequenz (Verwandelt)
        console.log('allezahlen2:', allezahlen2); // allezahlen2: (10) [2, 3, 4, 2, 3, 4, 7, 3, 9, 3]

        let zahlenClone = [...zahlen];
        console.log('zahlenClone:', zahlenClone); // zahlenClone: (3) [2, 3, 4]
    </script>
    ```
- Objects
    ```javascript
    <script>
         let myObjX = {
            x: "X",
            y: "Y",
            z: "Z"
        }

        console.log(myObjX); // {x: "X", y: "Y", z: "Z"}

        let myObjA = {
            a: "A",
            b: "B"
        }

        let myObjXClone = { ...myObjX };
        console.log(myObjXClone); // {x: "X", y: "Y", z: "Z"}
        console.log(myObjXClone === myObjX); // false

        myObjXClone = myObjX;
        console.log(myObjXClone); // {x: "X", y: "Y", z: "Z"}
        console.log(myObjXClone === myObjX); // true

        let myMergedObject = { ...myObjX, ...myObjA };
        console.log(myMergedObject); // {x: "X", y: "Y", z: "Z", a: "A", b: "B"}

        //Bereits vorhandes Property des Objekts kann überschrieben werden
        myMergedObject = { ...myObjX, ...myObjA, z: "Anders Z" };
        console.log(myMergedObject); // {x: "X", y: "Y", z: "Anders Z", a: "A", b: "B"}

        //Erzeugt ein neues Object
        function configurable(conf) {
            let defaults = {}
            let myConf = { ...defaults, ...conf };
            return myConf;
        }
    </script>
    ```

##### Rest
- https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Functions/rest_parameter
- Verwandelt durch ... eine Sequenz in ein Array (Funktionsparameter), also aus einzelnen Übergabewerten
```javascript
<script>
    let addiere2 = function (...args) {
        // Mit Funktionsparmeter als Sequenz -> Array
        console.log('args:', args);
        return args.reduce(function (a, b) {
            return a + b;
        })
    }

    let erg2 = addiere2(5, 8, 2, 9);  // args: (4) [5, 8, 2, 9]
    console.log('erg2:', erg2); // erg2: 24

    let addiere3 = function () {
        // ohne Funktionsparameter (Kein Rest)
        console.log(arguments) // Arguments(4) [5, 8, 2, 9, callee: (...), Symbol(Symbol.iterator): ƒ]
        return Array.prototype.reduce.call(arguments, function (a, b) {
            return a + b;
        });
    }

    let erg3 = addiere3(5, 8, 2, 9);  // Arguments(4) [5, 8, 2, 9, callee: ƒ, Symbol(Symbol.iterator): ƒ]
    console.log('erg3:', erg2); // erg2: 24
</script>
```

#### Destructuring
#### Objektliterale
#### Symbols
#### Arrays
#### Iterables -> Iterator
##### for ... of

### Funktionen vs. Arrow-Funktionen
### Promises -> Chains
### fetch-API
    Ablösung von XML-HTTP Request Objekt
### Generatoren
### class-Keyword vs. Konstruktor
### Vererbung
### Module (Webpack und TypeScript)
### Observables

## Typescript
- https://www.typescriptlang.org/

### Decorators
### Types
### Interfaces
### TS-Classes
### Generics
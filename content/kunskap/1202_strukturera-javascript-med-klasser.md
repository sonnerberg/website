---
author: efo
category: javascript
revision:
  "2022-01-07": (A, efo) Första utgåvan inför kursen webgl VT-22.
...
Strukturera JavaScript med klasser
==================================

Under de senaste åren har det hänt otroligt mycket med JavaScript, som har gått från att vara ett litet script-språk på webben till att bli ett av de mest använda programmeringsspråken. Vi ska i denna övningen titta på hur vi kan strukturera vår kod med hjälp av klasser.



<!--more-->



Klasser {#klasser}
--------------------------------------

Låt oss börja med att ta en titt på klasser i JavaScript. I kursrepot finns det ett litet exempelprogram [classes](https://github.com/dbwebb-se/webgl/tree/master/example/classes) för att visa upp klasser och webpack. En del av koden redovisas nedan, men det fullständiga programmet finns i kursrepot.

Dessutom är [MDN dokumentationen](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) av klasser ett bra utgångspunkt för att lära sig mer.



### Definiera en klass {definition}

En klass definieras med hjälp av det reserverade ordet `class`. Och vi skapar det dessutom en konstruktor med i exemplets fall fyra instansvariabler.

```javascript
class Color {
    constructor(red, green, blue, alpha=1) {
        this.red = red;
        this.green = green;
        this.blue = blue;
        this.alpha = alpha;
    }
}

export default Color;
```

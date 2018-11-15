---
...
Objekt
==================================

Objekt är en samling av namngivna värden som vanligen kallas "properties" (egenskaper). För att referera till ett objekts egenskap används punkt. I andra programmeringsspråk kan du se konstruktionen som en dictionary (Python) eller associativ array (php). Guiden kommer skapa ett objekt som representerar ett html-element med en form och en position på skärmen.

Man kan skapa ett objekt med objekt-literalen `{}`. Vi kan antingen lägga till properties direkt och/eller vid ett senare tillfälle.

```javascript
var myObject = {
    posX: 45,
    posY: 80
};

window.console.log(myObject.posX); // 45
window.console.log(myObject.posY); // 80
```

Objektet innehåller nu två egenskaper, `posX` och `posY` som ska representera x- och y-koordinaterna på skärmen.
Vi hade även kunnat lägga till en egenskap med `myObject.posY = 80`. Objekt i JavaScript är så kallt *mutable* vilket betyder att man kan ändra på det under resans gång. Det är både bra och dåligt. Om vi skulle råka stava fel på egenskapen så skapas det en ny egenskap istället för att ge ett felmeddelande att egenskapen inte finns:

```javascript
window.console.log(myObject.posZ); // prints undefined
```

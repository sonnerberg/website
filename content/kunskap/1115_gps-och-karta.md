---
author: efo
category: javascript
revision:
  "2018-03-02": (A, efo) Första utgåvan inför kursen webapp v3.
...
GPS och karta
==================================

[FIGURE src=/image/webapp/gps.png?w=c5 class="right"]

Vi ska i denna övning använda [leaflet.js](https://leafletjs.com) tillsammans med [OpenStreetMap](https://www.openstreetmap.org) och Cordova Pluginen geolocation för att visa positionsdata på en karta. Vi ska titta på hur vi med hjälp av den inbyggda GPS'en kan visa användarens position på kartan.



<!--more-->



Exempelprogrammet från denna övning finns i kursrepot [example/gps](https://github.com/dbwebb-se/webapp/tree/master/example/gps) och i `example/gps`. Använd det gärna tillsammans med övningen för att se hur de olika delarna hänger ihop. En del kod utelämnas i exemplet för att det ska vara mer lättläst i artikeln.



En karta {#karta}
--------------------------------------
Vi kommer i detta exemplet använda leaflet.js för att visa upp en karta i vår mobila enhet och för att rita ut markörer på denna karta.

Jag har skapat en Cordova app precis som vi har gjort tidigare och i `www` katalogen har vi en simpel mithril app. Vi lägger nu till leaflet.js genom att använda kommandot `npm install leaflet --save`. Vi kopierar in `leaflet.css` och `images/` från leaflet paketet i `node_modules/` med följande kommando och nedan har vi lagt till `leaflet.css` i `index.html`.

```bash
# Stå i me/kmom06/gps
cp node_modules/leaflet/dist/leaflet.css www/css/leaflet.min.css
cp -r node_modules/leaflet/dist/images/ www/css/
```

```html
<!DOCTYPE html>
<html>
    <head>
        <meta name="viewport" content="user-scalable=no, initial-scale=1, maximum-scale=1, minimum-scale=1, width=device-width">
        <link rel="stylesheet" type="text/css" href="css/index.css">
        <link rel="stylesheet" type="text/css" href="css/leaflet.min.css">
        <title>Maps and GPS</title>
    </head>
    <body>
        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="dist/app.js"></script>
    </body>
</html>
```

I filen `js/index.js` som är ingångspunkten för vår app väntar vi in att enheten är redo och sen använder vi `m.mount()` för att ladda den enda vyn i appen `map.js`.

```javascript
"use strict";

var m = require("mithril");
var map = require("./views/map.js");

var app = {
    initialize: function() {
        document.addEventListener('deviceready', this.onDeviceReady.bind(this), false);
    },
    onDeviceReady: function() {
        m.mount(document.body, map);
    },
};

app.initialize();
```

I vyn `map.js` importerar vi `leaflet.js`, sedan definieras `view`-funktionen, vi vill här ha en rubrik och en `div` där kartan ska visas. Klassen `.map` används för att ge kartan en bredd och en höjd. **Viktigt att explicit ge kartan en höjd i pixlar eller rem annars visas den inte**. ID't `#map` används av JavaScript för att hämta ut rätt element.

```javascript
"use strict";

var m = require("mithril");
var L = require("leaflet");

module.exports = {
    view: function() {
        return [
            m("h1", "Map"),
            m("div#map.map", "")
        ];
    }
};
```

Vi använder sedan livscykel funktionen `oncreate` för att anropa funktionen som ritar upp kartan och även ett antal markörer som visar platser baserad på koordinater.

```javascript
module.exports = {
    oncreate: showMap,
    view: function() {
        return [
            m("h1", "Map"),
            m("div#map.map", "")
        ];
    }
};
```

Funktionen `showMap` definierar ett objekt med platser i Karlskrona som sedan används för att rita ut markörerna och centrera kartan runt en av platserna. Jag har vald att definiera variabeln `map` som en global variabel, då den används i flera olika funktioner, se exempelprogrammet.

```javascript
function showMap() {
    var places = {
        "BTH": [56.181932, 15.590525],
        "Stortorget": [56.160817, 15.586703],
        "Hoglands Park": [56.164077, 15.585887],
        "Rödebybacken": [56.261121, 15.628609]
    };

    map = L.map('map').setView(places["BTH"], 13);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',    {
        attribution: `&copy;
        <a href="https://www.openstreetmap.org/copyright">
        OpenStreetMap</a> contributors`
    }).addTo(map);

    for (var place in places) {
        if (places.hasOwnProperty(place)) {
            L.marker(places[place]).addTo(map).bindPopup(place);
        }
    }
}
```

Vi skapar en karta (`map`) där vi definierar vilken punkt vi vill ha som centrum och även hur långt vi har zoomat in. Vi lägger sedan till vilka bilder vi vill använda som **tiles** i kartan. Jag väljer att använda OpenStreetMaps tiles, men det finns en uppsjö av andra man kan använda.



Använda adress istället för koordinater {#address}
--------------------------------------
Vi har inte alltid tillgång till koordinater för de platser vi vill visa upp på kartan. Och då är det bra om vi istället kan använda adressen. Vi vill därför göra om adresser till koordinater och för det använder vi npm modulen `leaflet-geosearch`, som installeras med kommandot `npm install leaflet-geosearch --save`.

Vi börjar med att skapa ett `OpenStreetMapProvider` objekt `geocoder` och även ett objekt med adresser istället för positioner. Vi använder sedan vår `geocoder` för att göra om en adress till koordinater och ritar ut en markör på rätt plats. Om `geocoder` inte lyckas koda om adressen ritas inte ut en plats. Bäst resultat får man om man inte har allt för specifika adresser, man kan till exempel utelämna post nummer.

```javascript
function showMap() {
    ...

    var geocoder = new geosearch.OpenStreetMapProvider();

    var addresses = [
        "Bastionsgatan 1, Karlskrona",
        "Kärleksstigen 1, Karlskrona"
    ];

    for (var i = 0; i < addresses.length; i++) {
        geocoder
            .search({ query: addresses[i] })
            .then(function(result) {
                if (result.length > 0) {
                    L.marker([result[0].y, result[0].x]).addTo(map).bindPopup(result[0].label);
                }
            });
    }
}
```



Användarens position {#gps}
--------------------------------------
Då vi använder en mobil enhet med tillgång till GPS har vi möjlighet att ta reda på användarens nuvarande position och rita ut detta på kartan.

Vi använder oss av pluginen `cordova-plugin-geolocation`.

```bash
# Stå i me/kmom06/gps
cordova plugin add cordova-plugin-geolocation
```

För att använda position på iOS enheter lägger vi till följande i `config.xml`.

```xml
<edit-config file="*-Info.plist" mode="merge" target="NSLocationWhenInUseUsageDescription">
    <string>I will use your GPS position to show on a map.</string>
</edit-config>
```

Vi har nu tillgång till objektet `navigator.geolocation`. Vi använder funktionen `navigator.geolocation.getCurrentPosition()` för att få nuvarande position. För att hämta nuvarande position skapar vi en modell `models/position.js`, när vi har lyckats hämta nuvarande position ritar vi om vyn med hjälp av `m.redraw()`.

```javascript
// models/position.js
"use strict";

var m = require("mithril");

var position = {
    currentPosition: {},

    getPosition: function() {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(
                position.geoSuccess,
                position.geoError
            );
        }
    },

    geoSuccess: function(pos) {
        position.currentPosition = pos.coords;
        m.redraw();
    },

    geoError: function(error) {
        console.log('code: '    + error.code    + '\n' +
              'message: ' + error.message + '\n');
    }
};

module.exports = position;
```

I funktionen `getPosition()` kollar vi först om vi har tillgång till `navigator.geolocation` och anropar sedan `navigator.geolocation.getCurrentPosition()`. Beroende på utfallet av den funktionen anropas antigen `geoSuccess` eller `geoError`. I `geoSuccess` sätter vi den nuvarande position och ritar om vyn.

I vyn använder vi `oninit` livscykel-metoden för att anropa `getPosition` i modellen.

```javascript
module.exports = {
    oninit: position.getPosition,
    oncreate: function() {
        showMap();
    },
    view: function() {
        showPosition();
        return [
            m("h1", "Map"),
            m("div#map.map", "")
        ];
    }
};
```

I `showMap` funktionen lägger vi till en ny sorts markör som markerar användarens position. Jag har skapat en ikon för att visa användarens position. Du kan kopiera ikonen med följande kommando. Du kan naturligtvis använda en egen ikon också.

```bash
# Stå i kursrepot
cp example/gps/www/location.png me/kmom06/gps/www
```

Vi skapar nu leaflet ikonen `locationMarker`.


```javascript
var locationMarker = L.icon({
    iconUrl: 'location.png',

    iconSize:     [24, 24],
    iconAnchor:   [12, 12],
    popupAnchor:  [0, 0]
});
```


Och vi skapar funktionen `showPosition()` där vi sätter positionen för vår markör `locationMarker`.

```javascript
function showPosition() {
    if (position.currentPosition.latitude && position.currentPosition.longitude) {
        L.marker(
            [position.currentPosition.latitude, position.currentPosition.longitude],
            {icon: locationMarker}
        ).addTo(map).bindPopup("Din plats");
    }
}
```



Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna artikel använd oss av OpenStreetMap och leaflet.js för att placera ut markörer på en karta på specifika platser. Vi har även tittat på hur vi kan använda `cordova-plugin-geolocation` för att rita ut användarens position på kartan.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7350) om denna artikeln.

Exempelprogrammet från denna övning finns i kursrepot [example/gps](https://github.com/dbwebb-se/webapp/tree/master/example/gps) och i `example/gps`.

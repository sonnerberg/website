---
author: efo
category: javascript
revision:
  "2018-03-02": (A, efo) Första utgåvan inför kursen webapp v3.
...
GPS och karta
==================================

[FIGURE src=/image/webapp/gps.png?w=c5 class="right"]

Vi ska i denna övning använda en Cordova Plugin och Google Places API för att visa positionsdata på en karta. Vi ska även titta på hur vi med hjälp av den inbyggda GPS kan visa användarens position på kartan.



<!--more-->



En karta {#karta}
--------------------------------------
Vi kommer i detta exemplet använda Google Maps och för att använda Google Maps API behövs en API nyckel. Skaffa en gratis API nyckel på [Google Maps API](https://developers.google.com/maps/web/) och välj GET A KEY. Skapa ett nytt projekt för att koppla nyckeln till det.

Jag har skapat en Cordova app precis som vi har gjort tidigare och i `www` katalogen har jag en simpel mithril app som laddar följande vy. I `index.html` har jag lagt till ytterligare en JavaScript fil annars är den som vanligt i en Cordova app.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta name="viewport" content="user-scalable=no, initial-scale=1, maximum-scale=1, minimum-scale=1, width=device-width">
        <link rel="stylesheet" type="text/css" href="css/index.css">
        <title>Maps and GPS</title>
    </head>
    <body>
        <script src="https://maps.googleapis.com/maps/api/js?key=[YOUR_API_KEY]"></script>
        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="bin/app.js"></script>
    </body>
</html>
```

Ersätt [YOUR_API_KEY] med din egna API nyckel.

I filen `js/index.js` som är ingångspunkten för vår app väntar jag in att enheten är redo och sen använder jag `m.mount()` för att ladda den enda vyn i appen `map.js`.

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

I vyn `map.js` har jag definierar jag först `view`-funktionen, jag vill här ha en rubrik och en `div` där kartan ska visas. Klassen `.map` används för att ge kartan en bredd och en höjd. Viktigt att explicit ge kartan en höjd annars visas den inte. ID't `#map` används av JavaScript för att hämta ut rätt element.

```javascript
module.exports = {
    view: function() {
        return [
            m("h1", "Map"),
            m("div#map.map", "")
        ];
    }
};
```

Vi använder sedan livscykel funktionen `oncreate` för att anropa en funktion som ritar upp kartan och även ett antal markörer som visar platser baserad på koordinater.

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

Funktionen `showMap` definierar ett objekt med platser i Karlskrona som sedan används för att rita ut markörerna och centrera kartan runt en av platserna.

```javascript
function showMap() {
    var places = {
        "BTH": { lat: 56.181932, lng: 15.590525 },
        "Stortorget": { lat: 56.160817, lng: 15.586703 },
        "Hoglands Park": { lat: 56.164077, lng: 15.585887 },
        "Rödebybacken": { lat: 56.261121, lng: 15.628609 }
    };

    var map = new google.maps.Map(document.getElementById('map'), {
        zoom: 8,
        center: places["BTH"]
    });

    for (var place in places) {
        if (places.hasOwnProperty(place)) {
            new google.maps.Marker({
                position: places[place],
                map: map,
                title: place
            });
        }
    }
}
```

Vi skapar en karta (`map`) där vi definierar vilken punkt vi vill ha som centrum och även hur långt vi har zoomat in. Vi skapar sedan markörer för varje plats vi definierat i `places` objektet.



Använda adress istället för koordinater {#address}
--------------------------------------
Vi har inte alltid tillgång till koordinater för de platser vi vill visa upp på kartan. Och då är det bra om vi istället kan använda adressen för platser. Google har även för det ett API kallat [Geocoding](https://developers.google.com/maps/documentation/javascript/examples/geocoding-simple).

Vi börjar med att skapa ett Geocoder objekt och även ett objekt med adresser istället för positioner. Vi använder sedan vår `geocoder` för att göra om en adress till koordinater och ritar ut en markör på rätt plats. Om `geocoder` inte lyckas koda om adressen får vi upp ett felmeddelande.

```javascript
function showMap() {
    var places = {
        "BTH": { lat: 56.181932, lng: 15.590525 },
        "Stortorget": { lat: 56.160817, lng: 15.586703 },
        "Hoglands Park": { lat: 56.164077, lng: 15.585887 },
        "Rödebybacken": { lat: 56.261121, lng: 15.628609 }
    };

    var addresses = [
        "Bastionsgatan 14, 371 32 Karlskrona, Sweden",
        "Krutholmskajen 1, 371 38 Karlskrona, Sweden"
    ];

    var map = new google.maps.Map(document.getElementById('map'), {
        zoom: 8,
        center: places["BTH"]
    });

    var geocoder = new google.maps.Geocoder();

    for (var place in places) {
        if (places.hasOwnProperty(place)) {
            new google.maps.Marker({
                position: places[place],
                map: map,
                title: place
            });
        }
    }

    addresses.map(function(address) {
        geocoder.geocode({'address': address}, function(results, status) {
            if (status === 'OK') {
                new google.maps.Marker({
                    map: map,
                    position: results[0].geometry.location
                });
            } else {
                alert('Geocode was not successful for the following reason: ' + status);
            }
        });
    });
}
```


Användarens position {#gps}
--------------------------------------
Då vi använder en mobil enhet med tillgång till GPS har vi möjlighet att rita ut


Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna artikel använd oss av Google Maps API för att placera ut markörer på en karta på specifika platser. Vi har även tittat på hur vi kan använda `cordova-plugin-geolocation` för att rita ut användarens position på kartan.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7350) om denna artikeln.

Exempelprogrammet från denna övning finns i kursrepot [example/gps](https://github.com/dbwebb-se/webapp/tree/master/example/gps) och i `example/gps`.

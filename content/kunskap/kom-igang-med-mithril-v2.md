---
author: efo
category: javascript
revision:
  "2018-01-30": (C, efo) Anpassade artikeln för webapp-v3.
  "2017-03-09": (B, aar) Cordova anpassade artikeln.
  "2017-03-03": (A, efo) Första utgåvan inför kursen webapp v2.
...
Kom igång med ramverket Mithril
==================================

[FIGURE src=/image/webapp/mithril-logo.png class="right"]

Vi har tidigare i kursen skrivit våra SPA-applikationer i vanilla JavaScript. Vanilla JavaScript är beteckningen för ren JavaScript där vi inte använder annat är det som är implementerat i weblläsaren. Det finns både fördelar och nackdelar med att använda enbart JavaScript för att skriva applikationer. Vi har i våra SPA-applikationer än så länge inte separerat vyer och hämtning av data, allt har gjorts i samma funktioner och/eller modul. Vi ska i denna övning titta på hur vi med hjälp av JavaScript ramverket mithril kan skapa bättre struktur i våra SPA-applikationer. Vi ska använda en router, dela upp våra vyer och modeller, där vi hämtar data, och använda virtuella noder för att skapa en SPA-applikation.

I övningen skapar vi en SPA-applikation inför Nobelfesten där vi hämtar data från det officiella Nobel API:t.



<!--more-->



Introduktion {#intro}
--------------------------------------

Du kan läsa mer om [begreppet SPA på Wikipedia](https://en.wikipedia.org/wiki/Single-page_application).

Vi kommer installera och använda [Mithril](http://mithril.js.org/) för att bygga en enkel applikation som använder sig av en router och använder virtuella noder för att visa upp våra vyer.

Låter det magiskt? Lika bra vi ser hur det fungerar i kod, så faller saker nog på plats.

[INFO]
Vi har valt att inte inkludera `node-modules`-mappen i Mithril exemplen. För att testa exempel koden kör kommandot `npm install`, som installerar node modulerna från `package.json`.
[/INFO]



Förutsättningar {#forutsattningar}
--------------------------------------
Du har installerat labbmiljön för kursen webapp. Du är bekant med SPA-applikationer i vanilla JavaScript och har bekantat dig med webpack.



Installera mithril via npm {#install}
--------------------------------------
I tidigare kursmoment installera vi webpack med hjälp av npm. Vi ska nu titta på hur vi installerar och konfigurerar ett mithril projekt med hjälp av npm, `package.json` och webpack. Vi börjar med att initiera en grund `package.json` fil som innehåller konfigurationen för vårt projekt.

```bash
# gå till me
$ cd me/kmom03/nobel
$ npm init --yes
```

Vi ska nu installerar nu mithril och webpack via npm och gör det med följande kommandon. Vi använder `--save` för att det ska sparas som en modul vi är beroende av i `package.json`. Webpack installerar vi för att som tidigare i kursen kunna skriva vår JavaScript kod i moduler.

```bash
$ npm install --save mithril
$ npm install --save webpack
```

Det kan hända att du får varningar när du kör ovanstående kommandon, men dessa kan du ignorera för nu.

Låt oss nu titta in i `package.json`, för att se vad vi har fått på plats och lägga till så vi kan köra våra mithril applikationer.

```json
{
  "name": "nobel",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "mithril": "^1.1.6",
    "webpack": "^3.10.0"
  }
}
```

Vi skapar även en webpack konfigurationsfil `webpack.config.js` där vi lägger till att vår ingångspunkt för appen ska vara filen `js/index.js` och den kompilerade filen ska heta `bin/app.js`.

```javascript
module.exports = {
    entry: './js/index.js',
    output: {
        filename: './bin/app.js'
    }
};
```

Vi kan nu använda oss av möjligheten för att skapa skripts i `package.json` och skapar två nya. Kör vi `npm start` kompileras filerna till `bin/app.js` och kör vi `npm run watch` kompileras filerna automatisk varje gång vi sparar.

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "webpack -d",
  "watch": "webpack -d --watch"
},
```



Början till en mithril app {#forsta}
--------------------------------------
Vi börjar med en enkel `index.html`, där vi känner igen det mesta från tidigare. Notera att jag har lagt till den minifierade CSS-filen från tidigare kursmoment, som baseras på `base.scss`. Vi inkluderar även `bin/app.js` längst ner i `index.html`.

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Nobel</title>

    <link rel="stylesheet" href="style.min.css" />
</head>
<body>

    <script type="text/javascript" src="bin/app.js"></script>
</body>
</html>
```

Nu saknas bara `js/index.js` så är vi på bana och redo för att skapa vår första mithril app.

```bash
# stå i me/kmom03/nobel
$ mkdir js
$ touch js/index.js
```

Filen `js/index.js` är vår utgångspunkt för appen och i den kommer vi senare i övningen lägga vår router, som pekar ut rätt vy.



Vår första vy {#vy}
--------------------------------------
En av fördelarna med att använda ett JavaScript ramverk är att vi kan separera vyerna från modeller och därmed hämtningen av data. Vi börjar med att skapa katalogen `js/views` och en vy `js/views/list.js`.


```bash
# utgår från www/
$ mkdir js/views
$ touch js/views/list.js
```

I `js/views/list.js` filen vill vi än så länge bara visa upp för användaren att vi har hamnat i en app för Nobelfesten. Vi börjar med att hämta in modulen mithril och spara den i variablen `m`. Vi exporterar sedan det som inom mithril kallas en komponent, det är ett objekt med en funktion kallat `view`. Det som händer när vi använder komponenten i filen `js/views/list.js` är att funktionen `view` anropas och där returneras den virtuell noden `m("h1", "Nobelfesten")`. Denna virtuella noden kommer sedan i webbläsaren renderas som `<h1>Nobelfesten</h1>`. Det virtuella DOM-trädet som ritas upp av JavaScript genom ramverket mithril består av dessa virtuella noder. För mer information om virtuella noder i kontexten av mithril se denna utmärkta [introduktion](http://mithril.js.org/vnodes.html).

```javascript
"use strict";

var m = require("mithril");

module.exports = {
    view: function() {
        return m("h1", "Nobelfesten");
    }
};
```

För att appen ska veta om att vi vill visa upp list-vyn måste vi in i appens utgångspunkt (`js/index.js`) och peka ut vyn. Vi anger först i vilket html-element vår vy skall renderas och skickar sedan med vår vy till funktionen `m.mount`:

```javascript
"use strict";

var m = require("mithril");
var list = require("./views/list.js");

m.mount(document.body, list);
```

Nu behöver vi bara packa ihop vår mithril app med hjälp av webpack för att se Nobelfest-appen för första gången. Detta gör vi i terminalen med `npm start`, som vi definerade tidigare som ett npm script i `package.json`.

Öppna upp filen `index.html` i din webbläsare och skåda mästervärket eller iallafall Nobelfesten som en fin rubrik. Låt oss använda lite av stylingen från tidigare kursmoment och samtidigt titta på hur vi lägger till flera virtuella noder i samma vy/komponent.

```javascript
"use strict";
var m = require("mithril");

module.exports = {
    view: function() {
        return m("main.container", [
            m("h1", "Nobelfesten"),
            m("p", "Välj ett årtal i listan:")
        ]);
    }
};
```



En router för flera sidor {#router}
--------------------------------------
Med bara en sida har vi inte kommit långt. Så låt oss titta på hur vi lägger till ytterligare en vy och en router så vi kommer åt vyn. Först skapar vi filen `js/views/year.js` och precis som `list.js` definerar våra nya `year.js` en vy. I denna här vyn ser du att vi returnerar en array av virtuella noder, som placeras i ordning efter varann i vyn.

```javascript
"use strict";
var m = require("mithril");

module.exports = {
    view: function() {
        return [
            m("h1", "My hobby"),
            m("p", "I run orienteering most of the time. And was pretty good at it before I blew my knee.")
        ];
    }
};
```

I vår `index.js` ändrar vi så vi använder funktionen `m.route()` istället för `m.mount()`. `m.route()` tar tre argument:

1. Vilket element som skall fyllas med de virtuella noder.

1. Vår ursprungsroute som är det vy där appen börjar.

1. Ett objekt som definerar alla routes i appen.

Och vår index.js fil ser nu ut så här:

```javascript
"use strict";
var m = require("mithril");
var Me = require("./views/me");
var Hobby = require("./views/hobby");
var app = {
    initialize: function() {
        document.addEventListener('deviceready', this.onDeviceReady.bind(this), false);
    },
    onDeviceReady: function() {
        m.route(document.body, "/", {
            "/": Me,
            "/hobby" : Hobby
        });
    },

};
app.initialize();
```

Om du manuellt skriver in `/hobby` efter `index.html#!` i din webbläsares adressfält, ser du innehållet från din hobby-vy. `#!` är en _hashbang_, det används vanligen till routing på klient sidan. Det går att ändra vad som ska vara hashbang med [m.route.prefix](http://mithril.js.org/route.html#mrouteprefix).

Vi vill inte skriva in adresser manuellt, så vi ska nu titta på hur vi kan skapa navigering för vår app. Vi kan skapa länkar precis som vi har skapat andra virtuella noder tidigare, så vi lägger till en länk längst upp i vårt me-vy med följande kod. Vi kan nu gå från vårt Me-vy till hobby-vyn.

```javascript
m("a", {href: "/hobby", oncreate: m.route.link}, "Hobby")
```

Mithrils route funktion är användbar för mer än bara vår huvudrouter. Vi kan till exempel göra omdirigeringar, hämta nuvarande route och mycket annat. [Dokumentationen för `m.route()`](http://mithril.js.org/route.html).



Styling {#styling}
--------------------------------------
Vi vill ju alltid att våra hemsidor, applikationer och program är snygga och användarvänliga, så därför vill vi kunna styla våra sidor. Öppna `css/index.css` och fixa en egen snygg design.

Jag valde att lägga till några extra element i min `me-vy` enligt nedan och en enkel responsiv styling, för ett resultat enligt det som syns nedan. Som du ser nedan har jag lagt in html-element i en array efter det andra elementet `div`. Elementen blir barn-element till det yttre och man kan ha så många nivåer man vill i det virtuella dom'et.

```javascript
"use strict";
var m = require("mithril");

module.exports = {
    view: function() {
        return [
            m("a", {href: "/hobby", oncreate: m.route.link}, "Hobby"),
            m("div", [
                m("h1", "Emil Folino"),
                m("p", "My name is Emil, I'm originally from Denmark, but now I live in Sweden."),
                m("p", "I run orienteering and drive an old Saab.")
            ])
        ];
    }
};
```

[FIGURE src="/image/snapvt17/mithril-me-screen.png" caption="Screenshot enkel me-sida i mithril"]



Layout {#layout}
--------------------------------------
Om vi vill ha navigering i alla vyer kan vi lägga till länkar längst upp, men som vanligt vill vi hålla vår kod DRY. I mithril kan vi använda oss av layouts för att återanvända kod i flera vyer. Vi skapar först ett nytt vy `js/views/layout.js`, som blir vår mall för andra vyer.

```javascript
"use strict";
var m = require("mithril");

module.exports = {
    view: function(vnode) {
        return m("main", [
            m("navbar", [
                m("div.container", [
                    m("h2.brand", "Emil Folino"),
                    m("ul.nav", [
                        m("li", [m("a", {href: "/", oncreate: m.route.link}, "Me")]),
                        m("li", [m("a", {href: "/hobby", oncreate: m.route.link}, "Hobby")])
                    ])
                ])
            ]),
            m("section.container", vnode.children)
        ]);
    }
};
```

I ovanstående kodexempel skapar vi vår navigation som en navbar med en "logga" och två stycken länkar. Efter navbar skapas ett section-element (`m("section.container", vnode.children)`), som innehåller de virtuella noder från vyn som använder sig av layout. Så lått oss titta på hur vi använder oss av layout från `index.js`.

```javascript
"use strict";
var m = require("mithril");
var Layout = require("./views/layout");
var Me = require("./views/me");
var Hobby = require("./views/hobby");
var app = {
    initialize: function() {
        document.addEventListener('deviceready', this.onDeviceReady.bind(this), false);
    },
    onDeviceReady: function() {
        m.route(document.body, "/", {
            "/": {
                render: function() {
                    return m(Layout, m(Me));
                }
            },
            "/hobby": {
                render: function() {
                    return m(Layout, m(Hobby));
                }
            }
        });
    }
};

app.initialize();
```

Vi använder oss utav en [RouteResolver](http://mithril.js.org/route.html#routeresolver) för att rendera layout och skickar med de virtuella noder, i detta fallet vår två vyer, som ska renderas inuti layouten.

Här under kan ni se ett exempel på en mithril me-app med navigation.

[FIGURE src="/image/snapvt17/mithril-me-screen-final.png" caption="Screenshot enkel me-sida i mithril med navigation"]



Avslutningsvis {#avslutning}
--------------------------------------

Det finns många olika varianter på MVC-liknande ramverk för klientbaserad utveckling av JavaScript. På webbplatsen [TodoMVC](http://todomvc.com/) kan du se en översikt av några av dem och jämföra hur deras kod ser ut när man bygger en Todo applikation.

Att använda designmönstret MVC kan ge dig en god uppdelning av din kod i olika delar som har olika syften. Det ger en god grund för en bra arkitektur i din applikation.

Mithril är en spännande lösning på klientbaserad programmering med JavaScript. Det är inte helt enkelt att komma in i det, men koden är liten och överskådlig.

Har du [tips, förslag eller frågor om artikeln](t/6313) så finns det en specifik forumtråd för det.

---
author: efo
category: javascript
revision:
  "2018-01-18": (A, efo) Första utgåvan inför kursen linux V18.
...
Struktur i JavaScript
==================================
[FIGURE src=image/webapp/backpack.jpg?w=c4 class="right"]

Vi har nu bra struktur på vår CSS/SASS kod och tiden har nu kommit för att ta ett steg i rätt riktning även för JavaScript koden. Sista delen av kursmoment 1 var att dela upp koden för Me-appen i olika filer för att få en bättre struktur på koden. Vi ska i denna övning titta på verktyg för att strukturera vår JavaScript kod. Målet är att vi bara importerar en JavaScript-fil i `index.html` och att vi använder modulerna på ett bättre sätt än vi har gjort tidigare.



<!--more-->



Du kan med fördel strukturera upp koden från uppgiften [Lager appen del 1](uppgift/lager-appen-del-1) i den första delen av artikeln. Smidigast är isåfall att kopiera koden från kmom01 till kmom02.

```bash
# stå i me-katalogen
cp kmom01/lager1/* kmom02/lager2/
```

I den andra delen av artikeln från och med [Återanvända data](#caching) tittar vi ytterligare på hur vi kan strukturera vår kod. Vi delar upp hämtningen av data och renderingen av element i webbläsaren, så vi får kod som är lättare att återanvända.



npm och package.json {#npm}
--------------------------------------
Vi har i tidigare kurser använd [npm](https://www.npmjs.com/) (Node Package Manager) för att installera JavaScript moduler. Nu ska vi ta detta ett steg vidare och titta på vissa av möjligheterna med npm och konfigurationsfilen `package.json`. Vi börjar med att initiera att vi vill ha ett npm projekt och att vi vill installera webpack som en modul vi är beroende av (dependency).

```bash
$ npm init --yes
$ npm install --save-dev webpack webpack-cli
```

Låt oss titta på filen `package.json` som skapades av kommandona ovan.

```json
{
  "name": "webpack-intro",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^4.29.3",
    "webpack-cli": "^3.2.3"
  }
}
```

Vi ser att vi har två moduler som vi är beroende (devDependencies) av `webpack` och `webpack-cli`. Förutom de två beroenden är det standard värden och vi ser att vårt paket har fått namnet lager2.



webpack {#webpack}
--------------------------------------
I koden vi skrev i kmom01 avslutade vi med att dela upp JavaScript koden i ett flertal `.js`-filer, som vi importerade i `index.html`. När vi använder en modul som finns i en annan JavaScript fil förlitar vi oss på att den har laddats i `index.html`. Det är aldrig bra att implicit förlita sig på att filer har laddats och för att komma bort från detta kan vi använda webpack. webpack används för att kompilera JavaScript moduler och gör det möjligt att dela upp vår JavaScript kod i ett flertal moduler. Vi kan även hämta in externa moduler och på samma sätt som de egna modulerna kompilera ner det till en enda fil.

Vi börjar med att skapa en konfigurationsfil för webpack där vi pekar ut vilken JavaScript fil vi vill ha som ingång (`entry`) för vår applikation. Vi definierar även vilken fil vi vill att alla moduler ska kompileras till (`output`). Vi döper konfigurationsfilen till `webpack.config.js`.

```javascript
// webpack.config.js

module.exports = {
    entry: './js/main.js',
    output: {
        filename: './bundle.js'
    }
};
```

Vi vill alltså börja appen från filen `/js/main.js` och den kompilerade filen hamnar i `/dist/bundle.js`, webpack har `/dist` som standard katalog. Jag har strukturerat upp min kod lite ytterligare från kmom01 och lagt alla JavaScript filer i katalogen `js`.

För att kompilera JavaScript koden använder vi oss av kommandot `webpack -d` och då vi har en konfigurationsfil `webpack.config.js` vet webpack redan om vilka filer vi ska utgå ifrån och vart den kompilerade filen ska läggas. Flaggan `-d` står för development och vi kommer köra med `-d` i dessa första kursmoment. För att automatisera detta ytterligare lägger vi till två skript i `package.json` som kör kommandot `webpack -d` varje gång vi sparar filer som ingår i projektet. Du kan nu köra kommandot `npm start` i terminalen och vår applikation kompileras.

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "webpack -d",
  "watch": "webpack -d --watch"
},
```

I andra skriptet `watch` använder vi flaggan `--watch`, som håller koll på vilka filer som uppdateras och kompilerar om de som behövs. Genom att köra kommandot `npm run watch` i terminalen kompileras alla filer som används från ingångspunkten, i detta fallet `/js/main.js`, till en fil `/dist/bundle.js`. Vi kan nu lägga till `/dist/bundle.js` längst ner i `index.html` som den enda JavaScript filen vi importerar.



import och export {#importexport}
--------------------------------------
Om vi öppnar upp `index.html` i en webbläsare stöter vi på patrull direkt. Öppnar vi upp JavaScript konsolen i webbläsaren ser vi varför.

> ReferenceError: Can't find variable: home

I och med att vi inte laddar JavaScript filerna implicit längre då vi bara har en  JavaScript fil `/dist/bundle.js` i `index.html` måste vi importera modulerna explicit. `import` och `export` är två nyckelord som vi kan använda för detta. För mer information om `import` och `export` se [import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) och [export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) dokumentationen.

Vi vill importera home-objektet från filen `/js/home.js` och det gör vi med följande kodrad längst upp i `main.js` och vår fil ser nu ut på följande sett.

```javascript
// js/main.js

"use strict";

import { home } from "./home.js";

(function () {
    window.rootElement = document.getElementById("root");

    window.mainContainer = document.createElement("main");
    window.mainContainer.className = "container";

    window.navigation = document.createElement("nav");
    window.navigation.className = "bottom-nav";

    home.showHome();
})();
```

Men för att vi kan importera en modul måste den först exporteras. Så i slutet av filen `/js/home.js` lägger vi in `export { home };`. Vi passar även på att ta bort en del av koden som användes för module pattern och i filen `js/home.js` har vi nu bara ett objekt med två attribut och en funktion. Notera hur attributen anropas från funktionen med hjälp av `home.titleText` och `home.description`.

```javascript
// js/home.js

"use strict";

var home = {
    titleText: "Infinity Warehouses",
    description: "Where products goes to disappear",

    showHome: function () {
        window.mainContainer.innerHTML = "";

        var title = document.createElement("h1");

        title.className = "title";
        title.textContent = home.titleText;

        var greeting = document.createElement("p");

        greeting.textContent = home.description;

        window.mainContainer.appendChild(title);
        window.mainContainer.appendChild(greeting);

        window.rootElement.appendChild(window.mainContainer);

        menu.showMenu("home");
    }
};

export { home };
```

Vi laddar om sidan och stora delar av vyn visas nu. Vi får dock fortfarande ett JavaScript fel i konsolen.

> ReferenceError: Can't find variable: menu

På samma sätt som vi importerade och exporterade `/js/home.js` måste vi nu göra med `/js/menu.js` och resterande filer i lager appen. I `/js/home.js` lägger vi till `import { home } from "./home.js";` längst upp i filen. Vi ser samtidigt till att exportera `menu` i filen `/js/menu.js` som nu ser ut som följer. Notera hur de olika modulerna importeras längst upp i filen för att kunna anropa de olika modulerna för att visa sidorna.

```javascript
"use strict";

import { home } from "./home.js";
import { product } from "./product.js";

var menu = {
    showMenu: function (selected) {
        window.navigation.innerHTML = "";

        var navElements = [
            { name: "Home", class: "home", nav: home.showHome },
            { name: "Products", class: "meeting_room", nav: product.showProducts },
        ];

        navElements.forEach(function (element) {
            var navElement = document.createElement("a");

            if (selected === element.class) {
                navElement.className = "active";
            }

            navElement.addEventListener("click", element.nav);

            var icon = document.createElement("i");

            icon.className = "material-icons";
            icon.textContent = element.class;
            navElement.appendChild(icon);

            var text = document.createElement("span");

            text.className = "icon-text";
            text.textContent = element.name;
            navElement.appendChild(text);

            window.navigation.appendChild(navElement);
        });

        window.rootElement.appendChild(navigation);
    }
};

export { menu };
```



Återanvända data {#caching}
--------------------------------------

Vid en del tillfällen är data tillgången för mobila enheter dålig, bristfällig eller till med helt saknad. Därför vill vi ibland försöka minska mängden förfrågningar till en backend och istället försöka återanvända den data vi redan har tillgänglig. Som ett exempel kan vi ta produktlistningen från uppgiften [Lager appen del 1](uppgift/lager-appen-del-1). Där hämtar vi alla produkter för listningen och den data kan vi återanvända sedan i produktvyn.

Det finns ett exempelprogram i kursrepot i katalogen `example/lager_caching` och på [GitHub](https://github.com/dbwebb-se/webapp/tree/master/example/lager_caching). Följ gärna med i exempelprogrammet i följande stycken.

Jag har strukturerat koden i olika moduler med hjälp av webpack enligt ovan och har delat upp strukturen ytterligare för att ge ett exempel på hur man kan strukturera sin kod på ytterligare sätt.

Vi börjar i den modul som hanterar att vi hämtar data om produkterna från API:t. Vi hämtar data från API:t i funktionen `getAllProducts` och sparar det i variabeln `allProducts` i samma modul. Nu kan vi alltså från andra JavaScript moduler anropa funktionen och sedan fylls variabeln `allProducts` med alla produkterna.

```javascript
var products = {
    allProducts: [],

    getAllProducts: function() {
        fetch("https://lager.emilfolino.se/v2/products?api_key=[API_KEY]")
            .then(function(response) {
                return response.json();
            })
            .then(function(result) {
                products.allProducts = result.data;
            });
    }
};

export { products };
```

Ett problem vi får är att då hämtningen av data från API:t är asynkront vet inte den andra modulen om när hämtningen av data är klar och när modulen kan rita upp de elementen som hämtas från API:t. Vi tar en titt på hur vi kan lösa detta med hjälp av funktioner i JavaScript. I vår modul `product_list.js`, som ska rendera elementen anropar vi först `products` modulen och funktionen `getAllProducts` som hämtar data. Vi skickar med en funktion som argument till `getAllProducts` som vi sedan anropar när data är hämtad.

```javascript
import { products } from "./products.js";
import { productDetails } from "./product_details.js";

let productList = {
    show: function() {
        products.getAllProducts(productList.renderProducts);
    },

    renderProducts: function() {
        let root = document.getElementById("root");

        root.innerHTML = "<h2>Produkter</h2>";

        products.allProducts.map(function (product) {
            let productElement = document.createElement("p");

            productElement.textContent = product.name;

            productElement.addEventListener("click", function() {
                productDetails.showProduct(product.id);
            });

            root.appendChild(productElement);
        });
    }
};

export { productList };
```

Funktionen `show` ovan anropas från en `index.js` fil som är ingångspunkten för vårt webpack projekt. I `show` anropar vi funktionen `getAllProducts` och vi skickar med callback-funktionen `renderProducts`, som sen i sin tur kommer rendera produkt-elementen. För att iterera över de hämtade produkterna används funktionen `Array.prototype.map` ([Dokumentation för map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)) på raden `products.allProducts.map(function (product) {`. `Array.prototype.map` är en 'higher-order function' som tar en funktion som argument. Att använda `map` och andra 'higher-order functions' är en del av programmeringsparadigmen funktionell programmering. Vi kommer i kursen ha inslag av funktionell programmering och detta var en första liten introduktion.

Vi måste göra en liten ändring i `getAllProducts` för att callback-funktionen anropas och den funktionen ser nu ut som nedan.

```javascript
var products = {
    allProducts: [],

    getAllProducts: function(callback) {
        fetch("https://lager.emilfolino.se/v2/products?api_key=[API_KEY]")
            .then(function(response) {
                return response.json();
            })
            .then(function(result) {
                products.allProducts = result.data;

                return callback();
            });
    }
};

export { products };
```

Än så länge har vi inte cachad någon data men med en liten ändring kan vi återanvända data istället för att hämta data varje gång. Nedan lägger vi till en `if`-sats, som kollar om det finns produkter i `allProducts`-arrayen. Om det finns anropar vi `callback()`. Anledningen till att vi har `return` innan funktions anropet är att vi vill avsluta exekveringen av `getAllProducts`-funktionen.

```javascript
var products = {
    allProducts: [],

    getAllProducts: function(callback) {
        if (products.allProducts.length > 0) {
            return callback();
        }

        fetch("https://lager.emilfolino.se/v2/products?api_key=[API_KEY]")
            .then(function(response) {
                return response.json();
            })
            .then(function(result) {
                products.allProducts = result.data;

                return callback();
            });
    },

    getProduct: function(productId) {
        return products.allProducts.filter(function(product) {
            return product.id == productId;
        })[0];
    }
};

export { products };
```

I kodexemplet ovan finns även en funktion `getProduct` för att hämta en enskild produkt från `allProducts`-arrayen. Här använder vi ytterligare en 'higher-order function' `Array.prototype.filter` ([Dokumentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)), den gör som väntad en filtrering av en array baserad på de element som returneras inuti funktionen som skickas med som argument. I detta fallet jämför vi produkternas id'n och returnerar om de matchar. Funktionen `getProduct` använder vi från modulen `productDetails`, som den uppmärksamma redan har upptäckt innehåller den funktionen som anropas när man klickar på en produkt.

Vi kommer längre fram i kursen titta ytterligare på cachning av data och till och med hur vi kan bygga ett offline-läge i våra appar.



Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna övning tittat på hur vi kan skapa en bättre struktur för vår JavaScript och hur vi explicit definierar vilka JavaScript moduler vi vill använda. Webpack kan konfigureras till att ta hand om alla våra assets: JavaScript, CSS/SASS och bilder, men i denna övning får det räcka med att vi kompilerar vår JavaScript till en enda fil. För mer information om [webpack](https://webpack.js.org) se deras utmärkta hemsida med bra dokumentation och guides.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7315) om denna artikeln.

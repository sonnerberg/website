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



Du kan med fördel strukturera upp koden från uppgiften [Lager appen del 1](uppgift/lager-appen-del-1). Smidigast är isåfall att kopiera koden från kmom01 till kmom02.

```bash
# stå i me-katalogen
cp kmom01/lager1/* kmom02/lager2/
```



npm och package.json {#npm}
--------------------------------------
Vi har i tidigare kurser använd [npm](https://www.npmjs.com/) (Node Package Manager) för att installera JavaScript moduler. Nu ska vi ta detta ett steg vidare och titta på vissa av möjligheterna med npm och konfigurationsfilen `package.json`. Vi börjar med att initiera att vi vill ha ett npm projekt och att vi vill installera webpack som en modul vi är beroende av (dependency).

```bash
$ npm init --yes
$ npm install --save webpack
$ npm install --save webpack-cli
```

Låt oss titta på filen `package.json` som skapades av kommandona ovan.

```json
{
  "name": "lager2",
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
    "webpack": "^4.1.1",
    "webpack-cli": "^2.0.11"
  }
}
```

Vi ser att vi har två moduler som vi är beroende (dependencies) av `webpack` och `webpack-cli`. Förutom de två beroenden är det standard värden och vi ser att vårt paket har fått namnet lager2.



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

I och med att vi inte laddar JavaScript filerna implicit längre då vi bara har en JavaScript fil i `index.html` måste vi importera modulerna explicit. `import` och `export` är två nyckelord som vi kan använda för detta. För mer information om `import` och `export` se [import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) och [export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) dokumentationen.

Vi vill importera home-objektet från filen `/js/home.js` och det gör vi med följande kodrad längst upp i `main.js`:

```javascript
import { home } from './home.js';
```

Men för att vi kan importera en modul måste den först exporteras. Så i slutet av filen `/js/home.js` lägger vi följande.

```javascript
export { home };
```

Vi laddar om sidan och stora delar av vyn visas nu. Vi får dock fortfarande ett JavaScript fel i konsolen.

> ReferenceError: Can't find variable: menu

På samma sätt som vi importerade och exporterade `/js/home.js` måste vi nu göra med `/js/menu.js` och de resterande filerna.



Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna övning tittat på hur vi kan skapa en bättre struktur för vår JavaScript och hur vi explicit definierar vilka JavaScript moduler vi vill använda. Webpack kan konfigureras till att ta hand om alla våra assets: JavaScript, CSS/SASS och bilder, men i denna övning får det räcka med att vi kompilerar vår JavaScript till en enda fil. För mer information om [webpack](https://webpack.js.org) se deras utmärkta hemsida med bra dokumentation och guides.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7315) om denna artikeln.

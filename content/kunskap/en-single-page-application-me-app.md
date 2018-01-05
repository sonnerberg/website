---
author: efo
category: javascript
revision:
  "2018-01-04": (A, efo) Första utgåvan inför kursen webapp-v3 V18.
...
En Single Page Application me-app
==================================

[FIGURE src=image/webapp/javascript-logo.png?w=c5 class="right"]

Vi ska i denna övning skapa en me-app i HTML5, CSS3 och JavaScript. Vi gör ett medvetet val om design för att vi ska få ett utseende som en "native" app. Vi skapar navigation som fungerar för både stora och små enheter. Webbläsarens inbyggda teknologier används för att hämta data från ett JSON API och vi gör en redovisningssida som är lättläst på alla enheter.



<!--more-->



Vi rekommenderar att du kodar med i denna övning så du själv får känna på hur det är att skriva en Single Page Application (SPA). Du kan spara din kod i katalogen `me/redovisa`, där du sedan kan bygga vidare på din me-app.



Grunden i HTML {#html}
--------------------------------------
Som med allt annat vi gör för webben behöver vi någonstans ha en HTML sida, som vi använder för att rita upp våra enskilda HTML-element i. Vi börjar med en enkel sida `index.html`, som inte kommer utvecklas mycket under övningens och kursens gång. Detta blir grunden för alla HTML-element, som vi sedan renderar med hjälp av JavaScript.

```html
<!-- index.html -->

<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>Me-app</title>

    <link rel="stylesheet" href="style.css" />
</head>
<body>
    <div id="root"></div>

    <script type="text/javascript" src="main.js"></script>
</body>
</html>
```

Vårt tränade öga ser direkt att vi behöver två filer till `style.css` för vår CSS kod och `main.js` för vår JavaScript kod. Vi skapar dessa två filer enkelt med `touch`.

```bash
# stå i me/redovisa
touch style.css
touch main.js
```

Vi har nu allt vi behöver för vår Single Page Application me-app.



Rendera HTML-element i JavaScript {#html-element}
--------------------------------------
Då vi inte har några element på HTML sida än så länge, förutom vårt rot-element `<div id="root"></div>`, öppnar vi upp `main.js`.

```javascript
// main.js
"use strict";

(function () {
    var rootElement = document.getElementById("root");
})();
```

För att vi ska kunna lägga till fler element i vår börjar vi med att hämta ut rot-elementet `#root`. Detta görs som vi har sett tidigare med funktionen `document.getElementById()`. Kodraden är omkretsat av en IIFE (Immediately-invoked function expression), som säkerställar att vi inte skräpar ner den globala namn rymden. Nu är vi redo för att lägga till element i rot-elementet. Detta görs med funktionerna `document.createElement()` och `element.appendChild()`. Vi tilldelar även klasser och innehåll med hjälp av attributen `className` och `textContent`. I [dokumentationen](https://developer.mozilla.org/en-US/docs/Web/API/Element) för element finns alla attribut.

```javascript
// main.js
"use strict";

(function () {
    var rootElement = document.getElementById("root");

    var mainContainer = document.createElement("main");
    mainContainer.className = "container";

    var title = document.createElement("h1");
    title.className = "title";
    title.textContent = "Emil Folino";

    mainContainer.appendChild(title);
    rootElement.appendChild(mainContainer);
})();
```

Vi har nu en enkel sida med en `main.container` och vårt namn som ett `h1`-element. Som beroende på webbläsare ser ut ungefär som skärmbilden nedan. Jag använder "responsive mode" i webbläsaren för att se det som en mobil enhet.

[FIGURE src=image/webapp/screenshot_namn.png?w=c8]

> Men Emil hade det inte varit enklare att bara lägga till det i `index.html`, är ju 3 rader HTML-kod och sen är vi klara med detta.

Just nu kanske det känns onödigt, men när vi i slutet av övningen har fyra olika vyer och dynamisk växling mellan dessa är det mer rimligt med alla dessa rader kod för att skriva ut ett namn.

Ett simpelt exempel som kan visa på de dynamiska egenskaperna med att rendera HTML-element med hjälp av JavaScript är om vi lägger till en liten hälsning i me-appen.

```javascript
// main.js
"use strict";

(function () {
    var rootElement = document.getElementById("root");

    var mainContainer = document.createElement("main");
    mainContainer.className = "container";

    var title = document.createElement("h1");
    title.className = "title";
    title.textContent = "Emil Folino";

    var greeting = document.createElement("p");
    var timeOfDayGreeting = "Hej";
    var now = new Date();
    if (now.getHours() < 10) {
        timeOfDayGreeting = "Godmorgon";
    } else if (now.getHours() >= 17) {
        timeOfDayGreeting = "Godkväll";
    }

    greeting.textContent = timeOfDayGreeting + ", jag heter Emil Folino och är lärare i kursen webapp.";

    mainContainer.appendChild(title);
    mainContainer.appendChild(greeting);

    rootElement.appendChild(mainContainer);
})();
```

Nu har vi en hälsning, som beroende på tiden på dagen, skriver ut olika öppningsfraser. En liten dynamisk del av sidan som visar på en av styrkorna hos JavaScript. Notera gärna ordningen som vi använder funktionen `appendChild()`. Vi lägger först till `title` och `greeting` i `mainContainer` innan vi lägger till den i rot-elementet.

Innan vi ser till att vår me-app blir snyggare med hjälp av CSS lägger vi till ytterligare ett element. En navigationsdel som vi senare med hjälp av CSS kommer placera i botten av skärmen för att underlätta för navigation på mobila enheter.

```javascript
"use strict";

(function () {
    var rootElement = document.getElementById("root");

    var mainContainer = document.createElement("main");
    mainContainer.className = "container";

    var title = document.createElement("h1");
    title.className = "title";
    title.textContent = "Emil Folino";

    var greeting = document.createElement("p");
    var timeOfDayGreeting = "Hej";
    var now = new Date();
    if (now.getHours() <= 10) {
        timeOfDayGreeting = "Godmorgon";
    } else if (now.getHours() >= 17) {
        timeOfDayGreeting = "Godkväll";
    }

    greeting.textContent = timeOfDayGreeting + ", jag heter Emil Folino och är lärare i kursen webapp.";

    mainContainer.appendChild(title);
    mainContainer.appendChild(greeting);

    rootElement.appendChild(mainContainer);

    var navigation = document.createElement("nav");
    navigation.className = "bottom-nav";

    var navElements = ["Me", "Om", "Github", "Redovisning"];
    navElements.forEach(function (element) {
        var navElement = document.createElement("a");
        navElement.textContent = element;
        navigation.appendChild(navElement);
    });

    rootElement.appendChild(navigation);
})();
```

Navigationen skapas som ett element med fyra stycken länkar i. En loop används då vi vill skapa fyra exakt likadana element förutom texten i länken. Ta gärna en stund och titta igenom JavaScript koden som vi har skrivit än så länge. Förstår du alla delar?

Nedan syns resultatet och som vi ser är vi definitivt redo för att börja jobba med utseendet för vår me-app.

[FIGURE src=image/webapp/screenshot_beforecss.png?w=c8]



CSS {#css}
--------------------------------------
Vi börjar med att normalisera så att grunden blir den samma oavsett vilken webbläsare våra användare tycker om att titta på våra mobila applikationer i. Vi använder oss av [normalize.css](https://necolas.github.io/normalize.css/) och laddas enklast ner genom att använda `wget`.

```bash
# me/redovisa
wget https://necolas.github.io/normalize.css/7.0.0/normalize.css
```

Och vi lägger till `normalize.css` filen i `index.html` så den laddas och kan nollställa ursprungsstilerna i de olika webbläsare. Notera att jag lägger till `normalize.css` innan vår än så länge tomma `style.css`.

```html
<!-- index.html -->
...
<title>Me-app</title>

<link rel="stylesheet" href="normalize.css" />
<link rel="stylesheet" href="style.css" />
...
```

Vi kommer i denna del fokusera på att göra om navigationen och kommer under redovisningsvyn fokusera på att tillämpa den kunskap vi fick i artikeln "[Typografi i mobila enheter](kunskap/typografi-i-mobila-enheter)".


[Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)


Avslutningsvis {#avslutning}
--------------------------------------
Asynkron programming ställer ofta till med huvudbry för utvecklare, som är vana vid synkron och sekventiell programming. De tre tekniker beskrivna i denna övning underlättar för oss när vi utvecklar vår kod. Men som alltid övning ger färdighet.

Alla kodexempel från denna övningen finns i kursrepot för [linux-kursen](https://github.com/dbwebb-se/linux/tree/master/example/asynkron) och här på [dbwebb](https://dbwebb.se/repo/linux/example/asynkron).

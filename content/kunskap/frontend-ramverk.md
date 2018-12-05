---
author: efo
category:
    - ramverk2
    - verktyg
revision:
    "2018-12-03": "(A, efo) Första utgåvan för ramverk2 version 2 av kursen."
...
Frontend ramverk
==================================

[FIGURE src=image/webapp/javascript-logo.png?w=c5 class="right"]

Vi ska i denna artikel titta på ett antal koncept, som används för att bygga webbapplikationer med hjälp av JavaScript. I artikeln går vi igenom koncepten med hjälp av tre exempel program, som är implementerad i JavaScript ramverken Angular, Mithril, React och Vue, samt i vanilla JavaScript ES5.

<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har bra kunskap om JavaScript och vilka möjligheter som finns i programmeringsspråket.



Introduktion {#intro}
--------------------------------------

Anledningen till att ovanstående tekniker har valts ut är att Angular, React och Vue i 2018 har setts som "The Big Three". Dessa tre ramverk är de tre mest nerladdade JavaScript ramverken under året enligt [npm trends](https://jsreport.io/javascript-frameworks-by-the-numbers-winter-2018/). För att jämföra med tidigare kända tekniker har vi även valt att inkludera JavaScript ramverket mithril som användes i [kursen webapp](https://dbwebb.se/kurser/webapp-v3) och JavaScript ES5, som vi har använt tidigare i bland annat [kursen javascript 1](https://dbwebb.se/kurser/javascript1-v2/).



Exempelprogram {#example}
--------------------------------------

I kursrepots exempel katalog finns tre olika exempel program skrivna med hjälp av de fem ovannämnda teknikerna. I `example/quote` finns ett simpelt program där dagens citat hämtas från ett API. I `example/tic-tac-toe` finns ett luffarschack implementerad med möjlighet att hoppa tillbaka i spelets historik. I `example/calculator` är en simpel miniräknare implementerad.



#### Rader skriven kod i exempelprogrammen {#loc}

I nedanstående tabell listas de rader kod som utvecklaren har skrivit för att implementera exempelprogrammen. De rader som är räknade är enbart de rader som innehåller källkod, så rader med kommentarer och tomma rader är borttagna.

|  | Angular | Mithril | React | Vue | Vanilla JS |
|-----|--------|--------|--------|---------|--------|
| calculator  |  | 103 |  | 98 | 118 (94 i DOM varianten) |
| multipage   |  |  46 |  |  |  59 |
| quote       |  |  47 |  70 |  |  24 |
| tic-tac-toe |  | 136 | 146 |  | 126 |



#### Storlek produktionsfil(er) {#filesize}

I nedanstående tabell listas storleken på produktionsfilerna som skapas av antingen bygg verktyget i ramverket, webpack eller uglify. Filstorlekar är utskrivna med hjälp av kommandot `ls -lh` i ett bash-skal.

|  | Angular | Mithril | React | Vue | Vanilla JS |
|-----|--------|--------|--------|---------|--------|
| calculator  |  | 30K |  |  | 2.6K (1.6K i DOM variant) |
| multipage   |  | 28K |  |  | 1.1K |
| quote       |  | 28K |  |  | 777B |
| tic-tac-toe |  | 29K |  |  | 2.8K |



RealWorld {#realworld}
--------------------------------------

För att ytterligare utvärdera våra valda ramverk tar vi en titt i GitHub repot [RealWorld Example](https://github.com/gothinkster/realworld).



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna artikel skrapat ytan på JavaScript ramverken Angular, Mithril, React och Vue, samt jämfört ramverken med vanilla JavaScript.

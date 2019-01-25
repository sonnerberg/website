---
author: efo
category:
    - nodejs
    - javascript
    - kursen ramverk2
revision:
    "2019-01-24": "(A, efo) Första utgåvan."
...
Integrationstester av backend
==================================

[FIGURE src=image/ramverk2/chai.jpg?w=c5 class="right"]

Vi har tidigare tittat på en testmiljö i JavaScript där vi fokuserade på enhetstester. I denna artikel ska vi bygga vidare på testmiljön och lägga till funktions/integrationstester. Vi bygger vidare med mocha och lägger till testverktygen `chai` och `chai http`.

Vi börjar dock med att fundera lite på vad det egentligen är vi vill testa och hur vi testar hela flödet istället för bara de små enheter.



<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har jobbat igenom övningen [Kom igång med en testmiljö i JavaScript](kunskap/kom-igang-med-en-testmiljo-i-javascript) och har en testmiljö för ditt me-API.



Introduktion {#intro}
--------------------------------------

I konferens keynoten nedan pratar skaparen av Ruby on Rails David Heinemeier Hansson (dhh) om hur hans syn på testning och programmering har ändrats genom åren. Hela keynoten är sevärd, men klippet nedan börjar när han pratar om TDD.

[YOUTUBE src="9LfmrkyP81M" time="24m12s" caption="David Heinemeier Hansson pratar om enhetstester och TDD"]

I keynoten visar dhh ett citat av Seth Godin.

> Just because you can measure it, doesn't mean it's important.

Vi ändrar det i vår värld till.

> Just because you can **test** it, doesn't mean it's important.

Med det vill jag inte argumentera för att vi inte ska skriva tester, men vi vill skriva tester som testar det som användaren ska använda. Ett sätt att göra det för API:er är att testa routerna precis som de anrops av klienter.



Integrationstester {#integrationtesting}
--------------------------------------

dökjfölkjdflkjf


Exempel {#exempel}
--------------------------------------

I [repot för Lager API:t](https://github.com/emilfolino/order_api/tree/master/test) som användes i kursen webapp finns det integrations tester med `chai` och `chai-http`. Ta en titt på detta för att se hur det kan se ut med fler testfall.



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna artikel titta på hur vi kan använda integrationstester för att öka vårt förtroende till att den kod vi skriver gör det den ska.

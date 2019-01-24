---
author: efo
category:
    - nodejs
    - javascript
    - kursen ramverk2
revision:
    "2019-01-24": "(A, efo) Första utgåvan."
...
Funktionstester av backend
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





Avslutningsvis {#avslutning}
--------------------------------------

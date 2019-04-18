---
author:
    - lew
revision:
    "2019-03-26": (A, lew) Ny inför HT19.
...
Kmom05: Docker network
==================================

[WARNING]

**Kursutveckling pågår**

Kursen ges hösten 2019 läsperiod 1.

[/WARNING]

<!--more-->

Nu har vi kontroll på hur vi kan hantera en webbserver i Docker. Tanken är nu att vi ska skapa en webbplats som använder den server som skapades i föregående kursmoment. Webbplatsen ska köras i en egen kontainer. Vi ska se hur vi kan lösa det med hjälp av "Docker network", där vi låter Docker skapa ett eget nätverk.

Så är upplägget. Låt se hur bra vingarna bär. Upplägget på detta kursmomentet är "lite friare", så vi går nästan rakt på själva uppgiften.

<!--more-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Det finns ingen läsanvisning i kurslitteraturen.

<!--
http://exploringjs.com/es6/index.html
-->



###Artiklar {#artiklar}

TBD

<!-- 1. Läs igenom hur du med Bash kan skapa ett mer avancerat kommandoradsprogram som tar argument. Artikeln ["Skapa Bash-skript med options, command och arguments"](kunskap/skapa-bash-skript-med-options-command-och-arguments) ger dig en struktur till hur du kan skapa mer avancerade och större Bash-skript. -->



###Video  {#video}

Titta på följande:

TBD

<!-- 1. Till kursen finns en videoserie, "[linux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_AGc9pBgaXFEQGjyFJe7XJ)", kika på de videor som börjar på 5.

1. Se videon om "[REST API concepts and examples](https://www.youtube.com/watch?v=7YcW25PHnAA)". Den visar exempel på grunderna i REST API och hur det förhåller sig till en webb URL.

1. I labbarna node1 - node3 skrapar vi ytan på funktionell programmering. Titta gärna på denna [spellista](https://www.youtube.com/playlist?list=PL0zVEGEvSaeEd9hlmCXrk5yUyqUag-n84) av MPJ som är programmerare på Spotify. -->

###Lästips {#lastips}

TBD

<!-- 1. Det finns en webbplats som föreslår en [JSON API specifikation](http://jsonapi.org/). Du kan titta översiktligt på den, börja med stycket om "Fetching Data". Specifikationen ger oss en guide, eller ledtrådar och tips, till hur man kan skriva ett JSON API för en server.

1. nodejs har ett [api](https://nodejs.org/api/) där de inbyggda funktionerna är dokumenterade, läs igenom översiktligt och använd som referens när du programmerar.

1. Följ gärna med i forumtråden [Functional Programming](https://dbwebb.se/forum/viewtopic.php?f=36&t=5980) där funktionell programmering diskuteras i allmänhet. -->

Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-14 studietimmar)*



###Övningar {#ovningar}

<!-- Det finns inga övningar. -->

1. Läs om [Docker network](guide/docker/docker-network) i guiden.


###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

<!-- 1. Gör uppgiften [node2](uppgift/linux-lab4-asynkron-programmering) för att träna på nodejs api funktioner.

1. Gör uppgiften "[Lös mazen med din mazerunner i bash](uppgift/los-mazen-med-din-mazerunner-i-bash)". -->

<!--
VT18 ÄNDRA TILL GENERELL LAB MED NODE
Gör laborationen [Node.js och inbyggda moduler (node2)](uppgift/nodejs-inbyggda-moduler) för att träna på inbyggda moduler i Node.js.
-->



###Extra {#extra}

Det finns inga extra uppgifter.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

TBD
<!-- * Hur kändes det att bekanta sig med inbyggda nodejs moduler?
* Är du bekant med JSON API sedan tidigare?
* Hur kändes det att skriva ett litet större bash-skript? Var det något som var mer eller mindre utmanande och tidskrävande?
* Kikade du på källkoden till maze-servern? Har du några reflektioner kring den?
* Är du nöjd med din mazerunner? Gjorde du nåt speciellt som du vill lyfta fram? -->

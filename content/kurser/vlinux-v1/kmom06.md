---
author:
    - lew
revision:
    "2019-03-26": (A, lew) Ny inför HT19.
...
Kmom06: Docker Compose
==================================

[WARNING]

**Kursutveckling pågår**

Kursen ges hösten 2019 läsperiod 1.

[/WARNING]

Nu har vi koll på hur vi kan strukturera lite större Bash-script. Vi ska gå vidare med Docker och kika på *Docker Compose*. Det underlättar för oss när Docker konstruktionerna växer. Vi ska ta vår Mazerunner från förra kursmomentet och använda oss utav Docker Compose för att köra igång kontainrarna och nätverket. Vi ska även lägga till lite funktionalitet till Mazerunner. Utöver Bash och Docker Compose ska vi titta på vad reguljära uttryck är och hur vi kan arbeta med dem.

<!--more-->

Du kommer skapa en spel-loop till din Mazerunner, likt nedan:

[ASCIINEMA src=244597]

Så kan det se alltså ut när ena delen är klar.



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 0 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Det finns ingen läsanvisning.
<!--
INFÖR VT18
Läs följande.

1. [Exploring ES6](kunskap/boken-exploring-es6) om Promise.
    * Ch 24: Asynchronous programming (background)
    * Ch 25: Promises for asynchronous programming
-->



###Artiklar {#artiklar}

Det finns inga artiklar.



###Video  {#video}

Titta på följande:

<!-- 1. Till kursen finns en videoserie, "[linux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_AGc9pBgaXFEQGjyFJe7XJ)", kika på de videor som börjar på 6. -->

<!-- 1. I labbarna node1 - node3 skrapar vi ytan på funktionell programmering. Titta gärna på denna [spellista](https://www.youtube.com/playlist?list=PL0zVEGEvSaeEd9hlmCXrk5yUyqUag-n84) av MPJ som är programmerare på Spotify. -->



###Lästips {#lastips}

<!-- 1. Följ gärna med i forumtråden [Functional Programming](https://dbwebb.se/forum/viewtopic.php?f=36&t=5980) där funktionell programmering diskuteras i allmänhet. -->




Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-18 studietimmar)*



### Övningar {#ovningar}

Genomför följande övningar.

1. Gå igenom delen i guiden som handlar om "[Docker Compose](guide/docker/docker-compose)".

<!-- 1. Läs igenom övningen "[Spela luffarschack med klient och server i Node.js](kunskap/spela-luffarschack-med-klient-och-server-i-node-js)". -->



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften [lab 3](uppgift/vlinux-lab-sed1) för att träna upp grundläggande färdigheter i reguljära uttryck.

1. Gör uppgiften [Spel loop i Mazerunner](uppgift/mazerunner-loop). Du arbetar i mappen `maze2/`.

<!-- 1. Gör uppgiften "[Skapa klienter och servrar som spelar luffarschack i Node.js](uppgift/skapa-klienter-och-servrar-som-spelar-luffarschack-i-node-js)". -->

<!-- 1. Gör uppgiften [Lab 5](uppgift/linux-lab5-fortsattning-asynkron-programmering) för att träna ytterligare på asynkron programmering. -->



###Extra {#extra}

<!-- 1. Förbered din kod för Gomocup. -->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Hur väl har du fått ordning på begreppen kring klient och server?
* Känner du dig bekväm med Docker överlag?
* Kommer du använda Docker utanför kursens ramar?
* Gjorde du någon uppdatering av Mazerunnerns struktur?

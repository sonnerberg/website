---
author:
    - lew
revision:
    "2019-03-26": (A, lew) Ny inför HT19.
...
Kmom04: En webbserver i Docker
==================================

[WARNING]

**Kursutveckling pågår**

Kursen ges hösten 2019 läsperiod 1.

[/WARNING]

<!--more-->

Nu vet vi hur vi bygger en egen image med hjälp av Docker. Vi har också gått igenom hur vi kan strukturera ett Bash-script som även exekveras inuti en kontainer. Vi tar ett steg till och tittar på hur vi kör en webbserver inuti Docker. I det här kursmomentet får du välja om du vill leka med Apache/php, Python eller JavaScript. Huvudsaken är att du får igång en server med en router som kan serva en JSON-fil.

<!-- Vi tar ett steg till och tittar på *volymer* i Docker. Än så länge har vi kopierat in datan och då gjort den statisk. När vi utvecklar med hjälp av Docker kan det vara bra att inte behöva bygga om imagen efter vi gjort ändringar. Det kan även vara så att applikationen som utvecklas förlitar sig på en lokal mapp som ska användas, oberoende av var kontainern körs. Till vår hjälp har vi då så kallade volymer. Kortfattat så "mountar" vi en mapp lokalt och delar den delen av filsystemet med kontainern. Vi ska också lära oss att -->

<!--more-->

<!-- [ASCIINEMA src=24691]

[ASCIINEMA src=22554] -->


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-8 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

TBD



###Video  {#video}

Titta på följande:

<!-- 1. Till kursen finns en videoserie, "[linux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_AGc9pBgaXFEQGjyFJe7XJ)", kika på de videor som börjar på 4. -->



###Lästips {#lastips}



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*

###Övningar {#ovningar}

Genomför följande övningar.

1. Jobba igenom guiden/artikeln "[sed, awk](guide-artikel/sed)".

1. Jobba igenom guiden/artikeln "[en router](guide/php-eller-js-eller-python?)".

1. Jobba igenom guiden/artikeln "[volymer](guide/volymer-delen)".


<!-- 1. Jobba igenom guiden "[Bygg en RESTful server med Node.js](kunskap/bygg-en-restful-server-med-node-js)".

1. Jobba igenom artikeln "[Skicka environment variabler till Bash och Node.js ](kunskap/skicka-environment-variabler-till-bash-och-node-js)".

1. Jobba igenom artikeln "[Spara serverns processid i en fil](kunskap/spara-serverns-processid-i-en-fil)". -->



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[sed-labb?](uppgift/something)".

1. Gör uppgiften "[Välj ett språk php/js och serva en json fil](uppgift/something)".  
ska fungera via webbläsaren.
Motivera valet?

1. Gör uppgiften "[Bash-script som curlar serverns routes](uppgift/something)".  
spara till fil



<!-- 1. Gör uppgiften [Lab 3](uppgift/linux-lab3-introduktion-till-nodejs)  -->

<!-- 1. Gör uppgiften "[Skapa en RESTful HTTP-server med Node.js och klient i Bash](uppgift/skapa-en-restful-http-server-med-node-js-och-klient-i-bash)". -->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

<!-- * Är detta din första bekantskap med JavaScript på servern eller har du testat det tidigare?
* Vad tänker du om ECMA6, dess nya funktioner jämfört med ES5?
* Hur gick det att förstå koncepten kring klient och server?
* Är du bekant med begreppet funktionell programmering och har du några tankar kring det? -->

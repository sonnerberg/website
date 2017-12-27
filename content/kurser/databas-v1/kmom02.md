---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom02: SQL
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Vi jobbar vidare med SQL och tränar mer på både enklare konstruktionerna och mer utmanande saker som vyer, subqueries och `RIGHT/LEFT OUTER JOIN`. När övningen är slut så har du både kommit in i MySQL och du har god översikt av olika baskonstruktioner med SQL.

Du kommer även jobba med JavaScript och Node.js för att se hur du kan koppla dig till en MySQL databas via ett applikationsspråk. Det innebär att du behöver installera en labbmiljö med Node.js och pakethanteraren npm.

<!--more-->

<!--
[FIGURE src=/image/snapht17/anax-flat-start.png?w=w2 caption="En me-sida med PHP-ramverket Anax Flat."]
-->


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [Databasteknik](kunskap/boken-databasteknik) om mer SQL.
    * Kap 8: Mer om SQL: Aggregatfunktioner, null-värden, yttre join
    * Kap 20: SQL inuti ett program

Vissa av kapitlen finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 2.

Det finns ytterligare ett kapitel i boken som är relaterat till SQL, det går utanför kursens ram men läs vid intresse.

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 10: Relationsalgebra

**LÄSANVISNING ES5**

1. [Exploring ES6](kunskap/boken-exploring-es6). Läs inledande kapitlet för att få en grov känsla av ES6 kontra ES5.
    * Ch 1: About ECMAScript 6 (ES6)
    * Ch 2: FAQ: ECMAScript 6

<!--
1. I boken [Exploring ES6](kunskap/boken-exploring-es6) handlar kapitel 15 om klasser och kapitel 16 om moduler, två goda sätt att strukturera sin kod i ES6.
-->

<!--
1. Bekanta dig med kurslitteraturen [Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript) genom att läsa igenom det första kapitlet [Ch1 Basic JavaScript](http://speakingjs.com/es5/ch01.html) (läs till och med stycket om "Strict Mode") som ger dig en introduktion till grundkonstruktioner i programmeringsspråket JavaScript.


1. [Speaking JavaScript](kunskap/boken-speaking-javascript).

    1. [Part I. JavaScript Quick Start](http://speakingjs.com/es5/pt01.html) läs översiktligt för att få en introduktion till språket.
    1. [Ch 13: Statements](http://speakingjs.com/es5/ch13.html)

1. [Speaking JavaScript](kunskap/boken-speaking-javascript).

    1. [Ch 15: Functions](http://speakingjs.com/es5/ch15.html)
    1. [Ch 16: Variables: Scopes, Environments, and Closures](http://speakingjs.com/es5/ch16.html)
-->



###MDN dokumentation {#mdn}

I kursen används Mozilla Developers Network (MDN) som en resurs generellt för webbresurser och specifikt för referensmanual till programmeringsspråket JavaScript.

Vill du hamna på rätt manualsida så lägger du alltid till "mdn" till din googling. Det finns många versioner av JavaScript och du vill gå tillbaka till källan i referensmanualen för att veta vad som är rätt (eller fel).

1. För en snabb introduktion till konstruktionerna i språket JavaScript kan jag rekommendera dokumentet "[MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)" och de inledande kapitlen som kompletterar det du läst i kurslitteraturen.
    * Introduction
    * Grammar and types
    * Expressions and operators



###Node.js dokumentation {#nodejs}

Node.js är en påbyggnad till grunden i JavaScript. Via webbplatsen för Node.js finner du referensdokumentationen med de delar som är specifika för Node.js.

1. Bekanta dig med [dokumentationen till Node.js](https://nodejs.org/en/docs/). Kika översiktligt på API dokumentationen för den senaste LTS-versionen (Long Time Support).



###Artiklar {#artiklar}

Läs följande:

1. I kursen används validatorer och en kodstandard för att testa att du skriver kod på ett, enligt kodstandarden, acceptabelt sätt. Du kan läsa om dbwebb-kodstandarden på [npm javascript-code-style](https://www.npmjs.com/package/javascript-style-guide). Du kan diskutera [kodstandarden i forumet](t/6327).


<!--
###Video  {#video}

Titta på följande:

1. Videoserien [Lär dig JavaScript](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_YXUQlr5aAzJ406vSsmeMT) är tätt kopplat till kursmaterialet. Kika igenom serien under kursens gång.
-->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Labbmiljö

Installera labbmiljön för nodejs delen av kursen.

1. [Installera nodejs och npm](kunskap/installera-node-och-npm)



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

1. Lös övningen...

1. **JS/Node.js klient?**

<!--

Någon övning som ger grunderna i Node.js och JavaScript på servern? Till någon som redan kan programmera.


1. Jobba igenom övningen "[Gör en kommandoradsklient i Node.js](kunskap/gor-en-kommandoradsklient-i-node-js)". Spara dina eventuella exempelprogram under `me/kmom04/client`.

1. Jobba igenom artikeln "[Skicka environment variabler till Node.js](kunskap/skicka-environment-variabler-till-nodejs)".

1. ??? Jobba igenom artikeln "[SQLite och Node.js](kunskap/sqlite-och-nodejs)". Spara dina exempelprogram i `me/kmom03/sqlite`.

-->

<!--

1. Jobba igenom övningen "[MySQL och Node.js](kunskap/mysql-och-nodejs)". Spara dina eventuella exempelprogram under `me/kmom04/npm-mysql`.

1. I artikeln "[Node.js, MySQL och Promise](kunskap/nodejs-mysql-och-promise)" kan du få hjälp att lösa ett problem med asykron/sekventiell programmering som du troligen kommer att upptäcka senare i uppgiften `terminal`.
-->

<!--
1. [Exploring ES6](kunskap/boken-exploring-es6) om Promise.
    * Ch 24: Asynchronous programming (background)
    * Ch 25: Promises for asynchronous programming
-->



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Jobba igenom uppgiften "[Kom igång med SQL (del 2)](uppgift/kom-igang-med-sql)" genom att utföra den i MySQL Workbench. Spara all SQL-kod i `me/kmom04/skolan/skolan.sql` och utför minst 2/3 av uppgifterna. Dokumentera vilka uppgifter du hoppar över. Jobba gärna i grupp och hjälp varandra, men se alltid till att skriva dina egna SQL-satser. Se till att du förstår begreppen HAVING, subqueries och OUTER JOIN. (läs in data från CSV, kopiera från tabell till tabell)

1. **JS/Node.js klient?**

<!--

1. Gör laborationen "[Node.js och inbyggda moduler (node2)](uppgift/nodejs-inbyggda-moduler)" för att träna på inbyggda moduler i Node.js. Spara koden i `me/kmom04/node2`.

1. Gör uppgiften "[Node.js terminalprogram mot MySQL](uppgift/nodejs-terminalprogram-mot-mysql)". Spara koden i `me/kmom04/terminal`.
-->



<!--
1. Gör laborationen "[Introduktion till nodejs (node1)](uppgift/introduktion-till-nodejs)" för att öva på grunderna i nodejs. Spara koden i `me/kmom03/node1`.

1. Gör laborationen "[SQL lab, fortsättning med SQL (sql2)](uppgift/sql-lab-fortsattning-med-sql)" som låter dig fortsätta träna på SQL med SQLite. Spara koden i `me/kmom03/sql2`.

-->



###Extra {#extra}

Gör följande extrauppgifter om du har tid och lust.

1. Jobba igenom guiden "[Kom igång med tmux och terminalen](kunskap/kom-igang-med-tmux-och-terminalen)" för att lära dig hur du jobbar mer effektivt i terminalen med tmux. Tmux ger dig möjlighet att dela in din terminal i olika flikar och varje flik i olika delar.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Du har nu repeterat SQL ett par gånger, börjar det sätta sig?
* Är detta den första bekantskap med JavaScript på serversidan och Node.js, hur känns det?
* Gick det smärtfritt att koppla ihop Node med SQLite?
* Fanns det något som var extra utmanande eller någon större svårighet i detta kursmomentet?
* Vilken är din TIL för detta kmom?

<!--
* Hur känns det med Node.js, har du till exempel känt av den asynkrona programmeringsmodellen?
* Förstod du hur Promise fungerar?
-->

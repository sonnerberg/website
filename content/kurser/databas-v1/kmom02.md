---
author: mos
revision:
    "2018-01-02": (A, mos) Första utgåvan.
...
Kmom02: SQL
====================================

Vi jobbar vidare med SQL och tränar mer på både enklare konstruktionerna och mer utmanande saker som vyer, subqueries, UNION och JOIN.

Du kommer även jobba med JavaScript och Node.js för att se hur du kan koppla dig till en MySQL databas via ett applikationsspråk. Det innebär att du behöver installera en labbmiljö med Node.js och pakethanteraren npm.

<!--more-->

[FIGURE src=/image/snapvt18/guide-skolan-select.png?w=w3 caption="Guiden hjälper oss med mer avancerade konstruktioner i SQL."]

[FIGURE src=/image/snapvt18/nodejs-mysql-search.png?w=w3 caption="Med JavaScript och Node.js bygger du ett skript som kopplar sig till din databas."]


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 6-8 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:



#### Databasteknik {#dbteknik}

1. [Databasteknik](kunskap/boken-databasteknik) om mer SQL.
    * Kap 8: Mer om SQL: Aggregatfunktioner, null-värden, yttre join
    * Kap 20: SQL inuti ett program

Vissa av kapitlen finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 2.

Det finns ytterligare ett kapitel i boken som är relaterat till SQL, det går utanför kursens ram men läs vid intresse.

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 10: Relationsalgebra



#### JavaScript {#javascript}

1. Bekanta dig med boken [Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript) genom att översiktligt läsa igenom följande kapitel som ger dig en introduktion till grundkonstruktioner i programmeringsspråket JavaScript.
    * [Ch 1: Basic JavaScript](http://speakingjs.com/es5/ch01.html) (läs till och med stycket om "Strict Mode")
    * [Ch 13: Statements](http://speakingjs.com/es5/ch13.html)

1. Bekanta dig med boken [Exploring ES6](kunskap/boken-exploring-es6). Skumläs ett av de inledande kapitlen för att få en grov känsla av ES6 kontra ES5.
    * [Ch 4: Core ES6 features](http://exploringjs.com/es6/ch_core-features.html)



###MDN dokumentation {#mdn}

I kursen används [Mozilla Developers Network (MDN)](https://developer.mozilla.org/) som en resurs generellt för webbresurser och specifikt för referensmanual till programmeringsspråket JavaScript.

Vill du hamna på rätt manualsida så lägger du alltid till "mdn" till din googling. Det finns många versioner av JavaScript och du behöver ofta gå tillbaka till källan i referensmanualen för att veta vad som är rätt (eller fel).

1. För en snabb introduktion till konstruktionerna i språket JavaScript kan jag rekommendera dokumentet "[MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)" och de inledande kapitlen som kompletterar det du läst i kurslitteraturen.
    * Introduction
    * Grammar and types
    * Expressions and operators



###Node.js dokumentation {#nodejs}

[Node.js](https://nodejs.org/) låter dig köra JavaScript utan en webbläsare. Via webbplatsen för Node.js finner du referensdokumentationen med de delar och moduler som är specifika för JavaScript i sammanhanget Node.js. Node.js innehåller ett API som bland annat ger dig tillgång till operativsystemets resurser och låter dig skriva terminalprogram.

1. Bekanta dig med [dokumentationen till Node.js](https://nodejs.org/en/docs/). Kika översiktligt på API dokumentationen för den senaste LTS-versionen (Long Time Support).



###Artiklar {#artiklar}

Läs följande:

1. I kursen används validatorer och en kodstandard för att testa att du skriver kod på ett, enligt kodstandarden, acceptabelt sätt. Du kan läsa kort om dbwebb-kodstandarden på [npm javascript-code-style](https://www.npmjs.com/package/javascript-style-guide). Du kan diskutera [kodstandarden i forumet](t/6327).



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Labbmiljö

Installera följande.

1. Installera labbmiljön för Node.js och npm via "[Installera nodejs och npm](labbmiljo/node-och-npm)".



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

<!--
Någon övning som ger grunderna i Node.js och JavaScript på servern? Till någon som redan kan programmera. Kanske labbverktyget, kombinera labbarna i js1 och node, enkla till någon som kan programmera men inte kan js?

1. Gör laborationen "[Introduktion till nodejs (node1)](uppgift/introduktion-till-nodejs)" för att öva på grunderna i nodejs. Spara koden i `me/kmom03/node1`.
-->

1. Jobba igenom artikeln "[MySQL och Node.js (v2)](kunskap/mysql-och-nodejs-v2)" som visar hur du kommer igång med programmeringsspråket JavaScript i miljön Node.js och hur du kopplar ett program till databasen MySQL. Spara dina exempelprogram under `me/kmom02/search`.



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Jobba igenom delen "Mer SQL" av guiden "[Kom igång med SQL i MySQL (Mer SQL)](guide/kom-igang-med-sql-i-mysql/mer-sql)". Spara all SQL-kod i filer i katalogen `me/kmom02/skolan2`. Du behöver kopiera alla skript du redan sparat i `me/kmom01/skolan1` och utgå från dem och bygga vidare.

1. Lös uppgiften "[Node.js terminalprogram mot MySQL (v2)](uppgift/nodejs-terminalprogram-mot-mysql-v2)". Spara alla filer i `me/kmom02/terminal1`.

<!--
Enkel SQL laboration som visar att studenten kan göra joins/subquery.

1. Gör laborationen "[SQL lab, fortsättning med SQL (sql2)](uppgift/sql-lab-fortsattning-med-sql)" som låter dig fortsätta träna på SQL med SQLite. Spara koden i `me/kmom03/sql2`.
-->



###Extra {#extra}

Gör följande extrauppgifter om du har tid och lust.

1. I nästa kmom kommer du att göra nästa del av guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql)". Du kan redan nu tjuvkika på guidens kommande delar.

1. Jobba igenom guiden "[Kom igång med tmux och terminalen](kunskap/kom-igang-med-tmux-och-terminalen)" för att lära dig hur du jobbar mer effektivt i terminalen med tmux. Tmux ger dig möjlighet att dela in din terminal i olika flikar och varje flik i olika delar.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Du har nu repeterat SQL ett par gånger, börjar det sätta sig, är det något du finner extra utmanande?
* Är detta den första bekantskap med JavaScript på serversidan och Node.js, hur känns det?
* Gick det smärtfritt att koppla ihop JavaScript, Node.js med MySQL?
* Vilken är din TIL för detta kmom?

---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom03: ER-modellering
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Vi övar i hur man modellerar och bygger upp en databas, det som kallas Entity-Relationship modelling, ER-modellering.

Vi jobbar vidare med SQL och tränar mer på utmanande saker som subqueries, JOIN och LEFT/RIGHT OUTER JOIN.

Vi bygger vidare på våra terminalskript i JavaScript och Node.js och kopplar dem till databasen.

<!--more-->

<!--
[ERBILD]
-->


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 8: (repetera) Mer om SQL: Aggregatfunktioner, null-värden, yttre join
    * Kap 2: ER-modellering
    * Kap 4: Designpocessen
    * Kap 5: Relationsmodellen
    * Kap 6: Översättning från ER-modellen till relationsmodellen

En översikt av kapitel ovan  finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 1.


<!--
Saker vi inte hanterat:

* Kap 3: Mer om datamodellering
* Kap 11: Normalformer och normalisering
-->


<!--
1. [Speaking JavaScript](kunskap/boken-speaking-javascript).

    1. [Ch 15: Functions](http://speakingjs.com/es5/ch15.html)
    1. [Ch 16: Variables: Scopes, Environments, and Closures](http://speakingjs.com/es5/ch16.html)
-->



###Artiklar {#artiklar}

Läs igenom följande artiklar.

1. Jobba igenom artikeln "[Kokbok för databasmodellering](kunskap/kokbok-for-databasmodellering)", den ger dig ett exempel på databasmodellering och dess olika faser.


<!--stop-->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

1. Jobba igenom delen "Koppla tabeller" av guiden "[Kom igång med SQL i MySQL (Koppla tabeller)](guide/kom-igang-med-sql-i-mysql/koppla-tabeller)". Spara all SQL-kod i filer i katalogen `me/kmom03/skolan3`. Du kan gärna kopiera de skript du sparat tidigare och utgå från dem.

1. **? (extra i dbjs)** Skapa en ER-modell för din databas Skolan via [reverse engineering med MySQL Workbench](coachen/reverse-engineering-av-databasen-mysql-med-workbench).

1. Gör några extra övningar från övningsfilen (skall redovisas).

<!--
1. **JS/Node.js klient?** kommandoradsklient. (CRUD), Lönerevision

1. Jobba igenom övningen "[Gör en kommandoradsklient i Node.js](kunskap/gor-en-kommandoradsklient-i-node-js)". Spara dina eventuella exempelprogram under `me/kmom04/client`.

1. Jobba igenom artikeln "[Skicka environment variabler till Node.js](kunskap/skicka-environment-variabler-till-nodejs)".

-->



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Skapa ER-modell av databasen Jetty](uppgift/skapa-er-modell-av-databasen-jetty)" för att träna på ER-modellering. (inklusive SQL, läs in data från CSV, kopiera från tabell till tabell)

1. Lös uppgiften ....

1. **KOPPLA SQL TILL KLIENT JS**

1. Gör uppgiften "[Bygg en faktureringsmotor för båtklubben (invoice)](uppgift/bygg-en-faktureringsmotor-for-batklubben)". Spara koden i `me/kmom03/invoice`.

<!--
1. Gör laborationen "[Node.js och inbyggda moduler (node2)](uppgift/nodejs-inbyggda-moduler)" för att träna på inbyggda moduler i Node.js. Spara koden i `me/kmom04/node2`.
-->

<!--
Enkel SQL laboration som visar att studenten kan göra joins/subquery.

1. Gör laborationen "[SQL lab, fortsättning med SQL (sql2)](uppgift/sql-lab-fortsattning-med-sql)" som låter dig fortsätta träna på SQL med SQLite. Spara koden i `me/kmom03/sql2`.
-->




Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* 
* Vilken är din TIL för detta kmom?

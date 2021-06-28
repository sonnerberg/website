---
views:
    flash:
        region: flash
        template: default/image
        data:
            src: "image/webtec/logo-sql.png"
author:
    - mos
revision:
    "2021-05-20": "(PA, mos) Arbete påbörjat för webtec-v1."
...
Kmom05/06: SQL
==================================

[WARNING]

**Arbete pågår**.

[/WARNING]

<!-- stop-->

Låt oss börja med databaser. Vi skall titta på databasen SQLite som är en filbaserad databas. En filbaserad databas förenklar hanteringen eftersom databasen ligger i en enda fil och det finns inga användare eller behörigheter att konfigurera.

Till databasen SQLite behövs klientprogram som kan användas för att prata med databasen. Vi prövar olika klienter, en variant för desktop och en terminalbaserad.

I en databas, en relationsdatabas som SQLite, så pratar vi SQL med databasen. Vi skriver SQL uttryck för att skapa tabeller och för att lägga till, uppdatera, visa och radera data från databasen.

När vi kan vår SQL så använder vi den kunskapen till att koppla samman PHP och databasen för att bygga en databasdriven webbplats. Via webbplatsen skall du kunna lägga till, uppdatera och ta bort innehåll. Detta är de vanliga funktionerna för create, read, update, delete och kallas även CRUD.

<!--more-->

<!--

Uppdatera med nya bilder.

[FIGURE src=image/snapht18/jetty-select-where-andor.png?w=w3 caption="Med SQL kan man ställa frågor mot databasen och visa urval av dess innehåll."]

När vi väl bekantat oss med SQLite, dess klienter och SQL så tar vi ett första steg in i att koppla ihop PHP-kod med databasen.

[FIGURE src=/image/snapvt15/pdo-select-table.png?w=w3 caption="En databas har tabeller med kolumner och rader, det finns olika sätt att visualisera detta."]

Vi avslutar med en programmeringsövning där du bygger en databasdriven webbplats.

-->


<small><i>Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.</i></small>



Studieplan & Upplägg {#studieplan}
---------------------------------

Följande är förslag till en grov och övergripande studieplan för att genomföra kursmomentet. Läs igenom hela dokumentet, innan du bestämmer din plan, det kan finnas mer aktiviteter och lärmoment som är relevanta att utföra inom ramen för kursmomentet.

<small><i>Kursmomentet omfattar cirka **20 + 20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke.</i></small>



### Del 1: SQL och SQLite {#v1}

Börja med att installera terminalklienten `sqlite3` som låter dig jobba mot en SQLite databas.

* Labbmiljö: [En kommandoradsklient för SQLite](labbmiljo/sqlite3)

Titta på följande föreläsningar. Föreläsningarna kan innehålla ytterligare läsanvisningar.

* [SQLite, en filbaserad databas](./../forelasning/sqlite-en-filbaserad-databas)
* [SQL med SQLite](./../forelasning/sql-med-sqlite)

Jobba på egen hand igenom följande artikel/övning.

* [Kom igång med SQL och databasen SQLite med terminalklienten sqlite3](kunskap/kom-igang-med-sql-och-databasen-sqlite-med-terminalklienten-sqlite3) (**artikeln är under bearbetning och uppdatering inför ht21**)

Delta i lektionen som förbereder dig för veckans uppgift.

* I lektionen "[Bygg en databas med SQL](./../forelasning/bygg-en-databas-med-sql)" får du hjälp att komma igång med uppgiften. Lektionen spelas in.

Genomför veckans uppgift.

* Gör uppgiften "[Bygg en databas med SQL](uppgift/bygg-en-databas-med-sql)".

<!--

1. Gör laborationen "[SQL lab 1, introduktion till SQL](uppgift/sql-lab-1-introduktion-till-sql)" som låter dig träna på SQL kommandon.

-->



### Del 2: Terminalprogram och webbplats med PHP PDO, SQL och SQLite {#v2}

Titta på följande föreläsningar. Föreläsningarna kan innehålla ytterligare läsanvisningar.

* [PHP PDO och databaser](./../forelasning/php-pdo-och-databaser)
* [Databasdriven webbplats med CRUD](./../forelasning/webbplats-med-crud)

Jobba på egen hand igenom följande övning.

* [Kom igång med SQLite och PHP PDO (v2)](kunskap/kom-igang-med-sqlite-och-php-pdo-v2) (**artikeln är under bearbetning och uppdatering inför ht21**)

Det är två uppgifter som skall utföras och det finns en lektion som förbereder dig inför varje uppgift.

1. Gör uppgiften "[Bygg en databasdriven terminalklient med PHP och SQL](uppgift/bygg-en-databasdriven-terminalklient-med-php-och-sql)".
    * I lektionen "[Bygg en databasdriven terminalklient med PHP och SQL](./../forelasning/bygg-en-databasdriven-terminalklient-med-php-och-sql)" får du hjälp att komma igång med uppgiften. Lektionen spelas in.

1. Gör uppgiften "[Bygg en databasdriven webbplats med PHP och SQL](uppgift/bygg-en-databasdriven-webbplats-med-php-och-sql)".
    * I lektionen "[Bygg en databasdriven webbplats med PHP och SQL](./../forelasning/bygg-en-databasdriven-webbplats-med-php-och-sql)" får du hjälp att komma igång med uppgiften. Lektionen spelas in.



<!--
1. Gör uppgiften "[Gör en multisida för att söka i en databas](uppgift/bygg-en-multisida-for-att-soka-i-en-databas)". Spara filerna under `me/kmom05/jetty`.

1. Gör uppgiften "[Lab 6: PHP PDO och databasen SQLite](uppgift/php-lab6-php-pdo-och-databasen-sqlite)". Spara filerna i katalogen `me/kmom06/lab6`.

1. Gör uppgiften "[Bygg ut din htmlphp me-sida till version 5](uppgift/htmlphp-projekt-5)". Spara filerna i katalogen `me/kmom05/me5`.

1. Gör uppgiften "[Bygg ut din me-sida till version 6](uppgift/bygg-ut-din-htmlphp-me-sida-till-version-6)". Spara filerna i katalogen `me/kmom06/me6`.

1. Lägg till en inloggning på din mesida och styr så att man måste vara inloggad för att kunna redigera (lägga till, uppdatera, radera) i databasen. Kursrepot innehåller ett exempel på login i `example/login` som du kan utgå ifrån. Använd doe:doe och admin:admin som användare och lösenord.

1. Flytta användare och lösenord från din `config.php` och lägg in dem i en ny tabell i databasen.

-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs instruktionen om [hur du skall redovisa](./../redovisa).

För att avrunda detta kmom, se till att följande frågor besvaras i redovisningstexten.

* Hur kändes det att bygga en databasdriven webbplats?
* Lyckades du återanvända koden till databasen mellan terminalprogrammet och webbplatsen?
* Vilken är din TIL för detta kmom?

Glöm inte att testa din inlämning med `dbwebb test kmom05`.

<!--
* Var det lätt att förstå SQL eller kändes det som en helt ny teknik?
* Var detta din första bekantskap med databaser och SQL, eller har du tidigare kunskaper som du kan relatera till?
* Hur gick det att utföra övningarna med enbart SQLite, var det något du fastnade på?
* Hur gick det med övningarna i PDO och SQLite, var det något som tog extra mycket tid?
* Gjorde du något extra, utöver det vanliga, i ditt arbete? Berätta gärna om det.

* Fick du hjälp av PHP PDO-artikeln och dess kod, eller skrev du mycket kod själv?
* Var det något som var extra svårt eller utmanande i kursmomentet?
* Nu när kursen närmar sig slutet, känns det som du har kommit in i HTML, CSS, PHP och SQL?
* Berätta kort om din syn på din me-sida, är du nöjd med den, eller ser du förbättringspotential?
* Gjorde du något extra, utöver det vanliga, i ditt arbete? Berätta gärna om det.
-->



Resurser & Referenser {#resurser}
---------------------------------

Här anges referenser och övriga resurser som kan användas för vidare studier i det som kursmomentet omfattar.



### SQLite {#sql}

Grundläggande resurser för SQLite äro följande.

* [SQLite](https://www.sqlite.org/index.html)
* [Exempel från SQL-manualen, SELECT](https://www.sqlite.org/lang_select.html)

Det finns flera klienter som man kan använda till SQLite.

* Desktop: [Kom igång med databasen SQLite med DB Browser för SQLite](kunskap/kom-igang-med-databasen-sqlite-med-db-browser-for-sqlite)
* Webb: [En webbaserad klient för SQLite, phpliteadmin](kunskap/en-webbaserad-klient-for-sqlite-phpliteadmin)



### W3Schools SQL {#w3sphp}

Webbplatsen W3Schools har en guide som är lättilgänglig när man vill komma igång med grunderna i SQL.

1. [SQL Tutorial](https://www.w3schools.com/sql/)
1. [PHP MySQL Database](https://www.w3schools.com/php/php_mysql_intro.asp). Även om guiden handlar om MySQL så är det samma interface i PHP, PHP PDO, och det används även till SQLite.



### PHP {#php}

Följande delar är relevanta för PHP.

1. [PHP Data Objects (PDO)](http://php.net/manual/en/intro.pdo.php). Kika översiktligt på det. Det handlar om ett gemensamt gränssnitt för att koppla sig mot flera olika databaser.



### Video för orientering {#video}

Titta på följande videor/filmer. Filmerna är tänkta att ge dig en liten orientering i det område som behandlas i kursmomentet.

* [Richard Hipp, SQLite main author - Two Weeks of Databases #DB2W](https://www.youtube.com/watch?v=2eaQzahCeh4) (57 min)
* [An Introduction to SQLite (by Richard Hipp)](https://www.youtube.com/watch?v=giAMt8Tj-84) (51 min)

Videorna ovan finner du även i spellistan "[ Om webbutveckling (HTML, CSS, PHP, SQL)](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-Qp6DTS_2s6q-Br66ufoWc)".

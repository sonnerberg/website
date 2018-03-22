---
author: mos
revision:
    "2018-03-22": (C, mos) Bort 404 länk till labbmiljön.
    "2018-03-20": (B, mos) Bort med kopplingar till XAMPP och BTHs labbmiljö är enbart extra.
    "2017-12-28": (A, mos) Första utgåvan.
...
Kmom01: Databas
====================================

Då dyker vi in i relationsdatabaser tillsammans med SQL och modellering av databaser.

I en relationsdatabas pratar vi SQL med databasen. Vi skriver SQL för att skapa tabeller och för att lägga till, uppdatera, visa och radera data från databasen.

Till databasen behövs klientprogram som kan användas för att prata med databasen.

Vi introduceras till databasen MySQL och dess olika klienter samt lär oss använda SQL tillsammans med MySQL. Du får jobba igenom en övning i SQL som introducerar dig i grundläggande konstruktioner för att skapa och uppdatera en databas.

Du får pröva att använda olika klienter till MySQL, de har alla sin plats och användningsområde vid olika tillfällen.

<!--more-->

[FIGURE src=/image/snapshot/mamp-mysql-clu-test.jpg?w=w3&q=60 caption="SQL i en textbaserad klient."]

[FIGURE src=/image/snapshot/sql-ovning-alter-table.jpg?w=w3&q=60 caption="SQL som det ser ut i desktop-klienten MySQL WorkBench."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Det finns en [längre beskrivning om kursens labbmiljö](./../installera-labbmiljo). Läs den om du är osäker på vad som skall göras, eller om detta är din första dbwebb-kurs.

Den korta varianten är att du behöver [installera labbmiljön](./../labbmiljo), uppdatera [dbwebb-cli](dbwebb-cli) samt klona och initiera kursrepot.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb selfupdate
dbwebb clone databas
cd databas
dbwebb init
```



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [Databasteknik](kunskap/boken-databasteknik) om MySQL.
    * Kap 1: Databaser och databashanterare
    * Kap 7: Introduktion till frågespråket SQL
    * Kap 28: Introduktion till MySQL

Viss information finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 1 och 3.



###Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Kika igenom referensmanualen för MySQL, bara kort och översiktligt, men se till att du kan hitta till den delen som visar hur SQL skall skrivas i MySQL.
    * [SQL Statement Syntax](https://dev.mysql.com/doc/refman/5.7/en/sql-syntax.html)



### Läsvärt {#lastips}

Följande kan du studera om du har tid och kraft över.

1. Vi kommer inte att använda BTH's labbmiljö för MySQL i denna kursen, men om du vill så kan du bekanta dig med den via dokumentet "[MySQL / MariaDB i BTH’s labbmiljö](labbmiljo/mysql-bth-labbmiljo)". Se hur du kan använda BTH's databasserver för MySQL och hur du kan använda de olika klienterna för att koppla upp dig inifrån skolans nätverk och utanför skolans nätverk. Spara dina eventuella testfiler i `me/kmom01/klient`.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Övningar {#ovningar}

Jobba igenom följande övningar, de förbereder dig inför uppgifterna.

1. Jobba översiktligt igenom guiden "[Kom igång med databasen MySQL och dess klienter](kunskap/kom-igang-med-databasen-mysql-och-dess-klienter)". Som databasutvecklare är det bra att du ha koll på olika varianter av klienter, testa de du har tillgång till och se till att din lokala utvecklingsmiljö fungerar. Artikeln bygger egentligen på att man installerat MySQL med XAMPP, men du kan säkert läsa igenom artikeln och få viss behållning av den, annars får du skumläsa den. I artikeln finns till exempel enklare SQL-kommandon du kan använda för att komma igång med dina klienter. Spara dina eventuella testfiler i `me/kmom01/klient`.



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Skapa en me-sida för redovisning i dbwebb-kurs](uppgift/skapa-en-me-sida-for-redovisning-i-dbwebb-kurs)". Spara resultatet i `me/redovisa`.

1. Jobba igenom första delen av guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql)". I guiden ombeds du göra övningar och spara din SQL-kod i filer. Lägg dem i katalogen `me/kmom01/skolan1` som din redovisning. I nästa kmom fortsätter du med nästa del i guiden.
    * [Första delen: Grunderna](guide/kom-igang-med-sql-i-mysql/grunderna)

<!--
IMPROVE: Gör någon enkel labb som kontrollerar att studenten har koll på vad guiden går igenom. Använd databasen som finns i guiden.

1. Gör laborationen "[SQL lab, introduktion till SQL](uppgift/sql-lab-introduktion-till-sql-dbjs)" som låter dig träna på grunderna i SQL kommandon.
-->



### Extra {#extra}

Gör följande extrauppgifter om du har tid och lust.

1. I nästa kmom kommer du att göra nästa del av guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql)". Du kan redan nu tjuvkika på guidens kommande delar.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Hur känns det att komma igång med MySQL och dess klienter?
* Har du jobbat med databaser eller liknande tidigare?
* Hur gick det att jobba med SQL?
* Jämför SQL med andra sätt att programmera.

TIL är en akronym för "Today I Learned" vilket leksamt anspelar på att det finns alltid nya saker att lära sig, varje dag. Man brukar lyfta upp saker man lärt sig och där man kanske hajade till lite extra över dess nyttighet eller enkelhet, eller så var det bara en ny lärdom för dagen som man vill notera.

* Vilken är din TIL för detta kmom?

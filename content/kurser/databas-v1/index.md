---
title: databas-v1
author: mos
revision:
    "2018-09-20": "(C, mos) Förbereder inför ny kurskod till vt19."
    "2018-02-27": "(B, mos) Inkluderad i Webbprogrammering från vt18 lp4."
    "2018-01-11": "(A, mos) Första utgåva inför kursstart VT2018."
...
Kursen databas (v1)
==================================

Kursen **Databasteknologier för webben**, a.k.a. *databas*, och syftet är att studenten ska förstå och lära sig modellera och implementera en databas samt utveckla en webbapplikation som använder databasen. Som applikationsspråk används serverbaserad JavaScript i webbmiljö.

Kursen erbjuds även under namnet "Webbprogrammering och databaser" med en annan kurskod.

<!--more-->



Förkunskaper {#forkunskaper}
------------------------

Det formella förkunskapskravet är:

> Genomgångna kurser motsvarande 15hp programmering och/eller webbteknologier.



Innehåll {#innehall}
------------------------

Kursen omfattar följande områden:

* Databasteknik
* Relationsmodellen och alternativa modeller.
* Databasmodellering
* SQL
* SQL med lagrade procedurer, funktioner och triggers.
* SQL med index. 
* Applikationsprogrammering med databaser.
* Applikationsprogrammering i webbmiljö med programmeringsspråket JavaScript på serversidan med Node.js med inslag av HTMl och CSS.
* Verktyg och tekniker för utveckling och test.



Mål {#mal}
------------------------

Följande är kursens mål, indelat i undergrupper.



### Kunskap och förståelse {#kunskap}

Efter genomförd kurs skall studenten:

* vara väl bevandrad i relationsdatabaser och ha en övergripande förståelse för dess användning, fördelar och nackdelar.



### Färdighet och förmåga {#fardighet}

Efter genomförd kurs skall studenten:

* ha en grundlig, både teoretisk och praktisk, förmåga att förstå och använda relationsdatabaser
* i detalj förstå och applicera processen att utveckla en databas från en problemställning till färdig klientapplikation i webbmiljö
* strukturerat och i detalj modellera och dokumentera en databas i form av en ER modell
* utifrån en befintlig modell, praktiskt skapa och förändra samt använda en databas med SQL
* designa och implementera en väl fungerande databasapplikation i webbmiljö



### Värderingsförmåga och förhållningssätt {#vardera}

Efter genomförd kurs skall studenten:

* översiktligt förstå, kunna förklara samt allmänt kunna argumentera kring databaser, databashanteringssystem och hur dessa implementeras i en webbaserad miljö.



Kursmoment {#kursmoment}
------------------------

Kursen är uppdelad i kursmoment där varje kursmoment uppskattas till 20h studerande i form av programmering, undersökning, läsande, övningar, uppgifter, redovisning och eftertanke. Alla kursmoment skall redovisas och du samlar alla redovisningar i din me-sida.


### Kmom01: Databas {#kmom01}

Vi introduceras till databasen MySQL och dess olika klienter samt lär oss använda SQL tillsammans med MySQL. Du får jobba igenom en övning i SQL som introducerar dig i grundläggande konstruktioner för att skapa och uppdatera en databas.

Du får pröva att använda tre olika klienter till MySQL, alla tre har sin plats och användningsområde vid olika tillfällen.

[Instruktion till kursmoment 01](./kmom01).



### Kmom02: SQL {#kmom02}

Vi jobbar vidare med SQL och tränar mer på både enklare konstruktionerna och mer utmanande saker som vyer, subqueries, UNION och JOIN.

Du kommer även jobba med JavaScript och Node.js för att se hur du kan koppla dig till en MySQL databas via ett applikationsspråk. Det innebär att du behöver installera en labbmiljö med Node.js och pakethanteraren npm.

[Instruktion till kursmoment 02](./kmom02).



### Kmom03: ER-modellering {#kmom03}

Vi övar i hur man modellerar och bygger upp en databas, det som kallas Entity-Relationship modelling, ER-modellering, eller bara databasmodellering. Vi delar in modelleringen i konceptuell, logisk och fysisk modellering.

Vi jobbar vidare med SQL och tränar mer på utmanande saker som subqueries, JOIN och LEFT/RIGHT OUTER JOIN.

Vi bygger vidare på våra terminalskript i JavaScript och Node.js och bygger en mer potent klient som kan utföra olika saker mot databasen.

[Instruktion till kursmoment 03](./kmom03).



### Kmom04: Transaktioner {#kmom04}

Kursmomenten hanterar begreppet transaktioner i en databas.

I kursmomentet introduceras också en webbserver för Node.js i form av Express. Du kommer igång med Express och ser hur du kan bygga upp grunderna i en webbtjänst och hur du kan skriva din applikationskod för att komma åt en databas, visa rapporter och uppdatera innehåll.

Vi sluför ER-modellen med fokus på logisk och fysisk modellering. Den resulterande databasen implementeras och vi använder Express för att skapa ett webbaserat gränssnitt. Vi bygger en terminalklient för att skapa ett textbaserat gränssnitt mot databasen.

[Instruktion till kursmoment 04](./kmom04).



### Kmom05: Procedur och trigger {#kmom05}

Det handlar om att programmera en databas med <!--inbyggda integritetsregler, -->lagrade procedurer och triggers. Dessa konstruktioner ger oss ökade möjligheter att formulera vår SQL-kod. Det ger oss också möjligheten till inkapsling av SQL-koden och publicera ett API som kan användas av de klienter som vill åt databasen.

Vi bygger vidare på vår databasdrivna applikationsserver och utvecklar terminalklienten parallellt med webbklienten.

Vi ser hur man bygger upp en CRUD-baserad webbklient med HTML-formulär som ger användaren möjlighet att skapa nya rader i databasen, ta bort dem, redigera dem och visa dem. CRUD står för Create, Read, Update, Delete.

[Instruktion till kursmoment 05](./kmom05).



### Kmom06: Prestanda {#kmom06}

Vi fortsätter med programmering i databasen, denna gången med egendefinierade funktioner som har en liknande struktur som lagrade procedurer och triggers.

Sedan studerar vi hur databasen internt jobbar för att optimera de SQL-frågor du skriver och hur du kan använda index för att optimera din databas.

Vi jobbar vidare med terminal- och webbaserade klienter mot databasen och förhoppningsvis har vi fått en allt bättre koll på JavaScript-koden.

[Instruktion till kursmoment 06](./kmom06).



### Kmom07/10: Projekt och examination {#kmom10}

Avslutningsvis gör du ett projekt enligt en specifikation. Projektet är det sista som du gör och tillsammans med alla redovisningar som finns på din me-sida så används detta som underlag för att examinera dig från kursen.

[Instruktion till kursmoment 10](./kmom10).



Kurslitteratur {#litteratur}
----------------------------

[Måste jag skaffa kurslitteraturen](kurser/maste-jag-skaffa-kurslitteraturen)?



### Kurslitteratur {#kurslitteratur}

Det finns läsanvisningar i samband med varje kursmoment.

* **[Databasteknik](kunskap/boken-databasteknik)** -- Radron-McCarthy och Risch  
    Komplett med det man vill veta om databasteknik, både grunder, modellering och SQL. En databasbok helt enkelt. 

* **[Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript)** -- Axel Rauschmayer  
    En bok om att komma igång med JavaScript som programmeringsspråk. Fungerar för nya programmerare såväl som för de som redan kan ett eller ett par programmeringsspråk.

* **[Exploring ES6](kunskap/boken-exploring-es6)** -- Axel Rauschmayer  
    En bok om ES6 som bygger vidare på att man kan ES5.


<!--
### Referenslitteratur {#referenslitteratur}

Referensdokumentationen är främst olika online-resurser i form av manualer.
-->


### Övrig litteratur {#ovriglitteratur}

I varje kursmoment kan det tillkomma läsanvisningar i till exempel artiklar, manualer och webbmaterial.



Läsanvisningar {#lasanvisning}
------------------------------

Här följer en sammanställning av de läsanvisningar till kurslitteraturen som ges i varje kursmoment.

| Kursmoment | Databasteknik          | Javascript ES5   | JavaScript ES6   |
|------------|------------------------|------------------|------------------|
| Kmom01     | 1, 7, 28               |                  |                  |
| Kmom02     | 8, 20 (10)             | 1, 13            | 4                |
| Kmom03     | 2, 4, 5, 6 (3, 11)     |                  |                  | 
| Kmom04     | 23 (24)                |                  |                  |
| Kmom05     | 12, 14, 15             |                  |                  | 
| Kmom06     | 9, 21 (22)             |                  |                  | 
| Kmom10     |                        |                  |                  |

Dessutom har varje kursmoment läsanvisningar i artiklar och videos. 



Lektionsplan och rekommenderad studieplan {#schema}
---------------------------------------------

Läser du kursen inom ramen för programmet Webbprogrammering (campus/distans) så finns det en [rekommenderad studieplan inom programmet](program/webbprogrammering/studieplan/termin2) samt en [lektionsplan](program/webbprogrammering/lektionsplan/lasperiod4).

<!-- [lektionsplan](program/webbprogrammering/lektionsplan/lasperiod3) -->

Läser du kursen som en del i ett kurspaket så finns det en [studieplan för kursen som är kopplad till kurspaketet](webprog#studieplan).

Läser du kursen som en del av programmet Software Engineering eller International Software Engineering, så finns en [studieplan för kurskurstillfället som är kopplad till ditt program](kurser/databas/studieplan). Det finns också en [lektionsplan](kurser/databas/lektionsplan) kopplad till kurstillfället.

En lektionsplanen visar de tillfällena som är schemalagda träffar. Finns det en lektionsplan så finns ofta bokningar av salar gjorda i bokningsschemat.

Studieplan, eventuell lektionsplan och eventuellt schema finns tillgängligt via kurstillfället på ITs.

Läs mer om den [rekommenderade studieplanen](kurser/faq/rekommenderad-studieplan) och [lektionsplanen](kurser/faq/lektionsplan-och-schema).



Lärarstöd och handledning {#handledning}
----------------------------------------

Schemalagda labbtillfällen, hangouts samt forum och chatt de viktigaste källorna för handledning. Läs om [handledning och hjälp-till-självhjälp](kurser/faq/lararstod-och-handledning).



Betygsättning {#betyg}
------------------------

Det finns ett särskilt dokument som beskriver [hur bedömning och betygsättning sker](kurser/bedomning-och-betygsattning). 



Ladok {#ladok}
------------------------

Enligt kursplanen finns ett antal ladokmoment och de är kopplade till kursens kursmoment enligt följande.

| Kursens moment  | Ladok moment enligt kursplan  | Betyg |
|-----------------|-------------------------------|-------|
| Kmom01 + kmom02 | Inlämningsuppgift 1 á 2.5hp   | G-U   |
| Kmom03 + kmom04 | Inlämningsuppgift 2 á 2.5hp   | G-U   |
| Kmom05 - kmom10 | Inlämningsuppgift 3 á 2.5hp   | A-F   |

Den sista inlämningen bestämmer kursens slutbetyg vilket utfärdas när samtliga moment godkänts.

Läs mer om [rapportering av resultat](kurser/faq/resultatrapportering).



Kursutvärdering och kursutveckling {#kursutvardering}
-----------------------------------------------------

Det finns ett särskilt dokument som beskriver hur arbetet med kursutvärderingar och kursutveckling sker. Det är oerhört viktigt att du säger till vad du tycker om kurs och kursmaterial, du kan alltid hojta till i både forum, chatt eller mail.

Läs om hur [vi jobbar med kursutvärdering och kursutveckling](kurser/kursutvardering-och-kursutveckling).



Kursplan {#kursplan}
-----------------------------------------------------

Kursplanen är kursens formella dokument som fastställts av högskolan. När kursen utvärderas görs det mot kursplanen. I kursplanen kan du läsa om kursens klassificering, syfte, innehåll, mål, generella förmågor, lärande och undervisning, bedömning och examination, litteratur, mm.

Kursen ges under olika kurskoder till olika målgrupper.

Från våren 2019 får kurserna nya kurskoder.

Följande gällde till och med 2018.

Kursens namn är "Databasteknologier för webben" för programmet Webbprogrammering och kurspaketet webprog (från VT18). Du hittar [kursplanen genom att söka på kurskoden PA1451 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=PA1451).

Kursens namn är "Webbprogrammering och databaser" till programmen Software Engineering och International Software Engieering (från VT17). Du hittar [kursplanen genom att söka på kurskoden PA1444 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=PA1444).

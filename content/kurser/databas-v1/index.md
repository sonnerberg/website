---
title: databas-v1
author: mos
revision:
    "2018-12-19": "(E, mos) Uppdaterat läsanvisning utgåva 2 av kursbok."
    "2018-11-29": "(D, mos) Uppdaterad med nya kurskoder till vt19."
    "2018-09-20": "(C, mos) Förbereder inför ny kurskod till vt19."
    "2018-02-27": "(B, mos) Inkluderad i Webbprogrammering från vt18 lp4."
    "2018-01-11": "(A, mos) Första utgåva inför kursstart VT2018."
...
Kursen databas (v1)
==================================

Kursen **Databasteknologier för webben**, a.k.a. *databas*, och syftet är att studenten ska förstå och lära sig modellera och implementera en databas samt utveckla en webbapplikation som använder databasen. Som applikationsspråk används serverbaserad JavaScript i webbmiljö.

Kursen erbjuds även under namnet "Webbprogrammering och databaser" med en alternativ kurskod.

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
* Applikationsprogrammering i webbmiljö med programmeringsspråket JavaScript på serversidan med Node.js med inslag av HTML och CSS.
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

| Kursmoment | Databasteknik      | Javascript ES5 | JavaScript ES6 |
|------------|--------------------|----------------|----------------|
| Kmom01     | 1, 7, 29           |                |                |
| Kmom02     | 8, 21 (11)         | 1, 13          | 4              |
| Kmom03     | 2, 4, 5, 6 (3, 12) |                |                |
| Kmom04     | 24 (25)            |                |                |
| Kmom05     | 13, 15, 16         |                |                |
| Kmom06     | 9, 22 (23)         |                |                |
| Kmom10     |                    |                |                |

Varje kursmoment kan ha ytterligare läsanvisningar i artiklar, video och annat studiematerial. 



Rekommenderad studieplan {#studieplan}
---------------------------------------------

Kursen har en [rekommenderad studieplan](kurser/databas/studieplan) som visar en översikt över kursens olika moment och när de i tiden bör utföras för att studenten skall ligga i fas med kursens planering.

I studieplanen visas när rättning sker av respektive inlämnat moment samt när det finns möjligheter att göra restinlämningar.

Läs mer om den [rekommenderade studieplanen](kurser/faq/rekommenderad-studieplan).



Lektionsplan {#lektionsplan}
---------------------------------------------

Det finns en [lektionsplan](kurser/databas/lektionsplan) som visar en detaljplanering för undervisningen i kursen, vecka för vecka.

Läs mer om [lektionsplanen](kurser/faq/lektionsplan-och-schema).



Handledning {#handledning}
----------------------------------------

Förutom den planerade undervisningen enligt lektionsplanen så kan du få hjälp och stöd i kursens chatt och i forumet. Chatten lämpar sig för korta enkla frågor och forumet för mer utredande och längre frågor och svar. Om du inte får svar i chatten så rekommenderas att du postar i forumet.

Läs om [lärarstöd och handledning](kurser/faq/lararstod-och-handledning).



Betygsättning {#betyg}
------------------------

Det finns ett särskilt dokument som beskriver [hur bedömning och betygsättning sker](kurser/faq/bedomning-och-betygsattning). 



Ladok {#ladok}
------------------------

Enligt kursplanen finns ett antal ladokmoment och de är kopplade till kursens kursmoment enligt följande.

| Kursens moment  | Ladok moment enligt kursplan      | Betyg |
|-----------------|-----------------------------------|-------|
| Kmom01 + kmom02 | Inlämningsuppgift 1 á 2.5hp (3hp) | G-U   |
| Kmom03 + kmom04 | Inlämningsuppgift 2 á 2.5hp (3hp) | G-U   |
| Kmom05 - kmom10 | Inlämningsuppgift 3 á 2.5hp (4hp) | A-F   |

Den sista inlämningen bestämmer kursens slutbetyg vilket utfärdas när samtliga moment godkänts.

Poängen inom parantes gäller kurskoden DV1605 för SE-programmet som läser kursen som en 10hp kurs då de inte har några förkunskaper i webbområdet. 

Läs mer om [rapportering av resultat](kurser/faq/resultatrapportering).



Kursutvärdering och kursutveckling {#kursutvardering}
-----------------------------------------------------

Det finns ett särskilt dokument som beskriver hur arbetet med kursutvärderingar och kursutveckling sker. Det är oerhört viktigt att du säger till vad du tycker om kurs och kursmaterial, du kan alltid hojta till i både forum, chatt eller mail.

Läs om hur [vi jobbar med kursutvärdering och kursutveckling](kurser/kursutvardering-och-kursutveckling).



Kursplan {#kursplan}
-----------------------------------------------------

Kursplanen är kursens formella dokument som fastställts av högskolan. När kursen utvärderas görs det mot kursplanen. I kursplanen kan du läsa om kursens klassificering, syfte, innehåll, mål, generella förmågor, lärande och undervisning, bedömning och examination, litteratur, mm.

Kursen ges under olika kurskoder till olika målgrupper.



### Aktuella kursnamn och kurskoder {#kurskod}

Från våren 2019 får kurserna nya kurskoder och uppdaterade kursplaner.

Kurspaket och programmet Webbprogrammering läser kursen under namnet "Databasteknologier för webben" och kurskoden DV1606. Du hittar [kursplanen genom att söka på kurskoden DV1606 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1606).

För programmet Software Engineering heter kursen "Webbprogrammering och databaser" och kurskoden är DV1605. Du hittar [kursplanen genom att söka på kurskoden DV1605 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1605).



### Tidigare utgåvor av kursen {#tidkurskod}

Följande gällde till och med 2018.

Kursens namn är "Databasteknologier för webben" för programmet Webbprogrammering och kurspaketet webprog (från VT18). Du hittar [kursplanen genom att söka på kurskoden PA1451 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=PA1451).

Kursens namn är "Webbprogrammering och databaser" till programmen Software Engineering och International Software Engieering (från VT17). Du hittar [kursplanen genom att söka på kurskoden PA1444 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=PA1444).

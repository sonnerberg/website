---
title: databas
author: mos
revision:
    "2017-12-27": "(PA1, mos) Arbetsmaterial inför kursstart VT2018."
...
Kursen databas
==================================

Kursen **Databasteknologier för webben**, a.k.a. *databas*. Syftet med kursen är att ge studenten generella kunskaper inom området databaser och webb samt specifika kunskaper i att arbete med <s>olika</s> databaser i ett applikationsspråk i webbsammanhang.

<!--more-->

[WARNING]
**Kursutveckling pågår.**
[/WARNING]



Förkunskaper {#forkunskaper}
------------------------

Det formella förkunskapskravet är:

> Genomgångna kurser i "Webbteknologier" och "Teknisk webbdesign och Användbarhet".



Innehåll {#innehall}
------------------------

Kursen omfattar följande områden:

* Databasteknik
* Relationsmodellen och alternativa modeller
* Databasmodellering
* SQL
* Applikationsprogrammering med databaser
* Verktyg och tekniker för utveckling och test



Mål {#mal}
------------------------



###Kunskap och förståelse {#kunskap}

Efter genomförd kurs skall studenten:

* vara väl bevandrad i relationsdatabaser och ha en övergripande förståelse för dess användning och dess fördelar och nackdelar.



###Färdighet och förmåga {#fardighet}

Efter genomförd kurs skall studenten:

<!-- se över dessa -->

* ha en grundlig, både teoretisk och praktisk, förmåga att använda relationsdatabaser
* i detalj förstå och applicera processen att utveckla en databas från en problemställning till färdig klientapplikation
* strukturerat och i detalj modellera och dokumentera en databas i form av en ER modell
* utifrån en befintlig modell, praktiskt skapa och förändra samt använda en databas med SQL
* designa och implementera en väl fungerande databasapplikation med tillhörande (client/server) klientapplikation



###Värderingsförmåga och förhållningssätt {#vardera}

Efter genomförd kurs skall studenten:

* översiktligt förstå, kunna förklara samt argumentera kring databaser och databashanteringssystem i allmänhet.



Kursmoment {#kursmoment}
------------------------

Kursen är uppdelad i kursmoment där varje kursmoment uppskattas till 20h studerande i form av programmering, undersökning, läsande, övningar, uppgifter, redovisning och eftertanke. Alla kursmoment skall redovisas och du samlar alla redovisningar i din me-sida.


###Kmom01: Databas {#kmom01}

Vi introduceras till databasen MySQL och dess olika klienter samt lär oss använda SQL tillsammans med MySQL. Du får jobba igenom en övning i SQL som introducerar dig i grundläggande konstruktioner för att skapa och uppdatera en databas.

Du får pröva att använda tre olika klienter till MySQL, alla tre har sin plats och användningsområde vid olika tillfällen.

[Instruktion till kursmoment 01](./kmom01).



###Kmom02: SQL {#kmom02}

Vi jobbar vidare med SQL och tränar mer på både enklare konstruktionerna och mer utmanande saker som vyer, subqueries, UNION och JOIN.

Du kommer även jobba med JavaScript och Node.js för att se hur du kan koppla dig till en MySQL databas via ett applikationsspråk. Det innebär att du behöver installera en labbmiljö med Node.js och pakethanteraren npm.

[Instruktion till kursmoment 02](./kmom02).



###Kmom03: ER-modellering {#kmom03}

Vi övar i hur man modellerar och bygger upp en databas, det som kallas Entity-Relationship modelling, ER-modellering.

[Instruktion till kursmoment 03](./kmom03).



###Kmom04: Transaktioner {#kmom04}

Kursmomenten handlar om begreppet transaktioner i en databas.

I kursmomentet introduceras också en webbserver för Node.js i form av Express. Du kommer igång med Express och ser hur du kan bygga upp en webb/RESTful server och hur du kan skriva din applikationskod för att till exempel komma åt en databas och visa och uppdatera dess innehåll.

[Instruktion till kursmoment 04](./kmom04).



###Kmom05: Procedur, trigger, funktion {#kmom05}

Kursmomenten handlar om att programmera en databas med inbyggda integritetsregler, lagrade procedurer, triggers och inbyggda funktioner.

Vi bygger vidare på vår databasdrivna applikationsserver.

[Instruktion till kursmoment 05](./kmom05).



###Kmom06: Prestanda {#kmom06}

Detta kursmoment erbjuder en introduktion till hur databasen internt jobbar för att optimera de SQL-frågor du skriver och hur du bör använda index för att optimera din databas.

Vi bygger vidare på vår databasdrivna applikationsserver.

[Instruktion till kursmoment 06](./kmom06).



###Kmom07/10: Projekt och examination {#kmom10}

Avslutningsvis gör du ett projekt enligt en specifikation. Projektet är det sista som du gör och tillsammans med alla redovisningar som finns på din me-sida så används detta som underlag för att examinera dig från kursen.

[Instruktion till kursmoment 10](./kmom10).



Kurslitteratur {#litteratur}
----------------------------

[Måste jag skaffa kurslitteraturen](kurser/maste-jag-skaffa-kurslitteraturen)?



###Kurslitteratur {#kurslitteratur}

Det finns läsanvisningar i samband med varje kursmoment.

* **[Databasteknik](kunskap/boken-databasteknik)** -- Radron-McCarthy och Risch  
    Komplett med det man vill veta om databasteknik, både grunder, modellering och SQL. En databasbok helt enkelt. 

* **[Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript)** -- Axel Rauschmayer  
    En bok om att komma igång med JavaScript som programmeringsspråk. Fungerar för nya programmerare såväl som för de som redan kan ett eller ett par programmeringsspråk.

* **[Exploring ES6](kunskap/boken-exploring-es6)** -- Axel Rauschmayer  
    En bok om ES6 som bygger vidare på att man kan ES5.



###Referenslitteratur {#referenslitteratur}

Referensdokumentationen är främst olika online-resurser i form av manualer.



###Övrig litteratur {#ovriglitteratur}

I varje kursmoment kan det tillkomma läsanvisningar i till exempel artiklar, manualer och webbmaterial.


<!--

Kursbok saknas så inga speciella läsanvisningar syns här.

Läsanvisningar {#lasanvisning}
------------------------------

Här följer en sammanställning av de läsanvisningar till kurslitteraturen som ges i varje kursmoment.

| Kursmoment | Eloquent JavaScript: A Modern Introduction to Programming | 
|------------|-----------------------------------------------------------|
| Kmom01     | Ch 1, 12                                                  |
| Kmom02     | Ch 2                                                      |
| Kmom03     | Ch 3,                                                     | 
| Kmom04     | Ch 4, 6                                                   |
| Kmom05     | Ch 12, 13, 14                                             | 
| Kmom06     |                                                           | 
| Kmom10     |                                                           |

Dessutom har varje kursmoment läsanvisningar i artiklar och videos. 

-->



Lektionsplan och rekommenderad studieplan {#schema}
---------------------------------------------

Läser du kursen inom ramen för programmet Webbprogrammering (campus/distans) så finns det en [rekommenderad studieplan inom programmet](program/webbprogrammering/studieplan/termin1) samt en [lektionsplan](program/webbprogrammering/lektionsplan/lasar1/lasperiod3).

Läser du kursen som en del i ett kurspaket så finns det en [studieplan som är kopplad till kurspaketet](webprog#studieplan).

Vissa av kurstillfällena har även en lektionsplan som du får i samband med kursstart. Lektionsplanen visar de tillfällena som är schemalagda träffar.

Finns det en lektionsplan så finns ofta bokningar av salar gjorda i bokningsschemat.

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

Kursens namn är "Databasteknologier för webben". Du hittar [kursplanen genom att söka på kurskoden PA1451 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=PA1451).

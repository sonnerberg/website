---
title: devops (v1)
author:
    - aar
    - mos
revision:
    "2019-04-16": "(B, aar) Uppdaterad inför V1."
    "2018-12-06": "(A, mos) Första revisionen efter kursens inrättande."
...
Kursen devops (v1)
==================================

Kursen **Kontinuerlig integration och driftsättning i molnet**, a.k.a. *devops*, lär ut hur man jobbar med utveckling och it-drift tillsammans genom att lära grunderna i att sätta upp och automatisera processer för kontinuerlig integration och driftsättning i en molnbaserad miljö.

<!--more-->



Förkunskaper {#forkunskaper}
------------------------

Det formella förkunskapskravet är:

> För tillträde till kursen krävs avklarade kurser motsvarande 45 högskolepoäng inom området datavetenskap/programvaruteknik/telekommunikation varav minst 20hp inom programmering och databaser.



Innehåll {#innehall}
------------------------

Kursen omfattar följande områden:

* Innebörden av arbetsfilosofin DevOps

* Kontinuerlig integration (Continuous Integration CI)

* Kontinuerlig driftsättning (Continuous Deployment - CD)

* Automatisering av processer för testning, byggning och driftsättning.

* Virtualisering med Docker för utveckling, test och driftsättning

* Testning av kod och applikation

* Versionshantering av kod

* Relaterade verktyg och tekniker.



Mål {#mal}
------------------------

Följande är kursens mål, indelat i undergrupper.



### Kunskap och förståelse {#kunskap}

Efter genomförd kurs skall studenten:

* vara väl bevandrad i arbetsfilosofin DevOps och ha en övergripande förståelse för dess användning, fördelar och nackdelar.

* ingående redogöra för utveckling baserat på DevOps och de tekniker som omfattas genom att skriftligen beskriva och sammanfatta erfarenheter och observationer från övningar.

* kunna visa goda kunskaper i att använda valda tekniker genom att tillämpa dessa tekniker i praktiska övningar.



### Färdighet och förmåga {#fardighet}

Efter genomförd kurs skall studenten:

* ha en grundlig, både teoretisk och praktisk, förmåga att förstå och använda Docker

* kunna utveckla, dokumentera och presentera ett projekt som använder verktyg och processer för automatisk CI och CD.

* ha god praktisk förmåga att hantera de verktyg och utvecklingsmiljöer som används vid utveckling och felsökning vid CI och CD.



### Värderingsförmåga och förhållningssätt {#vardera}

Efter genomförd kurs skall studenten:

* översiktligt förstå, kunna förklara samt allmänt kunna argumentera val av miljö och verktyg för DevOps och CI.



Kursmoment {#kursmoment}
------------------------

Kursen är uppdelad i kursmoment där varje kursmoment uppskattas till 20h studerande i form av programmering, undersökning, läsande, övningar, uppgifter, redovisning och eftertanke. Alla kursmoment skall redovisas och du samlar alla redovisningar i din me-sida.

Kursen avslutas med ett större avslutande moment som examinerar kursen.



### Kmom01: Introduktion till DevOps {#kmom01}

I kmom01 ska vi börja med bekanta oss med konceptet DevOps och börja på ett projekt.
Skriv enhetstester från början, tips att testa på TDD. Jag rekomenderar boken Clean Architecture för en intro till TDD och annat bra.
Gör ett GitHub repo och lägg till Travis/Circle CI som kör testerna och validerar kod.

Loggin från start?

Lämna in vad ni planerar för projekt och länk till github repot.

Läs [instruktionen till kursmoment 01](./kmom01).



### Kmom02: Docker {#kmom02}

Lära oss Docker, docker-compose och skapa en image för ert projekt.
Kör docker i CI miljön.
Skaffa cloud miljö, City networks/DO, och Domän.
Simple CD miljö till molnet?

Läs [instruktionen till kursmoment 02](./kmom02).



### Kmom03: IaC/CM {#kmom03}

Vi går vidare med Continues Deployment och fixar så vi automatisk kan bygga miljön vi deployar koden i.
Packer/Terraform/Ansible?
Ni ska även fixa HTTPS till er domän.
Proxy? 

Läs [instruktionen till kursmoment 03](./kmom03).



### Kmom04: Monitoring och logging {#kmom04}

Nu när vi har ett system upper och rullande behöver vi veta när något går fel, vi ska börja övervaka systemet och sätta upp notification när något går fel.
Vi kollar även på hur vi kan hantera att samla ihop loggar från flera olika VMs.
Litet kmom?

Läs [instruktionen till kursmoment 04](./kmom04).



### Kmom05: Container orchestration {#kmom05}

Hur kan vi skala vårt program på ett bra sätt? Vi kollar på Container orchestration för att lära oss hur vi kan skapa flera containrar av samma image och dela på arbetsbörndan mellan dem.
Swarm/Kubernets?

Caching och load balancing, flytta något till kmom04/06?

Läs [instruktionen till kursmoment 05](./kmom05).



### Kmom06:  {#kmom06}

Vi dyker ner i säkerhet kring Docker och lär oss sätta upp en staging miljö.

Läs [instruktionen till kursmoment 06](./kmom06).



### Kmom07/10: Uppsats {#kmom10}

Avslutningsvis skriver du en uppsats. Uppsatsen är det sista som du gör och tillsammans med alla redovisningar som finns på din me-sida så används detta som underlag för att examinera dig från kursen.

Läs [instruktionen till kursmoment 07/10](./kmom10).



Kurslitteratur {#litteratur}
----------------------------

[Måste jag skaffa kurslitteraturen](kurser/maste-jag-skaffa-kurslitteraturen)?



### Kurslitteratur {#kurslitteratur}

Det finns ingen speciell kursbok utan det är ersatt med läsanvisningar i varje kursmoment i form av exempelvis artiklar, guider, manualer.

<!--
Som kurslitteratur har jag valt följande böcker. Det är en god idé att läsa igenom dessa  under kursen, det finns läsanvisningar till dessa i samband med varje kursmoment.

* **[Beginning PHP and MySQL: From Novice to Professional](kunskap/boken-beginning-php-and-mysql-from-novice-to-professional)** -- Gilmore, W  
  En tjockare bok för den som vill ha en mer komplett vy över PHP och MySQL från början.
-->



### Referenslitteratur {#referenslitteratur}

Följande böcker har jag valt som referenslitteratur. De kan vara bra att ha tillhands och ger lite extra läsmöjligheter. De behövs inte för att klara kursen men vill du bemästra kursens område så är dessa böcker bra startpunkter. Välj och vraka och ta ett eget beslut om de böcker du vill använda.


* **[The Pheonix Project](kunskap/boken-the-pheonix-project)** -- Gene Kim, Kevin Behr, George Spafford  
  En roman om en IT chef som går över till DevOps.



### Övrig litteratur {#ovriglitteratur}

I varje kursmoment kan det tillkomma läsanvisningar i till exempel artiklar, manualer och webbmaterial.


<!--
Läsanvisningar {#lasanvisning}
------------------------------

Det finns inga specifika läsanvisningar till kurslitteraturen.


Här följer en sammanställning av de läsanvisningar som ges i varje kursmoment. Skaffa gärna böckerna i förväg och börja läsa dem innan kursen.

| Kursmoment | Beginning PHP and MySQL   | Webbutveckling med PHP och MySQL | Databasteknik       |
|------------|---------------------------|----------------------------------|---------------------|
| Kmom01     | Ch 1, 2, 3, 4, 5          | Kap 1, 2, 3, 4, 5, 6, 7          | Kap 1               |
| Kmom02     | Ch 6, 7, 8, 12            |                                  |                     |
| Kmom03     | Ch 25, 26, 27             | Kap 8 Databaser                  | Kap 7, 8, 9, 28     |
| Kmom04     | Ch 30, 31                 |                                  | Kap 18              |
| Kmom05     |                           |                                  |                     |
| Kmom06     |                           |                                  |                     |
| Kmom07/10  ||||

-->




Rekommenderad studieplan {#studieplan}
---------------------------------------------

Kursen har en [rekommenderad studieplan](kurser/devops/studieplan) som visar en översikt över kursens olika moment och när de i tiden bör utföras för att studenten skall ligga i fas med kursens planering.

I studieplanen visas när rättning sker av respektive inlämnat moment samt när det finns möjligheter att göra restinlämningar.

Läs mer om den [rekommenderade studieplanen](kurser/faq/rekommenderad-studieplan).



Lektionsplan {#lektionsplan}
---------------------------------------------

Det finns en [lektionsplan](kurser/devops/lektionsplan) som visar en detaljplanering för undervisningen i kursen, vecka för vecka.

Läs mer om [lektionsplanen](kurser/faq/lektionsplan).



Handledning {#handledning}
----------------------------------------

Förutom den planerade undervisningen enligt lektionsplanen så kan du få hjälp och stöd i kursens chatt och i forumet. Chatten lämpar sig för korta enkla frågor och forumet för mer utredande och längre frågor och svar. Om du inte får svar i chatten så rekommenderas att du postar i forumet.

Läs om [lärarstöd och handledning](kurser/faq/lararstod-och-handledning).



Betygsättning {#betyg}
------------------------

Det finns ett särskilt dokument som beskriver [hur bedömning och betygsättning sker](kurser/bedomning-och-betygsattning). 



Ladok {#ladok}
------------------------

Enligt kursplanen finns ett antal ladokmoment och de är kopplade till kursens kursmoment enligt följande.

| Kursens moment  | Ladok moment enligt kursplan  |
|-----------------|-------------------------------|
| Kmom01 + kmom02 | Inlämningsuppgift 1 á 2.5hp   |
| Kmom03 + kmom04 | Inlämningsuppgift 2 á 2.5hp   |
| Kmom07 - kmom10 | Inlämningsuppgift 3 á 2.5hp   |

Den sista inlämningen bestämmer kursens slutbetyg vilket utfärdas när samtliga moment godkänts.

Totalt omfattar kursen 7.5hp.

Läs mer om [rapportering av resultat](kurser/faq/resultatrapportering).



Kursutvärdering och kursutveckling {#kursutvardering}
-----------------------------------------------------

Det finns ett särskilt dokument som beskriver hur arbetet med kursutvärderingar och kursutveckling sker. Det är oerhört viktigt för mig att du säger till vad du tycker om kurs och kursmaterial, du kan alltid hojta till i både forum, chatt eller mail.

Läs om hur [vi jobbar med kursutvärdering och kursutveckling](kurser/kursutvardering-och-kursutveckling).



Kursplan {#kursplan}
-----------------------------------------------------

Kursens namn är "Kontinuerlig integration och driftsättning i molnet". Du hittar [kursplanen genom att söka på kurskoden DV1617 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1617).

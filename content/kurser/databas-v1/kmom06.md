---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom06: Prestanda
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Vi fortsätter med programmering i databasen, denna gången med egendefinierade funktioner som har en liknande struktur som lagrade procedurer och triggers.

Sedan studerar vi hur databasen internt jobbar för att optimera de SQL-frågor du skriver och hur du kan använda index för att optimera din databas.

Vi bygger vidare på vår databasdrivna applikationsserver.

<!--more-->

[FIGURE src=image/snapvt17/mysql-optimize.png?w=w2 caption="Optimering av en databas sker på många olika nivåer."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 9: Sammanfattning av SQL-kommandon
    * Kap 21: Index och prestanda

Vissa av kapitlen finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 2.

Det finns ytterligare ett kapitel i boken som är relaterat till prestanda, det går utanför kursens ram men läs vid intresse.

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 22: Fysiska lagringsstrukturer i databaser


<!--
Saker vi inte hanterat:

* Kap 13: Säkerhet i databaser
-->



###Artiklar {#artiklar}

Läs följande.

1. Bekanta dig översiktligt med de olika delarna av manualen i [MySQL om optimering](https://dev.mysql.com/doc/refman/5.7/en/optimization.html). Se vilka delar som kan optimeras och på vilket sätt. Skumma igenom de olika delarna.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

1. Jobba igenom "[Egendefinierade funktioner i databas](kunskap/egen-definierade-funktioner-i-databas)" för att lära dig hur konceptet kan användas i en databas. Spara dina exempelprogram i `me/kmom05/prog`.

<!--stop-->

1. Jobba igenom övningen "[Index och prestanda i MySQL](kunskap/index-och-prestanda-i-mysql)" som tränar dig i hur du kan optimera dina databasfrågor med index. Spara dina testprogram i `me/kmom06/index`.

<!--
1. Artikel om hur man skriver bra SQL frågor på ett optimerat sätt.

1. Inloggning, session, express.

1. Usability with messages on what happens.

1. Driftsättning?

1. Faktureringsmotor?

1. Exportera data från webben till csv?
-->



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. **FOKUS INDEX** Utför uppgiften "[Skapa en appserver mot MySQL](uppgift/skapa-en-appserver-mot-mysql)". I uppgiften får du jobba med både Express, MySQL och programmera i databasen. Spara koden i `me/app`.

1. **BYGG ÄVEN VIDARE PÅ KLIENTEN? MODUL SOM ÅTERANVÄNDS MED SERVERN?** (skolan, båtklubben)



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Förklara begreppet index i databas, och varför det är viktigt, på ett par rader.
* Se tillbaka på de kmom du gjort, känner du att du har koll på databas nu, eller känner du att något saknas eller behövs tränas ytterligare?

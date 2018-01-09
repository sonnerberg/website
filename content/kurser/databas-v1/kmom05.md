---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom05: Procedur, trigger, funktion
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Kursmomenten handlar om att programmera en databas med inbyggda integritetsregler, lagrade procedurer, triggers och inbyggda funktioner.

Vi bygger vidare på vår databasdrivna applikationsserver.

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

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 12. Integritetsvillkor
    * Kap 14: Lagrade procedurer
    * Kap 15: Aktiva databaser och triggers

Vissa av kapitlen finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 2.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

1. Jobba igenom "[Lagrade procedurer i databas](kunskap/lagrade-procedurer-i-databas)" för att lära dig om lagrade procedurer och vad du kan göra med dem. Spara dina exempelprogram i `me/kmom05/prog`.

1. Jobba igenom "[Triggers i databas](kunskap/triggers-i-databas)" för att lära dig om vad du kan göra med triggers och hur de fungerar. Spara dina exempelprogram i `me/kmom05/prog`.

1. Jobba igenom "[Egendefinierade funktioner i databas](kunskap/egen-definierade-funktioner-i-databas)" för att lära dig hur konceptet kan användas i en databas. Spara dina exempelprogram i `me/kmom05/prog`.

1. CRUD (web & client)



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

<!--stop-->


1. **FOKUS PROC, TRIG, FUNC** Utför uppgiften "[Skapa en appserver mot MySQL](uppgift/skapa-en-appserver-mot-mysql)". I uppgiften får du jobba med både Express, MySQL och programmera i databasen. Spara koden i `me/app`.

1. **BYGG VIDARE PÅ WEBBEN/KLIENTEN? MODUL SOM ÅTERANVÄNDS MED SERVERN?** (skolan, hacka lönen, ge betyg, båtklubben) CRUD? Terminalklienten.

<!--
1. Faktureringsmotor?

1. Exportera data från webben till csv?
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Ser du fördelar med inbyggda integritetsregler, ser du även nackdelar?
* Gick det bra att komma igång med lagrade procedurer, triggers, funktioner?
* Skriv ett kort stycke (3-5 meningar) om respektive inbyggda integritetsregler, lagrade procedurer, triggers och funktioner där du förklarar begreppen för en som inte är insatt i begreppen.
* Hur är din syn på att "programmera" på detta viset i databasen, jämför med traditionell SQL?
* Är du nöjd med din kodstruktur 

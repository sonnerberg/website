---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom05: Programmera i databas
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Det handlar om att programmera en databas med <!--inbyggda integritetsregler, -->lagrade procedurer och triggers. Dessa konstruktioner ger oss ökade möjligheter att formulera vår SQL-kod. Det ger oss också möjligheten till inkapsling av SQL-koden och publicera ett API som kan användas av de klienter som vill åt databasen.

Vi bygger vidare på vår databasdrivna applikationsserver och utvecklar terminalklienten parallellt med webbklienten.

Vi ser hur man bygger upp en CRUD-baserad webbklient med HTML-formulär som ger användaren möjlighet att skapa nya rader i databasen, ta bort dem, redigera dem och visa dem. CRUD står för Create, Read, Update, Delete.

<!--more-->

[FIGURE src=image/snapvt18/bank2-account-actions.png caption="Nu förberedd med ikoner för att göra edit och delete."]

[FIGURE src=image/snapvt18/bank2-edit-account-details.png caption="Nu kan jag uppdatera detaljer om kontot."]


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

1. Jobba igenom "[CRUD med Express, MySQL och lagrade procedurer](kunskap/crud-med-express-mysql-och-lagrade-procedurer)" som visar hur ett webbgränssnitt kan se ut där du kan lägga till, uppdatera och ta bort rader i en tabell. Spara de exempelprogram du gör i `me/kmom05/crud`.



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

* Gick det bra att komma igång med lagrade procedurer och triggers?
* Skriv ett kort stycke (3-5 meningar) om lagrade procedurer och om triggers där du förklarar begreppen (fördel, nackdel, användningsområde) för en som inte är insatt.
* Hur är din syn på att "programmera" på detta viset i databasen, jämför med traditionell SQL som exponeras i JavaScript-koden?
* Hur gick det att utföra uppgifterna? 
* Vilken är din TIL för detta kmom?

<!--
* Ser du fördelar med inbyggda integritetsregler, ser du även nackdelar?
-->

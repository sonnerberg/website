---
author: mos
revision:
    "2017-12-27": (PA1, mos) Arbete pågår.
...
Kmom04: Transaktioner
====================================

[WARNING]
Kursutveckling pågår inför VT18.
[/WARNING]

Kursmomenten hanterar begreppet transaktioner i en databas.

I kursmomentet introduceras också en webbserver för Node.js i form av Express. Du kommer igång med Express och ser hur du kan bygga upp grunderna i en webbtjänst och hur du kan skriva din applikationskod för att komma åt en databas, visa rapporter och uppdatera innehåll.

Vi sluför ER-modellen med fokus på logisk och fysisk modellering. Den resulterande databasen implementeras och vi använder Express för att skapa ett webbaserat gränssnitt. Vi bygger en terminalklient för att skapa ett textbaserat gränssnitt mot databasen.

<!--more-->

[FIGURE src=image/snapvt17/sqlite-transaction.png?w=w2 caption="Transaktioner för att utföra många saker i en sekvens utan avbrott och störmoment."]

[FIGURE src=image/snapvt17/express-loaded-resources.png?w=w2 caption="Node.js med webb- och applikationsservern Express."]

[FIGURE src=image/snapvt17/express-mysql-view-all.png?w=w2 caption="Via Express använder vi oss av MySQL och HTML formulär för att visa och uppdatera databasens innehåll."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 23: Transaktioner

Vissa av kapitlen finns i [bokens webbkurs](http://www.databasteknik.se/webbkursen/), del 2.

Det finns ytterligare ett kapitel i boken som är relaterat till transaktioner, det går utanför kursens ram men läs vid intresse.

1. [Databasteknik](kunskap/boken-databasteknik)
    * Kap 24: Hur transaktioner hanteras inuti databashanteraren



###Artiklar {#artiklar}

Läs följande:

1. Om du känner behov av att träna upp dig i, eller repetera, klientsidetekniker med HTML, CSS och JavaScript så kan du utgå från tipset "[Kom igång (snabbt) med HTML, CSS och JavaScript](coachen/kom-igang-snabbt-med-html-css-och-javascript)" som ger dig en snabb insyn i de tre teknikerna och hur de samverkar i webbläsaren.

1. Läs översiktligt om vad [Express](http://expressjs.com/) klarar av som webb- och applikationsserver. Kolla runt i dokumentationen och bekanta dig med begrepp och exempelkod.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*


<!--
1. Du behöver ha grundläggande koll på HTML och CSS. Som en uppfräschning av dina kunskaper, eller som en kort intro, så jobbar du igenom materialet i tipset "[Kom igång (snabbt) med HTML, CSS och JavaScript](coachen/kom-igang-snabbt-med-html-css-och-javascript)". Jobba igenom materialet grundligt eller översiktligt, beroende på ditt eget behov.
-->



###Övningar {#ovningar}

Genomför följande övning för att förbereda inför uppgifterna.

1. Jobba igenom "[Transaktioner i databas](kunskap/transaktioner-i-databas)" för att lära dig grunderna i hur du använder transaktioner i databaser. Spara dina exempelprogram i `me/kmom04/trans`.

1. Jobba igenom artikeln "[Grunderna i Express med Node.js](kunskap/grunderna-i-express-med-nodejs)" för att komma igång med webb- och applikationsservern Express i Node.js. Spara dina exempelprogram i `me/kmom04/myexpress`.

<!--stop-->

1. Jobba igenom artikeln "[Databas appserver med Express och MySQL](kunskap/databas-appserver-med-express-och-mysql)" som visar hur du kan jobba med MySQL tillsammans med Express och Node.js. Spara dina exempelprogram i `me/kmom04/express-sql`.


<!--
1. Update transaktions (new article) with document on Isolation levels and Dirty reads and Deadlock. https://docs.google.com/document/d/15k4XbQxNOpJp-sqxwWX-FmG8UyerGSF36YDerSelbBc/preview

-->


<!-- PHP alternativ? Eller kanske inte. -->

<!--
1. **KLIENT FÖR ATT TESTA TRANSAKTIONER OCH LÅSNING?**

1. Jobba igenom guiden "[Bygg en RESTful server med Node.js](kunskap/bygg-en-restful-server-med-node-js)". Du kan spara dina testprogram i `me/kmom03/nodetest`.

1. Jobba igenom artikeln "[Spara serverns processid i en fil](kunskap/spara-serverns-processid-i-en-fil)".

1. Jobba igenom artikeln "[Skicka environment variabler till Node.js](kunskap/skicka-environment-variabler-till-nodejs)".

1. Skicka options och arguments till en kommandoradsklient i JavaScript och Node.js.
-->



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Skapa ER-modell för en databas (logisk/fysisk)](uppgift/skapa-er-modell-for-en-databas-logisk-fysisk)". Detta är den avslutande delen av uppgiften. Spara allt du gör i `me/kmom04/er2`.

1. **Skapa KLIENT, ÅTERANVÄND GEMENSAM MODUL?** (skolan, båtklubben), ER-uppgiften, nu med data som kan importeras från csv?

1. BYGG VIDARE PÅ ER-UPPGIFTEN. Först i terminalklient och sen i express? Gör uppgiften "[Bygg en faktureringsmotor för båtklubben (invoice)](uppgift/bygg-en-faktureringsmotor-for-batklubben)". Spara koden i `me/kmom03/invoice`.

1. **FOKUS TRANSAKTION** Utför uppgiften "[Skapa en appserver mot MySQL](uppgift/skapa-en-appserver-mot-mysql)". I uppgiften får du jobba med både Express, MySQL och programmera i databasen. Spara koden i `me/app`.



<!--
1. Gör uppgiften "[Skapa en RESTful HTTP-server med Node.js (server)](uppgift/skapa-en-restful-http-server-med-node-js)". Spara koden i `me/kmom03/server`.

-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Hur gick det att förstå konceptet transaktioner i databas?
* Gick det bra att komma igång med Express?
* Gick det bra att komma igång med en kommandoradsklient i Node.js?
* Gick det bra att använda MySQL tillsammans med Express/Node.js?
* Känns det som du har koll på teknikerna och hur de samverkar?

---
author: lew
revision:
    "2021-05-12": "(A, lew) Nytt material inför HT21."
...

Kmom01: Utvecklingsmiljö
==================================

Låt oss komma i gång med en labbmiljö, och en miljö för kursen. För er som vill repetera eller inte har läst HTML/CSS innan kommer det finnas möjlighet att läsa på om det innan det används i den här kursen.

Detta kursmoment ger dig basen för resten av kursen, det hanterar grunderna som behövs så att vi i kommande kursmoment kan dyka ned mer i programmering i JavaScript.

<!--more-->

[FIGURE src=/img/js-v2/batman.png?w=w2 caption="En interpretator för JavaScript."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Det finns en [längre beskrivning om kursens labbmiljö](./../installera-labbmiljo). Läs den om du är osäker på vad som skall göras, eller om detta är din första dbwebb-kurs.

Den korta varianten är att du behöver [installera labbmiljön](./../labbmiljo), uppdatera [dbwebb-cli](dbwebb-cli) samt klona och initiera kursrepot.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb selfupdate
dbwebb clone js
cd js
dbwebb init
```



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 6-10 studietimmar)*


### Kurslitteratur  {#kurslitteratur}

Läs följande:

1. Bekanta dig med kurslitteraturen [Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript) genom att läsa igenom det första kapitlet [Ch1 Basic JavaScript](http://speakingjs.com/es5/ch01.html) (läs till och med stycket om "Strict Mode") som ger dig en introduktion till grundkonstruktioner i programmeringsspråket JavaScript.



###MDN {#mdn}

I kursen används Mozilla Developers Network (MDN) som en resurs generellt för webbresurser och specifikt för referensmanual till programmeringsspråket JavaScript.

Vill du hamna på rätt manualsida så lägger du alltid till "mdn" till din googling. Det finns många versioner av JavaScript och du vill gå tillbaka till källan i referensmanualen för att veta vad som är rätt (eller fel).

Gör följande:

1. Bekanta dig kort med översikten på [MDN: Web technology for developers](https://developer.mozilla.org/en-US/docs/Web). Där ser du generellt material om webbteknologier.

1. Bekanta dig specifikt med det som finns under rubriken "JavaScript". Använd minst 10 minuter av din tid för att kika runt och läsa någon av de inledande artiklarna om JavaScript.



### Video  {#video}

Titta på följande:

1. Videoserien [Lär dig JavaScript](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_YXUQlr5aAzJ406vSsmeMT) är tätt kopplat till kursmaterialet. Kika igenom serien under kursens gång.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 4-10 studietimmar)*



###Övningar {#ovningar}

Jobba igenom följande.

<!-- 1. Du behöver ha grundläggande koll på HTML och CSS. Som en uppfräschning av dina kunskaper, eller som en kort intro, så jobbar du igenom materialet i tipset "[Kom igång (snabbt) med HTML, CSS och JavaScript](coachen/kom-igang-snabbt-med-html-css-och-javascript)". Jobba igenom materialet grundligt eller översiktligt, beroende på ditt eget behov. -->

<!-- 1. Jobba igenom artikeln "[Kom i gång med HTML, CSS och JavaScript](kunskap/kom-i-gang-med-html-css-och-javascript)" som visar dig hur du gör ditt första program i JavaScript och ger dig en grundstruktur för kursens övningar. -->

1. Gå igenom [guiden](guide/js/) som följer kursens moment. För kursmoment 1 gäller delarna:
    * [Inledning](guide/js/section_break_1)
    * [Språkkonstruktioner](guide/js/section_break_2)
    * [Inbyggda typer - steg 1](guide/js/section_break_3)

1. Jobba igenom artikeln [Kom igång med JavaScript i terminalen](kunskap/kom-igang-med-javascript-i-terminalen).



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

<!-- 1. Gör laborationen "[JavaScript med variabler och inbyggda funktioner](uppgift/javascript-med-variabler-och-inbyggda-funktioner)". Labben genereras i `me/kmom01/lab1`.

1. Gör uppgiften "[Sandbox steg 1](uppgift/sandbox-steg-1)". Spara resultatet i `me/kmom01/sandbox`. -->

1. Gör uppgiften "[JavaScript i terminalen](uppgift/javascript-i-terminalen)". Spara dina filer `kmom01/script/`.

1. Gör uppgiften "[Skapa en me-sida för redovisning i dbwebb-kurs](uppgift/skapa-en-me-sida-for-redovisning-i-dbwebb-kurs)". Spara resultatet i `me/redovisa`.


<!-- 1. Gör uppgiften "[Skapa din egen Sandbox för JavaScript testprogram](uppgift/skapa-din-egen-sandbox-for-javascript-testprogram)". Har du gjort övningen är du nästan klar. Spara resultatet i `me/kmom01/sandbox`. -->





Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Vilken utvecklingsmiljö använder du (berätta om något förändrats sen sist, om du svarat på frågan i tidigare kurser)?
* Är du bekant med HTML och CSS tillsammans med JavaScript sedan tidigare?
* Gick det bra med JSFiddle/CodePen, några funderingar kring verktygen?
* Gick det bra att komma i gång med kursmomentet, var det lagom, för litet, för stort, något som var svårt eller saknades?
* Vilken är din TIL för detta kmom?

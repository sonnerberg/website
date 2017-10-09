---
author: mos
revision:
    "2017-10-09": (I, mos) Genomgång inför ht17, ny struktur labbmiljö.
    "2017-09-27": (H, lew) Ny kurslitteratur.
    "2016-03-15": (G, mos) Lade till videoserie med "Lär dig JavaScript".
    "2015-08-26": (F, mos) Ny struktur på inledning och installaiton av labbmiljö.
    "2015-01-19": (E, mos) Bort ruta om kursutveckling och bort länk till youtube-serie.
    "2014-10-01": (D, mos) Ändrade länken till redovisa-instruktionen.
    "2014-08-30": (C, mos) Första officiella releasen.
    "2014-08-19": (B, mos) Felaktig länk till uppgift för me-sidan.
    "2014-08-11": (A, mos) Första utgåvan för javascript1 kursen.
...
Kmom01: Utvecklingsmiljö
==================================

Låt oss komma i gång med en labbmiljö, och en miljö för kursen, tillsammans med en introduktion i HTML, CSS och JavaScript.

Detta kursmoment ger dig basen för resten av kursen, det hanterar grunderna som behövs så att vi i kommande kursmoment kan dyka ned mer i programmering i JavaScript.

<!--more-->

[FIGURE src=/image/snap/js1-sandbox-mod.png?w=w2 caption="En aningen gulare sandbox för mina testprogram."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Kursens labbmiljö  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Du behöver installera kursens labbmiljö samt ha tillgång till verktyget `dbwebb` som du installerar på terminalen. När du är klar kan du klona kursrepot där du finner en del av kursens material.



###Labbmiljön {#kurslabbmiljo}

Det första du behöver göra är att installera en labbmiljö för kursen. Om detta är din första dbwebb-kurs så kan det innebära en hel del jobb och en del nya tekniker. Se till att du har gott om tid när du gör detta.

1. [Installera labbmiljön](./../labbmiljo) som behövs för kursen. 



###Installera/uppdatera kommandot dbwebb {#dbwebbcli}

Om du redan har installerat kommandot dbwebb så gör du en selfupdate för att vara säker på att du har senaste versionen. Sedan kan du fortsätta till nästa stycke.

```text
dbwebb selfupdate
```

Om du vill ha en introduktion till installationen av dbwebb-kommandot så kikar du på videon "[Mikael installerar dbwebb-cli som en del av labbmiljön](https://www.youtube.com/watch?v=vlZRW2OZamE)".

Utför följande steg för att installera kommandot dbwebb.

1. [Installera kommandot `dbwebb`](dbwebb-cli/kom-igang-och-installera). Kommandot används under hela kursen för att jobba med kursmaterialet.

1. När du har installerat kommandot så fortsätter du med sektionen för att [konfigurera kommandot `dbwebb`](dbwebb-cli/konfiguration).



###Klona kursrepot {#clona}

Kursrepot innehåller en viss del av kursmaterialet och det ger en struktur där du skriver kod för att lösa övningar och uppgifter i kursen. Du hämter det med hjälp av kommandot dbwebb. Vi kallar det för att du klonar ditt kursrepo. Klona är ett begrepp som används i versionshanteringssystemet Git.

1. Läs om hur du [laddar ned (klona) ditt lokala kursrepo](dbwebb-cli/clone) som innehåller kursmaterial för kursen.

Den snabba vägen.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb clone javascript1
```

Bra, det var inledningen och vissa nödvändiga saker. Nu kan du sätta igång "på riktigt" med det första kursmomentet.



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 6-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. Bekanta dig med kurslitteraturen [Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript) genom att läsa igenom det första kapitlet [Ch1 Basic JavaScript](http://speakingjs.com/es5/ch01.html) (läs till och med stycket om "Strict Mode") som ger dig en introduktion till grundkonstruktioner i programmeringsspråket JavaScript.


<!--
    * [Ch7 Syntax](http://speakingjs.com/es5/ch07.html)
    * [Ch8 Values](http://speakingjs.com/es5/ch08.html)
    * [Ch9 Operators](http://speakingjs.com/es5/ch09.html)
    * [Ch10 Booleans](http://speakingjs.com/es5/ch10.html)
    * [Ch11 Numbers](http://speakingjs.com/es5/ch11.html)
    * [Ch12 Strings](http://speakingjs.com/es5/ch12.html)
-->

<!-- 1. [Eloquent JavaScript: A Modern Introduction to Programming](kunskap/boken-eloquent-javascript-a-modern-introduction-to-programming)
    * [Ch0 Introduction](http://eloquentjavascript.net/00_intro.html)
    * [Ch1 Values, Types, and Operators](http://http://eloquentjavascript.net/01_values.html)
    * [Ch12 JavaScript and the browser](http://eloquentjavascript.net/12_browser.html) -->



###MDN {#mdn}

I kursen används Mozilla Developers Network (MDN) som en resurs generellt för webbresurser och specifikt för referensmanual till programmeringsspråket JavaScript.

Vill du hamna på rätt manualsida så lägger du alltid till "mdn" till din googling. Det finns många versioner av JavaScript och du vill gå tillbaka till källan i referensmanualen för att veta vad som är rätt (eller fel).

Gör följande:

1. Bekanta dig kort med översikten på [MDN: Web technology for developers](https://developer.mozilla.org/en-US/docs/Web). Där ser du generellt material om webbteknologier.

1. Bekanta dig specifikt med det som finns under rubriken "JavaScript". Använd minst 10 minuter av din tid för att kika runt och läsa någon av de inledande artiklarna om JavaScript.

1. För en snabb introduktion till konstruktionerna i språket JavaScript kan jag rekommendera dokumentet "[MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)" och de inledande kapitlen som kompletterar det du läst i kurslitteraturen.
    * Introduction
    * Grammar and types
    * Control flow and error handling
    * Loops and iteation



###Artiklar {#artiklar}

Läs följande:

1. I kursen används validatorer och en kodstandard för att testa att du skriver kod på ett, enligt kodstandarden, acceptabelt sätt. Du kan läsa om dbwebb-kodstandarden på [npm javascript-code-style](https://www.npmjs.com/package/javascript-style-guide). Du kan diskutera [kodstandarden i forumet](t/6327).



###Video  {#video}

Titta på följande:

1. Videoserien [Lär dig JavaScript](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-Id4-mxJK1Pi91_7Ob1W-K) är tätt kopplat till kursmaterialet. Kika på de videor som börjar med 1.

1. Se JavaScript-gurun Douglas Crockford i en historisk bakgrund om programmeringsspråk och en introduktion till JavaScript: "[Crockford on JavaScript - Volume 1: The Early Years](https://www.youtube.com/watch?v=JxAXlJEmNMg)".



###Lästips {#lastips}

Följande är intressant att ha koll på.

1. Lär dig mer om historian om datorer, eller som de säger, "[The mother of All Demos](http://en.wikipedia.org/wiki/The_Mother_of_All_Demos)", när Douglas Engelbart, för första gången demonstrerar det som numer är vardagsmat för oss alla. [Se hela presentationen](https://www.youtube.com/watch?v=VScVgXM7lQQ&list=PL76DBC8D6718B8FD3).



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 4-10 studietimmar)*



###Övningar {#ovningar}

Jobba igenom följande.

1. Du behöver ha grundläggande koll på HTML och CSS. Som en uppfräschning av dina kunskaper, eller som en kort intro, så jobbar du igenom materialet i tipset "[Kom igång (snabbt) med HTML, CSS och JavaScript](coachen/kom-igang-snabbt-med-html-css-och-javascript)". Jobba igenom materialet grundligt eller översiktligt, beroende på ditt eget behov.

1. Jobba igenom artikeln "[Kom i gång med HTML, CSS och JavaScript](kunskap/kom-i-gang-med-html-css-och-javascript)" som visar dig hur du gör ditt första program i JavaScript och ger dig en grundstruktur för kursens övningar.



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Skapa din egen Sandbox för JavaScript testprogram](uppgift/skapa-din-egen-sandbox-for-javascript-testprogram)". Spara resultatet i `me/kmom01/sandbox`.

1. Gör uppgiften "[Skapa en me-sida för redovisning i kursen javascript1](uppgift/skapa-en-me-sida-for-redovisning-i-kursen-javascript1)". Spara resultatet i `me/redovisa`.

1. Gör laborationen "[JavaScript med variabler och inbyggda funktioner](uppgift/javascript-med-variabler-och-inbyggda-funktioner)". Labben genereras i `me/kmom01/lab1`.



<!--
###Extra {#extra}

Det finns inga extra uppgifter.
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Vilken utvecklingsmiljö använder du (berätta om något förändrats sen sist, om du svarat på frågan i tidigare kurser)?
* Är du bekant med HTML, CSS och JavaScript sedan tidigare?
* Gick det bra med JSFiddle/CodePen, några funderingar kring verktygen?
* Gick det bra att komma i gång med kursmomentet, var det lagom, för litet, för stort, något som var svårt eller saknades?

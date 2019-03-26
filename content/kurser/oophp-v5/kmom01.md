---
views:
    flash:
        region: flash
        template: default/image
        data:
            src: "img/snapvt19/oophp-kmom01-flash.svg"
author:
    - mos
    - lew
revision:
    "2019-03-13": "(E, mos) Uppdaterad till v5."
    "2018-03-23": "(D, mos) Lade till videoserie för kmom."
    "2018-03-19": "(C, mos) Uppdaterad till oophp v4."
    "2017-03-27": "(B, mos) Länkar till phpcs, phpmd, psr-1, psr-2."
    "2017-03-24": "(A, mos, lew) Första versionen släppt."
...
Kmom01: Objektorientering i PHP
==================================

Vi har mycket att göra så det är bäst vi sätter igång. Innan kursen är slut skall vi hantera objektorienterad PHP, enhetstestning, grunder i PHP-baserade ramverk och databaser med ramverk.

Vi börjar med grunderna i objektorienterad PHP, det blir objekt och klasser med inkapsling, konstruktorer och destruktorer, setters och getters, egenskapade exceptions och vi ser hur man kan lagra ett objekt i sessionen.

Vi jobbar i en guide och bygger små grundläggande testprogram för att testa och se hur objektorienterade konstruktionerna fungerar i PHP.

För att repetera våra PHP-kunskaper och samtidigt komma igång med klasser och objekt så bygger vi en variant av spelet "Gissa vilket nummer jag tänker på".

Vi bygger en me-sida (redovisa-sida) med PHP-ramverket Anax. Det ger oss möjligheten att bekanta oss med en färdig webbplats i eet PHP-ramverk. Senare i kursen kommer vi att flytta in spelet "Gissa mitt nummer" in i ramverkets struktur.



<!-- more -->

Här är ett par bilder som visar vad som nu skall hända.

[FIGURE src=image/snapvt18/oophp-constructor.png?w=w3 caption="Små testprogram hjälper oss att förstå grunderna."]

[FIGURE src=image/snapvt18/oophp-guess-my-number-post.png?w=w3 caption="Spela spelet Gissa mitt nummer med PHP."]

[FIGURE src=image/snapvt19/oophp-me.png?w=w3 caption="Mallen för me-sidan i oophp."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Labbmiljön är densamma som i design-kursen. Du behöver minst version 7.2 av PHP, både i webbservern och i terminalen.

Det finns en [längre beskrivning om kursens labbmiljö](./../installera-labbmiljo). Läs den om du är osäker på vad som skall göras, eller om detta är din första dbwebb-kurs.

Den korta varianten är att du behöver [installera labbmiljön](./../labbmiljo), uppdatera [dbwebb-cli](dbwebb-cli) samt klona och initiera kursrepot.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb selfupdate
dbwebb clone oophp
cd oophp
dbwebb init
```



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*



### Bok {#bok}

Kolla in följande.

1. I kursboken för htmlphp [Webbutveckling med PHP och MySQL](kunskap/boken-webbutveckling-med-php-och-mysql) kan du repetera dina kunskaper om PHP. Boken innehåller även delar som är relevanta till PHP med databaser vilket är aktuellt för senare kmom, dock finns inget om objektorienterad PHP.

1. Det finns en ny online-bok "[PHP Apprentice - An online book for learning PHP](https://phpapprentice.com/)" som håller på att utvecklas, den är rätt kort men kanske kan du eventuellt finna den nyttig till en snabb översikt av PHP och delar av objektorienterad PHP.



### Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Fräscha upp ditt minne av PHP genom att snabbt skumma igenom guiden "[Kom igång med programmering i PHP](guide/kom-igang-med-programmering-i-php)". Du bör sedan tidigare (htmlphp) ha koll på det som nämns i guiden. Om du bygger exempelprogram för att testa och leka så kan du lägga dem i `me/kmom01/php20`.

1. Bekanta dig snabbt och översiktligt med innehållet i PHP-manualen och stycket om [Klasser och Objekt](https://www.php.net/manual/en/language.oop5.php). Som vanligt är referensmanualen vår källa till information, så bli kompis med dess struktur och lär dig vilken typ av information du där kan hitta.

1. Bekanta dig översiktligt med dokumentet [PHP The Right Way](http://www.phptherightway.com/). Det är skrivet av PHP communityn och ger en översikt över PHP som språk och de verktyg och processer man normalt arbetar med. Vi kommer att återkomma till dokumentet under kursens gång. Du kan se dokumentet som en innehållsförteckning till vad en god PHP-programmerare bör ha koll på.



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller genomgångar och föreläsningar som spelas in (streamas) och därefter läggs i en spellista. Du kan nå spellistan på "[oophp streams vt19](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-igucRSQ6tFYg9x8to5HiE)".

1. Uppgifter och övningar kan innehålla extra videomaterial i form av spellistor kopplade till respektive artikel. Ofta syns dessa videor i inledningen av artikeln.

<!--
Det finns en [YouTube spellista kopplad till kursen](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_jh6fAj1iwiJSj70DXA2Vn), kika på de videos som börjar med 0 och 1. De hälsar dig välkommen och ger dig en introduktion till kursen och till detta kursmoment.
-->

<!--
Allmän video om oophp?
-->



### Ramverk Anax {#anax}

Följande referenser är relevanta för ramverket Anax, studera dem snabbt, kort och översiktligt.

1. Som bas använder vi ramverket Anax och dess moduler, tillsammans med ett antal andra moduler. [Källkoden för Anax finner du på GitHub](https://github.com/canax). Grunden för redovisa-sidan är [repot anax-oophp-me](https://github.com/canax/anax-oophp-me).

1. Vi skriver PHP enligt kodstandarden [PSR-1: Basic Coding Standard](http://www.php-fig.org/psr/psr-1/) och [PSR-2: Coding Style Guide](http://www.php-fig.org/psr/psr-2/). Dessa är standardiserade av PHP communityn och standardiseringen hanteras av organisationen [PHP-FIG](https://www.php-fig.org/) vars syfte är att standardisera komponenter så att de går att använda mellan olika ramverk.

1. Vi använder valideringsverktygen [phpcs](https://github.com/squizlabs/PHP_CodeSniffer/wiki) och [phpmd](https://phpmd.org/). Det går att installera dem som linters i Atom och se valideringsfelen direkt i texteditorn.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. I guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)" jobbar du igenom följande delar. Spara koden i `me/guide`.
    * [Intro till guiden](guide/kom-igang-med-objektorienterad-programmering-i-php/intro-till-guiden)
    * [Objekt och Klass](guide/kom-igang-med-objektorienterad-programmering-i-php/objekt-och-klass)

1. Gör uppgiften "[Gissa numret med PHP](uppgift/gissa-numret-med-php)". Uppgiften låter dig värma upp din gamla PHP-kunskaper och samtidigt träna på grunderna med objekt och klasser. Spara din kod i `me/kmom01/guess`.

1. Gör uppgiften "[Bygg en me-sida för oophp med Anax](uppgift/bygg-en-me-sida-for-oophp-med-anax)". Du skall bygga en me-sida som du taggar och publicerar på GitHub. Spara allt under `me/redovisa`.

1. Försäkra dig om att du har gjort `dbwebb publish redovisa` och taggat din inlämning med version 1.0.0 (eller högre) samt pushat repot inklusive taggarna till GitHub.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Har du tidigare kunskaper (eller förutfattade meningar) i objektorienterad programmering i PHP eller något annat språk?
* Hur gick det att komma in i PHP och programmering med objekt och klasser?
* Hur det gick det att utföra uppgiften "Gissa numret"?
* Vilken taktik valde du för att lagra spelet i sessionen?
* Gick det bra att komma igång med Git och GitHub (du gjorde samma i kursen design)?
* Har du några inledande reflektioner kring me-sidan och dess struktur?
* Vilken är din TIL för detta kmom?

TIL är en akronym för "Today I Learned" vilket leksamt anspelar på att det finns alltid nya saker att lära sig, varje dag. Man brukar lyfta upp saker man lärt sig och där man kanske hajade till lite extra över dess nyttighet eller enkelhet, eller så var det bara en ny lärdom för dagen som man vill notera.

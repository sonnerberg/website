---
author:
    - mos
    - lew
revision:
    "2018-02-26": "(PC1, mos) Arbetsmaterial oophp v4."
    "2017-03-27": "(B, mos) Länkar till phpcs, phpmd, psr-1, psr-2."
    "2017-03-24": "(A, mos, lew) Första versionen släppt."
...
Kmom01: Objektorientering i PHP
==================================

[WARNING]
**Version 4 av oophp.**

En uppdaterad version av kursen är under bearbetning och kursen ges första gången vårterminen 2018.

[/WARNING]

Vi får en möjlighet att repetera våra PHP-kunskaper och sedan fortsätter vi med grunderna i klasser och objekt med PHP. Vi gör en programmeringsövning med det käna konceptet om "Gissa vilket nummer jag tänker på" och implementerar spelet med GET, POST och en variant med SESSIONER. Det blir repetition av PHP och hur HTTP-protokollar, formulär och länkar fungerar tillsammans. Dessutom blir det en introduktion till klasser i PHP.

[FIGURE src=image/snapvt17/guess-my-number-session-object.png?w=w3 caption="Gissa numret i PHP hjälper dig komma igång och repetera det du redan kan."]

Vi bygger dessutom en me-sida i en katalogstruktur som i längden kommer att ge oss en insikt i hur ett webbaserat ramverk byggs upp.

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Det finns en [längre beskrivning om kursens labbmiljö](./../installera-labbmiljo). Läs den om du är osäker på vad som skall göras, eller om detta är din första dbwebb-kurs.

Den korta varianten är att du behöver [installera labbmiljön](./../labbmiljo), uppdatera [dbwebb-cli](dbwebb-cli) samt klona och initiera kursrepot.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb selfupdate
dbwebb clone oophp
cd oophp
dbwebb init
```

<!--stop-->



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*


<!--
###Kurslitteratur  {#kurslitteratur}

Det finns inga specifika läsanvisningar i kurslitteraturen.

-->


###Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Fräscha upp ditt minne av PHP genom att snabbt skumma igenom guiden "[20 steg för att komma igång med PHP (php20)](kunskap/kom-i-gang-med-php-pa-20-steg)". Du bör sedan tidigare (htmlphp) ha koll på det som nämns i guiden. Om du bygger exempelprogram så kan du lägga dem i `me/kmom01/php20`.

1. Bekanta dig översiktligt med PHP manualen och stycket [Klasser och Objekt](http://php.net/manual/en/oop5.intro.php). Som vanligt är referensmanualen vår källa till information, så bli kompis med dess struktur.

1. Bekanta dig översiktligt med dokumentet [PHP The Right Way](http://www.phptherightway.com/). Det är skrivet av PHP community och ger en översikt över PHP som språk och de verktyg och processer man normalt arbetar med. Vi kommer att återkomma till dokumentet under kursens gång.


<!--
1. Läs om "[The MicroPHP Manifesto](https://funkatron.com/posts/the-microphp-manifesto.html)" som ger en reaktion på ramverk och termen mikroramverk. ([Alternativ länk till artikeln](https://dbwebb.se/t/6379)).
-->



<!--
###Verktyg {#verktyg}

Läs översiktligt in dig på följande verktyg som används i kursen.

1. Vi använder pakethanteraren [Composer](https://getcomposer.org/) för att installera PHP moduler.

1. De PHP-moduler vi använder är publicerade på [Packagist](https://packagist.org/), ett sökbart repository för PHP-moduler.

1. Bekanta dig kort med [manualen till phpdoc](https://phpdoc.org/) som beskriver hur docblock-kommentarer skrivs till PHP.
-->



<!--
###Videor {#videor}

Det finns inga videos.

Kika på följande videos.

1. Det finns en [YouTube spellista kopplad till kursen](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_jh6fAj1iwiJSj70DXA2Vn), kika på de videos som börjar med 0 och 1.
-->


<!--
###Lästips {#lastips}

Följande lästips är att rekommendera.

1. [Dia](https://wiki.gnome.org/Apps/Dia/) är ett ritverktyg där du kan skapa UML-diagram. Du vill ha ett sådant, eller motsvarande, i din arsenal av verktyg.

1. Vi skriver PHP i enlighet med kodstandarden [PSR-1](http://www.php-fig.org/psr/psr-1/) och [PSR-2](http://www.php-fig.org/psr/psr-2/).

1. Kika gärna på valideringsverktygen vi använder, [phpcs](https://github.com/squizlabs/PHP_CodeSniffer/wiki) och [phpmd](https://phpmd.org/). Du kan installera dem som linters i Atom, men först måste du installera dem i din PATH på ditt lokala system.

-->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-16 studietimmar)*



###Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

1. Jobba igenom guiden "[Kom igång med objektorienterad PHP-programmering på 20 steg"](kunskap/kom-i-gang-med-oophp-pa-20-steg)". Det handlar om grunderna med objektorienterad programmering i PHP. Exempelprogram som du bygger för din egna skull kan du spara i `me/kmom01/oophp20`.

1. Jobba igenom artikeln "[Bygg ett eget PHP-ramverk](kunskap/bygg-ett-eget-php-ramverk)" som ger dig grunden till ett eget litet ramverk. Delvis känner du igen ramverket från kursen design. Du sparar koden i `me/anax-lite`.



###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Gör uppgiften "[Gissa vilket nummer jag tänker på](uppgift/gissa-numret)". Spara din kod i `me/kmom01/guess`. Uppgiften värmer upp din gamla PHP-kunskaper och inför några nya i form av objekt och lite mer.

1. Gör uppgiften "[Bygg en me-sida med Anax Lite](uppgift/me-sida-med-anax-lite)". Det handlar om att skapa ditt eget anax-lite och publicera på Github. Använd sedan ditt anax-lite för att göra grunden till en me-sida för kursen. Spara allt under `me/anax-lite`.

1. Pusha och tagga ditt Anax Lite, allt eftersom och sätt en avslutande tagg (1.0.\*) när du är klar med alla uppgifter i kursmomentet.

<!--
1. Gör uppgiften "[Bygg en me-sida med Anax Lite](uppgift/me-sida-med-anax-lite)". Det handlar om att skapa ditt eget anax-lite och publicera på Github. Använd sedan ditt anax-lite för att göra grunden till en me-sida för kursen. Spara allt under `me/anax-lite`.

1. Gör uppgiften "[En navbar till Anax Lite (steg 1)](uppgift/en-navbar-till-anax-lite-steg-1)" som ger dig en struktur för att separera HTML och konfiguration av din navbar. Spara din kod i `me/anax-lite`.
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Hur känns det att hoppa rakt in i klasser med PHP, gick det bra?

TIL är en akronym för "Today I Learned" vilket leksamt anspelar på att det finns alltid nya saker att lära sig, varje dag. Man brukar lyfta upp saker man lärt sig och där man kanske hajade till lite extra över dess nyttighet eller enkelhet, eller så var det bara en ny lärdom för dagen som man vill notera.

* Vilken är din TIL för detta kmom?

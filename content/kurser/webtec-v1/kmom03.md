---
views:
    flash:
        region: flash
        template: default/image
        data:
            src: "image/webtec/logo-php.png"
author:
    - mos
revision:
    "2021-05-20": "(PA, mos) Arbete påbörjat för webtec-v1."
...
Kmom03/04: PHP
==================================

[WARNING]

**Arbete pågår**.

[/WARNING]

<!-- stop-->

En webbplats med HTML och CSS kan man kalla en statisk webbplats då innehållet ligger statiskt i HTML- och CSS-filer. En dynamisk webbplats kan ändra sidornas innehåll baserat på inkommande argument eller om användaren är inloggad på webbplatsen eller ej. En dynamisk webbplats kan också hämta sitt innehåll från andra källor, till exempel en databas. Dynamiken i en webbplats kan implementeras i klienten (webbläsaren med JavaScript) och/eller på serversidan (webbservern). Vi kommer titta på hur man gör dynamiska webbplatser med PHP på serversidan.

PHP är ett programmeringsspråk som är populärt att använda för att bygga dynamiska webbplatser. Vi skall börja med att lära oss hur PHP fungerar som programmeringsspråk och sedan ser vi hur PHP kan användas för att bygga dynamiska webbplatser.

PHP är ett vanligt programmeringsspråk och har konstruktioner som variabler, uttryck, if-satser, loopar, funktioner, arrayer och så vidare.

När PHP används tillsammans med webbplatsen kan vi posta HTML formulär till servern som hanterar dess innehåll. Vi kan till exempel bygga en procedur för att logga in på en webbplats med hjälp av formulär och sessioner.

När en webbplats växer med fler sidor och konstruktioner så är det viktigt att ha en god grundstruktur för hur filerna sparas. Vi går igenom hur denna grundstruktur kan se ut.

<!--more-->

<!--
[FIGURE src=image/snapht18/multipage.png?w=w3 caption="En multisida i PHP, navigeringsmeny i vänsterkanten och färgad i pastellfärger."]
-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 + 20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljö  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Moped

* Installera PHP i pathen
* Installera composer



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-12 studietimmar)*

Följande är det som du bör studera för att läsa in dig på området och förbereda dig inför övningar och uppgifter.



### Introduktion till PHP {#f1}

Vi börjar med en introduktion till programmeringsspråket PHP, dess beståndsdelar och hur man skriver program med PHP.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->



### PHP och arrayer {#f2}

Vi tittar på hur vi kan jobba med arrayer i PHP.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->



### PHP och funktioner {#f3}

Vi ser hur vi kan arrangera och organisera PHP-kod i funktioner.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->



### PHP webbsidor med sidkontroller och vyer {#f4}

Vi fortsätter med att se hur PHP kan användas när vi bygger webbplatser och vi skapar en grundstruktur för webbplatsens sidor.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->



### PHP och HTML formulär {#f5}

Vi fortsätter med att se hur PHP kan användas när vi bygger webbplatser och vi skapar en grundstruktur för webbplatsens sidor.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->



### PHP, cookies och sessioner {#f6}

Vi fortsätter med att se hur PHP kan användas när vi bygger webbplatser och vi skapar en grundstruktur för webbplatsens sidor.

<!--
Slides till föreläsningen "[HTML, introduktion](https://dbwebb-se.github.io/webtec/lecture/L01-html-intro/slide.html)".

[YOUTUBE src="RJ5HKgZZs6w" width=700 caption="HTML, introduktion (med Mikael)."]
-->




<!--

Lägg läsanvisningar under respektive föreläsning

### PHP {#php}


Läs följande för att bekanta dig med tekniken.

1. Bekanta dig kort med [webbplatsen för PHP](http://php.net/), bara så att du har varit där och ser hur den ser ut. Det som vi framförallt kommer att använda framöver är [manualen för PHP](http://php.net/manual/en/). Kika snabbt igenom dess innehållsförteckning så att du ser vad det handlar om. Du behöver inte studera något i detalj för tillfället. Även för PHP funkar googling bra att nå rätt sida i referensmanualen, pröva "php echo" och min rekommendation är att du väljer PHP referensmanualen som landningssida, det blir bäst i längden.



### Kurslitteratur {#kursboken}

I kursboken [Webbutveckling med PHP och MySQL](kunskap/boken-webbutveckling-med-php-och-mysql) är följande kapitel relevanta att läsa igenom och/eller använda som referens.

* Kapitel 1 Introduktion
* Kapitel 2 Variabler
* Kapitel 3 Konstanter
* Kapitel 4 Operatorer
* Kapitel 5 Villkorssatser
* Kapitel 6 Iterationer

-->


### Video för orientering {#video}

Titta på följande videor/filmer.

* [A brief history of the World Wide Web](https://www.youtube.com/watch?v=sSqZ_hJu9zA)



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*



### Övningar {#ovningar}

Genomför följande övningar, det hjälper dig inför uppgifterna.

1. Jobba igenom övningen "[Gör en me-sida med HTML, CSS och PHP](kunskap/skapa-en-webbsida-med-html-css-och-php)". Övningen innehåller grunderna i HTML, CSS och PHP och visar hur du bygger upp en enkel webbplats. Filerna du jobbar med kan du spara i `me/kmom01/me`.

1. Jobba igenom övningen "[Gör en me-sida med HTML, CSS och PHP - steg 2](kunskap/skapa-en-webbsida-med-html-css-och-php-steg-2)". Övningen bygger vidare på grunderna i HTML, CSS och PHP och visar hur du bygger ut din webbplats med några vanliga bra-att-ha konstruktioner.

1. Jobba igenom övningen "[Bygg en multisida med PHP (v2)](kunskap/bygg-en-multisida-med-php-v2)". Spara filerna i katalogen `me/kmom03/multi`, så kan du använda dem i den kommande uppgiften.

Bygg formulär.
https://jonkopingenergi.se/privat/fiber/serviceavgift (använd även till databasen)

Debugbar
http://phpdebugbar.com/

Validator:
https://github.com/phan/phan/


<!--
Programmera PHP i cli-skript

Formulär GET
* POST
* FILE
* SESSION
* COOKIE
* login

* kontaktformulär, flashmeddelande

PHP
* funktioner, arrayer
-->



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[PHP lab 1: uttryck, datatyper och variabler](uppgift/php-lab1-uttryck-datatyper-och-variabler)". Spara alla filerna i katalogen `me/kmom01/lab1`.

1. Gör uppgiften "[PHP lab 2: villkor, loopar och inbyggda funktioner](uppgift/php-lab2-villkor-loopar-och-inbyggda-funktioner)". Spara alla filerna i katalogen `me/kmom02/lab2`.

1. Gör uppgiften "[PHP lab 3: Arrayer](uppgift/php-lab3-arrayer)". Spara alla filerna i katalogen `me/kmom03/lab3`.

1. Gör uppgiften "[Bygg en multisida och testa arrayer (v2)](uppgift/bygg-en-multisida-och-testa-arrayer-v2)". Spara filerna i katalogen `me/kmom03/multi`.

1. Gör uppgiften "[Bygg ut din me-sida till version 3 (v2)](uppgift/bygg-ut-din-htmlphp-me-sida-till-version-3-v2)". Spara filerna i katalogen `me/kmom03/me3`.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Hur känns det att komma igång med datastrukturer som arrayer? Är det koncept du känner igen sedan tidigare?
* Hur känns det med strukturer såsom sidkontroller, multisida och templatefiler?
* Är det något särskild du vill berätta om din me-sida och dess struktur? Något som du är extra nöjd med?
* Får du hjälp och stöd i guiderna (html/css-guiden och php-guiden)?
* Vilken är din TIL för detta kmom?

* Hur bekant är du med PHP och programmering rent allmänt, hur känns det att utveckla med PHP?
* Vad tyckte du om PHP-labben, enkel eller utmanande?



Resurser & Referenser {#resurser}
---------------------------------

Här anges referenser och övriga resurser som kan användas för vidare studier i det som kursmomentet omfattar.



### PHP {#php}

Grundläggande resurser för PHP äro följande.

* [Webbplatsen för PHP](http://php.net/)
* [Manualen för PHP](http://php.net/manual/en/)

Det fungerar bra att googla sig fram till relevant sida/funktion i manualen, pröva "php echo" och min rekommendation är att du väljer PHP referensmanualen som landningssida, det blir bäst i längden.



### W3Schools PHP {#w3sphp}

Webbplatsen W3Schools har en guide som är lättilgänglig när man vill komma igång med grunderna i PHP.

* [PHP Tutorial](https://www.w3schools.com/php/)



<!--
### PHP Guide {#phpguide}

Läs igenom följande sektion i guiden "[Kom igång med programmering i PHP](guide/kom-igang-med-programmering-i-php)". Det ger dig en grundläggande introduktion i att hantera PHP och hjälper dig inför de uppgifter du skall göra.

* [Grunder och struktur](guide/kom-igang-med-programmering-i-php/grunder-och-struktur)
* [Datastrukturer](guide/kom-igang-med-programmering-i-php/datastrukturer)
* [Värden, variabler och typer](guide/kom-igang-med-programmering-i-php/varden-variabler-och-typer)
* [Kontrollstrukturer](guide/kom-igang-med-programmering-i-php/kontrollstrukturer)
* [Sidkontroller](guide/kom-igang-med-programmering-i-php/sidkontroller)



### PHP videoserie {#phpvideo}

Det finns en videoserie som bygger på innehållet i guiden, kika gärna på den som ett komplement till guiden.

* [Kom igång med programmering i PHP (2019)](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-oIvGdREyAH-Oq_DQdqYW1)

-->

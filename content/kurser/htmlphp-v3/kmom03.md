---
author:
    - mos
revision:
    "2018-06-08": (prel, mos) Nytt dokument inför uppdatering av kursen.
    "2017-06-15": (F, mos) Uppdaterad labbserie.
    "2016-08-31": (E, mos) Lade till rätt videoserie från youtube.
    "2016-02-22": (D, mos) Bort med not om kursutveckling och länk till version 1.
    "2015-08-24": (C, mos) Släppt till ht15.
    "2015-08-06": (B, mos) Genomgången inför ht15.
    "2015-03-17": (A, mos) Första utgåvan för htmlphp version 2 av kursen.
...
Kmom03: Bygg multisida i PHP
==================================

[WARNING]

**Kursutveckling pågår till kurs htmlphp v3**

Kursstart hösten 2018.

[/WARNING]

I kursmomentet gås igenom de inbyggda arrayerna i PHP. Vi tittar på `$_GET`, och `$_SERVER` samt hur de kan användas som arrayer. Med hjälp av dessa arrayer, och lite mer PHP-kunskaper, gör vi ett par små testprogram för att klura ut hur saker och ting fungerar i PHP-världen.

Vi skapar en sida, som har sin egen meny, vi kallar den multisida och löser både den och lite andra småsaker med PHP-kod.

Till slut knyter vi ihop det genom att integrera multisidan i din me-webbplats. Resultatet blir me-sida version 3.0.

<!--more-->

Det blir en hel del PHP i detta kursmomentet.

[FIGURE src=image/snapht18/multipage.png?w=w3 caption="En multisida i PHP, navigeringsmeny i vänsterkanten och färgad i pastellfärger."]


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-8 studietimmar)*



### HTML & CSS {#htmlcss}

Läs följande för att fortsätta bekanta dig med teknikerna.

1. Läs igenom följande sektion i guiden "[Kom igång med HTML och CSS](guide/kom-igang-med-html-och-css)".
    * [Bakgrund](guide/kom-igang-med-html-och-css/bakgrund)



### PHP {#php}

Läs följande för att fortsätta bekanta dig med tekniken.

1. Läs igenom följande sektioner i guiden "[Kom igång med programmering i PHP](guide/kom-igang-med-programmering-i-php)".
    * [Datastrukturer](guide/kom-igang-med-programmering-i-php/datastrukturer)

1. I kursboken [Webbutveckling med PHP och MySQL](kunskap/boken-webbutveckling-med-php-och-mysql) är följande kapitel relevanta att läsa igenom.
    * Kapitel 2.3.5 Vektor
    * Kapitel 2.4 Miljövariabler
    * Kapitel 3 Konstanter



### Videor {#videor}

Det finns en samling videor som används i olika omfattning under kursens gång, [du finner dem på Youtube](https://www.youtube.com/channel/UCxX3bcidovf5MDLeXMcbDyg/playlists?view=50&shelf_id=9&sort=dd).



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*



### Övningar {#ovningar}

Genomför följande övningar.

1. Jobba igenom övningen "[Bygg en multisida med PHP (v2)](kunskap/bygg-en-multisida-med-php-v2)". Spara filerna i katalogen `me/kmom03/multi`, så kan du använda dem i den kommande uppgiften.



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[PHP lab 3: Arrayer](uppgift/php-lab3-arrayer)". Spara alla filerna i katalogen `me/kmom03/lab3`.

1. Gör uppgiften "[Bygg en multisida och testa arrayer (v2)](uppgift/bygg-en-multisida-och-testa-arrayer-v2)". Spara filerna i katalogen `me/kmom03/multi`.

1. Gör uppgiften "[Bygg ut din me-sida till version 3 (v2)](uppgift/bygg-ut-din-htmlphp-me-sida-till-version-3-v2)". Spara filerna i katalogen `me/kmom03/me3`.



<!--
###Extra {#extra}

En bra extrauppgift vore att bygga en ny multisida till din me-sida. En multisida där du kan göra egna små testprogram för att testa hur PHP, HTML och CSS fungerar. Du kan sedan fylla på den multisidan under resten av kursen. Det är en bra taktik att skriva små exempelprogram för att se hur något fungerar och i en multisida kan du enkelt fylla på med nya exempelprogram.
-->



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

---
author:
    - mos
    - lew
revision:
    "2018-02-26": "(PB1, mos) Arbetsmaterial oophp v4."
    "2017-03-31": "(A, mos, lew) Första versionen."
...
Kmom02: Arv och komposition
==================================

[WARNING]
**Version 4 av oophp.**

En uppdaterad version av kursen är under bearbetning och kursen ges första gången vårterminen 2018.

[/WARNING]


<!--
Arv komposition, namespace
UML, modellering.
Autom dokumentation.

Koda i ramverket med routes och vyer.
-->

Vi fortsätter träna på programmering med klasser och objekt.

Kursmomentet har fokus på ett par friare programmeringsövningar så du kan träna på objektorienterade konstruktioner.

<!--
[FIGURE src=/image/oophp/v3/test-session.png?w=w3&q=70 caption="Sessionstest är en av övningarna som finns med i detta kursmoment."]

[FIGURE src=/image/oophp/v3/dice100.png?w=w3&q=70 caption="Tärningsspelet 100 är en av övningarna som finns med i detta kursmoment."]

[FIGURE src=/image/oophp/v3/calendar1.png?w=w3&q=70 caption="En månadskalender är en av övningarna som finns med i detta kursmoment."]
-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>


<!--stop-->



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar, inklusive extra läsning i referenslitteraturen efter eget val)*


<!--

###Kurslitteratur  {#kurslitteratur}

Det finns inga specifika läsanvisningar i kurslitteraturen.

Läs följande:

1\. [Beginning PHP and MySQL: From Novice to Professional](kunskap/boken-beginning-php-and-mysql-from-novice-to-professional)

* Chapter 6: Object-Oriented PHP
* Chapter 7: Advanced OOP Features
* Chapter 8: Error and Exception Handling
* Chapter 12: Date and Time (Läs så mycket så att du klarar uppgiften längre ned)
-->


###Artiklar {#artiklar}

Läs följande artiklar.

1. Gå tillbaka till manualen och bekanta dig återigen med PHP manualen och stycket om [Klasser och Objekt](http://php.net/manual/en/oop5.intro.php). Kika på de sakerna som behandlades i förra kursmomentet, som en repetition.

1. Bekanta dig kort med verktyget [phpDocumentor](https://www.phpdoc.org/) som kan automatgenerera dokumentation av din kod, genom att bland annat läsa informationen från dina docblock kommentarer. Läs översiktligt så att de är medveten om vad verktyget kan göra.

1. Kika snabbt och översiktligt igenom [referensen till PHPDoc](https://docs.phpdoc.org/references/phpdoc/), det ger dig en bas för information när du nu börjar skriva dina egna docblock kommentarer.



###Lästips {#lastips}

Kika igenom följande lästips och ägna tid åt dem om du finner det intressant.

1. [Dia](https://wiki.gnome.org/Apps/Dia/) är ett ritverktyg där du kan skapa UML-diagram. Du vill ha ett sådant, eller motsvarande, i din arsenal av verktyg.

1. Ett webbaserat verktyg för UML är [draw.io](draw.io). Det har stöd för både ER-variant och UML. Verktyget är webbaserat och går att integrera med Google Docs.

1. När man pratar om objektorienterad programmering så behöver man också ha en viss bas i objektorienterad modellering, det underlättar. Därför kan du läsa lite om UML, "Unified Modelling Language". En bra plats att starta är [Wikipedia om UML](http://en.wikipedia.org/wiki/Unified_Modeling_Language).



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*


<!--

###Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

-->



###Uppgifter {#uppgifter}

Gör följande uppgifter.

1. I guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)" jobbar du igenom följande del. Spara koden i `me/kmom02/oophp2`.
    * [Intro till guiden](guide/kom-igang-med-objektorienterad-programmering-i-php/intro-till-guiden)

1. Gör uppgiften "[Tärningsspelet 100](uppgift/tarningsspel)" som modul till ditt Anax och visa upp spelet i din me-sida. Spara din kod under `me/redovisa`.

1. Gör uppgiften "[Dokumentera PHP med phpdoc och phpDocumentor](uppgift/dokumentera-php-med-phpdoc-och-phpdocumentor)". Spara uppdateringarna du gör i ditt `me/redovisa`.

1. Pusha och tagga ditt `me/redovisa`, allt eftersom och sätt en avslutande tagg (3.0.\*) när du är klar med alla uppgifter i kursmomentet.


<!--
Inkludera kmom01 guess som en del i me-sidan.

Rita klass och sekvensdiagram? Som en del i uppgiften?

Yatsy?
21, blackjack
Kasta gris (100)

-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Hur känns det att skriva kod utanför och inuti ramverket, ser du fördelar och nackdelar med de olika sätten?
* Berätta om hur du löste uppgiften med Tärningsspelet 100, hur du tänkte, planerade och utförde uppgiften samt hur du organiserade din kod?
* Berätta om din syn på modellering likt UML jämfört med verktyg som phpDocumentor. Fördelar, nackdelar, användningsområde?
* Vilken är din TIL för detta kmom?

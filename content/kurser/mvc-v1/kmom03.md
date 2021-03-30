---
author:
    - mos
revision:
    "2021-03-22": "(PA1, mos) Arbete påbörjat."
...
Kmom03: Enhetstestning
==================================

[WARNING]

**Arbete pågår**

[/WARNING]

<!--stop-->

<!--
[INFO]

**Publicerat - men inte komplett**

Detta kmom är publicerat men ännu inte komplett. Om du är en "early user" med relativt höga förkunskaper kan du gärna pröva att genomföra kursmomentet. Annars bör du avvakta tills denna blå ruta försvinner.

[/INFO]
-->

Vi skall enhetstesta våra klasser.

<small><i>Detta är instruktionen för kursmomentet och omfattar cirka **20 studietimmar**. Fokus ligger på uppgifter som du skall lösa och redovisa. För att lösa uppgifterna behöver du normalt jobba igenom övningar och läsanvisningar för att skaffa dig rätt kunskap och förståelse av uppgiftens alla delar. Läs igenom hela kursmomentet innan du börjar jobba.</i></small>

<!-- more -->




<!-- stop-->



### Dokumentation och PHPDoc {#phpdoc}

Följande handlar om att automatgenerera dokumentation baserad på kommentarer i koden. Det är bakgrundsinformation till en av uppgifterna nedan.

1. I dokumentet [PHP The Right Way](http://www.phptherightway.com/), finns en sektion som berör dokumentering av koden.
    * [PHP The Right Way: Documenting your Code](https://phptherightway.com/#documenting)

1. Bekanta dig kort med verktyget [phpDocumentor](https://www.phpdoc.org/) som kan automatgenerera dokumentation av din kod, genom att bland annat läsa informationen från dina docblock kommentarer. Läs översiktligt så att de är medveten om vad verktyget kan göra.

1. Kika snabbt och översiktligt igenom [referensen till PHPDoc](https://docs.phpdoc.org/references/phpdoc/), det ger dig en bas för information om hur du skriver dina egna docblock kommentarer.





1. Gör uppgiften "[Dokumentera PHP med phpdoc och phpDocumentor](uppgift/dokumentera-php-med-phpdoc-och-phpdocumentor)". Spara uppdateringarna du gör i ditt `me/redovisa`.


* Berätta om din syn på modellering likt UML jämfört med verktyg som phpDocumentor. Fördelar, nackdelar, användningsområde? Vad tycker du om konceptet `make doc`?



Labbmiljö  {#labbmiljo}
---------------------------------

*(ca: 1-2 studietimmar)*

Installera följande som en del av din labbmiljö. Se till att du installerar PHPUnit version 6.0 eller högre, men välj en version som matchar din version av PHP.

1. Installera [PHPUnit](labbmiljo/phpunit) och [Xdebug](labbmiljo/xdebug) för att kunna köra enhetstester med kodtäckning på din lokala maskin.



Uppgifter & Övningar {#uppgifter_ovningar}
-------------------------------------------

*(ca: 8-12 studietimmar)*

Uppgifter skall utföras och redovisas, övningar är träning inför uppgifterna.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas.

1. Lös uppgiften "[Enhetstesta dina klasser med PHPUnit](uppgift/enhetstesta-dina-klasser-med-phpunit)".



### Övningar {#ovningar}

<!-- Det finns inga övningar i detta kursmoment. -->

Jobba igenom övningarna, de förbereder dig inför uppgifterna.

* Övning med PHPUnit i kursrepot.



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*

För att lösa uppgifterna och redovisningen bör du studera enligt följande.

<!--

### Föreläsning {#flas}

* Allmänt om testning.

* Enhetstestning.

* Enhetstestning i PHP.

1. [Kursintro](./../forelasning/kursintro) som ger en introduktion till kursens struktur och upplägg samt en översikt av kursens innehåll.

1. [Databasteknik, relationsdatabaser och SQL](./../forelasning/databasteknik-relationsdatabaser-och-sql) ger dig en introduktion till de databaser och SQL.

-->


### Litteratur  {#litteratur}

1. PHPUnit

1. Bekanta dig snabbt och översiktligt med innehållet i PHP-manualen och stycket om [Klasser och Objekt](https://www.php.net/manual/en/language.oop5.php). Referensmanualen vår källa till information, lär dig dess struktur så att du kan slå upp saker vid behov.

1. Titta i guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)" och se om den kan hjälpa dig med att förstå grunderna till klassbegreppeti PHP. Välj själv om du enbart använder guiden som läsresurs eller om du kodar dess övningsprogram.

    * [Intro till guiden](guide/kom-igang-med-objektorienterad-programmering-i-php/intro-till-guiden)
    * [Objekt och Klass](guide/kom-igang-med-objektorienterad-programmering-i-php/objekt-och-klass)

1. I dokumentet [PHP The Right Way](http://www.phptherightway.com/), läs igenom delen om Test.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa). Observera att denna kursen skiljer sig från hur du normalt sett lämnar in din redovisningstext.

Se till att följande frågor besvaras i texten i din rapport:

* Berätta kort om dina förkunskaper och tidigare erfarenheter kring objektorientering. Kanske har du redan nu en uppfattning om det är bra eller ej?

* Berätta kort om PHPs modell för klasser och objekt. Vilka är de grunder man behöver veta/förstå för att kunna komma igång och skapa sina första klasser?

* Reflektera kort över den kodbas som användes till uppgiften, hur uppfattar du den?

* Berätta om ditt spel från uppgiften. Hur löste du uppgiften, är du nöjd/missnöjd, vilken förbättringspotential ser du i koden/spelet, var uppgiften svårt/enkelt/utmanande, håller din kod god/hög kvalitet?

* Med tanke på artikeln "PHP The Right Way", vilka delar in den finner du extra intressanta och värdefulla? Är det några särskilda områden som du känner att du vill veta mer om?

* Vilken är din TIL för detta kmom?



Resurser bra-att-ha {#resurser}
---------------------------------

Här anges övriga resurser som kan användas för vidare studier i det som kursmomentet omfattar.



### ? {#mvc}

Git är ett versionshanteringssystem för kod och GitHub/GitLab är en webbplats där man kan ladda upp sitt Git-repo och använda extra tjänster.

Om Git.

* [Git documentation](https://git-scm.com/doc)


<!--stop-->



Kmom02: Arv och Komposition
==================================

Vi jobbar vidare med programmering av klasser och objekt. Vi tar fler grundkonstruktioner i objektorientering och PHP. Vi tittar på arv och komposition för att se hur klasser kan samverka och bygga på varandra. Vi använder namespace för att strukturera koden och vi använder en autoloader enligt PSR-4.

Vi ser hur ett klassdiagram kan ritas i UML, för att skissa på relationerna mellan klasserna. Vi ser också hur man kan bygga upp automatisk dokumentation från koden via docblock-kommentarer.

Vi börjar koda inuti ramverket och använder oss av konstruktioner som routes, vyer och placerar klasserna inuti ramverket med givna namespaces och använder oss av ramverkets autoloader. Som övning tar vi och flyttar vårt spel "Gissa mitt nummer" in i ramverket.

<!-- more -->

[FIGURE src=image/snapvt18/dice-graphic-css-sprite.png?w=w3 caption="Ett antal tärningar representerade med olika grafiska metoder."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 3-6 studietimmar)*



### Bok & Artiklar {#bok}

Läs följande för att skaffa dig bakgrundskunskap i PHP och objektorientering. Gör din egen läsplan så att du hinner läsa igenom dem innan kursen är slut, du behöver inte läsa allt i detta kmom.

1. Följande böcker nämndes i första kmomet, det finns dock inga specifika läsanvisningar till dem, således fri läsning efter behov och intresse.

    1. [Webbutveckling med PHP och MySQL](kunskap/boken-webbutveckling-med-php-och-mysql)
    1. [PHP Apprentice - An online book for learning PHP](https://phpapprentice.com/)

1. PHP-manualen är läsvärd och specifikt det stycket som handlar om "[Klasser och Objekt](http://php.net/manual/en/oop5.intro.php)". Försök läsa igenom hela stycket innan kursen är slut, det ger dig en god insyn i objektorienterad PHP.

1. Läs dokumentet [PHP The Right Way](http://www.phptherightway.com/), skrivet och underhållet av PHP communityn ger det dig en god översikt till de verktyg, processer och begrepp som är viktiga ur ett helhetsperspektiv.



### Namespace och autoloader {#namespace}

En viktig del i detta kmom är begreppen namespace och autoloader. Här är en samling av läsvärt material som ger dig grundkunskapen.

1. Läs igenom, men hoppa över detaljer, det stycke i PHP manualen som handlar om [begreppet namespace](http://php.net/manual/en/language.namespaces.php). Skaffa dig en översikt vad det handlar om och hur man definierar och använder namespace.

1. När det gäller namespace så använder vi oss av [PHP-FIG](https://www.php-fig.org/) och standarden [PSR-4: Autoloader](https://www.php-fig.org/psr/psr-4/).

1. Vi använder composers implementation av autoloadern, läs om [Autoloading i manualen för composer](https://getcomposer.org/doc/01-basic-usage.md#autoloading).



### Modellering och UML {#uml}

Kika igenom följande lästips om UML och modellering, ägna tid åt dem om du finner det intressant.

1. I kursen databas introducerades du till ritverktyg för ER-modellering, du kan använda samma verktyg till UML-modellering. Här är två verktyg att välja bland.
    * [Dia](https://wiki.gnome.org/Apps/Dia/) (desktop)
    * [draw.io](draw.io) (webbaserat)

1. När man pratar om objektorienterad programmering så underlättar det om man har en viss bas i objektorienterad modellering. Därför kan du läsa kort om UML, "Unified Modelling Language". En bra plats att starta är någon av följande:
    * Andreas artikel "[Vad är UML?](kunskap/vad-ar-uml)" som är en del av kursen oopython.
    * [Wikipedia om UML](http://en.wikipedia.org/wiki/Unified_Modeling_Language).



### Dokumentation och PHPDoc {#phpdoc}

Följande handlar om att automatgenerera dokumentation baserad på kommentarer i koden. Det är bakgrundsinformation till en av uppgifterna nedan.

1. I dokumentet [PHP The Right Way](http://www.phptherightway.com/), finns en sektion som berör dokumentering av koden.
    * [PHP The Right Way: Documenting your Code](https://phptherightway.com/#documenting)

1. Bekanta dig kort med verktyget [phpDocumentor](https://www.phpdoc.org/) som kan automatgenerera dokumentation av din kod, genom att bland annat läsa informationen från dina docblock kommentarer. Läs översiktligt så att de är medveten om vad verktyget kan göra.

1. Kika snabbt och översiktligt igenom [referensen till PHPDoc](https://docs.phpdoc.org/references/phpdoc/), det ger dig en bas för information om hur du skriver dina egna docblock kommentarer.



### Ramverk Anax {#anax}

Följande referenser är relevanta för ramverket Anax, studera dem snabbt, kort och översiktligt.

1. Följande Anax moduler är extra relevanta i detta kmom, läs deras README för en översyn av hur de fungerar.
    * [anax/request](https://github.com/canax/request)
    * [anax/response](https://github.com/canax/response)
    * [anax/router](https://github.com/canax/router)
    * [anax/view](https://github.com/canax/view)



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller genomgångar och föreläsningar som spelas in (streamas) och därefter läggs i en spellista. Du kan nå spellistan på "[oophp streams vt19](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-igucRSQ6tFYg9x8to5HiE)".

1. Uppgifter och övningar kan innehålla extra videomaterial i form av spellistor kopplade till respektive artikel. Ofta syns dessa videor i inledningen av artikeln.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 10-14 studietimmar)*


### Uppgifter {#uppgifter}

Gör följande uppgifter.

1. I guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)" jobbar du igenom följande del. Spara koden i `me/guide`.
    * [Arv och Komposition](guide/kom-igang-med-objektorienterad-programmering-i-php/arv-och-komposition)

1. Gör uppgiften "[Flytta spelet Gissa mitt nummer till me-sidan (v5)](uppgift/flytta-spelet-gissa-mitt-nummer-till-me-sidan-v5)". Du skall kopiera koden för ditt gissa-spel och integrera in det i din me-sida och använda ramverkets struktur. Koden sparar du i `me/redovisa`.

1. Gör uppgiften "[Dokumentera PHP med phpdoc och phpDocumentor](uppgift/dokumentera-php-med-phpdoc-och-phpdocumentor)". Spara uppdateringarna du gör i ditt `me/redovisa`.

1. Pusha och tagga ditt repo `me/redovisa` allt eftersom och sätt en avslutande tagg (2.0.\*) när du är klar med alla uppgifter och redovisningstext i kursmomentet. Gör även en avslutande `make test` som en sista avstämning, innan du sätter sista taggen.

<!--
Dice med kontroller.
-->




Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Berätta om din syn på modellering likt UML jämfört med verktyg som phpDocumentor. Fördelar, nackdelar, användningsområde? Vad tycker du om konceptet `make doc`?
* Hur gick det att överföra spelet "Gissa mitt nummer" in i din me-sida, hade du en bra grundstruktur du kunde behålla eller fick du skriva om mycket av koden?
* Hur känns det att skriva kod utanför och inuti ramverket, ser du fördelar och nackdelar med de olika sätten?
* Vilken är din TIL för detta kmom?




<!--stop-->

Kmom03: Enhetstestning
==================================

Vi jobbar vidare med klasser och objekt och denna gången tittar vi på hur klasser kan enhetstestas med verktyget PHPUnit. PHPUnit är ett av de verktyg som vanligen används inom PHP för att utföra enhetstestning av koden.

Vi har tidigare pratat om begreppet inkapsling och att klasserna skall erbjuda ett publikt API, ett gränssnitt för användaren av klassen. Samtidigt vill vi skydda den interna implementationen inuti klassen. Vi vill låta användaren av vår klass ha ett tydligt gränssnitt, men inuti klassen vill vi själva bestämma hur vi implementerar klassens detaljer, utan att påverka/påverkas av det publika gränssnittet.

Liknande begrepp använder vi i enhetstestning. Vi ser varje klass som en enhet som skall testas och vi testar klassen via dess publika gränssnitt vilket är de metoder vi når som användare av klassen, dess publika metoder. När vi testar så är vi fullt medvetna om hur klassen är uppbyggd. Vi kallar det för _white box testing_, vi har tillgång till klassens källkod när vi skriver testfallen och vi vet exakt den källkod vi skall testa. Målet är att testa alla varianter av användning mot klassen, även felfall.

<!-- more -->

[FIGURE src=image/snapvt18/phpunit-terminal.png?w=w3 caption="Enhetstestning med PHPUnit via en Makefile."]

[FIGURE src=image/snapvt18/code-coverage-overview.png?w=w3 caption="Kodtäckning vid enhetstestning, en översikt av enheterna (klasserna)."]

[FIGURE src=image/snapvt18/code-coverage-detail.png?w=w3 caption="Detaljerad kodtäckning rad för rad i en enhet (klass)."]

<!--st op-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljö {#labbmiljo}
---------------------------------

*(ca: 1-2 studietimmar)*

Installera följande som en del av din labbmiljö. Se till att du installerar PHPUnit version 6.0 eller högre, men välj en version som matchar din version av PHP.

1. Installera [PHPUnit](labbmiljo/phpunit) och [Xdebug](labbmiljo/xdebug) för att kunna köra enhetstester med kodtäckning på din lokala maskin.



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 3-6 studietimmar)*



### Artiklar {#artiklar}

Läs följande.

1. Låt oss se över vilka delar som vi hittills har gått igenom i PHP-manualen om "[Klasser och Objekt](http://php.net/manual/en/oop5.intro.php)". Kika så att du har hyffsad koll på dem. Gör en kort repetition, dessa omfattar den viktiga grunden av objektorienterade konstruktioner i PHP.
    * [Introduction](https://www.php.net/manual/en/oop5.intro.php)
    * [The basics](https://www.php.net/manual/en/language.oop5.basic.php)
    * [Properties](https://www.php.net/manual/en/language.oop5.properties.php)
    * [Class Constants](https://www.php.net/manual/en/language.oop5.constants.php)
    * [Autoloading classes](https://www.php.net/manual/en/language.oop5.autoload.php)
    * [Constructors and destructors](https://www.php.net/manual/en/language.oop5.decon.php)
    * [Visibility (public, protected, private)](https://www.php.net/manual/en/language.oop5.visibility.php)
    * [Object inheritance](https://www.php.net/manual/en/language.oop5.inheritance.php)
    * [Scope resolution operator (::)](https://www.php.net/manual/en/language.oop5.paamayim-nekudotayim.php)



### Enhetstestning {#test}

Läs följande.

1. Läs introduktionen till enhetstester och enhetstestning i artikeln "[Enhetstestningens roll i test av mjukvara](kunskap/enhetstestningens-roll-i-test-av-mjukvara)".

1. I dokumentet [PHP The Right Way](http://www.phptherightway.com/), finns en sektion som berör testning i PHP.
    * [PHP The Right Way: Testing](https://phptherightway.com/#testing)

1. Gå till hemsidan för [PHPUnit](https://phpunit.de/) och bekanta dig kort och översiktligt med verktyget PHPUnit. Se till att du kollar upp vilka versioner av verktyget som stödjer de olika versionerna av PHP.

1. Kika kort på [PHPUnit på GitHub](https://github.com/sebastianbergmann/phpunit), det är öppen källkod så kolla snabbt hur ett större projekt fungerar på GitHub. Kolla dess commit-historik, hur issues diskuteras, releashanteringen, pull requests och hur källkoden ser ut. Använder de phpdoc och docblock kommentarer?

1. Bekanta dig med [PHPUnits dokumentation](https://phpunit.readthedocs.io/). Kika över innehållsförteckningen och skumläs snabbt följande kapitel (för att bekanta dig med manualens struktur och innehåll. Du kommer behöva gå tillbaka till manualen, senare när du skriver dina testprogram.
    * 2. Writing Tests for PHPUnit
    * 3. The Command-Line Test Runner
    * 4. Fixtures
    * 5. Organizing Tests
    * 9. Code Coverage Analysis
    * Appendix 1. Assertions

1. Bekanta dig kort och översiktligt med [Xdebug för PHP](https://xdebug.org/) och kika snabbt över vilken dokumentation som finns. Se vilka funktioner Xdebug kan tillföra till din utvecklingsmiljö. Vi kommer enbart använda Xdebug tillsammans med PHPUnit för att generera rapporter över kodtäckning.

1. För att läsa mer generellt om testning så är [Wikipedia Software Testing](https://en.wikipedia.org/wiki/Software_testing) en bra utgångspunkt. Kika där och läs mer om du har tid och intresse.



### Ramverk Anax {#anax}

Modulerna i ramverket Anax omfattas av enhetstestning i olika omfattning. Här kan du se de moduler du tidigare använt tillsammans med en _badge_ som berättar hur mycket av modulens kod som är täckt av ett eller flera enhetstester.

1. Ett par Anax moduler och omfattningen av enhetstester (kodtäckning) för respektive modul.
    * [![Code Coverage](https://scrutinizer-ci.com/g/canax/request/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/canax/request/?branch=master) [anax/request](https://github.com/canax/request)
    * [![Code Coverage](https://scrutinizer-ci.com/g/canax/response/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/canax/response/?branch=master) [anax/response](https://github.com/canax/response)
    * [![Code Coverage](https://scrutinizer-ci.com/g/canax/router/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/canax/router/?branch=master) [anax/router](https://github.com/canax/router)
    * [![Code Coverage](https://scrutinizer-ci.com/g/canax/session/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/canax/session/?branch=master) [anax/session](https://github.com/canax/session)
    * [![Code Coverage](https://scrutinizer-ci.com/g/canax/view/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/canax/view/?branch=master) [anax/view](https://github.com/canax/view)

Klickar du på "kodtäckningsbadgen" så kommer du till Scrutinizer som är ett automatiserat byggverktyg som checkar ut och utför enhetstesterna för modulen, varje gång som modulen uppdateras på GitHub.

Varje Anax modul har en katalog `test/` där alla enhetstester är samlade. **Välj ut en av modulerna och inspektera de filerna som ligger i dess test-katalog**. Du kommer snart att bygga en liknande struktur i din me-sida för att testa dina egna klasser.



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller genomgångar och föreläsningar som spelas in (streamas) och därefter läggs i en spellista. Du kan nå spellistan på "[oophp streams vt19](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-igucRSQ6tFYg9x8to5HiE)".

1. Uppgifter och övningar kan innehålla extra videomaterial i form av spellistor kopplade till respektive artikel. Ofta syns dessa videor i inledningen av artikeln.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 6-10 studietimmar)*



### Uppgifter {#uppgifter}

Gör följande uppgifter.

1. Lös uppgiften "[Kom igång med PHPUnit](uppgift/kom-igang-med-phpunit)" som guidar dig igenom de första stapplande stegen i enhetstestning. Spara all kod i `me/kmom03/phpunit`.

1. Gör uppgiften "[Tärningsspel 100](uppgift/tarningsspel-100)" inuti din me-sida. Spara din kod under `me/redovisa`.

1. Pusha och tagga ditt repo `me/redovisa` allt eftersom och sätt en avslutande tagg (3.0.\*) när du är klar med alla uppgifter och redovisningstext i kursmomentet. Gör även en avslutande `make test` som en sista avstämning, innan du sätter sista taggen.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Har du tidigare erfarenheter av att skriva kod som testar annan kod?
* Hur ser du på begreppen enhetstestning och "att skriva testbar kod"?
* Förklara kort begreppen white/grey/black box testing samt positiva och negativa tester, med dina egna ord.
* Berätta om hur du löste uppgiften med Tärningsspelet 100, hur du tänkte, planerade och utförde uppgiften samt hur du organiserade din kod?
* Hur väl lyckades du testa tärningsspelet 100?
* Vilken är din TIL för detta kmom?

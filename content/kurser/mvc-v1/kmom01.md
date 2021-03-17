---
author:
    - mos
revision:
    "2021-03-12": "(PA1, mos) Arbete påbörjat."
...
Kmom01: Objektorientering
==================================

[WARNING]

**Arbete pågår**

[/WARNING]

Vi skall lära oss programmera webbapplikationer på ett objektorienterat sätt med fokus på det arkitekturella designmönstret MVC.

I kurserna htmlphp och design använde vi oss av begreppet vyer, det är V:et i MVC. Det är något vi fortsätter använda i detta kursmomentet.

I nästa kursmoment skall vi introducera C:et i MVC, Controller. Men för att lära oss bygga Controllers så behöver vi någorlunda koll på hur klasser och objektorienterad programmering fungerar i PHP. Det får alltså bli huvudsyftet för detta inledande kursmoment.

Vi prövar därför att komma igång med grunderna i objektorienterad programmering i PHP genom att bygga ett antal enklare klasser som vi använder visar upp via ett par webbsidor.

Vi får även möjlighet att repetera begrepp som GET, POST och SESSION som är bra att ha koll på när vi bygger webbapplikationer.

<small><i>Detta är instruktionen för kursmomentet och omfattar cirka **20 studietimmar**. Fokus ligger på uppgifter som du skall lösa och redovisa. För att lösa uppgifterna behöver du normalt jobba igenom övningar och läsanvisningar för att skaffa dig rätt kunskap och förståelse av uppgiftens alla delar. Läs igenom hela kursmomentet innan du börjar jobba.</i></small>

<!-- more -->



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Se till att du har kursens labbmiljö installerad.

1. En [översikt av labbmiljön som krävs för att genomföra första kursmomentet](./../installera-labbmiljo).



<!--stop-->



Uppgifter {#uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*

Följande uppgifter skall utföras och resultatet skall redovisas.

1. I guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)" jobbar du igenom följande delar. Spara koden i `me/guide`.
    * [Intro till guiden](guide/kom-igang-med-objektorienterad-programmering-i-php/intro-till-guiden)
    * [Objekt och Klass](guide/kom-igang-med-objektorienterad-programmering-i-php/objekt-och-klass)

1. Gör uppgiften "[Gissa numret med PHP](uppgift/gissa-numret-med-php)". Uppgiften låter dig värma upp din gamla PHP-kunskaper och samtidigt träna på grunderna med objekt och klasser. Spara din kod i `me/kmom01/guess`.

1. Gör uppgiften "[Bygg en me-sida för oophp med Anax](uppgift/bygg-en-me-sida-for-oophp-med-anax)". Du skall bygga en me-sida som du taggar och publicerar på GitHub. Spara allt under `me/redovisa`.

1. Försäkra dig om att du har gjort `dbwebb publish redovisa` och taggat din inlämning med version 1.0.0 (eller högre) samt pushat repot inklusive taggarna till GitHub.



Övningar  {#ovningar}
-------------------------------------------

*(ca: 0-4 studietimmar)*

Det finns inga övningar i detta kursmoment.



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

1. Bekanta dig snabbt och översiktligt med innehållet i PHP-manualen och stycket om [Klasser och Objekt](https://www.php.net/manual/en/language.oop5.php). Som vanligt är referensmanualen vår källa till information, så bli kompis med dess struktur och lär dig vilken typ av information du där kan hitta. Vill du lära dig mycket om det som kursen handlar om så är detta stycket i manualen ytterst lämpligt att läsa igenom som helhet.

1. Bekanta dig översiktligt med dokumentet [PHP The Right Way](http://www.phptherightway.com/). Det är skrivet av PHP communityn och ger en översikt över PHP som språk och de verktyg och processer man normalt arbetar med. Vi kommer att återkomma till dokumentet under kursens gång. Du kan se dokumentet som en innehållsförteckning till vad en god PHP-programmerare bör ha koll på.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa). Observera att denna kursen skiljer sig från hur du normalt sett lämnar in din redovisningstext.

Se till att följande frågor besvaras i texten:

* Har du tidigare kunskaper (eller förutfattade meningar) i objektorienterad programmering i PHP eller något annat språk?
* Hur gick det att komma in i PHP och programmering med objekt och klasser?
* Hur det gick det att utföra uppgiften "Gissa numret"?
* Vilken taktik valde du för att lagra spelet i sessionen?
* Gick det bra att komma igång med Git och GitHub, du gjorde ungefär samma i design-kursen?
* Har du några inledande reflektioner kring me-sidan och dess struktur, känner du igen dig från design-kursen?
* Vilken är din TIL för detta kmom?

TIL är en akronym för "Today I Learned" vilket leksamt anspelar på att det finns alltid nya saker att lära sig, varje dag. Man brukar lyfta upp saker man lärt sig och där man kanske hajade till lite extra över dess nyttighet eller enkelhet, eller så var det bara en ny lärdom för dagen som man vill notera.



Resurser  {#resurser}
---------------------------------

*(ca: 1-2 studietimmar)*

Här anges övriga resurser som kan användas för vidare studier i det som kursmomentet omfattar.



### Videor och spellista {#playlist}

Kursen innehåller genomgångar och föreläsningar som spelas in eller streamas och därefter läggs i en spellista. Du kan nå spellistan på "[mvc streams v21](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_cbYbdnzKKF8-4igef73u6)".



### Git & GitHub {#git}

Git är ett versionshanteringssystem för kod och GitHub/GitLab är en webbplats där man kan ladda upp sitt Git-repo och använda extra tjänster.

* [Git documentation](https://git-scm.com/doc)
* [GitHub](https://github.com/)
* [GitHub Docs](https://docs.github.com/en)
* [GitLab](https://gitlab.com/)
* [GitLab Docs](https://docs.gitlab.com/)



### Kodstandard {#kodstandard}

Följande gäller för kodstandard och valideringsverktyg.

1. Vi skriver PHP enligt kodstandarden [PSR-1: Basic Coding Standard](http://www.php-fig.org/psr/psr-1/) och [PSR-2: Coding Style Guide](http://www.php-fig.org/psr/psr-2/). Dessa är standardiserade av PHP communityn och standardiseringen hanteras av organisationen [PHP-FIG](https://www.php-fig.org/) vars syfte är att standardisera komponenter så att de går att använda mellan olika ramverk.  
_PSR-2 är på väg att ersättas av [PSR-12: Extended Coding Style](https://www.php-fig.org/psr/psr-12/), så även den delen kan vara av intresse att studera._



### Linter och validatorer {#validering}

1. Vi använder valideringsverktygen [phpcs](https://github.com/squizlabs/PHP_CodeSniffer/wiki) och [phpmd](https://phpmd.org/). Det går att installera dem som linters i Atom och se valideringsfelen direkt i texteditorn.

<!-- phpstan? -->

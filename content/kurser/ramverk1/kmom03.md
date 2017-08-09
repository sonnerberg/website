---
author:
    - mos
revision:
    "2017-03-24": "(PA1, mos) Jobbet börjar."
...
Kmom03: DI
==================================

[WARNING]
**Version 1 av ramverk1.**

Utveckling av nytt kursmoment. Kursmomentet släpps hösten 2017.

[/WARNING]

Vi skall titta på tekniker som kan sammafattas med Dependency Injection (DI). Dessa tekniker används för att skapa en grundläggande struktur i ramverket avseende hur man lägger till "tjänster" och moduler in i ramverket. Hittills har vi använt `$app` som en kontainer för alla tjänster som finns i ramverket.

Vi skall se om det finns alternativa lösningar på detta. Vi vill ha en flexibilitet när vi utökar ramverket och lägger till nya moduler. Hittills har vi gjort detta i frontkontrollern `index.php`/`config/service.php` men kanske kan vi finna ett alternativt sätt som är bättre när antalet moduler växer.

Vi skall titta på begreppet Dependency Injection och några begrepp som är närliggande, nämligen service locator och lazy loading. Det handlar om designmönster och vanliga sätt att strukturera sin kod enligt det som betraktas som god programmeringssed.

När vi lärt oss grunden i begreppen så använder vi dem för att bygga vår kod. Samtidigt funderar vi på om det är en god kodstruktur vi uppnår, vi vill ha ett modulärt system och vi vill helst att varje modul skall vara oberoende av de andra, eller beroende av så få som möjligt och dess beroenden skall _injectas_ in i respektive modul.

<!--more-->



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-8 studietimmar)*



###Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Artikeln PHP The Right Way innehåller ett stycke om "[Dependency Injection](http://www.phptherightway.com/#dependency_injection)", läs igenom det som en introduktion till begreppet.

1. Bekanta dig med begreppet Dependecy Injection (DI) genom att översiktligt titta på [Wikipedia om DI](https://en.wikipedia.org/wiki/Dependency_injection).

1. Bekanta dig med begreppet Service Locator genom att översiktligt titta på [Wikipedia om Service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern).

1. Bekanta dig med begreppet Lazy Loading genom att översiktligt titta på [Wikipedia om Lazy loading](https://en.wikipedia.org/wiki/Lazy_loading).



###Videor {#videor}

Kika på följande videos.

1. Titta på en [kort kort intro till Dependency Injection](https://www.youtube.com/watch?v=IKD2-MAkXyQ) med Anthony Ferrara. Vdeo ger en mycket bra introduktion till begreppet.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 6-10 studietimmar)*



###Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

1. Jobba igenom artikeln "[Anax med dependency injection](kunskap/anax-med-dependency-injection)" som visar dig hur du använder begreppet DI i Anax. Du sparar koden i `me/anax` och integrerar den i din me-sida.



###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Gör uppgiften "[Kommentarssystem med användare](uppgift/kommentarssystem-med-anvandare)". Bygg vidare på ditt kommentarssystem och se till att integrera med användare. Spara koden under `me/anax`.

1. Skriv gruppvis en artikel om ["Dependency Injection (DI)"](uppgift/skriv-artikel-om-di). Spara artikeln i din me-sida.

1. Pusha och tagga ditt Anax, allt eftersom och sätt en avslutande tagg (3.0.\*) när du är klar med alla uppgifter i kursmomentet.




Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Hur känns det att jobba med begreppen dependency injection, service locator och lazy loading?
* Använde du begreppen när du vidareutvecklade ditt kommentarssystem?

Har du frågor eller funderingar så ställer du dem i forumet.

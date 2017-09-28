---
author:
    - mos
revision:
    "2017-03-24": "(PA1, mos) Jobbet börjar."
...
Kmom06: CI
==================================

[WARNING]
**Version 1 av ramverk1.**

Utveckling av nytt kursmoment. Kursmomentet släpps hösten 2017.

[/WARNING]

Automatiserad testning, regressionstest och CI.

Publicera modulen på packagist och testa på travis (och circleci, sensiolabs insights), scrutinizer.


<!--stop-->

Modul med rem eller som content?



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*



###Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Bekanta dig med begreppet TDD och Behaviour driven testing genom att översiktligt titta på Wikipedias information.

1. Bekanta dig med begreppet automatiserad testning och regression testing genom att översiktligt titta på Wikipedias information.

1. Begreppet CI.

1. Artikeln PHP The Right Way innehåller ett kort stycke om "[Testing](http://www.phptherightway.com/#testing)", läs igenom det som en introduktion.


###Videor {#videor}

Kika på följande videor.

1. Titta på [kursens spellista](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-IxTc7j499fXMJ9tMOpTHH) och de videor som börjar med 6, de är kopplade till detta kursmoment.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-16 studietimmar)*



###Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

1. Jobba igenom artikeln "[Integrera din packagist modul med verktyg för autmatisk test och validering](integrera-din-packagist-modul-med-verktyg-for-automatisk-test-och-validering)" som visar dig hur du använder använder `make test` för att bygga grunden till automatiserade tester och ett CI-flöde. Du kan jobba mot din egna modul för kommentarshanteringen och spara koden i `me/comment`.

1. Artikel om BDD.



###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Bygg vidare på en kommentarsmodul i ditt Anax och se till att den är integrerad mot Travis, CircleCI, Scrutinizer, Sensiolabs och Gitter. Bygg ut din testbas med fler enhetstester. Överväg att göra så att phpcs och/eller phpmd påverkar om tester misslyckas eller ej.

1. Utöka testbasen, inklusiva BDD.

1. Generera dokumentation för modulen med phpdoc.

1. Pusha och tagga ditt Anax, allt eftersom och sätt en avslutande tagg (6.0.\*) när du är klar med alla uppgifter i kursmomentet.

<!--
1. Skriv gruppvis en artikel om ["Continous Integration (CI)"](uppgift/skriv-artikel-om-ci). Spara artikeln i din me-sida.
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 2-4 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Berätta hur det gick att integrera mot de olika tjänsterna?
* Vilken extern tjänst uppskattade du mest, eller har du förslag på ytterligare externa tjänster att använda?

Har du frågor eller funderingar så ställer du dem i forumet.

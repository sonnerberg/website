---
author:
    - mos
revision:
    "2017-03-24": "(PA1, mos) Jobbet börjar."
...
Kmom04: Databasdrivna modeller
==================================

[WARNING]
**Version 1 av ramverk1.**

Utveckling av nytt kursmoment. Kursmomentet släpps hösten 2017.

[/WARNING]

Vi skall titta på klasser i modell-lagret och utöka vår struktur med formulärhantering och databasdrivna modell-klasser.

Vi skall använda en extern modul för HTML-formulär och vi skall använda en extern modul för databashanteringen.

I arbetet skapar vi basklasser i modellagret som underlättar då vi implementerar applikationsspecifik kod. Vi kan se det som vi bygger upp modellklasser som kan scaffoldas fram, en form av återanvändning och ett försök att effektivisera vårt kodande.

I slutet tar vi våra nya kunskaper och integrerar i vår befintliga kod, ytterligare en möjlighet till refactoring.

<!--stop-->



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*



###Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Bekanta dig med begreppet [Active record](https://en.wikipedia.org/wiki/Active_record_pattern) genom att översiktligt titta på Wikipedias information. Se referenserna till implementationer i PHP och välj ut några av dem och titta översiktligt på dem. Du vill skaffa dig en känsla för hur olika ramverk jobbar mot databaser.

1. Bekanta dig översiktligt med begreppet "[Object-relational mapping](https://en.wikipedia.org/wiki/Object-relational_mapping)" via Wikipedia. 

1. Artikeln PHP The Right Way innehåller ett kort stycke om "[Abstraction Layers (Databases)](http://www.phptherightway.com/#databases_abstraction_layers)", läs igenom det som en introduktion och kika på de länkar som leder till olika ramverks implementationer av databas-moduler.

1. Utifrån artiklarna så väljer du att översiktligt studera någon implementation av PHP ORM eller PHP Active Record. Du har nytta av det inför skrivövningen.



###Videor {#videor}

Det finns inga video.

<!--
Kika på följande videos.

1. Titta på seminariet?
-->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-16 studietimmar)*



###Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

1. Jobba igenom artikeln "[Anax och formulärhantering](kunskap/anax-och-formularhantering)" som visar hur du använder en extern modul för formulärhatering och hur du integrerar den i Anax. Du sparar koden i `me/kmom04/anax4`.

1. Jobba igenom artikeln "[Anax och formulärhantering](kunskap/kunskap/anax-och-databasdrivna-modeller)" som visar hur du använder en extern modul för databashantering och hur du integrerar den i Anax. Du sparar koden i `me/kmom04/anax4`.



###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Bygg vidare på en kommentarsmodul i ditt Anax. Använd databasdrivna modeller och formulärhantering enligt ovan övningar.

1. Skriv gruppvis en artikel om ["Active record"](uppgift/skriv-artikel-om-active-record) (eller ORM, bra eller dåligt). Spara artikeln i din me-sida.

1. Pusha och tagga ditt Anax, allt eftersom och sätt en avslutande tagg (4.0.\*) när du är klar med alla uppgifter i kursmomentet.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* HUr gick det att integrera formulärhantering och databashantering i ditt kommentarssystem?
* ORM, Active Record PHP implementation.

Har du frågor eller funderingar så ställer du dem i forumet.

---
author:
    - mos
revision:
    "2018-12-04": "(PA1, mos) Arbetskopia."
...
Kmom06: Säkerhetstestning
==================================

[WARNING]

**Kursutveckling pågår**

Kursen planeras ge hösten 2019.

[/WARNING]

Säkerhetstestning (test-driven security)

* koppla till OWASP, t.ex. Web Application Security Testing Cheat Sheet
* incident response management

<!--stop-->


Vi skall titta på klasser i modell-lagret och utöka vår struktur med formulärhantering och databasdrivna modell-klasser.

Vi skall använda en extern modul för HTML-formulär och vi skall använda en extern modul för databashanteringen.

I arbetet skapar vi basklasser i modellagret som underlättar då vi implementerar applikationsspecifik kod. Vi kan se det som vi bygger upp modellklasser som kan scaffoldas fram, en form av återanvändning och ett försök att effektivisera vårt kodande.

I slutet tar vi våra nya kunskaper och integrerar i vår befintliga kod, ytterligare en möjlighet till refactoring.

I vårt arbete kommer vi i kontakt med designmönstret Active Record och en implementation av databasen, en _query builder_ som erbjuder metoder för att producera SQL-koden.

<!--more-->

[FIGURE src=image/snapht17/create-user-4.png?w=w2 caption="Förbereder mig att skapa en ny användare."]

[FIGURE src=image/snapht17/login-user-1.png?w=w2 caption="Första försöket, redo att logga in med rätt akronym och rätt lösenord."]

[FIGURE src=image/snapht17/book-all.png?w=w2 caption="En lista av böcker i ett exempel med CRUD."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar)*



### Artiklar {#artiklar}

Kika igenom följande artiklar.

1. Bekanta dig med begreppet [Active record](https://en.wikipedia.org/wiki/Active_record_pattern) genom att översiktligt titta på Wikipedias information. Se referenserna till implementationer i PHP och välj ut några av dem och titta översiktligt på dem. Du vill skaffa dig en känsla för hur olika ramverk jobbar mot databaser.

1. Bekanta dig översiktligt med begreppet "[Object-relational mapping](https://en.wikipedia.org/wiki/Object-relational_mapping)" via Wikipedia. 

1. Artikeln PHP The Right Way innehåller ett kort stycke om "[Abstraction Layers (Databases)](http://www.phptherightway.com/#databases_abstraction_layers)", läs igenom det som en introduktion och kika på de länkar som leder till olika ramverks implementationer av databas-moduler.

<!--
1. Utifrån artiklarna så väljer du att översiktligt studera någon implementation av PHP ORM eller PHP Active Record. Du har nytta av det inför skrivövningen.
-->



### Videor {#videor}

Kika på följande videor.

1. Jag försökte finna en video som visade innebörden av Active Record och fann "[Easy PHP Database Handling With PHP ActiveRecord](https://www.youtube.com/watch?v=9Oau7fLiq7Y)", kika på den som ett komplement till artiklarna nedan.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-16 studietimmar)*



### Övningar {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna.

1. Jobba igenom artikeln "[Anax och formulärhantering](kunskap/anax-och-formularhantering)" som visar hur du använder en extern modul för formulärhatering och hur du integrerar den i Anax. Du sparar koden i `me/kmom04/anax4`.

1. Jobba igenom artikeln "[Anax och databasdrivna modeller](kunskap/anax-och-databasdrivna-modeller)" som visar hur du använder en extern modul för databashantering och hur du integrerar den i Anax samt hur du kan jobba med den tillsammans med formulär. Du sparar koden i `me/kmom04/anax4`.

1. Fortsätt fördjupa dig i databasdrivna modeller med ett exempel genom att jobba igenom artikeln "[Anax med databasdrivna modeller enligt Active Record, ett exempel](kunskap/anax-med-databasdrivna-modeller-enligt-active-record-ett-exempel)". Då får se hur koden hänger samman i ett CRUD-exempel som använder den databasdrivna modellen tillsammans med designmönstret Active Record. Du sparar koden i `me/kmom04/anax4`.



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Se över grunden till din me-sida och överväg om något av de nya begreppen bör introduceras i din generella me-sida. Eventuella ändringar gör du under `me/anax`.

1. Gör uppgiften "[Integrera Bok-exemplet i din me-sida](uppgift/integrera-bok-exempel-i-din-me-sida)". Ändringar gör du under `me/anax`.

1. Gör uppgiften "[Kommentarssystem med användare](uppgift/kommentarssystem-med-anvandare)". Bygg vidare på ditt kommentarssystem och se till att integrera med användare. Spara koden under `me/anax`.

1. Pusha och tagga din redovisa, allt eftersom och sätt en avslutande tagg (6.0.\*) när du är klar med kursmomentet.

<!--
1. Skriv gruppvis en artikel om ["Active record"](uppgift/skriv-artikel-om-active-record) (eller ORM, bra eller dåligt). Spara artikeln i din me-sida.
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 2-4 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Lägg extra tid på skrivandet i momentet då redovisningstexten är aningen mer omfattande än normalt.

* Hur gick det att integrera formulärhantering och databashantering i ditt kommentarssystem?
* Berätta om din syn på Active record och liknande upplägg, ser du fördelar och nackdelar?
* Utveckla din syn på koden du nu har i ramverket och din kommentars- och användarkod. Hur känns det?
* Om du vill, och har kunskap om, kan du även berätta om din syn på ORM och designmönstret Data Mapper som är närbesläktade med Active Record. Du kanske har erfarenhet av likande upplägg i andra sammanhang?
* Vad tror du om begreppet scaffolding, kan det vara något att kika mer på?
* Vilken är din TIL för detta kmom?

Har du frågor eller funderingar som du vill ha besvarade så ställer du dem i forumet.

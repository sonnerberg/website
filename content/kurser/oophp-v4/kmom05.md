---
author:
    - mos
category:
    - kurs oophp-v3
    - kurs oophp
revision:
    "2018-02-26": "(PB1, mos) Arbetsmaterial oophp v4."
    "2017-04-21": "(A, mos) Släppt i första utgåvan."
...
Kmom05: Enhetstestning
==================================

[WARNING]
**Version 4 av oophp.**

En uppdaterad version av kursen är under bearbetning och kursen ges första gången vårterminen 2018.

[/WARNING]

När det gäller enhetstestning så jobbar vi med PHPUnit och vi försöker hitta klasser som är testbara och vi ser hur bra vi lyckas uppnå kodtäckning.

<!--
-->

<!--
Introducera enhetstester (om det inte gjorts tidigare).
Uppgift, skriv enhetstester mot en klass.

Introducera backenden till eshopen?

Kundvagn
Enhetstesta kundvagn

Inloggning
Enhetstesta inloggning

Guide abstract methods, classes, final interface, trait

Du bekantar dig med begrepp som interface och traits.
Inloggning till webbplats?
Embryo till eshop sql?

Om testning?
Funktionstestning?
Enklare sådan, typ curl?

mockup
prepare testcase, prepare testclass, make mockobject.

Test a trait, interface, abstract class?
Enklare funktionstester.

Visa hur markdown formattering, bbcode.
anax/textfilter


INtro designpatterns? Ne, ramverk1
-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>


<!--stop-->




Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 0-6 studietimmar, inklusive extra läsning i referenslitteraturen efter eget val)*



###Kurslitteratur  {#kurslitteratur}

Det finns inga specifika läsanvisningar till detta kursmomentet.



###Artiklar {#artiklar}

Det finns inga artiklar.



###Lästips {#lastips}

Kika gärna på följande lästips.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-18 studietimmar)*


###Övningar {#ovningar}

Gör följande övning, den förbereder dig inför uppgifterna.




###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Pusha och tagga ditt Anax Lite, allt eftersom och sätt en avslutande tagg (5.0.\*) när du är klar med alla uppgifter i kursmomentet.

<!--
1. Gör uppgift "[Skapa backend till en webbshop](uppgift/skapa-backend-till-en-webbshop)". Spara koden i ditt `me/anax-lite`.

1. Gör uppgiften "[Dokumentera PHP med phpdoc och phpDocumentor](uppgift/dokumentera-php-med-phpdoc-och-phpdocumentor)". Spara uppdateringarna du gör i ditt `me/anax-lite`.

1. Gör uppgiften "[Dokumentera din ER-modell med Reverse Engineering](uppgift/dokumentera-din-er-modell-med-reverse-engineering)". Spara resultatet i `me/kmom05/er2`. Det är samma sak som du gjorde i förra kmomentent.

-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Några reflektioner kring din kod för backenden till webbshopen?
* Något du vill säga om koden generellt i och kring Anax Lite?
* Vilken är din TIL för detta kmom?





Kmom03: PHP PDO och MySQL
==================================

Detta kursmoment fokuserar på PHP PDO och databasen MySQL. Du får en inledande artikel som visar hur det fungerar och därefter får du på egen hand koda motsvarande funktionalitet in i ramverket Anax lite.

Det blir fokus på hur man löser inloggning, konton och administration av dessa. Det blir en hel del formulär, routes och kopplingar mot databasen. Vill man förenkla så handlar det om att lösa CRUD (Create, Read, Update, Read) för en webbapplikation mot en databas.

Dessutom blir övningar i hur man kan lösa såna här saker med hjälp av gränssnitt i sin webbplats. Här kan man behöva tänka till hur man vill att det skall se ut för slutanvändaren och de valen kan påverka vilken kod man behöver bygga för att implementera gränssnitten.

Du får träna PDO och MySQL genom att studera hur en filmdatabas kan byggas upp.

[FIGURE src=image/snapvt17/movie-paginate-sort.png?w=w2 caption="Din egen sökbara filmdatabas kan bli ett resultat av detta kursmoment."]

Du får grunden i hur inloggning fungerar och hur man hanterar och skyddar användarens lösenord.

[FIGURE src=image/oophp/v3/login-top.png?w=w2 caption="En enklare inloggningsruta som döljer en del databaskod."]

Sedan lägger du in allt i ditt Anax Lite och kanske väljer du att snygga till det också.

[FIGURE src=image/oophp/v3/loginexercise.png?w=w2&a=0,29,5,25 caption="En snyggare ruta för att registrera ett konto, bakom döljer sig databaskod."]

<!--
Använd anax/database som wrapper, visa hur den används via coachen.

Login som mindre exempel? Hur kryptera lösenordet?
Eshop som/med användaredelen.
-->


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>




Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 1-2 studietimmar, inklusive extra läsning i referenslitteraturen efter eget val)*



###Lästips {#lastips}

Studera följande lästips.

* I övningen får du jobba med PHP PDO så bekanta dig gärna med [PHP PDO i PHP manualen](http://php.net/manual/en/book.pdo.php). Studera vilka metoder som erbjuds av klasserna PDO och PDOStatement samt kika kort på vilka PDO drivers som finns till olika databaser. 



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 14-18 studietimmar)*


###Övningar {#ovningar}

Gör följande övningar, de förbereder dig inför uppgifterna.

1. Jobba igenom guiden "[Kom igång med PHP PDO och MySQL (v2)](kunskap/kom-igang-med-php-pdo-och-mysql-v2)". Spara eventuella exempelprogram i `me/kmom03/pdo`.

<!--
1. Jobba igenom artikeln "[Logga in med sessioner och cookies](kunskap/sessioner-cookies-login)". Spara eventuella exempelprogram i `me/kmom03/login`. Ett bra tips är att göra ditt egna lilla testprogram för att kolla hur inloggningen kan/skall fungera.
-->



###Uppgifter {#uppgifter}

Gör följande uppgifter.

1. Pusha och tagga ditt Anax Lite, allt eftersom och sätt en avslutande tagg (3.0.\*) när du är klar med alla uppgifter i kursmomentet.

<!--
Visa filmer via annan vy än bara tabell.

1. Gör uppgiften "[Inloggning till Anax Lite](uppgift/inloggning-till-anax-lite)". Spara dina filer under `me/anax-lite`.

1. Gör uppgiften ["Admin gränssnitt för hantering av användare och konton"](uppgift/admin-granssnitt-for-hantering-av-anvandare-och-konton). Dina filer skall sparas under `me/anax-lite`.
-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Hur kändes det att jobba med PHP PDO, SQL och MySQL?
* Reflektera kring koden du skrev för att lösa uppgifterna, klasser, formulär, integration Anax Lite?
* Känner du dig hemma i ramverket, dess komponenter och struktur?
* Hur bedömmer du svårighetsgraden på kursens inledande kursmoment, känner du att du lär dig något/bra saker?
* Vilken är din TIL för detta kmom?

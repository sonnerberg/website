---
author:
    - mos
category:
    - kurs oophp
    - kurs oophp-v3
revision:
    "2018-02-26": "(PB1, mos) Arbetsmaterial oophp v4."
    "2017-04-18": "(A, mos) Första utgåvan."
...
Kmom04: Lagra innehåll i databasen <!-- 03 PHP PDO och MySQL -->
==================================

[WARNING]
**Version 4 av oophp.**

En uppdaterad version av kursen är under bearbetning och kursen ges första gången vårterminen 2018.

[/WARNING]

<!--
Du bekantar dig med begrepp som interface och traits.
Inloggning till webbplats?
Embryo till eshop sql?

Om testning?
Funktionstestning?
Enklare sådan, typ curl?
Testa mot 100-spelet, inuti ramverket.
mockup
prepare testcase, prepare testclass, make mockobject.
Test a trait, interface, abstract class?
Enklare funktionstester.


Gör även enhetstestning på tärningsspelet?

Integrera "Gissa mitt nummer" med ramverkets klasser".
    * redirect
    * egen Game-klass
    * ej direkt access till GET, POST, SESSION

Låt stud integrera sitt eget spel med ramverkets klasser.

Inför enhetstestning, visa genom spelet "Gissa mitt nummer" och låt studenten skapa enhetstester till sitt egna spel.

Guide abstract methods, classes, final interface, trait

-->



Att lagra innehåll i databasen för att sedan kunna visa upp det i webbplatsen är en kärnfunktionalitet i många webbplatser. Så här långt har vi en fungerande webbplats om använder sig av databas och objektorienterad programmering. Vi fortsätter att använda de teknikerna för att bygga grunden i en databasdriven webbplats där innehåll lagras i databasen och kan redigeras av användaren (CRUD). Vi skall sedan visa upp innehållet som vanliga sidor i webbplatsen samt en blogg.

Utmaningen är att hitta en bra lagringsstruktur i databastabellen, en bra och flexibel struktur som låter oss använda innehållet på ett smidigt sätt i webbplatsen och leder till effektiv SQL. Tänker man till när man skapar lagringsstrukturen så kan man spara ett antal kodrader när man sedan skall redigera, och visa upp innehållet i webbplatsen.

Utmaningen ligger även i hur man väljer att konstruera sina klasser, kanske går det att skapa en generell struktur som klarar både det ena och det andra och även är förberedd för att byggas ut.

<!--
Visa hur markdown formattering, bbcode.
anax/textfilter
-->

[FIGURE src=image/snapvt17/content-delete-edit.png?w=w3 caption="Ett formulär för att jobba CRUD med innehåll i databasen."]

[FIGURE src=image/snapvt17/content-blog.png?w=w3 caption="En blogglista med alla inlägg med senaste inlägget först."]

[FIGURE src=image/snapvt17/content-textfilter.png?w=w3 caption="Innehållet formatteras och filtreras för att bli HTML."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>

<!--stop-->





Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 2-4 studietimmar, inklusive extra läsning i referenslitteraturen efter eget val)*



<!--
###Artiklar {#artiklar}

Läs följande artiklar.

-->


###Lästips {#lastips}

Följande tips från coachen används i övningen och uppgiften.

1. ["Reguljära uttryck i PHP ger BBCode formattering"](coachen/reguljara-uttryck-i-php-ger-bbcode-formattering)
1. ["Låt PHP-funktion make_clickable() automatiskt skapa klickbara länkar"](coachen/lat-php-funktion-make-clickable-automatiskt-skapa-klickbara-lankar)
1. ["Skriv för webben med Markdown och formattera till HTML med PHP (v2)"](coachen/skriv-for-webben-med-markdown-och-formattera-till-html-med-php-v2)



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 12-16 studietimmar)*


###Övningar {#ovningar}

Gör följande övning, den förbereder dig inför uppgifterna och löser ett par av dem.

1. Jobba igenom guiden ["Lagra innehåll i databas för webbsidor och bloggposter (v2)"](kunskap/lagra-innehall-i-databas-for-webbsidor-och-bloggposter-v2). Spara dina exempelprogram under `me/kmom04/content`.



###Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Gör uppgift "[Bygg webbsidor från innehåll i databasen](uppgift/bygg-webbsidor-fran-innehall-i-databasen)" och spara filerna i `me/anax-lite`. <!-- Gör egen WordPress med page, posts -->

1. Pusha och tagga ditt Anax Lite, allt eftersom och sätt en avslutande tagg (4.0.\*) när du är klar med alla uppgifter i kursmomentet.

<!--
1. Gör uppgiften "[Skapa en klass för textfiltrering och formattering](uppgift/skapa-en-klass-for-textfiltrering-och-formattering)". Den färdiga klassen integrerar du i `me/anax-lite`. Vill du testa och utveckla i en separat katalog så använder du `me/kmom04/textfilter`.

1. Gör uppgiften "[Dokumentera din ER-modell med Reverse Engineering](uppgift/dokumentera-din-er-modell-med-reverse-engineering)". Spara resultatet i `me/kmom04/er1`.
-->



<!--
Gör följande extrauppgifter om du har tid, lust eller ambition.

1. Anax Flat File.

-->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

* Finns något att säga kring din klass för texfilter, eller rent allmänt om formattering och filtrering av text som sparas i databasen av användaren?
* Berätta hur du tänkte när du strukturerade klasserna och databasen för webbsidor och bloggposter?
* Förklara vilka routes som används för att demonstrera funktionaliteten för webbsidor och blogg (så att en utomstående kan testa).
* Hur känns det att dokumentera databasen så här i efterhand?
* Om du är självkritisk till koden du skriver i Anax Lite, ser du förbättringspotential och möjligheter till alternativ struktur av din kod?
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

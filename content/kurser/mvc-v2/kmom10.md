---
author:
    - mos
revision:
    "2022-05-06": "(A, mos) Första utgåvan mvc-v2."
...
Kmom07/10: Projekt och examination
==================================

Detta kursmoment avslutar och examinerar kursen.

Alla delar i detta kursmoment skall utföras individuellt och självständigt.

Upplägget är enligt följande:

* Projekt
* Redovisning med videopresentation

Totalt omfattar kursmoment 07/10 i storleksordningen 20--60 studietimmar.

<!--more-->


<!--
Projekt med olika fokus

* Spel site.
* Adventurespel som projekt kan tillåta fokus på Ux.
* Hållbarhetsfokus.
* Cards in 5x5 (Poker square)
* Dice 5x5 (Dice square) (inkl highscore och histogram)
* Blog

Ett optionellt krav är inloggningen, man kan logga in och redigera uppgifterna som ligger i databasen.

Gör en uppgift som kräver att man tittar och opponerar på varandras kod utifrån phpmetrics och scrutinizer, eller som del av examinationen?

Ge poäng för den statiska valideringen för att uppmuntra att den biten blir rätt (dbwebb test kmom10).

Gör tydligt att repot skall se bra ut, så det kan användas för att länka till.

Inloggning på Game kan erbjuda möjlighet att reinitiera databasen eller andra admin-saker.

-->



Bedömning och betygsättning {#bedomning}
--------------------------------------------------------------------

Det finns ett särskilt dokument som beskriver [grunderna för bedömning och betygsättning](kurser/faq/bedomning-och-betygsattning).



Projektidé {#ide}
--------------------------------------------------------------------

Du skall fortsätta bygga vidare på din kodbas i `me/report` och där lägger du till en ny landningssida för projektets webbplats.

Du behöver göra ett aktivt val om vilket projekt du vill utveckla. Här är förslagen till projektidéer.

* Casino med kortspel (poker)
* Äventyrsspel (adventure)
* Visualisera indikatorer för hållbarhet (sustainability)
* Eget fokus (eget)

Tänk till så att du inte väljer ett alltför stort och komplext projekt som tar allt för mycket tid. Välj ett projekt där du kan slutföra grundkraven inom 20-40h.

Här följer en utökad beskrivning av varje projektidé.



### Casino med kortspel (poker) {#proj1}

Mikael håller på och skriver.



### Äventyrsspel (adventure) {#proj2}

Mikael håller på och skriver.



### Visualisera indikatorer för hållbarhet (sustainability) {#proj3}

Mikael håller på och skriver.



### Eget fokus (eget) {#proj4}

Mikael håller på och skriver.



Krav {#krav}
--------------------------------------------------------------------

Det finns 3 grundläggande krav (1, 2, 3) du måste lösa för att få godkänt på denna uppgiften.

Det finns 3 optionella krav (4, 5, 6) som du kan välja att utföra om du har tid, lust, energi och förmåga. Varje komplett utfört optionellt krav kan höja ditt slutbetyg ett steg.



Krav 1, 2, 3: Webbplats {#k123}
--------------------------------------------------------------------

Din nya webbplats skall minst uppfylla följande krav.


### Projektfokus {#p}

Välj ditt fokus för ditt projekt.

Implementera det i din webbplats.



### Struktur och innehåll {#s}

* En landningssida `/proj` som syns i navbaren på din report-sida.
* En sida `/proj/about` som berättar utförligt om ditt projekt och vad det handlar om.
* Din about-sida skall innehålla en sektion om dokumentation av ditt projekt där följande är inkluderat.
    * Länk till dokumentationen som är genererad via phpdoc.
    * Länk till rapporten från phpmetrics.
    * Länk till ditt GitHub repo.
    * Länk till Scrutinizer för ditt repo.
        * Inkludera dina badges i sidan.
* Din about-sida skall innehålla en summering där du berättar om projektets kodkvalitet. Berätta vilka åtgärder du gjort för att kvalitetssäkra projektet och hur du jobbat med kodkvaliteten och vilka verktyg du använt. Har du fokuserat på vissa saker, verktyg eller metrics, så kan du berätta om dem.



### Databas med ORM {#o}

* Din webbplats skall använda databas via ORM.
* Det skall finnas en route `/proj/reset` som återställer databasen till dess ursprungliga läge. Placera en länk till denna routen i din about-sida.



### Utseende och användbarhet {#u}

* Din webbplats skall ha en stil och utseende som tydligt skiljer sig från din report-sida. Det skall utseendemässigt se ut som en ny webbplats så bygg en "ny" stylesheet eller modifiera din befintliga. Modifiera minst färg, typsnitt och utseende på header och footer.
* Användbarhet är viktigt, så fokusera på att din webbplats känns lätt att använda. Använd det du lärt dig om detta hittills.



### Kodstil {#k}

* Din kod i `me/report` skall passera phpcs utan anmärkning.



### Linters {#l}

* Din kod i `me/report` skall passera phpmd och phpstan (valfri level) utan anmärkning. Det är okey att disabla varningar med kommentarer i koden.



### Enhetstestning & Kodtäckning {#e}

* Alla delar (klasser) av din kod i `me/report` skall täckas av testfall och assertions. Du kan exkludera  katalogerna `Controller`, `Entity`, `Repository` och filen `Kernel.php` samt de filer som är relaterade till övningar du gjort.
* Nå en kodtäckning om minst 70%.



### Dokumentation {#d}

* Använd DocBlock kommentarer när du gör projektet.
* Generera dokumentation med phpdoc och spara i `docs/api`.
* Din about-sida skall innehålla en länk till dokumentationen.



### Metrics {#m}

* Använd phpmetrics för att generera en rapport. Spara den i `docs/metrics`.
* Din about-sida skall innehålla en länk till din metrics rapport.



### Git repo och GitHub/Lab {#g}

* Din kod skall vara ett Git repo och den skall ligga publicerad på GitHub/GitLab eller liknande webbtjänst.
* Ditt git repo skall ha en `README.md` som beskriver innehållet i någon omfattning.
* Din about-sida skall innehålla en länk till GitHub (eller motsvarande).



### Scrutinizer {#s}

* Ditt repo skall vara kopplat till Scrutinizer.
* Din about-sida skall innehålla:
    * Länk till Scrutnizer.
    * Inkludera badges.



Krav 4: Snygg kod (optionellt) {#k4}
--------------------------------------------------------------------

För att visa dina goda förmågor i att relatera till konceptet "Snygg och god kod" så presenterar du din egen syn på detta i en artikel eller presentation.

Du kan inleda så här:

> "Finns det verkligen ett begrepp som är 'Snygg och god kod'? Kan en programmerare uppfatta kod som 'snygg' och vad innebär det och hur producerar man 'snygg kod'?"

Använd och relatera till de begrepp, verktyg och mätvärden som kursen hanterat.

Visa gärna något exempel.

Avsluta med din egen personliga syn.



### Artikel {#k4a}

Du skriver din artikel på routen `proj/cleancode` och länkar till den från din about-sida.

Din artikel bör vara omfångsmässigt som 1.5-2.0 A4 sidor. Det är ungefär som 1.5 - 2 x en normalbra redovisningstext. Vi pratar alltså om cirka 40-60 meningar text, cirka 4-5000 ord.



### Presentation {#k4p}

Du gör en "powerpoint" presentation och spelar in på video.

Länka till presentationen, en pdf-variant, via din about-sida.

Nämn videon på din about-sida, länka till den via din about-sida eller via Canvas.

Presentationen skall vara "exakt" 3 minuter lång.

Försök göra en så "professionell" presentation du kan. Tänk på inledning,  avslutning och "energinivå".

Håll tiden och försök göra presentationen till "exakt 3 minuter". Ett "proffs" kan alltid avsluta en presentation när tiden är slut.

Det är fritt fram att klippa och redigera din video i efterhand liksom att lägga till intro och outro.



Krav 5: Inloggning (optionellt) {#k5}
--------------------------------------------------------------------

Ditt projekt skall innehålla en möjlighet att logga in. Man skall kunna logga in med följande två användare.

* akronym doe, lösenord doe
* akronym admin, lösenord admin

En användare kan ha en roll som vanlig användare eller som administratör.

Användaren doe är en vanlig användare som inte har tillgång till administratörsfunktioner.

Användaren admin har tillgång till administratörsfunktioner.

Användare har en profilsida med detaljer om användaren. Någon av detaljerna skall kunna redigeras av användaren.

En användare skall ha en profilbild.

Man skall kunna registrera en ny användare genom att ange en akronym och ett lösenord.

När administratören är inloggad kan den se en översikt av samtliga användare i databasen. Administratören kan även lägga till, uppdatera och ta bort en användare.



Krav 6: ORM (optionellt) {#k6}
--------------------------------------------------------------------

Du har valt att göra en större databas där du har fler än 3 tabeller och du har minst två tabeller som har en relation mellan varandra. Du har alltså minst två tabeller som behöver joinas.

Du använder ORM för att jobba mot tabellerna.

Du kan använda SQL för att joina eller så lär du dig mer om Symfony och Doctrine och "[How to Work with Doctrine Associations / Relations](https://symfony.com/doc/current/doctrine/associations.html)".

Du har gjort ett logiskt ER-diagram över din databas och sparat som en bild.

* I din about-sida, skriv ett stycke "ORM" och lista vilka tabeller du har och ge en beskrivning av dina tabeller (en rad räcker). Berätta även vilka tabeller som är kopplade (har en relation).
* I din about-sida, inkludera bilden på ditt ER diagram.



Redovisning {#redovisning}
--------------------------------------------------------------------

Avsluta och redovisa din projektinlämning enligt följande.

1. Testa ditt projekt med `dbwebb test kmom10`. Se till att alla delar passerar grönt.

1. Tagga som v10.0.0, pusha till GitHub/Lab.

1. Driftsätt din applikation på studentservern. Dubbelkolla att alla delar fungerar, inklusive nollställningen av databasen.

1. På din me/report sida, skriv följande:

    1. För varje krav du implementerat, dvs 1-3, 4, 5, 6, skriver du ett textstycke om ca 5-10 meningar där du beskriver hur du löste kravet. Poängsättningen tar sin start i din text så se till att skriva väl för att undvika poängavdrag. Missar du att skriva/dokumentera din lösning så blir det 0 poäng. Du kan inte komplettera en inlämning för att få högre betyg.

    2. Skriv ett allmänt stycke om hur projektet gick att genomföra. Problem/lösningar/strul/enkelt/svårt/snabbt/lång tid, etc. Var projektet lätt eller svårt? Tog det lång tid? Vad var svårt och vad gick lätt? Var det ett bra och rimligt projekt för denna kursen?

    3. Avsluta med ett sista stycke med dina tankar om kursen och vad du anser om materialet och handledningen (ca 5-10 meningar). Ge feedback till lärarna och förslå eventuella förbättringsförslag till kommande kurstillfällen. Är du nöjd/missnöjd? Kommer du att rekommendera kursen till dina vänner/kollegor? På en skala 1-10, vilket betyg ger du kursen?

2. Ta en kopia av texten på din redovisningssida och kopiera in den på Canvas. Glöm inte att bifoga länken till projektet på studentservern.

3. Spela in en redovisningsvideo för projektet och lägg länken till videon i en kommentar på din inlämning i Canvas. Detta kan du göra dagen efter projektets deadline. Läs mer om hur du kan [spela in en redovisningsvideo](kurser/faq/slutpresentation).

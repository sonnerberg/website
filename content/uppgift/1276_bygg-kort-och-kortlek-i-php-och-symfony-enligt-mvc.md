---
author: mos
category:
    - kurs mvc
revision:
    "2021-04-03": "(A, mos) Första utgåvan i mvc-v1."
...
Bygg kort och kortlek i PHP och Symfony enligt MVC
===================================

Du skall skapa ett antal klasser i PHP. Dessa klasser skall du sedan använda i ett par webbsidor och visa upp att de fungerar. Tanken är att du bygger grunden till någon form av enklare kortspel med objektorienterade tekniker i ramverket Symfony.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap i hur man skapar en klass i PHP och hur arv och komposition fungerar.

Du kan bygga webbsidor via kontroller och templatefiler i Symfony.

Du vet hur man använder GET, POST och SESSION i en webbapplikation.



Introduktion och förberedelse {#intro}
-----------------------

Läs och förbered dig.

Om du är osäker på hur en kortlek ser ut så kan du kontrollera med [Wikipedia Kortlek](https://sv.wikipedia.org/wiki/Kortlek). Eftersom vi skall spela kort så kan det vara bra att välja en klassisk Fransk-engelsk kortlek.

Försök göra många små commits. När du är klar med en "feature" i din kod så kan det vara lämpligt att också göra en commit. Detta skapar dig en bra historik över ändringarna i din kod. Läs gärna igenom artikeln "[How to Write a Git Commit Message](https://cbea.ms/git-commit/)" för att få tips om hur du kan skriva bra commit-meddelanden.

<!--
### Välj ett kortspel att implementera {#kortspel}

Du skall bygga ett kortspel i din webbplats. Tanken är att göra ett enkelt kortspel men du kan själv välja vilket kortspel du försöker bygga. Du kommer få möjlighet att bygga vidare på ditt kortspel i de kommande kursmomenten.

Börja med att bekanta dig med det spelet du skall bygga. Förslaget är kortspelet "War".

* [Wikipedia om kortspelet War (card game)](https://en.wikipedia.org/wiki/War_(card_game))
* [Provspela en variant av kortspelet War](https://cardgames.io/war/)

Läs igenom reglerna och om det finna olika variationer att spela spelet. Bestäm dig för den varianten du vill köra på. Det är fritt fram att hitta på en egen variant.

Förslaget är att du börjar med enklaste möjliga variant av spelet. Använd principen KISS och "Keep it simple stupid". Det kan vara en utmaning i uppgiften att verkligen försöka hålla det enkelt och avgränsat. Glöm inte bort det.

Här följer ett par förslag till klasser som du eventuellt kan tänkas behöva implementera.

* Game, Player, ComputerPlayer, Card, Deck, CardHand, Histogram, Intelligence, HighScore

Du har möjlighet att bygga vidare på spelet i nästa kursmoment så börja med något enkelt som fortfarande leder fram till ett spelbart spel.



### Alternativa kortspel {#alt}

Några alternativa varianter på kortspel kan vara 21, black jack, poker.



### Är JavaScript en möjlighet? {#js}

Detta är en kurs i backend PHP så tanken är att du implementerar spelet på det viset. Man klickar på länkar eller knappar som postar någon form av formulärdata till servern som via sessionen har koll på spelets ställning.

Får man göra spelets frontend i JavaScript?

Det är inget som rekommenderas inom ramen för denna kursen.
-->

<!--
* Game, Player, ComputerPlayer, Card, Deck, CardHand, Histogram, Intelligence, HighScore

Optionellt 21, black jack.
Optionellt korträkning, histogram.
Optionellt någon form av patiens.
Game

Nästa kmom kan vara spel med logik och higscorelista i sessionen.
Problemlösning.Jobba med samma klasser men bygg ut dem.
Cohesion, Coupling, CC, Interface.
Intelligens med trait?
Krav på interface?
-->



Krav {#krav}
-----------------------

Kraven är uppdelade i sektioner.

Placera din kod i `me/report`.



### Skapa klasser och använd dem i webbsidor {#webb}

Börja med att utveckla dina klasser och testa dem i webbsidor enligt följande.

1. Skapa en kontroller i Symfony där du kan skapa webbsidor för denna delen av uppgiften.

1. Gör en förstasida `card` som länkar till samtliga undersidor för denna delen av uppgiften. Placera sidan i din navbar.

1. Skapa klasser för att hantera kort (card) och kortlek (deck). Skapa en sida `card/deck` som visar samtliga kort i kortleken sorterade per färg och värde. Ess kan vara antingen 1 eller 14 beroende av vilket kortspel man spelar.

1. Skapa en sida `card/deck/shuffle` som visar samtliga kort i kortleken när den har blandats.

1. Skapa en sida `card/deck/draw` som drar ett kort från kortleken och visar upp det. Visa även antalet kort som är kvar i kortleken.

1. Skapa en sida `card/deck/draw/:number` som drar `:number` kort från kortleken och visar upp dem. Visa även antalet kort som är kvar i kortleken.

1. Kortleken skall sparas i sessionen så om man anropar sidorna `draw` och `draw/:number` så skall hela tiden antalet kort från korleken minskas tills kortleken är slut. När man gör `card/deck/shuffle` så kan kortleken återställas.

1. Skapa en sida `card/deck/deal/:players/:cards` som delar ut ett antal  `:cards` från kortleken till ett antal `:players` och visar upp de korten som respektive spelare har fått. Visa även antalet kort som är kvar i kortleken. Här kan det vara bra att skapa klasser för player och cardHand eller liknande.

1. Skapa en sida `card/deck2` som är en kortlek inklusive 2 jokrar. Visa kortleken på samma sätt som sidan `card/deck`. Här kan det troligen vara lämpligt med någon form av arv när du bygger koden. Försök återanvända `Deck` och bygg förslagsvis `DeckWith2Jokers extends Deck`.

Optionellt krav.

1. Fundera på om du kan använda konstruktionen "interface" för att bygga din kod förberedd för återanvändning. Tänk att din kod jobbar mot ett interface `DeckInterface` istället för en hård implementation av `Deck` alternativt `DeckWith2Jokers`. Se om du kan uppdatera din kod och dina sidor så applikationen blir mer flexibel för implementationen av själva kortleken. Spelaren, korthanden, och utdelningen av korten samt blandningen bör ju inte behöva bry sig om vilka kort som ligger i kortleken.



### Bygg JSON API {#json}

Börja med att utveckla dina klasser och testa dem i webbsidor enligt följande.

1. Skapa en kontroller i Symfony där du kan skapa ett JSON API för denna delen av uppgiften.

1. Skapa en vanlig webbsida som landningssida `card/json` där du kan länka till samtliga JSON sidor.

1. Skapa en route `GET card/api/deck` som returnerar en JSON struktur med hela kortleken sorterad per färg och värde.

1. Skapa en route `POST card/api/deck/shuffle` som blandar kortleken och därefter returnerar en JSON struktur med kortleken.

1. Skapa route `POST card/api/deck/draw` och `card/api/deck/draw/:number` som drar 1 eller `:number` kort från kortleken och visar upp dem i en JSON struktur samt antalet kort som är kvar i kortleken. Kortleken sparas i sessionen så om man anropar dem flera gånger så minskas antalet kort i kortleken.

1. Skapa en sida `card/api/deck/deal/:players/:cards` som delar ut ett antal  `:cards` från kortleken till ett antal `:players` och visar upp de korten som respektive spelare har fått i en JSON struktur. Visa även antalet kort som är kvar i kortleken.



### Problemlösning {#problemlos}

Du skall försöka problemlösa ett spel med flödesschema och pseudokod.

1. Välj ett kortspel som du vill problemlösa (och implementera i nästa kmom). Är du osäker så väljer du [kortspelet 21](https://sv.wikipedia.org/wiki/Tjugoett_(kortspel)) eller [kortspelet Black Jack](https://en.wikipedia.org/wiki/Blackjack) där en spelare kan spela mot datorn som är bank. Du kan även välja olika spelvarianter på dessa kortspel eller ett annat kortspel eller en [patiens](https://sv.wikipedia.org/wiki/Patiens) (se [exempel på olika kort patienser](https://www.123patiens.se/)).

1. Samla all din dokumentation i en webbsida under routen `game/card` och placera en länk till sidan i din navbar.

1. Inled med en kort beskrivning av ditt kortspel och hur du valt att det skall fungera.

1. Skapa ett flödesschema som representerar hur du tänker lösa grunderna i spelet. Resultatet kan du placera som en bild i webbsidan.

1. Skapa psuedokod som visar hur du tänker lösa delar av spelet. Du kan spara resultatet som text eller bild men visa upp det i webbsidan.

1. Fundera igenom vilka klasser du behöver för att implementera spelet. Beskriv klasserna i text med klassens namn och en mening som beskriver vad klassens syfte är.

1. Om du vill kan du komplettera med att rita ett UML klass diagram (optionellt).



<!--
### Spel i Symfony {#symfony}

1. Gör en kontroller med routes i Symfony som hanterar flödet i ditt kortspel. Din kontroller skall innehålla så lite kod som möjligt. All applikationskod placerar du i andra klasser som din kontroller använder.

1. Använd templatefiler för att rendera webbsidorna.

1. Du bygger detta som en del i din report-sida. Lägg till ett menyval i din navbar som man kan klicka på för att komma till spelet.

1. Landningsidan på spelet ger information om vilket spel det är och dess regler. Här skall det även finnas en länk som leder till en sida med spelets dokumentation. Det skall finnas en knapp/länk där man kan starta spelet.

1. Skapa en sida som dokumenterar spelet genom att du kort för varje klass (en mening) beskriver klassens syfte och dess relationer till varandra (arv, komposition). Beskrivningen kan vara i text och det är valfritt om du vill komplettera med ett UML klassdiagram.

1. Sidan för dokumentation skall även innehålla resultatet från ditt flödesschema och din pseudokod.



### Kortspel {#spel}

Om du har valt ett annat spel än "War" så kan du behöva modifiera och tolka något av kraven.

1. Skapa klasser för att skapa en webbsida där man kan spela kortspelet. Din kontroller i Symfony skall använda dina klasser. Kontrollern skall innehålla så lite kod som möjligt. Din kod skall ligga i "modellagret" som är M i MVC. Förenklat är det de klasser som inte tillhör ramverket utan är mer applikationens klasser.

1. I första versionen av ditt spel räcker det om man kan spela spelet mot 1 spelare (datorn) och det kan sakna stöd för "war-delen".

1. Spelets ställning kan du lagra i sessionen.

1. När spelet är slut räknas korten och du visar vem som vann. Bygg in stöd för att spela med färre kort så det blir enklare att testa slutdelen av spelet.

1. Under spelets gång skall man när som helst kunna "Ge upp" och komma till en slutscen som visar aktuell ställning med korten.
-->



### Publicera {#publicera}

1. Committa alla filer och lägg till en tagg 2.0.0. Om du gör uppdateringar så ökar du taggen till 2.0.1, 2.0.2, 2.1.0 eller liknande.

1. Kör `dbwebb test kmom02` för att kolla att du inte har några fel.

1. Pusha upp repot till GitHub, inklusive taggarna.

1. Gör en `dbwebb publishpure report` för att kolla att det fungerar på studentservern.


<!--

php-cs-fixer via composer.json

1. När du är klar, kör `make test` för att köra alla testerna mot ditt repo. När man kör `make test` så bör det passera utan allvarliga felmeddelanden.

-->



<!--
Extrauppgift {#extra}
-----------------------

Lös följande extrauppgifter om du har tid och lust.

-->



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i chatt och forum om du behöver hjälp!

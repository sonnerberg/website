---
author: mos
category:
    - kurs mvc
revision:
    "2021-04-01": "(A, mos) Första utgåvan i mvc-v1."
...
Bygg kortspel i PHP och Symfony enligt MVC
===================================

Du skall skapa ett antal klasser i PHP. Dessa klasser skall du sedan använda i ett par webbsidor och visa upp att de fungerar. Tanken är att du bygger ett enklare kortspel med objektorienterade tekniker i ramverket Symfony.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap i hur man skapar en klass i PHP och hur arv och komposition fungerar.

Du kan bygga webbsidor via kontroller och vyer i Symfony.



Introduktion och förberedelse {#intro}
-----------------------

Läs och förbered dig.



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



Krav {#krav}
-----------------------

Kraven är uppdelade i sektioner.



### Problemlösning {#problemlos}

Gör ett försök att designa din lösning innan du börjar koda.

1. Skapa ett flödesschema som representerar hur du tänker lösa grunderna i spelet. Resultatet skall du senare placera i en webbsida så du kan spara det som en bild.

1. Skapa psudokod som visar hur du tänker lösa delar av spelet.  Resultatet skall du senare placera i en webbsida så du kan spara det som en bild eller ren text.



### Spel i Symfony {#symfony}

1. Gör en kontroller med routes i Symfony som hanterar flödet i ditt kortspel. Din kontroller skall innehålla så lite kod som möjligt. All applikationskod placerar du i andra klasser som din kontroller använder.

1. Använd templatefiler för att rendera webbsidorna.

1. Du bygger detta som en del i din report-sida. Lägg till ett menyval i din navbar som man kan klicka på för att komma till spelet.

1. Landninggsidan på spelet ger information om vilket spel det är och dess regler. Här skall det även finnas en länk som leder till en sida med spelets dokumentation. Det skall finnas en knapp/länk där man kan starta spelet.

1. Skapa en sida som dokumenterar spelet genom att du kort för varje klass (en mening) beskriver klassens syfte och dess relationer till varandra (arv, komposition). Beskrivningen kan vara i text och det är valfritt om du vill komplettera med ett UML klassdiagram.

1. Sidan för dokumentation skall även innehålla resultatet från ditt flödesschema och din pseudokod.



### Kortspel {#spel}

Om du har valt ett annat spel än "War" så kan du behöva modifiera och tolka något av kraven.

1. Skapa klasser för att skapa en webbsida där man kan spela kortspelet. Din kontroller i Symfony skall använda dina klasser. Kontrollern skall innehålla så lite kod som möjligt. Din kod skall ligga i "modellagret" som är M i MVC. Förenklat är det de klasser som inte tillhör ramverket utan är mer applikationens klasser.

1. I första versionen av ditt spel räcker det om man kan spela spelet mot 1 spelare (datorn) och det kan sakna stöd för "war-delen".

1. Spelets ställning kan du lagra i sessionen.

1. När spelet är slut räknas korten och du visar vem som vann. Bygg in stöd för att spela med färre kort så det blir enklare att testa slutdelen av spelet.

1. Under spelets gång skall man när som helst kunna "Ge upp" och komma till en slutscen som visar aktuell ställning med korten.



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

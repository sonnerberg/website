---
author: mos
category:
    - javascript
    - test
    - kurs ramverk2
revision:
  "2017-11-03": (A, mos) Första utgåvan.
...
Integrera en testmiljö med JavaScript i me-sida och Express
==================================

Du skall bygga upp en testmiljö för ditt JavaScript-projekt. Det handlar om vilka verktyg du använder för enhetstestning, kodtäckning och en kedja av Continuous Integration samt hur du kan använda Docker vid tester.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har kunskaper motsvarande artikeln "[Kom igång med en testmiljö i JavaScript](kunskap/kom-igang-med-en-testmiljo-i-javascript)".



Introduktion {#intro}
-----------------------

Du skall skapa grunden för enhetstester och kodtäckning samt integrera dessa i ditt projekt, din redovisa-sida. 

Du skall använda dessa grunder för att bygga en CI-kedja med externa tjänster som bygger din kod och visar kodtäckning samt kodkvalitet.

Du skall lägga till images för test. Du skall kunna exekvera enhetstester i flera kontainrarna som kör olika versioner av din mälmiljö.

Som ett alternativ till `make` kan du använda script i `npm`. Men se till att de fungerar på liknande sätt.



Krav {#krav}
-----------------------

1. Allt som behövs i ditt repo skall installeras vid `make install`.

1. Välj och integrera ett verktyg för enhetstester. Verktyget skall exekvera enhetstester vid `make test`.

1. Lägg till så att kodtäckning fungerar vid enhetstester.

1. Docker skall fungera tillsammans med dina tester. Använd egna Dockerfiler som skapar dina anpassade images. Skapa minst tre images för olika versioner av din målmiljö. Starta testerna via `docker-compose run` och genom `make` mot dina tre images via `make test1`, `make test2` och `make test3`.

1. Bygg en CI-kedja och integrera med en byggtjänst likt Travis eller CircleCI som checkar ut ditt repo och utför `make install test`. Badga din README.

1. Bygg vidare på din CI-kedja och integrera med minst en tjänst för kodkvalitet och kodtäckning. Du kan välja att integrera mot flera tjänster och/eller en tjänst som löser kodtäckning och en tjänst som löser kodkvalitet. Badga din README.

1. Committa och tagga ditt redovisa-repo med taggen 3.0.0 eller senare, ladda upp till GitHub.

1. Kontrollera att allt validerar och fungerar. Ladda upp det på studentservern.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

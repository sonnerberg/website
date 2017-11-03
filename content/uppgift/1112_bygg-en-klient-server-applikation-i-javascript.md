---
author: mos
category:
    - javascript
    - test
    - kurs ramverk2
revision:
  "2017-11-03": (A, mos) Första utgåvan.
...
Bygg en klient/server applikation i JavaScript
==================================

Du skall bygga programvara i JavaScript, en variant av klient/server applikation. Syftet är främst att ha relevant programvara att jobba med under kursen. Exakt vilket fokus din applikation har är godtyckligt, men det är ett par viktiga aspekter som måste beaktas när du gör ditt val.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har ufört uppgiften "[Integrera en testmiljö med JavaScript i me-sida och Express](uppgift/integrera-en-testmiljo-med-javascript-i-me-sida-och-express)" och därmed har du en grund till testmiljö för din JavaScript applikation.



Introduktion {#intro}
-----------------------

Din applikation har en server-del och en klient-del. Klienten är godtycklig JavaScript, SPA, webb, desktop, mobil, etc. Server-delen är troligen en Express-server som "frontend/router/REST-API" mot din applikationskod.

Din kod skall vara testbar. Du kan organisera din kod i ett eller flera repon eller i redovisa-repot. Du kan göra det enkelt till att börja med och fortsätta jobba i redovisa-repot, eller så bryter du ut din applikationskod till eget/egna repon.

Din applikation skall omslutas av enhetstester.

I kommande kursmoment gäller även följande.

Din applikation kommer omslutas av funktionstester.

Din applikation skall kunna användas av flera användare samtidigt och användarna skall samverka.

Din applikation skall innehålla inslag av realtid med websockets.

Din applikation skall integreras med en databas.

Din applikation, eller delar av den, skall publiceras som en npm-modul.

Det finns en forumtråd som ger [mer information rörande val av applikationen](t/7005).



Krav {#krav}
-----------------------

1. Påbörja arbetet med din applikation. Ha ambitionen att i liten skala utveckla enligt TDD för att utvärdera konceptet.

1. Bygg en testsuite av enhetstester till din applikation.

1. Se till att din applikation (ditt repo) omfattas av en CI-kedja.

1. Infoga en landningssida/demo/prototyp av din applikation i din redovisa-sida.

1. Committa, tagga (v3.x.x) och pusha relevanta repon.

1. Om du lägger applikationen i eget repo så länka till det från din redovisa/about-sida.

1. Kontrollera att allt validerar och fungerar. Ladda upp det på studentservern.



Extrauppgift {#extra}
-----------------------

Det finns ingen extrauppgift.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

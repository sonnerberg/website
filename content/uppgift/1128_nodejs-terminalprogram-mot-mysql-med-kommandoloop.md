---
author: mos
category:
    - javascript
    - nodejs
    - mysql
    - kursen dbjs
    - kursen databas
revision:
    "2018-01-05": (A, mos) Första utgåvan.
...
Node.js terminalprogram mot MySQL med kommandoloop
==================================

Du skall bygga ett terminalprogram med JavaScript i Node.js som jobbar mot en MySQL databas.

Du jobbar mot en databas du har sedan tidigare och skapar både rapporter och uppdaterar data i databasen.

Terminalklienten bygger du som ett program som har en inbyggd meny där användaren kan välja vilka operatotioner som skall utföras mot databasen.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql/grunderna)".

Du har tidigare löst uppgiften "[Node.js terminalprogram mot MySQL (v2)](uppgift/nodejs-terminalprogram-mot-mysql-v2)" där du har kod som jobbar mot databasen. Du kan jobba vidare på den koden nu.

Du har jobbat igenom artikeln "[Gör en kommandoradsklient i Node.js (v2)](kunskap/gor-en-kommandoradsklient-i-node-js-v2)" vilken gav dig upplägget om hur du gör ett menysystem i terminalklienten tillsammans med en oändlig loop som läser in kommandon från terminalen.



Introduktion {#intro}
-----------------------

Du skall skriva terminalprogram som jobbar mot databasen "skolan". Ditt program skall kunna presenterar rapporter från databasens innehåll. Programmet skall också kunna uppdatera tabellerna i databasen.

Försök att skapa en god kodstruktur, använd filer, moduler, funktioner. Försök separera kod som är relaterad till databasen från kod som är relaterad till Node.js terminalprogram. Försök så gott det går.



Krav {#krav}
-----------------------

1. Skapa din main-funktion för programmet i filen `index.js`.

1. Inloggningsdetaljer till databasen skall sparas i `config.json` och läsas in av programmet.

1. Ditt program skall fungera som en oändlig kommandoloop där man kan skriva in kommandon som programmet utför. Det skall finnas ett kommando `menu` som visar menyn med samtliga kommandon. När man skriver kommandot `exit` skall programmet avslutas.

1. Skapa kommandot `larare` som visar all information om lärare, inklusive deras ålder. 

1. Skapa kommandot `kompetens` som visar en rapport hur kompetensen ändrats i senaste lönerevisionen ([se rapporten](guide/kom-igang-med-sql-i-mysql/joina-tabell#proc)).
 
1. Skapa kommandot `lon` som visar en rapport hur lönen ändrats i senaste lönerevisionen ([se rapporten](guide/kom-igang-med-sql-i-mysql/joina-tabell#proc)).

1. Skapa kommandot `lonerevision <procent>` som tar ett argument som anger hur mycket lönen skall uppdateras för samtliga lärare.

1. Skapa kommandot `pension` som visar en rapport över de kurser där de kursansvariga närmar sig pensionen ([se rapporten](guide/kom-igang-med-sql-i-mysql/joina-tabeller#age)).

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate terminal2
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Gör följande om du har tid och ro.

1. Lägg till kommandot `search <table> <where>` där man kan söka/filtrera och visa innehållet i en tabell.

1. Lägg till kommandot `lonerevision <procent> <where>` som även tar ett argument som anger villkoret för vilka lärare som skall få lönejusteringen.

1. Studera koden i dina filer, finns det delar av koden som du kan lyfta ut i externa filer/moduler och dela på liknande sätt som `config.json` delas mellan programmen?



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

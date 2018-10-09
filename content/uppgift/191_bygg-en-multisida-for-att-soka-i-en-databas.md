---
author: mos
category:
    - webbprogrammering
    - databas
    - sqlite
    - php pdo
revision:
    "2019-09-24": "(B, mos) Genomgången i samband med htmlphp v3."
    "2015-06-15": "(A, mos) Första utgåvan i samband med kursen htmlphp v2."
...
Bygg en multisida för att söka i en databas
==================================

Skriv en multisida i PHP för att visa hur kopplingar till databasen SQLite fungerar.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du vet vad en multisida är och du har jobbat igenom "[Bygg en multisida med PHP (v2)](kunskap/bygg-en-multisida-med-php-v2)".

Du har jobbat igenom övningen "[Kom igång med databasen SQLite med DB Browser för SQLite](kunskap/kom-igang-med-databasen-sqlite-med-db-browser-for-sqlite)". 

Du har gått igenom de första stegen i artikeln "[Kom igång med SQLite och PHP PDO](kunskap/kom-igang-med-sqlite-och-php-pdo)", minst till och med stycket "[Gör ett sökformulär med SELECT](kunskap/kom-igang-med-sqlite-och-php-pdo#select-form)".



Introduktion {#intro}
-----------------------

Du skall skapa en multisida som kopplar upp sig mot databasen SQLite samt utför SELECT-frågor mot databasen och visar resultatet.

I kursrepot finns exempelprogram som du kan utgå ifrån. Dels finns det i [`example/sqlite`](https://github.com/mosbth/htmlphp/tree/master/example/sqlite) och dels i [`pdo-sqlite`](https://github.com/mosbth/htmlphp/tree/master/example/pdo-sqlite).

Spara din multisida i ditt kursrepo under katalogen `me/kmom05/jetty`.

Dina SQLite-filer lägger du i katalogen `me/kmom05/jetty/db`. 

Börja med att kopiera databasfilen boatclub.sqlite, så har du en databas som du kan använda i uppgiften.



Krav {#krav}
-----------------------

1. Skapa grunden för en multisida, fristående från din me-sida, döp själva multisidan till `jetty.php`.

1. Skapa en undersida som kopplar sig till databasen. Om det gick bra så visas ett meddelande som säger "Ok".

1. Lägg koden som kopplar sig till databasen i en funktion `connectToDatabase()`. Sökvägen till databasen skall skickas som en parameter till funktionen. Funktionen skall returnera databasobjektet `$db`. Funktionen skall ligga i en fil, `src/functions.php`, skapa den filen.

1. Skriv om koden för de två första kraven ovan, så att du använder funktionen `connectToDatabase()`.

1. Skapa en undersida som skriver ut innehållet i tabellen `jetty` i en HTML tabell.

1. Skapa en undersida där man kan söka efter båtar.

1. Skapa en funktion `printJettyResultsetToHTMLTable()` i `src/functions.php`. Funktionen skall ta *resultsetet*, `$res`, som en inparameter och skriva ut innehållet i `$res` till en HTML-tabell. Resultatet blir en funktion, som du kan använda för att lösa de två föregående kraven. Strukturera om dem så att de använder funktionen. 

1. Validera och publicera din kod enligt följande.

```bash
# Ställ dig i kursrepot
#dbwebb validate jetty
dbwebb publish jetty
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar. 



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

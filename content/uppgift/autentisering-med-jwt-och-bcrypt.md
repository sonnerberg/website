---
author:
    - efo
category:
    - js
    - ramverk
    - kurs ramverk2
revision:
    "2019-01-14": "(A, efo) Första utgåva."
...
Autentisering med JWT och bcrypt
===================================

Vi ska bygga vidare på vårt me-api från kmom01. I denna uppgift tittar vi på hur vi använder JWT, bcrypt och en sqlite databas för att spara och autentisera användare. Vi tittar sedan på hur vi kan skapa en route för att skapa redovisningstexter.



<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har gjort uppgiften [Bygg ett me API till ramverk2](uppgift/bygg-ett-me-api-till-ramverk2).



Introduktion {#intro}
-----------------------

I följande stycken går vi igenom tekniker som kan vara användbara för att implementera uppgiften som är specificerad i stycket [Krav](#krav).



En databas i grunden {#databas}
-----------------------

För att kunna spara användare och så småningom redovisningstexter installerar vi npm modulen node-sqlite3 i vårt me-api repo med följande kommando. [Dokumentationen för modulen](https://www.npmjs.com/package/sqlite3) är som alltid vår bästa vän.

```bash
npm install sqlite3 --save
```

Vi skapar sedan katalogen `db` i vårt repo och i den katalogen filen `texts.sqlite`. Vi ville inte att denna och andra sqlite filer är under versionshantering då de isåfall skriver över vår produktions databas när vi driftsätter så vi lägger till `*.sqlite` i `.gitignore`.

Ett smart drag i detta skedet är att skapa en migrations-fil `db/migrate.sql` som du kan använda för att skapa tabeller. Min migrate-fil innehåller än så länge följande SQL.

```sql
CREATE TABLE IF NOT EXISTS users (
    email VARCHAR(255) NOT NULL,
    password VARCHAR(60) NOT NULL,
    UNIQUE(email)
);
```

Vi har alltså två kolumner `email` och `password` och vi vill att `email` är unik. Vi kan nu med hjälp av följande kommandon skapa tabellen i vår `texts.sqlite` databas.

```bash
cd db
sqlite3 texts.sqlite
sqlite> .read migrate.sql
sqlite> .exit
```

Vi kan nu använda `sqlite3` modulen för att lägga till en användare i vår `texts.sqlite` databas på följande sätt.

```javascript
const sqlite3 = require('sqlite3').verbose();
const db = new sqlite3.Database('./db/texts.sqlite');

db.run("INSERT INTO users (email, password) VALUES (?, ?)",
    "user@example.com",
    "superlonghashedpasswordthatwewillseehowtohashinthenextsection", (err) => {
    if (err) {
        // returnera error
    }

    // returnera korrekt svar
});
```



### sqlite3 på servern

För att detta ska fungera på din droplet måste vi installera `sqlite3` innan vi kör `npm install`. Vi gör detta med `sudo apt-get install sqlite3` som vår `deploy` användare. Vi kan nu hämta senaste versionen av vårt API med `git pull` och köra `npm install` för att installera det nya paketet. Vi behöver även skapa databas filen `db/texts.sqlite` och köra migrations filen.



Säker hantering av lösenord {#passwords}
-----------------------

När vi sparar lösenord i en databas vill göra det så säkert som möjligt. Därför använder vi [bcrypt](https://codahale.com/how-to-safely-store-a-password/). Vi installerar bcrypt paketet med npm med hjälp av kommandot `npm install bcrypt --save`. [Dokumentationen för modulen](https://www.npmjs.com/package/bcrypt) är som alltid vår bästa vän.

För att hasha ett lösenord med bcrypt modulen importerar vi först modulen och sedan använder vi `bcrypt.hash` funktionen.

```javascript
const bcrypt = require('bcrypt');
const saltRounds = 10;
const myPlaintextPassword = 'longandhardP4$$w0rD';

bcrypt.hash(myPlaintextPassword, saltRounds, function(err, hash) {
    // spara lösenord i databasen.
});
```

Det finns även en promise version av biblioteket om man gillar promise eller async/await teknikerna. Läs mer om det i dokumentationen.

För att jämföra ett sparad lösenord med det användaren skrivit in använder vi `bcrypt.compare`.

```javascript
const bcrypt = require('bcrypt');
const myPlaintextPassword = 'longandhardP4$$w0rD';
const hash = 'superlonghashedpasswordfetchedfromthedatabase';

bcrypt.compare(myPlaintextPassword, hash, function(err, res) {
    // res innehåller nu true eller false beroende på om det är rätt lösenord.
});
```



JSON Web Tokens {#jwt}
-----------------------



Route med POST {#post}
-----------------------



JWT middleware {#middleware}
-----------------------



Krav {#krav}
-----------------------

1. Committa alla filer och lägg till en tagg (2.0.\*).

1. Pusha upp repot till GitHub, inklusive taggarna.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

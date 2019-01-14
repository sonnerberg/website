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



En databas i grunden {#databas}
-----------------------

För att kunna spara användare och så småningom redovisningstexter installerar vi npm modulen node-sqlite3 i vårt me-api repo med följande kommando.

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

### sqlite3 på servern

För att att detta ska fungera på din droplet måste vi installera `sqlite3` innan vi kör kör `npm install`. Vi gör detta med `sudo apt-get install sqlite3` som vår `deploy` användare. Vi kan nu hämta senaste versionen av vårt API med `git pull` och köra `npm install` för att installera det nya paketet. Vi behöver även skapa databas filen `db/texts.sqlite` och köra migrations filen.



Säker hantering av lösenord {#passwords}
-----------------------



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

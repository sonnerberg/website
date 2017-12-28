---
author: mos
revision:
    "2017-12-27": "(A, mos) Första versionen, uppdelad av större dokument."
...
Skapa en databas
==================================

Vi skapar en databas för detta exemplet och vi lägger till en användare som kan använda databasen. Vi sparar allt vi gör i en fil och döper den till `setup.sql`.

[INFO]
Om du kör på BTH's server så har du [inte rättigheter att skapa en ny databas](kunskap/bth-s-labbmiljo-for-databasen-mysql#dbserver) eller lägga till en användare. Du har en befintlig databas och du har fått en användare och lösenord tilldelat.
[/INFO]

Det vi nu skall göra hjälper dig alltså inte på BTHs labbmiljö, men det hjälper dig att komma igång och skapa databasen på din egna lokala miljö.



Skapa databas {#create-db}
----------------------------------

Öppna din klient med en databasanvändare som har högsta behörighet (tex root) och skapa en ny databas "skolan" och välj att använda den.

```sql
-- Skapa databas
CREATE DATABASE skolan;

-- Välj vilken databas du vill använda
USE skolan;
```

För att ta bort och radera en hel databas med hela dess innehåll använder du kommandot DROP.

```sql
-- Radera en databas med allt innehåll
DROP DATABASE skolan;
```

Testa att radera din nyskapade databas och skapa sedan om den.

För att se vilka databaser som finns använder vi kommandot SHOW.

```sql
-- Visa vilka databaser som finns
SHOW DATABASES;

-- Visa vilka databaser som finns
-- som heter något i stil med *skolan*
SHOW DATABASES LIKE "%skolan%";
```

Nu kan du se vilka databaser som finns skapade.



Skapa användare till databasen {#user}
----------------------------------

Det finns ett behörighetssystem som kan koppla en användare med lösenord till en viss databas, inklusive behörigheter. För vårt syfte skapar vi en ny användare som kan göra allt mot vår nyskapade databas.

```sql
-- Skapa användaren "user" med
-- lösenordet "pass" och ge
-- fulla rättigheter till databasen "skolan"
-- när användaren loggar in från maskinen "localhost"
GRANT ALL ON skolan.* TO user@localhost IDENTIFIED BY 'pass';
```

Du kan se vilka GRANTs du givit en användare.

```sql
-- Visa vad en användare kan göra mot vilken databas.
SHOW GRANTS FOR user@localhost;

-- Visa för nuvarande användare
SHOW GRANTS FOR CURRENT_USER;
```

Det kan se ut så här.

```sql
mysql> SHOW GRANTS FOR user@localhost;
+--------------------------------------------------------------------------------------------------------------+
| Grants for user1@localhost                                                                                   |
+--------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'user'@'localhost' IDENTIFIED BY PASSWORD '*196BDEDE2AE4F84CA44C47D54D78478C7E2BD7B7' |
| GRANT ALL PRIVILEGES ON `skolan`.* TO 'user'@'localhost'                                                    |
+--------------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```

Nu kan du använda din klient för att logga in med den nya användaren och se att den kommer åt databasen.

Jag testar genom att starta kommandoradsklienten och ange användare, lösenord och databas.

```text
$ mysql -uuser -ppass skolan

... utskrifter från inloggingen

mysql>
```

Det kan se ut så här.

[ASCIINEMA src=154434 caption="Logga in mot en databas med angiven användare och lösenord."]

Om inget felmedelande visas och prompten för kommandoradsklienten visas så gick det bra att logga in med vald användare och lösenord.



Spara i fil {#fil}
----------------------------------

Glöm nu inte att du skulle spara alla SQL-kommandon du skriver i filen `setup.sql`.

Det som är bra med att spara all sin SQL kod är att det är enkelt att skapa om hela databasen från början om det blir något fel.

Tänk att du skall köra hela denna övningen på en ny dator som du tidigare inte använt. Du behöver skapa databasen och användaren, kanske vill du droppa databasen om den finns, kanske inte, där kan du välja väg. I mitt exempel nedan har jag kommenterat ut den raden som droppar databasen och jag skapar bara databasen om den inte redan finns.

Så här kan filen se ut. Se till att du har den och dubbelkolla att du kan köra alla kommandon i filen i en sekvens (på en gång), om och om igen.

```sql
-- Skapa databas
CREATE DATABASE IF NOT EXISTS skolan;

-- Välj vilken databas du vill använda
USE skolan;

-- Radera en databas med allt innehåll
-- DROP DATABASE skolan;

-- Visa vilka databaser som finns
-- SHOW DATABASES;

-- Visa vilka databaser som finns
-- som heter något i stil med *skolan*
SHOW DATABASES LIKE "%skolan%";

-- Skapa användaren "user" med
-- lösenordet "pass" och ge
-- fulla rättigheter till databasen "skolan"
-- när användaren loggar in från maskinen "localhost"
GRANT ALL ON skolan.* TO user@localhost IDENTIFIED BY 'pass';

-- Visa vad en användare kan göra mot vilken databas.
SHOW GRANTS FOR user@localhost;

-- Visa för nuvarande användare
-- SHOW GRANTS FOR CURRENT_USER;
```

Nu är trixet att du inte kan återskapa databasen när du är inloggad som användaren "user", den användaren har inte rättigheter att skapa en databas. För att köra hela skriptet på en gång måste du alltså vara inloggad som en användare (root) som har behörighet att skapa en databas.

Så här kan jag återskapa databasen, genom att köra SQL-filen med kommandoradsklienten.

```text
$ mysql --table -uroot -p < setup.sql
```

Kommandot fungerar när inga felmeddelanden visas. Switchen `--table` ger en tydligare utskrift. Det kan se ut så här.

[ASCIINEMA src=154430 caption="Skapa om databasen via SQL-kommandon i filen `setup.sql`."]

Det såg ut som min user-användare hade fler behörigheter på mitt system, men annars såg det ut precis som det var tänkt.

Se till att din fil fungerar likt ovan och använd kommentarer för att beskriva vad du gör. Rätt använd blir dessa filer en värdefull tillgång efter kursen, eller inför kursens examination.

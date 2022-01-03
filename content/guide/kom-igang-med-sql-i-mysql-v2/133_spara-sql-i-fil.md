---
author: mos
revision:
    "2022-01-03": "(B, mos) Genomgången inför v2 och MariaDB."
    "2021-01-14": "(A, mos) Uppdatead från ett större artikel."
...
Spara SQL i fil
==================================

Du har nu sparat SQL-koden från föregående artiklar i en fil. Låt oss gå igenom hur den filen kan se ut.



Filen setup.sql {#fil}
----------------------------------

Det som är bra med att spara all sin SQL kod är att det är enkelt att skapa om hela databasen från början om det blir något fel. Du kan köra en sådan här SQL-fil i godtycklig klient, det går lika bra i Workbench som i terminalen.

Tänk tanken att du skall kunna köra hela denna övningen på en ny dator som du tidigare inte använt. Du behöver skapa databasen och användaren, kanske vill du droppa databasen om den finns, kanske inte, där kan du välja väg. Du kan se hur jag gjorde nedan, jag valde att alltid droppa och skapa om databasen.

Jag väljer att ta med alla kommandon jag jobbat med. Jag ser det som en möjlighet att göra anteckningar tillsammans med koden. Jag kommenterar bort de kommandon som inte skall köras.

Så här kan filen se ut. Du kan jämföra min fil med din egen men koden behöver inte se likadan ut. Det viktigaste är att dubbelkolla att du kan köra alla kommandon i filen i en sekvens (på en gång), om och om igen. Då fungerar det.

```sql
-- Börja med att radera databasen om den finns
DROP DATABASE IF EXISTS skolan;

-- Skapa databas
CREATE DATABASE skolan;

-- Välj vilken databas du vill använda
USE skolan;

-- Radera en databas med allt innehåll
-- DROP DATABASE skolan;

-- CREATE DATABASE skolan;
-- CREATE DATABASE IF NOT EXISTS skolan;

-- Visa vilka databaser som finns
-- SHOW DATABASES;

-- Visa vilka databaser som finns
-- som heter något i stil med *skolan*
SHOW DATABASES LIKE "%skolan%";
```

Använd kommentarer för att beskriva vad du gör. Rätt använd blir dessa filer en värdefull tillgång efter kursen, eller inför kursens examination.

Nu är trixet att du inte kan återskapa databasen när du är inloggad som användaren "user", den användaren har inte rättigheter att skapa en databas. För att köra hela skriptet på en gång måste du alltså vara inloggad som en användare (root) som har behörighet att skapa en databas.

Pröva nu återigen att återskapa databasen, genom att köra SQL-filen med kommandoradsklienten.

```text
$ mariadb --table < setup.sql
```

Kommandot fungerar när inga felmeddelanden visas.

Prova gärna även att köra din fil i Workbench, så har du olika alternativ när du jobbar med databaserna. Ibland är det smidigt att jobba i Workbench och ibland är det smidigt att jobba i terminalen.

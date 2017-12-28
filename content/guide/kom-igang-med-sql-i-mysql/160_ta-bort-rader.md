---
author: mos
revision:
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Ta bort rader
==================================

Vi använder `DELETE` för att radera rader från en tabell. Lägg all SQL-kod för detta exemplet i filen `dml_delete.sql` och inled filen med en header som berättar vem du är.

```sql
--
-- Delete from database skolan.
-- By mos for course "XXX".
-- 2017-12-27
--
```

Slå upp hur DELETE fungerar i refmanualen och läs på om hur du kan ta bort rader från en tabell.

I princip ser det ut så här.

```sql
--
-- Delete rows from table
--
DELETE FROM larare WHERE efternamn = 'Hagrid';
```

Skriv SQL-kod för att utföra följande:

1. Radera Hagrid (1 rad).
1. Radera alla som jobbar på avdelningen DIPT (3 rader).
1. Radera alla som har en lön, men begränsa antalet rader som får raderas till 2 (`LIMIT`) (2 rader påverkas).
1. Radera samtliga återstående lärare.

Det sista kommandot bör ha raderat 2 lärare (2 rader i tabellen).

[INFO]
**MySQL Workbench: Felmeddelande om safe update mode**

Får du felmeddelandet om safe update mode när du försöker radera Hagrid?

> <i>Error Code: 1175. You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column To disable safe mode, toggle the option in Edit -> Preferences -> SQL Editor -- and reconnect.</i>

Gör som det står i felmeddelandet, gå in och klicka bort "Safe updates" under "SQL Editor" i Edit -> Preferences. Reconnecta därefter via "Query" -> "Reconnect to server". Sedan skall det gå. Det är en rimligt säkerhetsinställning som de har satt på i klienten.
[/INFO]

När du raderar rader så kan det vara bra att lägga till en `LIMIT` klausul som säger hur många rader du raderar. Annars finns risken att en liten felskrivning i satsen gör att du raderar hela innehållet i tabellen. Ta för vana att alltid använda LIMIT.

Återskapa alla lärare genom att köra SQL-kommandon från filen `dml_insert.sql`. Du skall nu återigen ha en tabell med samtliga lärare.

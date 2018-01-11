---
author: mos
revision:
    "2017-12-27": "(A, mos) Första versionen, uppdelad av större dokument."
...
Skapa tabell
==================================

Vi börjar nu att skapa tabeller.

Lägg SQL-koden i filen `ddl.sql` och inled filen med en header som berättar vem du är.

```sql
--
-- Create scheme for database skolan.
-- By mos for course "XXX".
-- 2017-12-27
--
```

En skola har lärare, skapa en tabell för lärare enligt följande:

**larare**

| Namn            | Datatyp     |
|-----------------|-------------|
| akronym         | CHAR(3)     |
| avdelning       | CHAR(4)     |
| fornamn         | VARCHAR(20) |
| efternamn       | VARCHAR(20) |
| kon             | CHAR(1)     |
| lon             | INT         |
| fodd            | DATETIME    |

Jag väljer att inte använda svenska tecken, även om det hade varit en möjlighet. 

Generellt skriver jag helst kommentarer på engelska och inte svenska, jag känner generellt att engelska ligger närmare programmeringsspråk och känns mer naturligt.

Här är SQL-kod som går att använda för att skapa tabellen. Akronym är unik och vi använder den som primärnyckel.

```sql
--
-- Create table: larare
--
CREATE TABLE larare
(
    akronym CHAR(3),
    avdelning CHAR(4),
    fornamn VARCHAR(20),
    efternamn VARCHAR(20),
    kon CHAR(1),
    lon INT,
    fodd DATETIME,

    PRIMARY KEY (akronym) 
);
```

Radera tabellen med `DROP` och skapa om den igen.

När du sparar CREATE och DROP i en SQL-fil som `ddl.sql` så kan du behöva kombinera dem för att uppnå önskat utfall. I mitt fall så tänker jag alltid börja med en tom databas och jag tänker droppa tabellen om den finns. I min fil blir ser det ut så här.

```sql
--
-- Create table: larare
--
DROP TABLE IF EXISTS larare;
CREATE TABLE larare
(
-- resten av CREATE statementet.
```

Jag kan visa vilka tabeller som finns med `SHOW TABLES`.

```sql
mysql> SHOW TABLES;
+------------------+
| Tables_in_skolan |
+------------------+
| larare           |
+------------------+
1 row in set (0.00 sec)
```

Jag kan se innehållet i tabellen med SELECT via `SELECT * FROM larare`. Än så länge är tabellen tom.

```sql
mysql> SELECT * FROM larare;
Empty set (0.01 sec)
```

Slå upp syntaxen för `CREATE TABLE` i refmanualen, skumma igenom den för att se varianter som finns för att skapa en tabell. Gör samma sak för `DROP TABLE`. Använd sökfunktionen för att hitta det du letar efter, bekanta dig också med innehållsförteckningen, det kommer att spara dig mycket tid framöver om du hittar snabbt i manualen.

> *Kom ihåg vem som är din bästa vän -- referensmanualen.*

Innan du avslutar, dubblekolla att du kan köra hela filen `ddl.sql` i en sekvens.

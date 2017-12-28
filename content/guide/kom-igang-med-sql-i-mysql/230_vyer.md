---
author: mos
revision:
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Vyer
==================================

Vyer är smidiga när SELECT-satserna blir lite väl stora. Vi kan se på vyer som ett alias för en SELECT-sats.

I referensmanualen kan du läsa [om vyer](https://dev.mysql.com/doc/refman/5.7/en/create-view.html).

Spara dina konstruktioner i filen `dml_view.sql`.



Vy med Namn  och Ålder {#vy-alder}
----------------------------------

Låt se på ett exempel där vi jobbar med en vy. Vi vill ha en översikt av lärarnas namn, deras avdelning och deras ålder. Vi gör en SELECT som ger oss svaret.

```sql
mysql> SELECT
    -> CONCAT(fornamn, ' ', efternamn, ' (', LOWER(avdelning), ')') AS Namn,
    ->     TIMESTAMPDIFF(YEAR, fodd, CURDATE()) AS Ålder
    -> FROM larare;
+---------------------------+--------+
| Namn                      | Ålder  |
+---------------------------+--------+
| Alastor Moody (dipt)      |     74 |
| Albus Dumbledore (adm)    |     76 |
| Argus Filch (adm)         |     71 |
| Gyllenroy Lockman (dipt)  |     65 |
| Hagrid Rubeus (adm)       |     61 |
| Madam Hooch (didd)        |     69 |
| Minerva McGonagall (didd) |     62 |
| Severus Snape (dipt)      |     66 |
+---------------------------+--------+
8 rows in set (0.00 sec)
```

Nu skapar vi en vy av samma SELECT.

```sql
CREATE VIEW VNamnAlder
AS
SELECT
	CONCAT(fornamn, ' ', efternamn, ' (', LOWER(avdelning), ')') AS Namn,
    TIMESTAMPDIFF(YEAR, fodd, CURDATE()) AS Ålder
FROM larare;

SELECT * FROM VNamnAlder;
```

Svaret blir det samma när vi gör en SELECT mot vyn.

Som vanligt kan vi begränsa urvalet med WHERE, ORDER BY och LIMIT.

```sql
mysql> SELECT * FROM VNamnAlder
    -> WHERE Namn LIKE '%di%'
    -> ORDER BY Ålder DESC
    -> LIMIT 3;
+----------------------+--------+
| Namn                 | Ålder  |
+----------------------+--------+
| Alastor Moody (dipt) |     74 |
| Madam Hooch (didd)   |     69 |
| Severus Snape (dipt) |     66 |
+----------------------+--------+
3 rows in set (0.01 sec)
```

Vyer är kraftfullt och gör databasen mer lättanvänd.

Radera vyn med `DROP VIEW`, vill du ändra en befintlig vy kan du använda `ALTER VIEW`.



Vy med Larare.* och Ålder {#vy-larare}
----------------------------------

1. Skapa en vy "Vlarare" som innehåller samtliga kolumner från tabellen Lärare inklusive en ny kolumn med lärarens ålder.
2. Gör en SELECT-sats mot vyn som beräknar medelåldern på respektive avdelning. Visa avdelningens namn och medelålder sorterad på medelåldern.

Resultatet kan se ut så här.

```sql
+-----------+-------------+
| avdelning | Snittålder  |
+-----------+-------------+
| ADM       |          69 |
| DIPT      |          68 |
| DIDD      |          66 |
+-----------+-------------+
3 rows in set (0.00 sec)
```



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

---
author: mos
revision:
    "2018-02-09": "(B, mos) Genomgången, mindre typo."
    "2017-12-29": "(A, mos) Första versionen, uppdelad av större dokument."
...
UNION och slå samman tabeller
==================================

Vi skall slå samman raderna från två tabeller i ett resultset.

Spara den SQL-kod du skriver i filen `dml_union.sql`.

Vi jobbar vidare med lönerevisionen och vi vill granska utfallet.



Visa alla rader med UNION {#union}
----------------------------------

Säg vi vill jämföra värdet i respektive tabell genom att slå ihop dem i en rapport. Det kan vi göra med UNION.

UNION kan slå samman två olika resultset, förutsatt att de delar samma struktur på kolumnerna.

```sql
--
-- UNION
--
SELECT *, 'src' AS "Källa" FROM larare
UNION
SELECT *, 'pre' AS "Källa" FROM larare_pre
ORDER BY akronym
;
```

I ovan så slår jag samman resultatet från två källor, med källans namn som extra kolumn, och sorterar per akronym

Säg att jag bara vill skriva ut delar av resultatet, och kanske begränsa vilka rader som skrivs ut, då kan jag omringa frågan med `()` och använda resultatet som ett implicit resultset, eller [_derived table_](https://dev.mysql.com/doc/refman/5.7/en/derived-tables.html) som är en form av _subquery_, en fråga i en fråga.

Jag kan då skapa en fråga som ser ut så här.

```sql
SELECT
	l.kalla,
    akronym,
    fornamn,
    efternamn,
    kon,
    kompetens,
    lon
FROM
(
	SELECT *, 'src' AS 'kalla' FROM larare
	UNION
	SELECT *, 'pre' AS 'kalla' FROM larare_pre
) AS l
WHERE
	akronym IN ('ala', 'dum')
ORDER BY akronym, l.kalla
;
```

En variant hade varit att göra en view av UNION-delen. Se det som ett alternativ.

När jag först gjorde bekantskap med databaser så föll jag för vyer och använde dem i tid och otid. Numer föredrar jag att se hela SQL-frågan utan att "dölja" den i vy på vy. Men var sak har sin tid och användningsområde.

Så här ser det ut om vi kör frågan.

```text
mysql> SELECT
    ->     l.kalla,
    ->     akronym,
    ->     fornamn,
    ->     efternamn,
    ->     kon,
    ->     kompetens,
    ->     lon
    -> FROM
    -> (
    ->     SELECT *, 'src' AS 'kalla' FROM larare
    ->     UNION
    ->     SELECT *, 'pre' AS 'kalla' FROM larare_pre
    -> ) AS l
    -> WHERE
    ->     akronym IN ('ala', 'dum')
    -> ORDER BY akronym, l.kalla
    -> ;
+-------+---------+---------+------------+------+-----------+-------+
| kalla | akronym | fornamn | efternamn  | kon  | kompetens | lon   |
+-------+---------+---------+------------+------+-----------+-------+
| pre   | ala     | Alastor | Moody      | M    |         1 | 30000 |
| src   | ala     | Alastor | Moody      | M    |         1 | 27594 |
| pre   | dum     | Albus   | Dumbledore | M    |         1 | 80000 |
| src   | dum     | Albus   | Dumbledore | M    |         7 | 85000 |
+-------+---------+---------+------------+------+-----------+-------+
4 rows in set (0.00 sec)
```

Vi kan nu se och jämföra rad för rad och se hur lönerevisionen har påverkat respektive individ.

Vi kan dock inte besvara frågorna vi hade ännu. För att göra det behöver vi lägga informationen på samma rad, inte på två olika rader som nu.

Vi tar det i nästa stycke.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

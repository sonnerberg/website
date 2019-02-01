---
author: mos
revision:
    "2019-02-01": "(C, mos) Nyare artikel ersätter denna."
    "2019-01-15": "(B, mos) Uppdelad i två delar då HAVING fick mer material."
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Aggregerande funktioner HAVING (OBSOLETE)
==================================

[WARNING]
Det finns en **nyare version av denna artikel**, klicka bara fram till nästa artikel i guiden, med samma titel, och gör den istället.

Det finns saker i denna artikel som gör den lite väl svår i vissa delar. Så du kan hoppa över den och ta den uppdaterade artikeln istället.

Om du redan gjort denna artikel så är allt väl, bara fortsätt i guiden.

Om du sitter mitt i denna artikeln nu, så kan du göra klart den eller ta den uppdaterade varianten, båda alternativen fungerar.
[/WARNING]

Vi jobbar med inbyggda aggregerande funktioner som kan beräkna värdet över många rader och vi ser hur vi kan göra urval av de rader som beräknas (WHERE) och urval av de rader som visas i rapporten (HAVING).

Fortsätt spara dina konstruktioner i filen `dml_agg.sql`.



Om HAVING {#omhaving}
----------------------------------

HAVING är för att begränsa vilka aggregerade värden som visas i rapporten.

WHERE jobbar på radnivå när kolumnens värde jämförs, de individuella raderna i tabellen.

HAVING jobbar på de aggregerade värdena, de som räknats fram med SUM, COUNT mm.

Med HAVING kan man begränsa urvalet, genom att jämföra med värden som är aggregerade.

Låt oss jobba igenom ett exempel. Vi börjar med att plocka fram snittlönen per avdelning.

```sql
SELECT
    avdelning,
    ROUND(AVG(lon)) AS Snittlon,
    COUNT(lon) AS Antal
FROM larare
GROUP BY
    avdelning
ORDER BY
    avdelning
;
```

Det ser ut så här.

```text
MySQL [skolan]> SELECT
    ->     avdelning,
    ->     ROUND(AVG(lon)) AS Snittlon,
    ->     COUNT(lon) AS Antal
    -> FROM larare
    -> GROUP BY
    ->     avdelning
    -> ORDER BY
    ->     avdelning
    -> ;
+-----------+----------+-------+
| avdelning | Snittlon | Antal |
+-----------+----------+-------+
| ADM       |    47531 |     3 |
| DIDD      |    43730 |     2 |
| DIPT      |    33396 |     3 |
+-----------+----------+-------+
3 rows in set (0.00 sec)
```

Vi har nu beräknat snittlönen per avdelning, vi kan se hur många lärare det är i respektive avdelning under "Antal". Det är deras löner som nu är snittlönen per rad.

När vi sorterar tabellen så kan vi använda vårt alias "Snittlon" (jag väljer att inte använda ö med flit) för att sortera på snittlönen.

Pröva med `ORDER BY Snittlon DESC` så får du rapporten sorterad per snittlön.

Om det av någon anledning inte fungerar, så kan man sortera per den aggregerande funktionen som man använder via `ORDER BY ROUND(AVG(lon)) DESC`. Du kan se den konstruktionen i exempel som visas, när du googlar, så pröva den också så att du vet att det fungerar.

Så, låt då se hur HAVING kan hjälpa oss.

1. Vi vill se snittlön per avdelning (och antal), men bara om snittlönen är större än 35000.
2. Vi vill se snittlönen per avdelning (och antal), men bara om det är 3 eller fler personer på den avdelningen.

Ovan begränsningar jobbar båda på de aggregerade värdena så här använder vi HAVING då WHERE inte kan hjälpa oss.

Jag visar lösningen på 1) så kan du själv lösa 2).

HAVING skriver du direkt efter GROUP BY.

```sql
SELECT
    avdelning,
    ROUND(AVG(lon)) AS Snittlon,
    COUNT(lon) AS Antal
FROM larare
GROUP BY
    avdelning
HAVING
    Snittlon > 35000
ORDER BY
    Snittlon DESC
;
```

Resultatet blir nu att alla snittlöner över 35 000 visas.

```text
MySQL [skolan]> SELECT
    ->     avdelning,
    ->     ROUND(AVG(lon)) AS Snittlon,
    ->     COUNT(lon) AS Antal
    -> FROM larare
    -> GROUP BY
    ->     avdelning
    -> HAVING
    ->     Snittlon > 35000
    -> ORDER BY
    ->     Snittlon DESC
    -> ;
+-----------+----------+-------+
| avdelning | Snittlon | Antal |
+-----------+----------+-------+
| ADM       |    47531 |     3 |
| DIDD      |    43730 |     2 |
+-----------+----------+-------+
2 rows in set (0.00 sec)
```

Nu får du lösa 2).



Om WHERE kontra HAVING {#wherehaving}
----------------------------------

Låt oss nu beräkna snittlönen igen, denna gången vill vi se snittlönen per avdelning, för alla som har kompetens 1. Kanske vill vi göra en extra insats på lönen för de som har låg kompetens. Nåja.

Vi lägger till `WHERE kompetens = 1` för att avgränsa vilka rader som används i rapporten.

```sql
SELECT
    avdelning,
    ROUND(AVG(lon)) AS Snittlon,
    COUNT(lon) AS Antal
FROM larare
WHERE
    kompetens = 1
GROUP BY
    avdelning
ORDER BY
    avdelning
;
```

Det ser ut så här. Alla på avdelningen ADM har större kompetens än 1, så de kommer vi inte att se i rapporten.

```text
MySQL [skolan]> SELECT
    ->     avdelning,
    ->     ROUND(AVG(lon)) AS Snittlon,
    ->     COUNT(lon) AS Antal
    -> FROM larare
    -> WHERE
    ->     kompetens = 1
    -> GROUP BY
    ->     avdelning
    -> ORDER BY
    ->     avdelning
    -> ;
+-----------+----------+-------+
| avdelning | Snittlon | Antal |
+-----------+----------+-------+
| DIDD      |    37580 |     1 |
| DIPT      |    27594 |     2 |
+-----------+----------+-------+
2 rows in set (0.00 sec)
```

WHERE väljer ut raderna innan den aggregerande funktionen börjar räkna ut snittlönen. Dessa rader finns alltså inte med i underlaget som skickas till de aggregerade funktionerna.

Du kan se på SELECT-satsen att WHERE klausulen ligger innan GROUP BY, det kan vara en minnesregel som påminner dig om hur SQL-satsen fungerar.

Vi kan nu kombinera detta med HAVING.

Säg att vi vill göra en insats på de avdelningar som har låga löner och vi fokuserar på de lärare som har kompetensen 1.

Vi har redan snittlönen på avdelningarna, för de som har kompetensen 1. Nu behöver vi bara lägga till så att rapporten begränsar och enbart visa de avdelningar där snittlönen är under, låt säga 30 000.

Det kan bli så här, vi lägger till en HAVING.

```sql
SELECT
    avdelning,
    ROUND(AVG(lon)) AS Snittlon,
    COUNT(lon) AS Antal
FROM larare
WHERE
    kompetens = 1
GROUP BY
    avdelning
HAVING
    Snittlon < 30000
ORDER BY
    avdelning
;
```

Resultatet blir så här.

```text
MySQL [skolan]> SELECT
    ->     avdelning,
    ->     ROUND(AVG(lon)) AS Snittlon,
    ->     COUNT(lon) AS Antal
    -> FROM larare
    -> WHERE
    ->     kompetens = 1
    -> GROUP BY
    ->     avdelning
    -> HAVING
    ->     Snittlon < 30000
    -> ORDER BY
    ->     avdelning
    -> ;
+-----------+----------+-------+
| avdelning | Snittlon | Antal |
+-----------+----------+-------+
| DIPT      |    27594 |     2 |
+-----------+----------+-------+
1 row in set (0.00 sec)
```

Det är alltså avdelningen DIPT som har en snittlön på mindre än 30 000 där två lärare har en kompetens av 1.

För att dubbelkolla vilka det är så tjuvkikar vi med en SELECT-sats.

```text
MySQL [skolan]> SELECT
    ->     akronym,
    ->     avdelning,
    ->     lon
    -> FROM larare
    -> WHERE
    ->     kompetens = 1
    ->     AND avdelning = 'DIPT'
    -> ;
+---------+-----------+-------+
| akronym | avdelning | lon   |
+---------+-----------+-------+
| ala     | DIPT      | 27594 |
| gyl     | DIPT      | 27594 |
+---------+-----------+-------+
2 rows in set (0.00 sec)
```

Ah, där har vi de två lärarna som vi kanske borde fokusera på, eller inte.



Uppgifter HAVING {#having}
----------------------------------

Gör nu en egen rapport med GROUP BY och HAVING.

1. Visa per avdelning de kompetenser som finns och hur många anställda det finns per kompetens samt gruppens snittlön, men visa bara för kompetenser som är lägre än 7 och bara om gruppens snittlön är mellan 30 000 - 45 000. Sortera per kompetens i sjunkande ordning.

Ditt svar bör se ut så här.

```sql
+-----------+-----------+-------+-----------+
| avdelning | kompetens | Antal | Snittlön  |
+-----------+-----------+-------+-----------+
| ADM       |         2 |     1 |     30000 |
| DIPT      |         2 |     1 |     45000 |
| DIDD      |         1 |     1 |     37580 |
+-----------+-----------+-------+-----------+
3 rows in set (0.00 sec)
```

Alltså, HAVING är till för att göra urval på aggregerad data och enbart visa de rader som matchar villkoret. WHERE gör urvalet innan det aggregerade datat beräknas.

Minnesregeln "WHERE kommer innan GROUP BY och HAVING kommer efter".



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

---
author: mos
revision:
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Aggregerande funktioner
==================================

Vi jobbar med inbyggda funktioner som kan beräkna värdet över många rader.

Spara dina konstruktioner i filen `dml_agg.sql`.



MIN och MAX {#minmax}
----------------------------------

Använd `MIN()` och `MAX()` för att besvara följande.

1. Hur mycket är den högsta lönen som en lärare har?
2. Hur mycket är den lägsta lönen som en lärare har?



GROUP BY {#groupby}
----------------------------------

Använd de inbyggda aggregerande funktionerna `SUM()`, `COUNT()`, och `AVG()` tillsammans med `GROUP BY`, för att räkna ut  följande:

1. Hur många lärare jobbar på de olika avdelningarna?
2. Hur mycket betalar respektive avdelning ut i lön varje månad?
3. Hur mycket är medellönen för de olika avdelningarna?
3. Hur mycket är medellönen för kvinnor kontra män?


Aggregerande betyder att de räknar samman värden baserat på många rader i tabellen. Dubbelkolla alltid mot din värdemängd, innehållet i tabellerna, om dina svar känns rimliga.

Gör nu följande rapport.

1. Visa snittet på kompetensen för alla avdelningar, sortera på kompetens i sjunkande ordning och visa enbart den avdelning som har högst kompetens.

Ditt svar kan se ut så här.

```sql
+-----------+-----------+
| avdelning | Kompetens |
+-----------+-----------+
| ADM       |    4.0000 |
+-----------+-----------+
1 row in set (0.00 sec)
```

Gör ytterligare en rapport.

1. Visa en avrundad snittlönen (`ROUND()`) grupperad per avdelning och per kompetens, sortera enligt avdelning och snittlön. Ditt svar skall se ut så här.

```sql
+-----------+-----------+-----------+
| avdelning | kompetens | Snittlön  |
+-----------+-----------+-----------+
| ADM       |         7 |     85000 |
| ADM       |         2 |     30000 |
| ADM       |         3 |     27594 |
| DIDD      |         2 |     49880 |
| DIDD      |         1 |     37580 |
| DIPT      |         1 |     32023 |
+-----------+-----------+-----------+
6 rows in set (0.00 sec)
```



HAVING {#having}
----------------------------------

Låt oss titta på snittlönen och säg vi vill räkna ut snittlönen på en avdelning för alla som har en kompetens av en viss nivå. Det gjorde vi ovan. Säg att vi vill se för alla kompetenser som inte är 2. Säg sedan att vi enbart vill visa de rader där snittlönen är större än 30 000.

WHERE väljer ut raderna innan den aggregerande funktionen börjar räkna ut snittlönen. Det kan vi använda till _alla kompetenser som inte är 2_.

HAVING kan jobba på det aggregerade värdet. Det gör ett urval efter att snittlönen räknats ut. Det kan vi använda till _snittlön större än 30 000_.

Ett exempel kan se ut så här.

```sql
mysql> SELECT avdelning, kompetens, ROUND(AVG(lon)) as Snittlön
    -> FROM larare
    -> WHERE kompetens != 2
    -> GROUP BY avdelning, kompetens
    -> HAVING Snittlön > 30000
    -> ORDER BY avdelning, Snittlön DESC
    -> ;
+-----------+-----------+-----------+
| avdelning | kompetens | Snittlön  |
+-----------+-----------+-----------+
| ADM       |         7 |     85000 |
| DIDD      |         1 |     37580 |
| DIPT      |         1 |     32023 |
+-----------+-----------+-----------+
3 rows in set (0.00 sec)
```

Se hur WHERE ligger i SELECT-satsen, innan GROUP BY som innebär att den aggregerande funktionen AVG styrs av, efter att snittlönen är uträknad kan HAVING göra sitt urval.

Gör nu en egen rapport.

1. Visa per avdelning de kompetenser som finns och hur många anställda det finns per kompetens samt gruppens snittlön, men visa bara för kompetenser som är lägre än 7 och sortera per avdelning i stigande ordning och per kompetens i sjunkande ordning.

Ditt svar bör se ut så här.

```sql
+-----------+-----------+-------+-----------+
| avdelning | kompetens | Antal | Snittlön  |
+-----------+-----------+-------+-----------+
| ADM       |         3 |     1 |     27594 |
| ADM       |         2 |     1 |     30000 |
| DIDD      |         2 |     1 |     49880 |
| DIDD      |         1 |     1 |     37580 |
| DIPT      |         1 |     3 |     32023 |
+-----------+-----------+-------+-----------+
5 rows in set (0.00 sec)
```

Alltså, HAVING är till för att göra urval på aggregerad data och enbart visa de rader som matchar villkoret.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

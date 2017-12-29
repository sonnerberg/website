---
author: mos
revision:
    "2017-12-29": "(A, mos) Första versionen, uppdelad av större dokument."
...
Joina tabell
==================================

Vi jobbar vidare med lönerevisionen och joinar två tabeller för att kontrollera hur många % löneökning respektive individ har fått.

Spara den SQL-kod du skriver i filen `dml_join.sql`.

De frågorna vi vill besvara är alltså följande.

1. Visa de lärare som inte har fått en löneökning om minst 3%.
1. Gör en rapport som visar hur många % respektive lärare fick i löneöning.

Låt oss nu lösa dem.



Joina tabeller {#join}
----------------------------------

För att beräkna hur många % löneökning en lärare har fått så behövs föregående lön och den nya lönen, alternativt påslaget i kronor. Vi har den gamla lönen i en tabell och den nya lönen i en annan tabell. Låt oss slå samman dem och visa informatinen från de två tabellerna i en och samma rad.

När vi joinar rader på detta viset så behöver vi ett villkor som säger vilka rader som skall kopplas ihop. I detta fallet kan vi använda akronymen.

Så här joinar vi två tabeller.

```sql
--
-- JOIN
--
SELECT
	l.*,
    p.lon AS "pre-lön",
    p.kompetens AS "pre-kompetens"
FROM larare AS l
	JOIN larare_pre AS p
		ON l.akronym = p.akronym
ORDER BY akronym
;
```

Vi kopplar ihop informationen från två tabeller och matchar de raderna där JOIN-villkoret för ON stämmer.



Rapport från lönerevisionen {#proc}
----------------------------------

Nu är det egentligen rätt enkelt. Nu behöver vi bara jämföra och räkna ut förhållandet mellan den gamla och den nya lönen. Det vore trevligt att se både den procentuella höjningen och höjningen i kronor samt ett varningstecken om löneökningen inte uppnår lägsta nivån om 3%.

Dessutom vill man kunna se nuvarande och gamla kompetensen samt skillnanden mellan dem.

1. Skapa rapporten som visar resultatet enligt nedan.
1. Spara rapporten som en vy `Vlonerevision`.

Så här kan det se ut när man lyckats få ihop det. Först med lönerna.

```sql
mysql> SELECT
    -> akronym, fornamn, efternamn, pre, nu, diff, proc, mini
    -> FROM Vlonerevision
    -> ORDER BY proc DESC
    -> ;
+---------+-----------+------------+-------+-------+-------+-------+------+
| akronym | fornamn   | efternamn  | pre   | nu    | diff  | proc  | mini |
+---------+-----------+------------+-------+-------+-------+-------+------+
| min     | Minerva   | McGonagall | 40000 | 49880 |  9880 | 24.70 | ok   |
| hag     | Hagrid    | Rubeus     | 25000 | 30000 |  5000 | 20.00 | ok   |
| sna     | Severus   | Snape      | 40000 | 45000 |  5000 | 12.50 | ok   |
| fil     | Argus     | Filch      | 25000 | 27594 |  2594 | 10.38 | ok   |
| hoc     | Madam     | Hooch      | 35000 | 37580 |  2580 |  7.37 | ok   |
| dum     | Albus     | Dumbledore | 80000 | 85000 |  5000 |  6.25 | ok   |
| ala     | Alastor   | Moody      | 30000 | 27594 | -2406 | -8.02 | nok  |
| gyl     | Gyllenroy | Lockman    | 30000 | 27594 | -2406 | -8.02 | nok  |
+---------+-----------+------------+-------+-------+-------+-------+------+
8 rows in set (0.00 sec)
```

Sedan tittar vi enbart på kompetensen.

```sql
mysql> SELECT
    -> akronym, fornamn, efternamn, prekomp, nukomp, diffkomp
    -> FROM Vlonerevision
    -> ORDER BY nukomp DESC, diffkomp DESC
    -> ;
+---------+-----------+------------+---------+--------+----------+
| akronym | fornamn   | efternamn  | prekomp | nukomp | diffkomp |
+---------+-----------+------------+---------+--------+----------+
| dum     | Albus     | Dumbledore |       1 |      7 |        6 |
| fil     | Argus     | Filch      |       1 |      3 |        2 |
| min     | Minerva   | McGonagall |       1 |      2 |        1 |
| sna     | Severus   | Snape      |       1 |      2 |        1 |
| hag     | Hagrid    | Rubeus     |       1 |      2 |        1 |
| hoc     | Madam     | Hooch      |       1 |      1 |        0 |
| gyl     | Gyllenroy | Lockman    |       1 |      1 |        0 |
| ala     | Alastor   | Moody      |       1 |      1 |        0 |
+---------+-----------+------------+---------+--------+----------+
8 rows in set (0.01 sec)
```

Se till att din rapport ser exakt likadan ut som min. Ta det som en utmaning. Det kan finnas någon extra svårighet i att lyckas, sök i manualen efter lösningar.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

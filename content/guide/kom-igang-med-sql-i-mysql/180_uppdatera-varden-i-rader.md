---
author: mos
revision:
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Uppdatera värden i rader
==================================

Vi skall använda `UPDATE` för att uppdatera värden i rader och kolumner. Bekanta dig med refman för UPDATE.

Spara det du nu gör i filen `dml_update.sql`.



Grundlön till alla lärare {#grund}
----------------------------------

Så här kan en UPDATE se ut.

```sql
--
-- Update a column value
--
UPDATE larare SET lon = 30000 WHERE akronym = 'gyl';
```

Börja med att se till så att alla lärare har en lön. De som inte har en lön skall ha 30000 i startlön.

Låt mig visa hur du kan göra det. Ovan ser du hur du uppdaterar en lärares lön. Du kan också uppdatera två lärares lön om du vinklar WHERE-delen på följande sätt.

```sql
UPDATE larare
    SET
        lon = 30000
    WHERE
        akronym = 'gyl'
        OR akronym = 'ala'
;
```

Här är ytterligare en likvärdig konstruktion.

```sql
UPDATE larare
    SET
        lon = 30000
    WHERE
        akronym IN ('gyl', 'ala')
;
```

Ett alternativ hade varit att sätta grundlönen för alla lärare som har NULL i lön.

```sql
UPDATE larare
    SET
        lon = 30000
    WHERE
        lon IS NULL
;
```

Oavsett vad så har nu alla lärare en lön. Du kan dubbelkolla att du har samma värden som jag genom att summera deras lönesumma.

```sql
mysql> SELECT SUM(lon) AS 'Lönesumma' FROM larare;
+------------+
| Lönesumma  |
+------------+
|     305000 |
+------------+
1 row in set (0.00 sec)
```

Låt oss även kolla vilka löner lärarna har för tillfället. Det är bra inför nästa övning.

```sql
mysql> SELECT akronym, avdelning, fornamn, kon, lon, kompetens FROM larare ORDER BY lon DESC;
+---------+-----------+-----------+------+-------+-----------+
| akronym | avdelning | fornamn   | kon  | lon   | kompetens |
+---------+-----------+-----------+------+-------+-----------+
| dum     | ADM       | Albus     | M    | 80000 |         1 |
| min     | DIDD      | Minerva   | K    | 40000 |         1 |
| sna     | DIPT      | Severus   | M    | 40000 |         1 |
| hoc     | DIDD      | Madam     | K    | 35000 |         1 |
| fil     | ADM       | Argus     | M    | 25000 |         1 |
| hag     | ADM       | Hagrid    | M    | 25000 |         1 |
| ala     | DIPT      | Alastor   | M    |  NULL |         1 |
| gyl     | DIPT      | Gyllenroy | M    |  NULL |         1 |
+---------+-----------+-----------+------+-------+-----------+
8 rows in set (0.00 sec)
```

Då är vi redo för en övning.



Årlig lönerevision {#revision}
----------------------------------

Det har skett en årlig lönerevision för lärarna, det har varit ett bra år på skolan och lärarna som länge varit underbetalda har fått en lönepott om totalt 6.4% som skall fördelas över samtliga lärare.

Ingen lärare skall få lägre löneökning än 3%.

1. Skriv en SELECT-sats som räknar ut hur mycket pengar som ligger i lönepotten och skall fördelas ut.

Skriv SQL för att genomföra följande ändringar:

1. Albus kompetens är nu 7 och lönen har ökat till 85 000.
2. Minervas lön har ökat med 4 000.
3. Argus har fått ett risktillägg om 2 000 och kompetensen är satt till 3.
4. Gyllenroy och Alastor har hög frånvaro och har fått ett löneavdrag med 3 000.
5. Alla lärare på avdelningen DIDD fick en extra lönebonus om 2%.
6. Alla låglönade kvinnliga lärare, de som tjänar färre än 40 000, fick en lönejustering om extra 3%.
7. Ge Snape, Minerva och Hagrid ett extra lönetillägg om 5 000 för extra arbete de utför åt Albus och öka deras kompetens med +1.
8. Ge alla lärare en ökning om 2.2% men exkludera Albus, Snape, Minerva och Hagrid som redan fått tillräckligt.

Kontrollera nu den nya lönesumman och hur mycket % som lönesumman har ökat genom att göra rapporter med SELECT.

1. Vilken är numer den totala lönesumman?
1. Hur många % har lönesumman ökat från föregående lönesumma?

Så här ser det ut för mig och du skall ha samma resultat.

```sql
mysql> SELECT SUM(lon) AS 'Lönesumma' FROM larare;
+------------+
| Lönesumma  |
+------------+
|     326122 |
+------------+
1 row in set (0.00 sec)

mysql> SELECT SUM(lon)/305000*100-100 AS 'Lönesumma ökning %' FROM larare;
+--------------------+
| Lönesumma ökning % |
+--------------------+
|             6.9252 |
+--------------------+
1 row in set (0.00 sec)
```

Nåväl, det blev lite högre löneökning än planerat, men så må det vara.



### Frågor som ej kan besvaras {#ej}

Fundera nu över hur du kan, eller inte kan, besvara följande frågor genom att göra rapporter till skolans ledning via SELECT.

1. Visa de lärare som inte har fått en löneökning om minst 3%.
1. Gör en rapport som visar hur många % respektive lärare fick i löneöning.

Om du inte kan besvara frågorna, fundera kort över vad du tror hade krävts för att besvara dem. Vi skall besvara dem i en kommande övning, men det kräver lite mer jobb och vi är inte redo för det än.



### Kontrollera att det blev rätt {#kontroll}

Se till att du har samma värden på lönerna som jag har, det underlättar i kommande övningar om du får samma svar som jag fått.

```sql
mysql> SELECT akronym, avdelning, fornamn, kon, lon, kompetens FROM larare ORDER BY lon DESC;
+---------+-----------+-----------+------+-------+-----------+
| akronym | avdelning | fornamn   | kon  | lon   | kompetens |
+---------+-----------+-----------+------+-------+-----------+
| dum     | ADM       | Albus     | M    | 85000 |         7 |
| min     | DIDD      | Minerva   | K    | 49880 |         2 |
| sna     | DIPT      | Severus   | M    | 40880 |         1 |
| hoc     | DIDD      | Madam     | K    | 37580 |         1 |
| hag     | ADM       | Hagrid    | M    | 30000 |         2 |
| ala     | DIPT      | Alastor   | M    | 27594 |         1 |
| fil     | ADM       | Argus     | M    | 27594 |         3 |
| gyl     | DIPT      | Gyllenroy | M    | 27594 |         1 |
+---------+-----------+-----------+------+-------+-----------+
8 rows in set (0.00 sec)
```



### Kontrollera filerna {#filer}

Det sista du gör är att dubbelkolla att du nu kan återskapa och köra allt via filerna i följande ordning.

1. `ddl.sql`
2. `dml_insert.sql`
3. `ddl_migrate.sql`
4. `dml_update.sql`

Det kan se ut så här om du gör det i terminalen (exklusive utskrifter), inklusive en kontroll att lönesumman är korrekt efter lönerevisionen.

```text
$ mysql -uuser -ppass skolan < ddl.sql
$ mysql -uuser -ppass skolan < dml_insert.sql
$ mysql -uuser -ppass skolan < ddl_migrate.sq
$ mysql -uuser -ppass skolan < dml_update.sql
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
+------------+
| Lönesumma  |
+------------+
|     326122 |
+------------+
```

Om du av någon anledning hamnar i trångomål och du vill återställa din databas så kan du även göra det med följande "enradskommando" i terminalen i form av en foor-loop i bash.

```text
$ for f in ddl dml_insert ddl_migrate dml_update; do mysql -uuser -ppass skolan < $f.sql; done
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
+------------+
| Lönesumma  |
+------------+
|     326122 |
+------------+
```

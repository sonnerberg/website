---
author: mos
revision:
    "2017-12-28": "(A, mos) Första versionen, uppdelad av större dokument."
...
Lägg till rader
==================================

Vi lägger till lärare i tabellen.

Lägg SQL-koden, som handlar om att lägga in värden i en tom databas, i filen `dml_insert.sql` och inled filen med en header som berättar vem du är.

```sql
--
-- Insert values into database skolan.
-- By mos for course "XXX".
-- 2017-12-27
--
```

Vi skall skapa 10 lärare och lägg in dem i tabellen med `INSERT`. Du kan använda `SELECT * FROM Larare` för att se  och kontrollera vad tabellen innehåller.

Först lägger vi in ett par lärare med varsin INSERT sats.

```sql
--
-- Add teacher staff 
--
INSERT INTO larare VALUES ('sna', 'DIPT', 'Severus', 'Snape', 'M', 40000, '1951-05-01');
INSERT INTO larare VALUES ('dum', 'ADM', 'Albus', 'Dumbledore', 'M', 80000, '1941-04-01');
INSERT INTO larare VALUES ('min', 'DIDD', 'Minerva', 'McGonagall', 'K', 40000, '1955-05-05');
```

Vi kan lägga in många rader i en och samma INSERT.

```sql
INSERT INTO larare VALUES
    ('hag', 'ADM', 'Hagrid', 'Rubeus', 'M', 25000, '1956-05-06'),
    ('fil', 'ADM', 'Argus', 'Filch', 'M', 25000, '1946-04-06'),
    ('hoc', 'DIDD', 'Madam', 'Hooch', 'K', 35000, '1948-04-08')
;
```

Vi kan lägga in rader, trots att vi ännu inte har all information, men då behöver vi specificera vilka kolumner som vi lägger in datan i.

```sql
INSERT INTO larare
    (akronym, avdelning, fornamn, efternamn, kon, fodd)
VALUES
    ('gyl', 'DIPT', 'Gyllenroy', 'Lockman', 'M', '1952-05-02'),
    ('ala', 'DIPT', 'Alastor', 'Moody', 'M', '1943-04-03')
;
```

Vi har ännu inte satt lönen för dessa två lärare så vi kan inte ge den ett värde. I vårt fall kommer värdet att bli NULL.

Visst, som du kanske ser så kunde vi angivit NULL för kolumnen `lon`, istället för att explicit ange vilka kolumner vi jobbar mot, se det som två olika varianter på hur data kan läggas till, resultatet blir detsamma.

För att säkerställa att du kan köra alla INSERT-kommandon i en sekvens så väljer du att lägga en DELETE-sats överst, så du alltid vet att tabellen är tom, innan du lägger in värden.

```sql
DELETE FROM larare;
```

Dubbelkolla att allt ligger i din fil och att du kan köra alla kommandon i filen, om och om igen.

Verifiera att innehållet i din databas är detsamma som i min.

```sql
mysql> SELECT akronym, avdelning, fornamn, efternamn, kon, lon, fodd FROM larare;
+---------+-----------+-----------+------------+------+-------+------------+
| akronym | avdelning | fornamn   | efternamn  | kon  | lon   | fodd       |
+---------+-----------+-----------+------------+------+-------+------------+
| ala     | DIPT      | Alastor   | Moody      | M    |  NULL | 1943-04-03 |
| dum     | ADM       | Albus     | Dumbledore | M    | 80000 | 1941-04-01 |
| fil     | ADM       | Argus     | Filch      | M    | 25000 | 1946-04-06 |
| gyl     | DIPT      | Gyllenroy | Lockman    | M    |  NULL | 1952-05-02 |
| hag     | ADM       | Hagrid    | Rubeus     | M    | 25000 | 1956-05-06 |
| hoc     | DIDD      | Madam     | Hooch      | K    | 35000 | 1948-04-08 |
| min     | DIDD      | Minerva   | McGonagall | K    | 40000 | 1955-05-05 |
| sna     | DIPT      | Severus   | Snape      | M    | 40000 | 1951-05-01 |
+---------+-----------+-----------+------------+------+-------+------------+
8 rows in set (0.00 sec)
```

Du behöver ha samma innehåll i din databas som jag har, då kommer du att få samma resultat i kommande uppgifter och du får ett facit att kontrollera mot.

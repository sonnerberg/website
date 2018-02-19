---
author: mos
revision:
    "2018-01-03": "(A, mos) Första versionen, uppdelad av större dokument."
...
Joina tabeller
==================================

Nu har vi tre tabeller och möjligheten att koppla ihop dem för att se vilka lärare som ansvarar för vilka kurser och när kurserna är planerade i tiden enligt de kurstillfällen som erbjuds.

Spara den SQL-kod du skriver i filen `dml_join2.sql`.



Joina med WHERE {#where}
----------------------------------

Säg att du vill se alla kurstillfällen tillsammans med kursens namn. För att lyckas med det så måste du joina informationen från tabellerna kurs och kurstillfälle.

Gör en SELECT där du anger både kurs och kurstillfalle. Pröva med följande kommando. Vad blir resultatet?

```sql
--
-- A crossjoin
--
SELECT * FROM kurs, kurstillfalle; 
```

Du får väldigt många rader. Lika många rader som du har rader i Kurs (11 stycken) multiplicerat med antalet rader i Kurstillfälle (10 stycken). Totalt blir det 110 rader, kopplade på ett ej logiskt sätt.

Du har gjort en join, en cross join vilken säger "för varje rad i ena tabellen, matcha mot samliga rader i den andra tabellen".

När man joinar så  brukar man vilka koppla ihop raderna på dett bättre sätt. Vad är det som länkar ihop dessa två tabeller? Kurskoden. Prova med att lägga till en WHERE-sats för att göra länkningen. Så här:

```sql
--
-- Join using WHERE, use alias AS to shorten the statement
--
SELECT *
FROM kurs AS k, kurstillfalle AS kt
WHERE k.kod = kt.kurskod;
```

Om du testar den så får du en utskrift so är lättare att tyda. Ser rapporten rimligt ut? Du borde se lika många rader som det finns matchande träffar mellan tabellen kurs och kurstillfälle (10 rader).

Så här.

```sql
mysql> SELECT *
    -> FROM kurs AS k, kurstillfalle AS kt
    -> WHERE k.kod = kt.kurskod;
+--------+------------------------------------+-------+------+----+---------+--------------+-----------+
| kod    | namn                               | poang | niva | id | kurskod | kursansvarig | lasperiod |
+--------+------------------------------------+-------+------+----+---------+--------------+-----------+
| SVT101 | Försvar mot svartkonster           |     8 | G1N  | 37 | SVT101  | gyl          |         1 |
| SVT101 | Försvar mot svartkonster           |     8 | G1N  | 38 | SVT101  | gyl          |         3 |
| SVT201 | Försvar mot svartkonster           |     6 | G1F  | 39 | SVT201  | ala          |         1 |
| SVT202 | Försvar mot svartkonster           |     6 | G1F  | 40 | SVT202  | ala          |         2 |
| SVT401 | Försvar mot svartkonster           |     6 | G2F  | 41 | SVT401  | sna          |         1 |
| KVA101 | Kvastflygning                      |     4 | G1N  | 42 | KVA101  | hoc          |         1 |
| DJU101 | Skötsel och vård av magiska djur   |     4 | G1F  | 43 | DJU101  | hag          |         3 |
| DRY101 | Trolldryckslära                    |     6 | G1N  | 44 | DRY101  | sna          |         2 |
| DRY102 | Trolldryckslära                    |     6 | G1F  | 45 | DRY102  | sna          |         3 |
| MUG101 | Mugglarstudier                     |     6 | G1F  | 46 | MUG101  | min          |         4 |
+--------+------------------------------------+-------+------+----+---------+--------------+-----------+
10 rows in set (0.00 sec)
```

Det vi ser är alltså samtliga kurstillfällen tillsammans med all data om kursen.



Joina med JOIN..ON {#joinon}
----------------------------------

Det finns ett annat sätt att skriva samma join, men via konstruktionen JOIN..ON. Det ser ut så här.

```sql
--
-- Join using JOIN..ON
--
SELECT *
FROM kurs AS k
	JOIN kurstillfalle AS kt
		ON k.kod = kt.kurskod;
```

För min del föredrar jag denna varianten, jag tycker den blir tydligare i vad jag gör. Välj alla rader från tabellen kurs, joina med tabellen kurstillfalle där kurskoden matchar.

Låt oss nu bygga vidare och joina information även om den kursansvarige läraren. Vi behöver joina tre tabeller, så här kan det se ut.

```sql
--
-- Join three tables
--
SELECT *
FROM kurs AS k
	JOIN kurstillfalle AS kt
		ON k.kod = kt.kurskod
	JOIN larare AS l
		ON l.akronym = kt.kursansvarig;
```

Vi får fortfarande fram 10 rader men nu inklusive alla kolumner från tabellen lärare. En del kolumner är dubblerade, likt akronymen, men det beror ju på att de finns i flera tabeller och vi valde att välja samtliga kolumner via `*`.



Rapporter {#rapporter}
----------------------------------

Nu när vi kan joina alla tabellerna så kan vi definiera ett antal rapporter som kan vara bra att ha för skolan. Sen försöker vi skapa rapporterna.



### Lärares arbetsbelastning {#belastning}

Skriv SELECT för att lösa följande.

Skolan har ett arbetsmiljöansvar för lärarna och vill se över deras planering och lista de lärare som undervisar i kurser med antalet kurstillfällen de ansvarar för.

I rapporten visar du lärarens akronym och namn följt av antalet kurstillfällen som hen är kursanvarig för. Sortera per antal tillfällen och därefter per akronym.

Ditt svar bör se ut så här.

```sql
+---------+--------------------+-------------+
| Akronym | Namn               | Tillfällen  |
+---------+--------------------+-------------+
| sna     | Severus Snape      |           3 |
| ala     | Alastor Moody      |           2 |
| gyl     | Gyllenroy Lockman  |           2 |
| hag     | Hagrid Rubeus      |           1 |
| hoc     | Madam Hooch        |           1 |
| min     | Minerva McGonagall |           1 |
+---------+--------------------+-------------+
6 rows in set (0.00 sec)
```

Det ser ut som Snape är den som jobbar mest med undervisningen.



### Kursansvariges ålder {#age}

Skriv SELECT för att lösa följande.

Skolan är orolig för att lärarna börjar närma sig pensionen och behöver "bytas ut". Skolans ansvariga vill se en rapport över de kurstillfällen som ges, sorterade på åldern för den kursansvarige. Ledningen vill prioritera sitt arbete så de vill bara se de tre kurserna (inte kurstillfällen) där kursansvarige har högst ålder.

I rapporten akronymen, lärarens för och efternamn och lärarens avdelning samt lärarens ålder.

Ditt svar bör se ut så här, får du dubletter av vissa rader så är tipset att se vad SELECT DISTINCT gör.

```sql
+---------+---------------+-----------+--------+
| Akronym | Namn          | Avdelning | Ålder  |
+---------+---------------+-----------+--------+
| ala     | Alastor Moody | DIPT      |     74 |
| hoc     | Madam Hooch   | DIDD      |     69 |
| sna     | Severus Snape | DIPT      |     66 |
+---------+---------------+-----------+--------+
3 rows in set (0.00 sec)
```

Nu har du fått fram de tre namnen som undervisar på kurser och är närmast pensionen, men vilka kurser är de ansvariga för? Hur många och vilka kurser handlar det om?

I rapporten visa kurskoden, kursens namn, akronymen, lärarens för och efternamn.

Det bör se ut så här när du svarar.

```sql
+---------+---------------------------+------------+---------+---------------+
| Kurskod | Kursnamn                  | Läsperiod  | Akronym | Namn          |
+---------+---------------------------+------------+---------+---------------+
| SVT201  | Försvar mot svartkonster  |          1 | ala     | Alastor Moody |
| SVT202  | Försvar mot svartkonster  |          2 | ala     | Alastor Moody |
| KVA101  | Kvastflygning             |          1 | hoc     | Madam Hooch   |
| SVT401  | Försvar mot svartkonster  |          1 | sna     | Severus Snape |
| DRY101  | Trolldryckslära           |          2 | sna     | Severus Snape |
| DRY102  | Trolldryckslära           |          3 | sna     | Severus Snape |
+---------+---------------------------+------------+---------+---------------+
6 rows in set (0.00 sec)
```

Nu har ledningen fått hjälp i sin planering inför nyrekrytering av lärare.



Vy för att förenkla {#vy}
----------------------------------

Det verkar som rapportunderlaget vi använder är bra, låt oss skapa en vy av grundrapporten. Den kanske kan komma tillhanda lite senare. Döp vyn till `Vplanering`.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

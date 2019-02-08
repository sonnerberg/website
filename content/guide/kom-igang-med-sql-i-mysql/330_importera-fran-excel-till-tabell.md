---
author: mos
revision:
    "2019-02-09": "(C, mos) Förtydligade felsökning av load local infile."
    "2019-01-29": "(B, mos) Uppdaterad med felhantering och hur man fixar det."
    "2018-01-02": "(A, mos) Första versionen, uppdelad av större dokument."
...
Importera från Excel till Tabell
==================================

Ibland sitter man i Excel (eller liknande verktyg) och har en lång lista på saker som man vill föra in i en databastabell. Hur gör man det på ett snabbt och enkelt sätt?

Låt oss fylla tabellerna för kurs och kurstillfalle med innehåll genom att hämta det från ett format som Excel kan exportera.

Spara den SQL-kod du skriver i filen `dml_insert_csv.sql`.

Tjuvkika på refmanualen [LOAD DATA INFILE](https://dev.mysql.com/doc/refman/8.0/en/load-data.html) så kan du se vad det är vi skall göra.



Excelark för kurs och kurstillfälle {#excel}
----------------------------------

Det finns ett Excel-ark du kan använda för att hämta innehållet till tabellerna kurs och kurstillfälle. Börja med att studera [excel-arket och dess olika flikar](https://goo.gl/x7w9tA). Du kan se innehållet för respektive tabell i varsin flik.

[FIGURE src=image/snapvt18/excel-kurs.png caption="Blivande innehåll i en databastabell, men för tillfället i Excel."]

Första fliken innehåller två länkar via vilka du kan ladda ned respektive fliks innehåll som en CSV-fil. CSV står för Comma Separated Value och är ett vanligt format när man exporterar från  och/eller importerar till Excel.

Ladda ned respektive CSV-fil och spara som `kurs.csv` och `kurstillfalle.csv`. Du kan också finna de båda filerna i ditt kursrepo under `example/skolan`.

Innehållet i filerna är rader som avslutas med `\n` och fält som är komma-separerade och omsluts med ett `"` tecken.

Filen `kurs.csv` kan se ut så här om du öppnar den i din texteditor.

```text
"Kod","Namn","Poäng","Nivå"
"AST101","Astronomi","5","G1N"
"SVT101","Försvar mot svartkonster","8","G1N"
"SVT201","Försvar mot svartkonster","6","G1F"
"SVT202","Försvar mot svartkonster","6","G1F"
"SVT401","Försvar mot svartkonster","6","G2F"
"KVA101","Kvastflygning","4","G1N"
"DJU101","Skötsel och vård av magiska djur","4","G1F"
"DRY101","Trolldryckslära","6","G1N"
"DRY102","Trolldryckslära","6","G1F"
"VAN101","Förvandlingskonst","5","G1F"
"MUG101","Mugglarstudier","6","G1F"
```

Den översta raden är bara för information, det är resterande rader som vi vill föra in i databastabellen, rad för rad, kolumn för kolumn.



LOAD DATA INFILE {#into}
----------------------------------

När vi vet formatet på filen så kan vi översätta detta till instruktioner till LOAD DATA INFILE och berätta hur filens innehåll skall tolkas och läsas in.

Kommandot LOAD DATA INFILE kommer då att läsa rad för rad från filen och göra om det till INSERT satser.

I koden nedan används en relativ sökväg till filen `kurs.csv`, det fungerar om du startar din terminalklient i samma katalog där filen ligger.

Låt oss studera koden _innan vi kör den_.

```sql
--
-- Insert into kurs 
--
DELETE FROM kurs;

LOAD DATA LOCAL INFILE 'kurs.csv'
INTO TABLE kurs
CHARSET utf8
FIELDS
	TERMINATED BY ','
    ENCLOSED BY '"'
LINES
	TERMINATED BY '\n'
IGNORE 1 LINES
;

SELECT * FROM kurs;
```

Vi anger sökvägen till filen och berättar att teckenkodningen är UTF-8. Fälten i filen är separerade med `,` och omslutna med `"`. Varje rad separeras med `\n` och den första raden som innehåller namnen på kolumnerna väljer vi att ignorera.

Då kan vi köra koden.



Exekvera LOAD DATA INFILE {#execinto}
----------------------------------

Det kan vara lite klurigt att få LOAD DATA INFILE att fungera, det är normalt avstängt 

Eventuellt får du nu ett felmeddelande.

> "ERROR 1148 (42000): The used command is not allowed with this MySQL version"

Det kan bero både på terminalklienten och på din databasserver. Låt oss lösa båda dessa potentiella problem.



### Terminalklienten {#fixterminal}

Felet kan bero på att du inte startade klienten mysql med optionen `--local-infile=1`.

```text
$ mysql -uuser -ppass --local-infile=1 skolan 
```

Du kan också lägga till denna inställning i din `$HOME/.my.cnf` som alltid tillåter dig använda LOAD DATA INFILE.

```text
[mysql]
loose-local-infile = 1
```

Du kan verifiera att din fil `.my.cnf` ger rätt default inställningar till terminalklienten.

```text
$ mysql --print-defaults
mysql would have been started with the following arguments:
--loose-local-infile=1
```

Det är flera inställningar som skrivs ut, de kommer från din `.my.cnf`. Det är specifikt inställningen för `--loose-local-infile=1` som vi vill se.



### Databasservern {#fixserver}

Felet 1148 kan också bero på att LOAD LOCAL INFILE är avstängt på databasservern och vi behöver sätta på det.

Vi använder följande kommando för att kolla om LOCAL INFILE är på eller av.

```sql
SHOW VARIABLES LIKE 'local_infile';
```

Hos mig var den "Off".

```text
mysql> SHOW VARIABLES LIKE 'local_infile';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| local_infile  | OFF   |
+---------------+-------+
1 row in set (0.00 sec)
```

Då sätter jag på den.

```sql
SET GLOBAL local_infile = 1;
```

Nu bör den vara "On".

```text
mysql> SHOW VARIABLES LIKE 'local_infile';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| local_infile  | ON    |
+---------------+-------+
1 row in set (0.00 sec)
```

Nu kan jag köra mitt kommando med LOAD DATA INFILE.

Man får vara uppmärksam på eventuella varningar man kan få när filens innehåll och fält inte kan mappas in i tabellen. Men det bör gå bra för dig. Får du problem så kollar du hur du skapade tabellen kurs och ser om innehållet i CSV-filen mappar mot den strukturen, dubbelkolla till exempel längden på kolumnen och längden på texten i csv-filen.



Matcha kolumner {#kol}
----------------------------------

När antalet kolumner i CSV-filen inte mappar exakt mot strukturen i tabellen så kan man, likt vid INSERT, ange vilka kolumner som skall mappas.

När du läser in innehållet till tabellen kurstillfälle som märker du att det inte finns något fält som matchar det automatgenererade id:et i tabellen. Du behöver alltså ange vilka kolumner som skall få sina värden från CSV-filen.

Refmanualen visar hur man gör. Du kan göra det i slutet LOAD DATA, så här.

```sql
LOAD DATA LOCAL INFILE '/home/mos/dbwebb-kurser/databas/skolan/kurstillfalle.csv'
-- resten av uttrycket
IGNORE 1 LINES
(kurskod, kursansvarig, lasperiod)
;
```

Dubbelkolla att du inte får varningar när du läser in datan och kika med SELECT att innehållet i tabellerna motsvarar det som finns i CSV-filerna.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

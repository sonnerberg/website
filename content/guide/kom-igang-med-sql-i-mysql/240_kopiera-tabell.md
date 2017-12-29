---
author: mos
revision:
    "2017-12-29": "(A, mos) Första versionen, uppdelad av större dokument."
...
Kopiera tabell
==================================

Vi skall skapa en ny tabell genom att kopiera en befintlig tabell.

Spara den SQL-kod du skriver i filen `ddl_copy.sql`.

När vi gjorde [övningen med UPDATE](./uppdatera-varden-i-rader) så var det ett par frågor vi inte kunde svara på.

1. Visa de lärare som inte har fått en löneökning om minst 3%.
1. Gör en rapport som visar hur många % respektive lärare fick i löneöning.

Men, om vi hade tagit en backup av tabellen och tabellens data, innan vi utföre lönerevisionens alla UPDATE-satser, så hade vi haft en möjlighet att besvara frågorna.

Låt se om vi kan lösa det nu.



Återskapa databasen innan lönerevisionen {#pre}
----------------------------------

Först behöver vi återskapa databasen med dess innehåll innan vi utförde lönerevisionen. Här är två rader som sätter upp databasen och kontrollerar att lönesumman är rätt.

```text
$ for f in ddl dml_insert ddl_migrate; do mysql -uuser -ppass skolan < $f.sql; done
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
+------------+
| Lönesumma  |
+------------+
|     245000 |
+------------+
```

Bra, då är vi i läget precis innan lönerevisionen.



Kopiera tabell {#copy}
----------------------------------

Så, alla uppdateringar i lönerevisionen ligger i filen `dml_update.sql`, men innan vi kör dem så tar vi en kopia, eller backup, av tabellen.

```sql
--
-- Make copy of table
--
DROP TABLE IF EXISTS larare_pre;
CREATE TABLE larare_pre LIKE larare;
INSERT INTO larare_pre SELECT * FROM larare;
SELECT SUM(lon) AS 'Lönesumma' FROM larare;  
```

Principen är att skapa en ny tabell med den gamla som mall. Sedan kan man inserta rader i den nya tabellen genom att selecta dem från den gamla tabellen.

Innan vi går vidare så har vi två lärare som ännu inte fått lön. Vi ger dem deras grundlön innan vi går vidare, det var ju en del av arbetet inför lönerevisionen.

```sql
UPDATE larare_pre
    SET lon = 30000
    WHERE
        lon IS NULL
;
```

Då kan vi göra lönerevision.



Utför lönerevisionen {#revision}
----------------------------------

Då utför vi lönerevisionen genom att köra filen `dml_update.sql`.

```text
$ mysql -uuser -ppass skolan < dml_update.sql
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
+------------+
| Lönesumma  |
+------------+
|     330242 |
+------------+
```

Vi kan dubbelkolla lönesummar i vår kopierade tabell.

```text
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare_pre;"
+------------+
| Lönesumma  |
+------------+
|     245000 |
+------------+
```

Perfekt, så långt.

Nu vore det trevligt om vi kunde slå samman raderna från de båda tabellerna och få en visuell översikt av resultatet.

Vi tar det i nästa stycke.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

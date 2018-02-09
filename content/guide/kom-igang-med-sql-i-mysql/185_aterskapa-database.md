---
author: mos
revision:
    "2018-02-09": "(A, mos) Tillagd för att fokusera på hur man återställer databasen."
...
Återställ databasen
==================================

Vi skall se hur vi kan återställa databasen genom att köra de SQL-skript som sätter upp databasen, skapa tabellerna, lägger till rader och manipulerar innehållet.

Spara det du nu gör i filen `reset_part1.bash`.

Vi vill återställa databasen genom att köra ett kommando, så här.

```text
$ bash reset_part1.bash
```



Vilka filer behövs köras? {#filer}
----------------------------------

Följande är de filer som behöver köras för att återställa databasen.

| Fil               | Vad gör den?         |
|-------------------|----------------------|
| `setup.sql`       | Kör som root för att skapa om databasen och skapa användaren user:pass. |
| `ddl.sql`         | Skapa tabellen för lärare. |
| `dml_insert.sql`  | Lägg till rader i tabellen lärare. | 
| `ddl_migrate.sql` | Alter table lärare och lägg till kompetensen. |
| `dml_update.sql`  | Utför lönerevisionen. |

Det kan se ut så här om du kör varje SQL-skript i terminalen (exklusive utskrifter). Notera att setup.sql måste köras som din root-användare och resten körs som användaren user.

```text
mysql -uroot -p skolan < setup.sql
mysql -uuser -ppass skolan < ddl.sql
mysql -uuser -ppass skolan < dml_insert.sql
mysql -uuser -ppass skolan < ddl_migrate.sq
mysql -uuser -ppass skolan < dml_update.sql
```

När du har kört igenom alla så kan du dubbelkolla att du har den korrekta lönesumman.

```text
$ mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
+------------+
| Lönesumma  |
+------------+
|     330242 |
+------------+
```

Låt se hur vi kan samla dessa kommandon till ett bash-skript.


Ett bash-skript för många kommandon {#bash}
----------------------------------

Ett bash-skript är en textfil med kommandon som kan exekveras. De kommandon du skriver i terminalen kan du skriva i ett bash-skript. Inuti ett bash-skript kan du även skriva programmeringskod, variabler, loopar och funktioner. Bash är alltså ett programmeringsspråk i sig, man brukar kalla den typen av programmeringsspråk för "skriptspråk".

Grunden till bash-skriptet ser ut så här.

```text
#!/usr/bin/env bash
#
# Recreate and reset the database to be as after part I.
#
echo ">>> Check Lönesumman = 330242."
mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
```

Den första raden kallas shebang och säger att alla raderna i filen skall exekveras med kommandot bash. Brädgården på rad 2-4 `#` är kommentar och echo skriver ut texten.

Den sista raden exekverar en SQL-sats i terminalklienten mysql och skriver ut resultatet. Det kan se ut så här när man kör programmet via kommandot `bash reset_part1.bash`. Tecknet `$` representerar din prompt.

```text
$ bash reset_part1.bash 
>>> Check Lönesumman = 330242.
+------------+
| Lönesumma  |
+------------+
|     330242 |
+------------+
```

Bra, då lägger vi in samtliga kommandon i skriptet.



Komplett skript för att återställa databasen {#reset}
----------------------------------

Här kan du se hur mitt skript ser ut, du kan använda det rakt av och det bör fungera för dig. Gå igenom skriptet och se att det kör alla SQL-filerna för att återställa databasen. I slutet kör den SQL-satsen som hjälper dig att dubbelkolla att lönesumman ser korrekt ut.

```text
#!/usr/bin/env bash
#
# Recreate and reset the database to be as after part I.
#
echo ">>> Reset skolan to after part 1"
echo ">>> Recreate the database"
mysql -uroot -p skolan < setup.sql > /dev/null

file="ddl.sql"
echo ">>> Create tables ($file)"
mysql -uuser -ppass skolan < $file > /dev/null

file="dml_insert.sql"
echo ">>> Insert into larare ($file)"
mysql -uuser -ppass skolan < $file > /dev/null

file="ddl_migrate.sql"
echo ">>> Alter table larare ($file)"
mysql -uuser -ppass skolan < $file > /dev/null

file="dml_update.sql"
echo ">>> Lönerevision larare ($file)"
mysql -uuser -ppass skolan < $file > /dev/null

echo ">>> Check Lönesumman = 330242."
mysql -uuser -ppass skolan -e "SELECT SUM(lon) AS 'Lönesumma' FROM larare;"
```

Konstruktionen `file="filnamnet"` är en variabel som sedan nås via `$file`.

Konstruktionen `> /dev/null` gör så att alla utskrifter inte syns, det enda som kommer synas är de eventuella felmeddelande som skripten ger. Felmeddelanden vill du se för att kunna felsöka.

När jag kör mitt program får jag följande utskrift, du bör få motsvarande.

```text
$ bash reset_part1.bash 
>>> Reset skolan to after part 1
>>> Recreate the database
Enter password: 
>>> Create tables (ddl.sql)
>>> Insert into larare (dml_insert.sql)
>>> Alter table larare (ddl_migrate.sql)
>>> Lönerevision larare (dml_update.sql)
>>> Check Lönesumman = 330242.
+------------+
| Lönesumma  |
+------------+
|     330242 |
+------------+
```

Du får gärna modifiera och vidarutveckla ditt bash-skript. Men det räcker om det fungerar som jag visar ovan.

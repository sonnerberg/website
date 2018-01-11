---
author: mos
revision:
    "2018-01-09": "(A, mos) Första versionen, uppdelad av större dokument."
...
Ta backup av databasen
==================================

Vi skall ta en backup av databasen med verktyget mysqldump. Resultatet blir en testfil med SQL-kommandon som är både DDL för att skapa databas och tabeller samt DML för att lägga till innehållet i tabellerna.

Spara din backup i filen `skolan.sql`.

Vi får alltså hela vår databas exporterad till SQL-kommandon i en behändig fil som enkelt går att flytta mellan olika system.

Du kan läsa om programmet [mysqldump i manualen](https://dev.mysql.com/doc/refman/5.7/en/mysqldump.html).



Var ligger kommandot? {#var}
----------------------------------

På min dator kan jag använda `which mysqldump` för att se var kommandot finns. Du bör finna det på samma plats där kommandot mysql finns.

```bash
$ which mysql
/usr/bin/mysql

$ which mysqldump
/usr/bin/mysqldump
```

På din dator kan de ligga på en annan plats, beroende av hur du installerat MySQL. Kommandona kan till exempel vara en del av din installation för XAMPP.

När du hittar programmet kan du dubbelkolla att det går att köra genom att visa dess version.

```text
$ mysqldump --version
mysqldump  Ver 10.13 Distrib 5.6.30, for debian-linux-gnu (x86_64)
```

Då är vi redo.



Skapa backupfil {#backup}
----------------------------------

Låt oss ta en backup på databasen skolan.

```bash
$ mysqldump skolan > skolan.sql
```

Nu finns alla SQL-kommandon som kan återskapa databasen skolan i filen `skolan.sql`.

Spara filen som en backup, såna är bra att ha.



Skapa en kopia av en databas {#kopia}
----------------------------------

Låt säga att du nu vill återskapa databasen skolan, men du vill lägga den i en helt annan databas, som extra backup.

Då skapar du en ny databas och gör grant på en user till databasen. Sedan kör du filen för att återskapa alla tabeller och deras innehåll.

```bash
# Låt säga att du har skapat en ny databas som heter skolan1
$ mysql -uuser -ppass skolan1 < skolan.sql
```

Nu har du en kopia av databasen skolan, i skolan1.

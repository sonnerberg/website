---
author: mos
revision:
    "2018-01-03": "(A, mos) Första versionen, uppdelad av större dokument."
...
Ta backup av databasen
==================================

Vi skall ta en backup av databasen med verktyget mysqldump. Resultatet blir en testfil med SQL-kommandon som är både DDL för att skapa databas och tabeller samt  DML för att lägga till innehållet i tabellerna.

Vi får alltså hela vår databas exporterad till SQL-kommandon i en behändig fil som enkelt går att flytta mellan olika system.



Skapa backupfil {#backup}
----------------------------------




Skapa en kopia av en databas {#kopia}
----------------------------------

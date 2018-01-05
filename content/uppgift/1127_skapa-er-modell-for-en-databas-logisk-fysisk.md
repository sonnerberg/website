---
author: mos
category:
    - databas
    - er-modellering
    - kursen dbjs
    - kursen databas
revision:
    "2018-01-05": (A, mos) Första utgåvan.
...
Skapa ER-modell för en databas (logisk/fysisk)
==================================

Du skall jobba med databasmodellering och skapa en ER-modell av en databas som du själv väljer efter ett par förslag som erbjuds.

Detta är sista delen av uppgiften och du skall utföra den logiska och den fysiska modelleringsfasen.

Du kan lösa uppgiften genom att jobba enskilt eller i grupp om max 3 deltagare. Var och en gör sin egen inlämning, även om man jobbar i grupp.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Kokbok för databasmodellering](kunskap/kokbok-for-databasmodellering)" som ger dig metoden för hur du skall jobba med modelleringen.

Du har löst första delen av uppgiften i "[Skapa ER-modell för en databas (konceptuell)](uppgift/skapa-er-modell-for-en-databas-konceptuell)".

Du har en befintlig modell med konceptuell modellering som du kan jobba vidare på.



Introduktion {#intro}
-----------------------

Du skall jobba vidare på din ER-modell och fortsätta dokumentera vad du gör i ditt dokument.

Du skall nu utföra den logiska modelleringsfasen och den fysiska modelleringsfasen.

Du kan behöva fräscha upp minnet om [vad det är du skall modellera](uppgift/skapa-er-modell-for-en-databas-konceptuell#valj).

Du kan friska upp minnet om vad det stod om [ritverktyg i föregående uppgift](uppgift/skapa-er-modell-for-en-databas-konceptuell#ritverktyg). MySQL Workbench kan vara ett bra alternativ för denna uppgift. Speciellt eftersom du då får stöd i generering av SQL DDL.

Se till att spara SQL DDL i separat `.sql` fil så att du kan skapa tabeller i ett senare skede.

I ditt slutliga modelleringsdokument kan du lägga till SQL DDL-koden som appendix.

Varje steg du gör (enligt kokboken) skall du dokumentera i ett dokument som du lämnar in som pdf. När du är klar finns samtliga delsteg dokumenterade i ditt dokument.



Krav {#krav}
-----------------------

1. Bygg vidare på ditt befintliga dokument och din konceptuella modell.

1. Skapa en ny sida med rubrik "Logisk modell" och utför och dokumentera alla delsteg för den logiska modelleringsfasen.

1. Skapa en ny sida med rubrik "Fysisk modell" och utför och dokumentera alla delsteg för den fysiska modelleringsfasen. Berätta hur du gjorde för att skapa SQL DDL (per hand eller genererade). SQL DDL lägger du som ett Appendix i ditt dokument, för information.

1. Din SQL DDL sparar du även som egen fil i `ddl.sql`. Denna filen skall inte innehålla SQL för att skapa själva databasen.

1. Skapa en separat fil `setup.sql` som skapar databasen `eshop` (CREATE DATABASE) och lägger till en användare `user` med lösenordet `pass` (GRANT) som har fulla rättigheter på databasen.

1. Försäkra dig om att din SQL DDL (`setup.sql`, `ddl.sql`) fungerar och skapar den databasen och de tabellerna du vill ha.

1. Försäkra dig själv om att din databasmodell kommer att klara av att hantera ordrar och fakturer. Se det som ditt eget sätt att verifiera att din modell fungerar.

1. Spara ditt dokument som pdf i katalogen du jobbar.

1. När du är klar så publicerar du ditt kursrepo.

```bash
# Ställ dig i kurskatalogen
dbwebb publish me
```



Extrauppgift {#extra}
-----------------------

Det finns ingen extrauppgift.



Tips från coachen {#tips}
-----------------------

Lycka till och ställ frågor i forumet om du behöver hjälp!

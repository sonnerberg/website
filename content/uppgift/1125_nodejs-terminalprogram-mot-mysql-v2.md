---
author: mos
category:
    - javascript
    - nodejs
    - mysql
    - kursen dbjs
    - kursen databas
revision:
    "2017-12-29": (A, mos) Uppdaterad version från tidigare dokument.
...
Node.js terminalprogram mot MySQL (v2)
==================================

Du skall bygga terminalprogram i Node.js som skapar rapporter och söker i en MySQL databas.


<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom första delarna av guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql/grunderna)".

Du har jobbat igenom artikeln "[MySQL och Node.js (v2)](kunskap/mysql-och-nodejs-v2)".



Introduktion {#intro}
-----------------------

Du skall skriva ett par enklare skript som söker i databasen "skolan" och presenterar rapporter från dess innehåll.



Krav {#krav}
-----------------------


1. Kopiera in filen `allan.sql` till katalogen du arbetar i. Använd filen för att skapa de tabeller som behövs med det innehåll som förväntas.

1. Skapa ett terminalkommando som heter allan och startas via `./allan`. Programmet skall fungera med option `--version` och `--help`.

1. När du startar `./allan` så skall du kunna skicka med options som säger till vilken databas programmet skall koppla upp sig och med vilken användare och lösenord. Det kan se ut ut så här `./allan --host localhost --user mos --password XXX --database mos`.

1. I ditt program, skapa ett menyval "products" som visar vilka produkter Allan säljer. Sortera dem i bokstavsordning.

1. Skapa ett menyval "inventory1" som visar namnet på produkten och hur många som finns i det lokala lagret (inventory). Sortera på den produkt som finns flest av. Om produkten inte finns i lager så skall den inte visas.

1. Skapa ett menyval "inventory2" som gör som "inventory1" men visar alla produkter, även om de inte finns i det lokala lagret.

1. Skapa ett menyval "supplier1" som visar namnet på produkten och hur många som finns i det centrala lagret (supplier). Sortera på den produkt som finns flest av. Om produkten inte finns i lager så skall den inte visas.

1. Skapa ett menyval "supplier2" som gör som "supplier1" men visar alla produkter, även om de inte finns i det centrala lagret.

1. Skapa ett menyval "all" som visar de produkter som antingen finns i det lokala lagret, eller hos leverantörens centrala lagret. Visa hur många som finns i respektive lager. Visa produkten även om den inte finns i något av lagren. Sortera per bokstavsordning.

1. Skapa ett menyval "only" som fungerar som "all" men visar de produkter som finns både i det lokala lagret och i leverantörens centrala lagret.

1. Skapa ett menyval "menu" som visar information om samtliga menyval.

1. Använd Promise så att din prompt skrivs ut på rätt ställe.

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate terminal
#dbwebb publish terminal
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns ingen extra uppgift.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!



Tidigare versioner {#tidigare}
-----------------------

Node.js terminalprogram mot MySQL

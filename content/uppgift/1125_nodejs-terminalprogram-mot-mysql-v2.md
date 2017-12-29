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

Du skall bygga terminalprogram med JavaScript i Node.js som skapar rapporter och söker i en MySQL databas.


<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom första delarna av guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql/grunderna)".

Du har jobbat igenom artikeln "[MySQL och Node.js (v2)](kunskap/mysql-och-nodejs-v2)".



Introduktion {#intro}
-----------------------

Du skall skriva ett par enklare skript som söker i databasen "skolan" och presenterar rapporter från dess innehåll.

Du har i guiden "Kom igång med SQL i MySQL" skapat SQL-satser som du nu skall återanvända och lägga in i en terminalklient som du bygger med JavaScript och Node.js.



Krav {#krav}
-----------------------

1. Inloggningsdetaljer till databasen skall sparas i `config.json` och läsas in av respektive fil.

1. Skapa filen `skolan.js` och lägg all kod i den filen. Strukturera din kod i funktioner.

1. Skapa filen `lonerevision.js` och lägg all kod i den filen. Strukturera din kod i funktioner.

1. Skapa filen `kompetens.js` och lägg all kod i den filen. Strukturera din kod i funktioner.

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate terminal1
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Gör följande om du har tid och ro.

1. Studera koden i dina filer, finns det delar av koden som du kan lyfta ut i externa filer/moduler och dela på liknande sätt som `config.json` delas mellan programmen?



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!



Tidigare versioner {#tidigare}
-----------------------

En tidigare utgåva av en ungefärlig liknande uppgift finns i "[Node.js terminalprogram mot MySQL](uppgift/nodejs-terminalprogram-mot-mysql)".

Denna uppdaterade utgåva är dock helt omarbetad. 

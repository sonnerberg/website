---
author: mos
category:
    - javascript
    - nodejs
    - mysql
    - express
    - er-modellering
    - kursen databas
revision:
    "2019-02-18": "(prel, mos) Första utgåvan, sammanslagen av tre andra uppgifter och vidarutvecklad."
...
Bygg databasen till en Eshop (del 2)
==================================

Du har utfört en ER-modellering av en databas för en Eshop som du också har påbörjat att implementera i en databas med en webbklient och en terminalklient.

Du skall nu jobba vidare med implementationen av din databas.

Du kan utföra denna uppgift enskilt, eller i samma grupp som du tidigare jobbat i.

<!--more-->

Alla lämnar in en egen lösning i sitt kursrepo, även om man jobbat i grupp.



Förkunskaper {#forkunskaper}
-----------------------

Du har utfört uppgiften "[Bygg databasen till en Eshop (del 1)](uppgift/bygg-databasen-till-en-eshop-del-1)".

Du har utfört övningarna "[Egendefinierade funktioner i databas](kunskap/egen-definierade-funktioner-i-databas)" och "[Index och prestanda i MySQL](kunskap/index-och-prestanda-i-mysql)" så du vet innebörden av egendefinierade funktioner och index.



Introduktion {#intro}
-----------------------

Du bygger vidare på det du gjorde i del 1 av uppgiften. Ta en kopia av din gamla katalog och fortsätt utveckla.

[WARNING]

**Arbete pågår**

Uppgiftens krav håller på att konstrueras.

[/WARNING]

KRAV om egendefinierade funktioner.

KRAV om index.

<!--
När du fyller databasen med innehåll så kan du utgå från följande Excelark, "[Databasen eshop, del 1, innehåll till tabeller](https://docs.google.com/spreadsheets/d/1yz0-C1SFYvNw_mN5CrZd9QrjKUXqKv3OhSlGUci8Mls/edit?usp=sharing)". Ta en egen kopia av arket och därefter kan du fritt modifiera innehållet i tabellerna och vilka kolumner som finns.
-->



Krav {#krav}
-----------------------

Uppgiften är indelad i tre huvudsakliga delar, en generell del inklusive databasdetaljer, en för webbklienten och en för terminalklienten.



### Generella krav {#gen}

Att göra.

<!--
1. Inloggningsdetaljer till databasen skall sparas i `config/db/eshop.json`.

1. SQL-filer lägger du i `sql/eshop`. Skapa filen `setup.sql` för att skapa databasen och användaren. Låt din databas heta `eshop` och skapa användaren `user:pass` som tidigare.

1. Skapa filen `ddl.sql` där du samlar all kod som skapar tabeller och vyer.

1. Skapa filen `insert.sql` med SQL-kod för att lägga in 5 produkter, 2 produktkategorier och 3 kunder.
-->



### Webbklient {#webb}

Att göra.

<!--
1. Skapa en webbklient med Express. Servern startas via `node index.js`.

1. I webbklienten, skapa routen `/eshop/index` som visar en välkomstssida med header, footer och navigering mellan sidorna. Alla sidor skall ha samma sidlayout och det skall gå att klicka sig fram mellan sidorna, via navigeringen.

1. I webbklienten, skapa en sida `/eshop/products` som visar en tabell över de produkter som finns.
-->



### Terminalklient {#term}

Att göra.

<!--
1. Bygg ett terminalprogram och spara main-funktionen i `cli.js`. Eventuell övrig kod lägger du i moduler under katalogen `src/`. Terminalprogrammet skall startas med `node cli.js`.

1. Ditt terminalprogram skall fungera som en oändlig kommandoloop där man kan skriva in kommandon som programmet utför. Det skall finnas ett kommando `menu` som visar menyn med samtliga kommandon. När man skriver kommandot `exit` skall programmet avslutas.

1. I terminalprogrammet, skapa kommandot `products` som visar en tabell över de produkter som finns.

-->



### Lämna in {#lamnain}

1. När du är helt klar och har testkört ditt system mot din egen databas, så tar du en backup av databasen med mysqldump och sparar i `sql/eshop/backup.sql`. Verifiera att backup-filen fungerar och tänk att rättaren kan ladda denna databas för att testköra mot ditt system.

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate eshop2
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



<!--
Extrauppgift {#extra}
-----------------------

Gör följande om du har tid och ro.

-->



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

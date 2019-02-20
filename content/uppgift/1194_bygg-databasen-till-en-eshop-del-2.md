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

1. Du behöver uppfylla de krav du hade i del 1 av uppgiften.

1. En order skall ha kolumner med tidsstämplar för när ordern skapades (1), när ordern uppdaterades (2), när ordern beställdes (3).
  
1. Skapa en egendefinierad funktion som tar ett argument av en tidsstämpel för när ordern beställdes. Om tidsstämpeln är NULL skall returneras "Pågående", annars returneras "Beställd".

1. Databasen skall innehålla INDEX på minst tre platser, förutom primärnycklar.  



### Webbklient {#webb}

1. Du behöver uppfylla de krav du hade i del 1 av uppgiften.

1. Skapa en sida `/eshop/customer` som visar en översikt av de kunder som finns. Visa (minst) kundens id, namn, adress, telefon.

1. Bygg stöd för att en kund kan skapa en order.

1. Bygg stöd för att en kund kan lägga till produkter och antal (orderrader) till en order.

1. En order har status som kan vara "pågående" eller "beställd". När kunden beställt alla delar i ordern så kan kunden ändra status på ordern till "beställd". (TIPS TIMESTAMP)

1. Skapa en sida `/eshop/order` som visar en översikt av de ordrar som finns. Visa (minst) order id, order datum, kundens id, totalt antal orderrader den innehåller, dess status ("pågående"/"beställd").

1. Om man klickar på en order kan man se en översikt av dess orderrader.



### Terminalklient {#term}

1. Du behöver uppfylla de krav du hade i del 1 av uppgiften.

1. Skapa kommandot `order <search>`. Om man enbart skriver `order` så visas samtliga ordrar (order id, order datum, kund id, antal orderrader, status). Om man skriver `order search` så filtreras resultatet och enbart visar de ordrar som matchar `search` på order id eller kund id.

1. En plocklista kopplar orderrader till en lagerhylla. Tanken är att lagerpersonalen tar en plocklista, åker runt i lagret och packar ihop ditt paket med samtliga produkter.

1. Skapa kommandot `picklist <orderid>` som fungerar på följande sätt.

    1. `picklist` visar en översikt av alla plocklistor.
    1. `picklist orderid` visar detaljerna för den plocklista som tillhör ordern med orderid.
    1. Om det inte finns en plocklista till vald order, så skapas en plocklista automatiskt, och visas.
    1. Vårt lager hanterar inte restnoteringar när produkten saknas på lagret, du behöver alltså inte ta hänsyn till om det blir minus på en produkt på en lagerhylla, det löser vi i "nästa version".



### Lämna in {#lamnain}

1. När du är helt klar och har testkört ditt system mot din egen databas, så tar du en backup av databasen med mysqldump och sparar i `sql/eshop/backup.sql`. Verifiera att backup-filen fungerar och tänk att rättaren kan ladda denna databas för att testköra mot ditt system.

1. Validera din kod.

```bash
# Flytta till kurskatalogen
dbwebb validate eshop2
```

Rätta eventuella fel som dyker upp och publisera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Gör följande om du har tid, energi och ro.

1. I webbklienten, gör en snygg sida som visar all information om ordern och samtliga orderrader, precis som det brukar se ut i godtycklig webshop på nätet.



Tips från coachen {#tips}
-----------------------

<!--
Tips i forum om tidsstämplar för created, updated, deleted, status, och sof delete.

Tips i forum om formulär SELECT/DROPDOWN.

Tips om loop i lagrad procedur och hantera rad för rad.

Anropa procedur i procedur
-->

Lycka till och hojta till i forumet om du behöver hjälp!

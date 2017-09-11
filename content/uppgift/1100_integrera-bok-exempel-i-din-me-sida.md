---
author:
    - mos
category:
    - php
    - anax
    - kurs ramverk1
revision:
    "2017-09-11": "(A, mos) Första utgåvan."
...
Integrera Bok-exemplet i din me-sida
===================================

Du skall integrera ett Bok-exempel i din me-sida för att visa att du hanterar ett komplett CRUD-exempel i ditt Anax.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Anax med databasdrivna modeller enligt Active Record, ett exempel](kunskap/anax-med-databasdrivna-modeller-enligt-active-record-ett-exempel)" och de som den är beroende av.



Introduktion {#intro}
-----------------------

Du har ett fungerande scaffoldat exempel. Nu skall du integrera det i din me-sida och uppdatera databastabellen (och det andra) så exemplet blir mer boklikt.



Krav {#krav}
-----------------------

1. Gör bok-exemplet till en del i din me-sida.

1. Uppdatera databastabellen så den blir mer boklik och har kolumner som "title" och "author". Lägg till fler kolumner (bild, länk till riktig bok, mm) om du så vill.

1. Det skall vara tydligt hur man når bokexemplet. Förslagsvis gör en landningssida för exemplet och lägger till i navbaren.

1. Kör `make test` för att kolla att du inte har några valideringsfel.

1. Gör en `dbwebb publish anax` för att kolla att allt validerar och fungerar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

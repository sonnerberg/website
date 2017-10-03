---
author:
    - mos
category:
    - php
    - anax
    - kurs ramverk1
revision:
    "2017-10-02": "(B, mos) Välj Travis eller CircleCI."
    "2017-10-02": "(A, mos) Första utgåvan."
...
Integrera din modul med externa byggtjänster
===================================

Du skall använda dig av din numer fristående modul som du publicerat på GitHub och Packagist och du skall integrera den med extra byggtjänster för automatiserad testning och du skall skapa ett flöde för continuous integration.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Integrera din packagist modul med verktyg för automatisk test och validering](kunskap/integrera-din-packagist-modul-med-verktyg-for-automatisk-test-och-validering)".



Introduktion {#intro}
-----------------------

Du skall använda dig av din modul från GitHub (och Packagist) för att integrera mot externa byggtjänster som automatiserar dina tester.




Krav {#krav}
-----------------------

1. Du jobbar i repo för din modul som du publicerar på GitHub (och Packagist).

1. Fortsätt utveckla koden så som du anser behövs.

1. Försök nå 100% kodtäckning med dina enhetstester. Men 50% kan också vara okey. Även andra procenttal kan accepteras lite beroende på hur stor din modul är. Var tydlig i redovisningstexten hur långt du nådde.

1. Integrera din modul med Travis alternativt CircleCI. Lägg badgen i din README.

1. Integrera din modul med Scrutinizer. Lägg tre badges i din README.

1. När du är klar så taggar du din modul och kör en `composer update` i din Anax-installation.

1. Kör `make test` för att kolla att du inte har några valideringsfel.

1. Gör en `dbwebb validate` för att kolla att allt validerar och fungerar.



Extrauppgift {#extra}
-----------------------

Gör följande extrauppgifter om du finner dem givande.

* Pröva gärna integrera med fler externa verktyg, om du hittar något som verkar spännande.

* Försök verkligen att nå 100% kodtäckning i dina enhetstester, bara för att visa att det går. Om det inte går, skriv då om det i redovisningstexten och berätta varför, eller berätta vilka kodändringar som behövs för att göra koden mer testbar.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

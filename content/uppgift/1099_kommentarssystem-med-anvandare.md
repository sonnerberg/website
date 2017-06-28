---
author:
    - mos
category:
    - php
    - anax
    - kurs ramverk1
revision:
    "2017-06-28": "(A, mos) Första utgåvan."
...
Kommentarssystem med användare
===================================

Bygg ut ditt kommentarssystem så att endast inloggade användare kan göra kommenterar.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Anax med dependency injection](kunskap/anax-med-dependency-injection)".



Introduktion {#intro}
-----------------------

Vi kan anta att ditt kommentarssystem kommer att kräva inloggade användare, det är alltså inte ett kommentarssystem för anonyma användare som vi skall skapa.

Du behöver alltså stöd för att användare kan registrera sig och logga in i ditt system och att de enbart kan påverka sina egna kommentarer.

Du kan fortsätt att spara kommentarerna i sessionen, snart inför vi en databas.

Fundera på hur mycket tid du har och se till att få en fungerade prototyp inom den tiden du har och prioritera bort det som inte är nödvändigt.



Krav {#krav}
-----------------------

1. Koden du skriver skall använda sig av MVC och Dependency Injection där det passar.

1. Man kan registrera ett konto och logga in.

1. Man kan ange sin emailadress när man registrerar sig. Emailadressen används som gravatar. Man kan uppdatera sin emailadress via en profilsida.

1. En registrerad användare kan lägga till en kommentar, redigera den och ta bort den.

1. En administratör kan redigera och ta bort kommentarer oavsett användare.

1. Kör `make test` för att kolla att du inte har några valideringsfel.

1. Gör en `dbwebb publish anax` för att kolla att allt validerar och fungerar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

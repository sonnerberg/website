---
author: mos
revision:
    "2017-12-27": "(A, mos) Första versionen, uppdelad av större dokument."
...
Introduktion
==================================

Denna guide/övning/laboration handlar om att komma igång med SQL mot databasen MySQL/MariaDB. Den består av övningar där du får börja skapa tabeller, fylla dem med innehåll och därefter ställa SQL-frågor för att söka ut och bearbeta innehållet. Övningen tar dig igenom de vanliga förekommande konstruktionerna som du behöver känna till. Lär dig dem och du kommer att ha en god grund för att behärska databaser. De första övningarna är enkla och övningarna mot slutet lite mer utmanande.

Övningen är utvecklad för MySQL och visar både på standard SQL och på databasspecifika frågar av mer databasadministrativ karaktär.

När det finns hänvisningar till referensmanualen så avses [referensmanualen för MySQL](http://dev.mysql.com/doc/refman/5.7/en/). Välj senaste GA versionen av manualen.

Du kan välja att göra övningen i valfri klient. Jag har gjort övningen i MySQL Workbench och kommandoradsklienten.



Förkunskaper {#forkunskaper}
----------------------------------

Du behöver ha tillgång till en [databasserver för MySQL](labbmiljo/mysql).

Du behöver tillgång till en klient likt MySQL WorkBench, PHPMyAdmin eller kommandoradsklient. Behöver du hjälp så finns guiden "[Kom igång med databasen MySQL och dess klienter](kunskap/kom-igang-med-databasen-mysql-och-dess-klienter)".

Du kan jobba [BTH's labbmiljö för MySQL](kunskap/bth-s-labbmiljo-for-databasen-mysql).



Tidigare version {#tidigare}
----------------------------------

Denna guide bygger på, och vidarutvecklar, dokumentet "[Kom igång med SQL](uppgift/kom-igang-med-sql)" som kom ut första gången 2008.

I samband med att denna guide skapades (årsskiftet 2017/2018) så gicks dokumentet igenom och testades och alla bilder byttes ut mot utskrifter från terminalkommandot och kompletterades med asciinemas. Det lades till en del administrativa kommandon för att inspektera databasens schema.

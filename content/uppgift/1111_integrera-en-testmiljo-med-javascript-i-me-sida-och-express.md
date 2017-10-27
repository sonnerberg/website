---
author: mos
category:
    - javascript
    - test
    - kurs ramverk2
revision:
  "2017-10-23": (A, mos) Första utgåvan.
...
Integrera en testmiljö med JavaScript i me-sida och Express
==================================

Du skall bygga upp en testmiljö för ditt JavaScript-projekt. Det handlar om vilka verktyg du använder för enhetstestning, kodtäckning, funktionstester och en kedja av Continuos Integration samt hur du kan använda Docker vid tester.

<!--more-->
[WARNING]
** Arbete pågår **
<[/WARNING]
<!--stop-->



Förkunskaper {#forkunskaper}
-----------------------

Du har installerat Docker och du har jobbat igenom artikeln "[Kom igång med Docker som utvecklingsmiljö](kunskap/kom-igang-med-docker-som-utvecklingsmiljo)".



Introduktion {#intro}
-----------------------

Du skall lägga till kontainrar för test. Kontainrarna skall kunna köra flera versioner av Node (och PHP).



Krav {#krav}
-----------------------

1. Skapa en fil `docker-compose.yml` som startar upp tre olika kontainrar av olika version med PHP och Apache (eller Nginx). Spara filen i `me/kmom02/docker`.

1. Skapa en fil `docker-compose.yml` som startar upp tre olika kontainrar av olika version med Node. Spara filen i `me/redovisa`.

1. Gör en dbwebb publish för att kolla att allt validerar och fungerar.

```text
dbwebb publish me
```



Extrauppgift {#extra}
-----------------------

Här är en extrauppgift som du verkligen borde försöka lösa. Sen har du god koll på basen i Docker.

1. Se hur Cimage har skapat egna images och publicerat dem i Docker Store. Gör en egen image (som bygger på Node) som du publicerar på Docker Store och använder i ditt repo i `me/redovisa`.



Tips från coachen {#tips}
-----------------------

Docker är virtualisering, så det kan troligen krångla beroende på den miljö du har. Ta det lugnt och var envis.

Läs manualen för Docker för att förstå hur det hänger ihop och fungerar.

Lycka till och hojta till i forumet om du behöver hjälp!

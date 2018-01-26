---
author: lew
revision:
    "2018-01-25": (B, aar) Added requirements.
    "2018-01-25": (A, lew) First version.
category:
    - oopython
...
Skapa queue
===================================

Vi ska bygga om datastrukturen "queue".  
Utgå från koden för en Queue från övningen om datastrukturer och skriv om den så den inte använder Pythons inbyggda lista utan istället använder Node objekt för att hålla datan.

<!--more-->

[YOUTUBE src=1Kj1qVpRD50 width=630 caption="Så här kan det se ut när det är färdigt."]


Förkunskaper {#forkunskaper}
-----------------------

Du har läst artikeln "[Exceptions](kunskap/exceptions)".  
Du har läst artikeln "[Datastrukturer](kunskap/datastrukturer)".  



Krav {#krav}
-----------------------

Ställ dig i mappen `queue/`.

```bash
# Ställ dig i kurskatalogen
cd me/kmom04/queue
```

1. Skapa en fil med namnet `queue.py` i "queue" mappen. Kopiera koden [för en Queue](kunskap/datastrukturer#queue) och klistra in i queue.py filen.  

1. Skapa en fil med namnet `node.py` i "queue" mappen. Kopiera koden [för en Node](kunskap/datastrukturer#node) och klistra in i node.py filen.  

1. Pythons inbyggda lista ska inte användas längre. Varje element i kön ska ligga i ett Node objekt och bilda en list struktur.  
Byt namn på instans attributet `items` till `head` i Queue klassen. Använd `head` för att referera till första noden i kön.  

1. Det är helt OK att lägga till fler metoder/attribut om man vill det i Queue klassen.

1. Skapa filen `main.py` i "queue" mappen. Den ska innehålla en handler klass med en evighets loop (tänk marvin i python kursen). I loopen ska det finnas input alternativ för alla metoder i Queue klassen. Det ska gå att kolla om en kö är tom, lägga till data, plocka ut data, kolla vilket som är nästa element och se storleken. Det ska givetvis också gå att avsluta loopen.

1. Om man gör peek på en tom kö ska ett exception lyftas som fångas i din handler. Det ska alltså inte krascha.

1. Skapa filen `main.py` i "list" mappen. Den ska innehålla en handler klass med en evighets loop (tänk marvin i python kursen). I loopen ska det finnas input alternativ för alla metoder i UnorderedList klassen. Det ska gå att kolla om en kö är tom, lägga till data, plocka ut data, kolla vilket som är nästa element och se storleken. Det ska givetvis också gå att avsluta loopen.



```bash
# Ställ dig i kurskatalogen
#dbwebb validate list
dbwebb publish queue
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. Skapa ett sekvensdiagram över flödet som sker vid en valfri input från användaren. Spara det som "sekvens.png" i "queue" mappen.

1. Skapa ett klassdiagram över Queue klassen. Spara det som "klass.png" i "queue" mappen.

Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

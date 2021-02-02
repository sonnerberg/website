---
author: aar
revision:
    "2021-02-02": (D, moc) Uppdaterade kraven till att gå igenom tester.
    "2019-02-01": (C, aar) Tog bort extrauppgiften om sekvensdiagram.
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

1. Börja med att kopiera koden som ligger i [example/queue](https://github.com/dbwebb-se/oopython/tree/master/example/queue). Mappen innehåller två filer, den **viktiga** är `tests.py` där alla tester behöver passera för att uppgiften skall bli godkänd.  
Filen `main.py` är ett färdigt cli program som kan användas för att hjälpa till med felsökningen, det är **ingenting** vi kommer att kolla på under rättningen. 


```bash
# Ställ dig i kurskatalogen
# börja med att uppdatera mappen med senaste exempelkoden
dbwebb update
cp -ri example/queue me/kmom04/
cd me/kmom04/queue
```

2. Skapa en fil med namnet `queue.py` i "queue" mappen. Kopiera koden [för en Queue](kunskap/datastrukturer#queue) och klistra in i queue.py filen.  

1. Skapa en fil med namnet `node.py` i "queue" mappen. Kopiera koden [för en Node](kunskap/datastrukturer#nod) och klistra in i node.py filen.  

1. Pythons inbyggda lista ska inte användas längre. Varje element i kön ska ligga i ett Node objekt och bilda en list struktur.  
Byt namn på instans attributet `items` till `head` i Queue klassen. Använd `head` för att referera till första noden i kön.  

1. Det är helt OK att lägga till fler metoder/attribut om man vill det i Queue klassen.

1. Skapa en fil med namnet `errors.py` i "queue" mappen. Här skall du skapa ett eget exception med namnet `EmptyQueueException`. Denna skall uppstå när man använder `peek()` eller `dequeue()` på en tom kö.

1. Se till att `Queue` klassen passerar alla tester.


```bash
# Ställ dig i kurskatalogen
#dbwebb validate list
dbwebb publish queue
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

<!-- 1. Skapa ett sekvensdiagram över flödet som sker vid en valfri input från användaren. Spara det som "sekvens.png" i "queue" mappen. -->

1. Skapa ett klassdiagram över Queue klassen. Spara det som "klass.png" i "queue" mappen.

Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

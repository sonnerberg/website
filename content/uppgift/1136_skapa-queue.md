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

Vi ska skapa en egen datastruktur, en "queue".  
Utgå från koden för en Queue från övningen om datastrukturer och skriv om den så den inte använder Pythons inbyggda lista utan istället använder Node objekt.

<!--more-->


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

1. Skapa filen `main.py`. ...innehålla loop som marvin, med val för lägga till och andra saker...



```bash
# Ställ dig i kurskatalogen
#dbwebb validate list
dbwebb publish list
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.


Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

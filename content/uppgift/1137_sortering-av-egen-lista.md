---
author: aar
revision:
    "2018-01-31": (A, aar) Första versionen.
    "2016-04-12": (PA, lew) Pre-release.
category:
    - python
...
Terminalprogram med sortering av lista
===================================

Vi ska jobba med sorteringsalgoritmer. Ni uppdatera koden för Insertion sort så den funkar med er UnsortedList och sen ska ni skriva er egna Bubble sort.

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har gjort uppgiften "[Skapa lista](uppgift/skapa-lista)".
Du har läst artikeln "[Klassiska sorteringsalgoritmer](kunskap/sorteringsalgoritmer)".  
Du har läst artikeln "[Datastrukturer](kunskap/datastrukturer)".  



Krav {#krav}
-----------------------

Kopiera UnorderedList filerna från kmom04.

```bash
# Ställ dig i kurskatalogen
cd me
cp -i kmom04/list/*.py kmom05/sort/
cd kmom05/sort
```

1. Skapa filen `sort.py` och kopiera in insertion sort från [artikeln](kunskap/sorteringsalgoritmer#insertion-sort).  
"sort.py" behöver inte innehålla någon klass. Det räcker med enbart funktion för algoritmen.

1. Lägg till ett menyval i `main.py` som sorterar listan med din Insertion sort.

1. Justera din Insertion sort så den kan sortera din UnorderedList.

1. I `sort.py` skapa en Bubble sort algoritm som kan sortera din lista.

1. Lägg till ett menyval i `main.py` som sorterar listan med din Bubble sort.

1. Lägg till minst två tester för din Bubble sort i `test.py`. 

```bash
# Ställ dig i kurskatalogen
dbwebb validate sort
dbwebb publish sort
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. Gör en ny implementation av Bubbel sort med rekursion. Gör ett eget menyval i main.py för att sortera med den.

1. Gör en ny implementation av Insertion sort med rekursion. Gör ett eget menyval i main.py för att sortera med den.



Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

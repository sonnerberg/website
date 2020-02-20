---
author: aar
revision:
    "2020-02-05": (B, aar) Bytte bubble sort för rekursiv insertion sort.
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
Du har läst artikeln "[Klassiska sorteringsalgoritmer](kunskap/sorteringsalgoritmer-v2)".  
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

1. Justera din Insertion sort så den kan sortera din UnorderedList. PS! När ni skapar sorterings algoritmerna ska ni använda er av listans metoder för att flytta på element. Ni ska **inte** hämta head och traversera noder med den i era algoritmer.

1. Lägg till ett menyval i `main.py` som sorterar listan med din Insertion sort.

1. I `sort.py` skapa en rekursiv insertion sort algoritm som kan sortera din lista.

1. Lägg till ett menyval i `main.py` som sorterar listan med din rekursiva insertion sort.

1. Lägg till minst två tester för din rekursiva insertion sort i `test.py`.

```bash
# Ställ dig i kurskatalogen
dbwebb validate sort
dbwebb publish sort
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. Gör en implementation av Bubbel sort med rekursion. Gör ett eget menyval i main.py för att sortera med den.

1. I sortering stöd att särskilja på heltal och strängar. Om en lista innehåller strängar och heltal ska heltalen sorteras till vänster och strängarna till höger, för sig.  
Exempel `[3, "b", 1, "a", 2]` --> `[1, 2, 3, "a", "b"]`.



Tips från coachen {#tips}
-----------------------

Ni kan hårdkoda värden till er lista så ni slipper skriva in nya tal i terminalen hela tiden när ni ska utveckla sorteringsalgoritmen.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

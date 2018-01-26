---
author: lew
revision:
    "2018-01-26": (B, aar) Added requirements.
    "2018-01-25": (A, lew) First version.
category:
    - oopython
...
Skapa lista
===================================

Vi ska skapa en egen datastruktur, en "unordered list".

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har läst artikeln "[Exceptions](kunskap/exceptions)".  
Du har läst artikeln "[Datastrukturer](kunskap/datastrukturer)".  



Unordered list {#unordered-list}
-----------------------  

Vi ska skapa en egen datastruktur, en "Unordered list", som en klass. Unordered list kan liknas vid en vanlig lista i Python. Det ska gå att lagra element i den. En representation av en unordered list kan se ut såhär:  

[FIGURE src=/image/oopython/kmom05/list1.png]  

<!-- För att kika på koden till uppgiften, kan du [klicka här](https://github.com/dbwebb-se/oopython/blob/master/example/unorderedlist/unorderedlist.py)  -->

Nedanför ser vi ett klassdiagram för en UnorderedList klass. Under diagrammet beskrivs varje metod. Diagrammet ska uppfyllas av er implementation.

[FIGURE src=/image/oopython/kmom04/UnorderedList_klass.png caption="klass diagram för UnorderedList"]  

* `is_empty`: Returnera True/False för om listan är tom eller inte.
* `add`: Lägg till nytt element/nod sist i listan.
* `insert`: Lägg till nytt element/nod på specifikt index.
* `set`: Skriv över element med ny data som finns på index.
* `size`: Returnera antaler element i listan.
* `get`: Returnera värde på index.
* `index_of`: Om data finns i listan returnera dess index.
* `print_list`: Skriv ut listans innehåll.
* `remove`: Ta bort nod med samma data.



Krav {#krav}
-----------------------

Ställ dig i mappen `list/`.

```bash
# Ställ dig i kurskatalogen
cd me/kmom04/list
```

1. Skapa en fil med namnet `node.py` i "list" mappen. Kopiera koden [för en Node](kunskap/datastrukturer#node) och klistra in i node.py filen.  

1. Skapa en fil med namnet `unorderedlist.py` i "list" mappen. Den ska innehålla klassen UnorderedList.  

1. UnorderedList klassen ska följa klassdiagrammet ovanför. Minst de metoderna och attributen måste finnas i din implementation. Det är Ok att lägga till mer.

1. Implementera UnorderedList med noder för att bygga listan.

1. Välj själv om listan ska vara cirkulär, dubbellänkad eller enkellänkad.  

1. Skapa filen `exceptions.py` i "list mappen. Den ska innehålla minst 2 egna exceptions. Använd dig av dem i UnorderedList klassen. T.ex. ett för Value error och ett för Index error. Skriv i redovisningstexten vilka det är och hur man får dem.

1. Skapa filen `main.py` i "list" mappen. Den ska innehålla en handler klass med en evighets loop (tänk marvin i python kursen). I loopen ska det finnas input alternativ för alla metoder i UnorderedList klassen.

1. Skapa en fil med namnet `test.py` i "list" mappen. Skriv enhetstester för metoderna i UnorderedList klassen. Det ska finnas minst ett test för varje metod.  



```bash
# Ställ dig i kurskatalogen
#dbwebb validate list
dbwebb publish list
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

<!-- 1. Skapa en "ordered list" som automatiskt placerar elementen på rätt plats i listan. -->

1. Implementera den [magiska metoden __len__](https://docs.python.org/3/reference/datamodel.html#object.__len__) för din UnorderedList. Gör så `len(list)` fungerar.

1. Implementera den [magiska metoden __str__](https://docs.python.org/3/reference/datamodel.html#object.__str__) för din UnorderedList. Gör så `print(list)` och `str(list)` fungerar.

1. Implementera den [magiska metoden __getitem__](https://docs.python.org/3/reference/datamodel.html#object.__getitem__) för din UnorderedList. Gör så `list[0]` fungerar.

1. Implementera den [magiska metoden __setitem__](https://docs.python.org/3/reference/datamodel.html#object.__setitem__) för din UnorderedList. Gör så `list[0] = 4` fungerar.



Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

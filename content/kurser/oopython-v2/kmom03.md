---
author: lew
category:
    - oopython
revision:
    "": (C, moc) La in bank2 och ändrade war uppgiften till klassdiagram. 
    "2019-01-19": (B, aar) Tog bort uppgifter om sekvensdiagram.
    "2017-12-13": (A, lew) New version for v2.
...
Kmom03: UML och unittest
====================================

[FIGURE src=/image/oopython/kmom02/kmom02_top.jpg class="right"]

Kom igång med _UML_ och _unittest_. Det är kraftfulla verktyg som används i "riktig" produktionsmiljö. UML kan användas för att beskriva klassernas relation och unittester (enhetstester) används för att testa delar av koden såsom funktioner och metoder.  

Du kommer att skapa ett UML-diagram utifrån en färdig kodbas och skriva unittester.

<!--more-->

[WARNING]
Detta kmom uppdateras och är inte redo att jobbas igenom.
[/WARNING]

<!-- Flytta nedan text till eget dokument/vy/block -->

<small>*(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka 20 studietimmar inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)*</small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

[Python 3 Object-oriented Programming](kunskap/boken-python3-object-oriented-programming)  
    * Ch 3 - When Objects Are Alike  
    * Ch 5 - When to use Object-oriented Programming  
    * Ch 12 - Testing Object-oriented Programs


###Artiklar {#artiklar}

Läs följande:

1. [The art of unit testing](http://artofunittesting.com/definition-of-a-unit-test/)  

1. [UML notation](https://atomicobject.com/resources/oo-programming/uml-notation)

1. [Visualizing program execution](https://atomicobject.com/resources/oo-programming/visualizing-program-execution)

1. [UML basics på IBM](http://www.ibm.com/developerworks/rational/library/769.html)  



###Video  {#video}

Titta på följande video:  

1. Videos 12-22 i spellistan [Software Development Process: Part 2 of 3](https://www.youtube.com/watch?v=pZ9-ujSP_48&index=12&list=PLAwxTw4SYaPm8PAGH7ov2Bj-nG4sXgCtJ)  om class diagrams.

1. Video om unittester: [Python Functions 2: Unit Testing](https://www.youtube.com/watch?v=F7a0iUH6kVA)

1. Längre video om testning i Python: [Testing is Fun in Python!](https://www.youtube.com/watch?v=Sb2tz9Hlbp8)



###Lästips {#lastips}

1. [UML class relationships](http://creately.com/blog/diagrams/class-diagram-relationships/)

1. [OO development process](https://atomicobject.com/resources/oo-programming/oo-development-process)

1. [CRC cards](https://atomicobject.com/resources/oo-programming/crc-cards)




Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



###Övningar {#ovningar}

Genomför följande övningar för att träna dig.

1. Läs igenom artikeln om UML-diagram "[Introduktion till UML?](kunskap/intro_till_uml)". Ni behöver förstå hur man gör egna klassdiagram. Sekvens och use case diagram behöver ni bara läsa om och förstå syftet med.

2. Läs igenom artikeln som handlar om enhetstester "[Att skriva unittester](kunskap/unittest-i-python)".



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

<!-- 1. Gör uppgiften "[Skapa objekt efter UML](uppgift/skapa-objekt-efter-uml)" -->

<!-- 1. Gör uppgiften "[Skriv testfall för ett objekt](uppgift/skriv-testfall-for-ett-objekt)".   -->

<!-- 1. Gör uppgiften "[Kortspelet War](uppgift/kortspelet-war)". Utför uppgiften i mappen `war`.   -->

1. Gör uppgiften "[Skapa ett UML diagram](uppgift/skapa_ett_uml_diagram)". 

1. Gör uppgiften "[Bygg en bank med flask - Del 2](uppgift/bank_med_flask_del_tva)". Spara koden i `me/kmom03/bank2/` 

<!-- 1. Gör uppgiften "[Skapa sequence diagram](uppgift/skapa-sequence-diagram2)". Utför uppgiften i mappen `uml`.   -->


1. Fyll på redovisning.html med kursmomentets redovisningstext.

```bash
# Ställ dig i kurskatalogen
# dbwebb validate kmom03
dbwebb publish kmom03p
```



###Extra {#extra}

Det finns ingen extrauppgift.
<!-- 1. Gör uppgiften "[Skapa ett klassdiagram](uppgift/skapa-klassdiagram)". -->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Är du bekant med UML sedan tidigare?  
* Är du bekant med unittester sedan tidigare?
* Kan du se nyttan med UML och tester inom ramen för ett projekt?
* Vad tycker du om objektorienterad programmering än så länge?
* Gick det bra att komma i gång med kursmomentet, var det lagom, för litet, för stort?
<!-- * Överskuggade du någon metod i "Kortspelet War"? -->
<!-- * Hur gick det med sekvensdiagrammet? -->
* Gjorde du extrauppgiften?

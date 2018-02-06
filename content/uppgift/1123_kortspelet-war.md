---
author: lew
revision:
    "2018-02-05": (B, aar) clarified two requirements.
    "2017-12-15": (A, lew) First version for v2.
category:
    - oopython
...
Kortspelet War
===================================

[FIGURE src=/image/oopython/kmom03/cards-top.jpg?w=c5 class="right"]

Vi ska skapa ett kortspel som används från terminalen. Kortspelet kallas *War*, eller *Svälta räv* på svenska. Vi ska använda klasser med arv. Efter implementationen skapar vi några enhetstester för en av klasserna. För spelreglerna kan du kika på [här](https://en.wikipedia.org/wiki/War_(card_game)) för engelska eller [här](https://sv.wikipedia.org/wiki/Sv%C3%A4lta_r%C3%A4v) för svenska.

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har gått introduktionskursen i Python.  
Du har gått igenom artikeln "[Att skriva enhetstester](kunskap/unittest-i-python)".  
Du har läst artikeln "[Klass relationer](kunskap/klass-relationer)".  



Introduktion {#intro}
-----------------------    

Vi utgår från två stycken spelare som turas om att lägga ut ett kort framför sig. Är färgen samma, (hjärter, spader, ruter eller klöver), vinner den som har kortet med högst värde. Vinnaren tar då båda spelarnas högar och lägger i botten av sin egna. Om färgen inte är samma, fortsätter spelet och spelarna placerar ut varsitt nytt kort i sin hög framför sig. Spelet tar slut när en av spelarna har slut på kort. Nedan kan du se ett exempel på hur det är tänkt att fungera:

[ASCIINEMA src=152927]

<!-- infoga diagram här -->

Krav {#krav}
-----------------------

Arbeta i mappen war/.

```bash
# Ställ dig i kurskatalogen
$ cd me/kmom03/war
```

1. Spelet ska startas med kommandot `python3 main.py`.

1. Spelet ska använda klasserna `Deck`, `Hand` och `Card`. `Deck` ska bestå av 52 stycken `Card`. `Hand` kan ärva från `Deck`.

1. Spelfunktionaliteten ska hanteras via klassen `War`.

1. Skapa en fil, `test.py`, som ska bestå av enhetstester för klassen `Hand`. Alla medlemsvariabler och metoder ska testas. Spara den i mappen `war`.

1. Skapa klassdiagram över två valfria klasser. Döp filen till `uml.png` och spara den i mappen `war`.

```bash
# Ställ dig i kurskatalogen
$ dbwebb validate war
$ dbwebb publish war
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

<!-- 1. Lägg till fler former, tex en [cylinder](https://sv.wikipedia.org/wiki/Cylinder) eller [hyptagon](https://sv.wikipedia.org/wiki/Heptagon). -->



Tips från coachen {#tips}
-----------------------

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

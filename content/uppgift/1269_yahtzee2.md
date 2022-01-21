---
author:
    - aar
    - grm
revision:
    "2022-01-20": (A, grm) Första upplagan.
category:
    - oopython
...
Fortsättning på Yahtzee spelet
===================================

I denna uppgiften ska ni fortsätta med Yahtzee spelet ni började på i kmom01.

<!--more-->

Ni kommer att fortsätta utveckla spelet igenom flera kursmoment. I denna uppgiften skapar vi ett formulär där vi väljer vilka tärningar som ska slås om och vilken regel som ska användas.



Förkunskaper {#forkunskaper}
-----------------------

Ni har gått igenom delarna “Intro till guiden” och “Klass relationer” i guiden "[Kom igång med objekt](guide/kom-igang-med-objektorienterad-programmering-i-python)".

Ni har jobbat igenom övningen "[Flask, POST och GET](kunskap/flask-get-post)".

Ni har jobbat igenom övningen med UML del 2.

Om ni har gjort övningarna så har ni nästan kommit i mål med uppgiften.



Introduktion {#intro}
-----------------------

Ni ska som sagt utveckla ett Yahtzee spel över flera kursmoment. Ni som jobbar ensamma ska utveckla spelet för terminalen medan ni som jobbar i grupp ska utveckla spelet för webbläsaren med hjälp av Flask.

Spelet ska följa de internationella reglerna och inte svenska reglerna. Här kan ni hitta [reglerna](https://gamerules.com/rules/yahtzee-dice-game/). Denna veckan ska vi skapa klasserna för reglerna. Vi ska kunna välja regel och se dess poängsumma.

Vi ska lägga till checkboxar bredvid tärningarna för att på så sätt visa vilka som ska slås om. När vi slagit om tärningarna vill vi också se föregående tärningsslag.

Era klasser ska uppfylla beskrivningarna nedanför. Beskrivningarna är vad som måste finnas, ni får och är **rekommenderade** att skapa ytterligare metoder och attribut där ni tycker att det behövs.



### Die {#die}

Lägg till en ny metod.

- `__eg__()` ska returnera värdet som tärningen har som en sträng.



#### Hand {#hand}

Lägg till en ny metod.

- `to_list()` ska returnera en lista som innehåller värdet på tärningarna.


### Rule {#rule}

Denna klassen är en abstrakt klass och representerar en regel.

[FIGURE src="/image/oopython/kmom02/rule.png" caption="Rule klass"]

#### Attributen {#rule-attr}

Inga.

#### Metoderna {#rule-met}

- `points(hand)` - metoden är tom och innehåller `pass` vilket innebär att metoden `points` för underklasserna körs istället.

### SameValueRule {#same-value-rule}

Denna klassen representerar reglerna i övre delen, antalet 1:or, 2:or etc.

[FIGURE src="/image/oopython/kmom02/same_value_rule.png" caption="SameValueRule klass"]

#### Attributen {#same-value-rule-attr}

- `value` - Ska innehålla värdet för regeln, t.ex. 1 för 1:or.
- `name` - Ska innehålla namnet på regeln, t.ex. Ones() för ettor.

#### Metoderna {#same-value-rule-met}

- `__init__(value, name)` - inga defaultvärden
- `points(hand)` - ska returna poängsumman för regeln, t.ex. 3 för 3 stycken 1:or.

### Ones {#ones}

Denna klassen representerar regeln med 1:or.

[FIGURE src="/image/oopython/kmom02/ones.png" caption="Ones klass"]

#### Attributen {#ones-attr}

- `value` - Ska innehålla värdet för regeln, t.ex. 1 för 1:or.
- `name` - Ska innehålla namnet på regeln, t.ex. Ones() för ettor.

#### Metoderna {#ones-met}

- `__init__()` - anropar basklassens konstruktor.

Klasserna Twos, Threes, Fours, Fives och Sixes är uppbyggda på samma sätt.

### ThreeOfAKind {#three-of-a-kind}

Denna klassen representerar regeln med 1:or.

[FIGURE src="/image/oopython/kmom02/ones.png" caption="Ones klass"]

#### Attributen {#three-of-a-kind-attr}

- `name` - Ska innehålla namnet på regeln "Three of a kind".

#### Metoderna {#three-of-a-kind-met}

- `__init__()` - sätter namnet på regeln.
- `points(hand)` - ska returna poängsumman för regeln. I detta fallet kolla att det finns minst 3 likadana tärningar och returnera dess poängsumma, t.ex. 9 för 3 stycken 3:or.

De andra reglerna FourOfAKind, FullHouse, SmallStraight, LargeStraight, Yahtzee och Chance är uppbyggda på samma sätt som ThreeOfAKind.

Krav {#krav}
-----------------------

Kraven är uppdelade i tre sektioner nedanför. Ni som jobbar i grupp måste uppfylla kraven i [Krav för alla](#krav-alla) och [Krav grupp](#krav2). Ni som jobbar ensamma måste uppfylla kraven i [Krav för alla](#krav-alla) och kan **välja** mellan att göra [Krav ensam](#krav1) eller [Krav grupp](#krav2).

### Krav för alla {#krav-alla}

1. Kopiera er kod från `me/kmom01/yahtzee1` till `me/kmom02/yahtzee2`.

1. Implementera de nya metoderna för Die och Hand.

1. Gör nya klassdiagram för Die och Hand. Spara dem som uml.pdf och rita gärna i [draw.io](https://drawio-app.com/)

1. Lägg till ett test för Die klassen i `me/kmom02/yahtzee2/tests/test_die.py`. Testa följande saker i Die klassen:
    1. Att `__eg__()` returnerar rätt värde som en sträng.

1. Skapa tester för Hand klassen i `me/kmom02/yahtzee2/tests/test_hand.py`. Testa följande saker i Hand klassen:
    1. Att skapa ett objekt utan skicka argument till konstruktorn.
    1. Att skapa ett objekt och skicka lista med tärningar till konstruktorn.
    1. Att `roll()` slår om rätt tärningar.
    1. Att `roll()` utan indata inte slår om några tärningar.
    1. Att `to_list()` returnerar en lista med tärningarnas värde.

1. Implementera koden för Rule enligt klassdiagrammen ovanför. Spara filen i `me/kmom02/yahtzee2/src`.


### Krav ensam {#krav1}

Du ska lägga till följande funktionalitet till ditt terminalprogram.

1. Vid menyval "r" så ska användaren kunna välja vilka tärningar som ska slås om. Slå om de tärningarna och visa användaren.

1. Vid menyval "r" efter att användaren valt vilka tärningar som ska slås om så ska regel väljas. Då ska terminalprogrammet svara med poängsumman för den regeln.

1. Tänk på att varje omgång består av 3 slag. När regel för 3:e gången så bör loopen startas om. Poängsumman nollställs inför nästa runda.

1. Testa, validera och publicera applikationen på studentservern.



### Krav grupp {#krav2}

När ni är färdiga kan det se ut så här:

[FIGURE src="/image/oopython/kmom02/yahtzee2.png" caption="Bild på slag 3"]

1. Lägg till checkboxar bredvid tärningarna för att visa vilka vilka tärningar som ska slås om. Gör en knapp för att submit:a resultatet. Testa.

1. Håll reda på antalet slag och spara det som heltal i session. Presentera vilket slag det är i rubriken. Testa att rubriken ändrar sig och räknar upp när du slår tärningarna. Gör gärna print(session) och kolla att det stämmer.

1. Lägg till "Last die rolls" överst. Spara nuvarande värde på tärningarna med `to_list()` till sessionen innan du slår om tärningarna. Testa.

1. Lägg till en route `reset` som nollställer sessionen och därmed startar om spelet. Lägg till den i navbaren om du vill. Testa.

1. Lägg till radiobuttons för de olika reglerna i samma formulär. Bredvid en radiobutton för en viss regel ska namnet på regeln skrivas ut. Testa.

1. Lägg till så att poängsumman för respektive regel visas bredvid regeln radiobutton. Testa.

1. Spara poängsumman i session och visa upp den under knappen. Testa.

1. Tänk på att varje omgång består av 3 slag. När du klickar på knappen på 3:e slaget så bör spelet startas om. Poängsumman nollställs inför nästa runda.

1. Testa, validera och publicera applikationen på studentservern.



```bash
# Ställ dig i kurskatalogen
dbwebb test yahtzee2
dbwebb publish yahtzee2
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lär dig felsöka med debuggern, använd den när du får problem. Komplettera med utskrifter av `print()`.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

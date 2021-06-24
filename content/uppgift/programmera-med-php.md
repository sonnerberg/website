---
author: mos
category:
    - kurs webtec
revision:
    "2021-06-15": "(A, mos) Första utgåvan."
...
Programmera med PHP
===================================

Du skall träna dig på grunderna i PHP genom att utföra ett antal mindre programmeringsövningar.

Det handlar om grunder såsom problemlösning och programmering med variabler, if-satser, loopar, arrayer, funktioner och att dela upp koden i olika filer.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap om att programmera med PHP.

Du har PHP i din PATH och kan exekvera kommandot `php` i terminalen.

Du har installerat en utvecklingsmiljö med validatorer som testkör din kod via statisk kodanalys.



<!--
Genomgång {#genom}
------------------------

Här är en video som "pratar" dig igenom uppgiftens upplägg och visar hur du kommer igång.

[YOUTUBE src="gKzwQTG9eCI" width=700 caption="Kurs mvc kmom03 tisdagsgenomgång, del 3/3 uppgiften (Zoom med Mikael)."]
-->



Introduktion och förberedelse {#intro}
-----------------------

Uppgifterna löser du genom att skriva kod i filer som du exekverar via terminalen.

Spara alla filerna under `me/php`.

Du skall ha ett main-program och den koden sparar du i filen `main.php`. Main-programmet skriver ut menyn och läser input från användaren och utför sedan en uppgift.

Lösningen på varje uppgift skall kodas som en funktion med ett bestämt namn. Samtliga funktioner placeras i filen `src/functions.php` som inkluderas i `main.php`. När koden växer blir det troligen fler funktioner som delas upp i olika filer och då är det bra att samla dem i en underkatalog och `src` är ett vanligt namn på en sådan katalog.

Så här kan det se ut när de första menyvalen är implementerade.

[ASCIINEMA src="421936" caption="De första menyvalen är implementerade."]



### Strikta type i PHP {#strict}

Se till att alla dina filer inleds med att använda strikta typer.

```text
<?php

declare(strict_types=1);
```



### Konfigurationsfil och felutskrifter {#error}

Skapa en fil `config.php` och lägg dit följande kod som sätter på felutskrifter. Detta gör att det blir tydligt om något är fel i din kod. När man utvecklar sin kod vill man att dessa felmeddelanden syns. När man har levererat sin kod till "produktionsläge" vill man dock stänga av dem som en säkerhetsåtgärd.

Sätt på felutskrifter i `config.php`.

```php
error_reporting(-1);              // Report all type of errors
ini_set("display_errors", 1);     // Display all errors
```

Se till att denna filen inkluderas som den första filen i din `main.php`.



### DocBlock kommentarer {#docblock}

Ovanför varje funktion skall du skriva en DockBlock kommentar och ge en kort introduktion till vad funktionen gör. Dessa kommentarer gör att vi senare kan automatgenerera dokumentation för koden.

Det är mest lämpligt att använda engelska när man skriver kod och kommentarer.

```php
/**
 * Prints details about this program.
 */
function about() : void {
    // some code
}
```

När funktionerna växer kan man även dokumentera inkommande parametrar till funktionen, vad den returnerar och om den kastar exception.



### Utvecklingsmiljö med validatorer {#validate}

Du bör sedan tidigare ha installerat en utvecklingsmiljö för PHP under katalogen `me/` där du via composer kan köra verktyg för statisk kodvalidering.

Glöm inte att köra dessa verktyg kontinuerligt.

Denna uppgift skall passera följande verktyg.

* `composer phpcs`
* `composer phpmd`

Du kan köra båda verktygen direkt via `composer test`.

Du måste stå i kagalogen `me/` när du kör ovan kommandon.



Uppgift 1: Ett menydrivet program i terminalen {#u1}
-----------------------

Skapa grunden för ditt menydrivna program. Följande menyval skall finnas.

```
1. Skriv ut detaljer om programmet
9. Avsluta
```

Om användaren skriver in `1` så skall programmet skriva ut en kort beskrivning av programmet samt vem som skrivit det. Koden för att utföra utskriften skall skrivas i en funktion `about()` som placeras i filen `functions.php`

Om användaren skriver in `9` så skall programmet avslutas via funktionen `exitProgram()` samt skriva ut ett avslutningsmeddelande.

När programmet startar skall du skriva ut en välkomsttext och en ascii-bild (välj själv motiv på bilden).

Om användaren skriver in ett val som inte finns så anropas en funktion `notValidChoice()` som skriver ut ett meddelande att det var ett felaktigt menyval.

När det valda menyvalet är utfört så visas menyn och ascii-bilden igen.

För tips, leta i manualen.

* [`readline()`](https://www.php.net/manual/en/function.readline.php)
* [`require()`](https://www.php.net/manual/en/function.require.php)
* [`match()`](https://www.php.net/manual/en/control-structures.match.php)



Uppgift 2: Detaljer om din PHP installation {#u2}
-----------------------

Lägg till menyvalet "2. Detaljer om PHP" som gör enligt följande.

* Skriv ut versionen av PHP.
* Skriv ut vilket operativsystem som ligger i botten av PHP-installationen.
* Sökväg till PHP binären.
* Visa värdet för konfigurationen av `display_errors` via `ini_get()`.
* Visa värdet för konfigurationen av `display_startup_errors` via `ini_get()`.

Döp funktionen till `printPhpVersion()`.

För tips, leta i manualen.

* [Predefined Constants](https://www.php.net/manual/en/reserved.constants.php)
* [`ini_get()`](https://www.php.net/manual/en/function.ini-get.php)



Uppgift 3: XXX {#u3}
-----------------------

Dagens tid och datum samt formattera.



Uppgift 4: XXX {#u4}
-----------------------

Stränghantering. Mata in en sträng och kör vissa modifikationer och tester på den strängen.

Eller mata in en text från fil och analysera den.
md, rot13, password_hash, password_verify

Check the strlen() and mb_strlen() of the word "skärgårdsö". Answer with the two results as a comma and space-separated string.



Uppgift 5: XXX {#u5}
-----------------------

You are going to solve the well-known ‘chessboard and rice grain problem’.

Imagine you have a standard chessboard and put one rice grain on the first square. Then you put two grains on the second square, four on the third, eight on the fourth and so on… How many rice grains are there on the last square?



Uppgift 6: XXX {#u6}
-----------------------

Create a function called fibonacci(). The function should use the Fibbonacci Sequence, starting with 1, 1, 2. Return the sum of all odd numbers in the sequence, when the sequence value dont exceed 1.000.000.

Answer with a call of the function. A Fibonacci-sequence can look like this: 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 etc. You add the current value with the last, i.e. 1+2=3, 3+2=5, 5+3=8 etc.


Uppgift 7: XXX {#u7}
-----------------------

arrayer. både med siffror och key/val
tänk på databas resultat
sortera array med siffror?
summera
medelvärde

implode, explode, serialized/unserialize from file



Uppgift 8: XXX {#u8}
-----------------------

Kolla vilka primtal som finns upp till en viss nivå?



Redovisning {#redovisa}
-----------------------

Besvara följande frågor i din redovisningstext.

* Berätta hur det gick att lösa uppgiften, var något extra svårt, lurigt, krångligt eller flöt det på smidigt?
* Är det något som du är extra nöjd med i ditt resultat från uppgifterna?



Publicera {#publicera}
-----------------------

Avsluta uppgiften så här.

1. Testa att din kod validerar genom att ställa dig i katalogen `me/` och köra dem via `composer test`.

1. Testa ditt resultat så att det passera de automatiska testerna med `dbwebb test php`.

1. När du är klar kan du publicera resultatet med `dbwebb publish php`.

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

Det handlar om grunder såsom variabler, if-satser, loopar, arrayer, funktioner och att dela upp koden i olika filer.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap om att programmera med PHP.

Du har PHP i din PATH och kan exekvera kommandot i terminalen.



<!--
Genomgång {#genom}
------------------------

Här är en video som "pratar" dig igenom uppgiftens upplägg och visar hur du kommer igång.

[YOUTUBE src="gKzwQTG9eCI" width=700 caption="Kurs mvc kmom03 tisdagsgenomgång, del 3/3 uppgiften (Zoom med Mikael)."]
-->



Introduktion och förberedelse {#intro}
-----------------------




Krav {#krav}
-----------------------

Utför följande krav.

1. Spara alla filerna i ditt kursrepo under `me/php`.

1. Skapa en fil `main.php` som är ditt huvudprogram som innehåller en meny där du kan välja vilken del av koden som skall köras. Användaren ombeds mata in ett menyval i terminalen.

1. Skapa en fil `function.php` som inkluderas av `main.php`. I denna filen lägger du till de funktioner som löser uppgifterna. I `main.php` anropar du funktionerna. Efter att en funktion är anropad skall menyn skrivas ut igen och användaren kan välja ett nytt menyval.

1. Det skall finnas ett menyval "9. Avsluta" och när man skriver in en 9 så avslutas programmet.

Så här kan det se ut.

```text
Välkommen till mitt PHP program.

1. Text för menyval 1
2. Text för menyval 2
3. Text för menyval 3
... och så vidare för alla menyval
9. Avsluta

Gör ditt val: _
```



### Uppgift 1 {#uppgift1}

1. XXX



Redovisning {#redovisa}
-----------------------

Besvara följande frågor i din redovisningstext.

* Berätta hur det gick att lösa uppgiften, var något extra svårt, lurigt, krångligt eller flöt det på smidigt?
* Är det något som du är extra nöjd med i ditt resultat från uppgifterna?



Publicera {#publicera}
-----------------------

Avsluta uppgiften så här.

1. Testa ditt resultat så att det passera de automatiska testerna med `dbwebb test php`.

1. När du är klar kan du publicera resultatet med `dbwebb publish php`.

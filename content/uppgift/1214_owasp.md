---
author:
    - lew
category: itsec
revision:
    "2019-11-26": (A, lew) Initial release.
...

OWASP {#owasp}
==================================

Uppgiften går ut på att analysera en applikation utefter sårbarheterna som listas i OWASPs top10 lista.

<!--more-->

Förkunskaper {#forkunskaper}
-----------------------------

Du har deltagit i lektionen som tillhör kursmomentet.



Installation {#installation}
-----------------------------

Börja med att kopiera in mappen med applikationen till er me-katalog:

```bash
# Flytta till kurskatalogen
$ rsync -ravd example/kmom04-app/ me/kmom05/owasp/
```



#### Docker

Starta applikationen med `docker-compose up -d`. Mer information finns i `README.md`



#### Utanför Docker

Följ installationsinstruktionerna i `README.md`



Intro {#intro}
-----------------------------

I kursmoment 03 skapades en sårbarhetsanalys av den här applikationen. Du ska nu utgå ifrån din tidigare analys och skapa en ny rapport, `kmom05/owasp.pdf`.



### Krav

Utöver ovanstående krav gäller följande:

* Jämför de sårbarheter du redan hittat med de som listas av OWASP. Kan du hitta ytterligare sårbarheter som återfinns i deras lista?
* Strukturera om din analys så du för varje sårbarhet beskriver hur man skulle gå tillväga för att hantera den.
* Beskriv för varje sårbarhet varför den är viktig att hantera.
    * Ge exempel på hur en attack skulle gå till.
    * Ge exempel på eventuella konsekvenser.


För ett godkänt betyg ska minst 3 sårbarheter identifieras och beskrivas.



Redovisa {#redovisa}
-----------------------

Publicera dina uppgifter:

```bash
# Flytta till kurskatalogen
$ dbwebb publish me
```

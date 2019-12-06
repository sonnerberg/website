---
author:
    - lew
    - nik
category: itsec
revision:
    "2019-12-06": (A, lew, aurora) First edition.
...

Sårbarhetsanalys - Del 2 {#analys}
========================================

Uppgiften går ut på att ni ska, utifrån eran tidigare sårbarhetsanalys och dess prioritering, välja ut sårbarheter och åtgärda dem i den mån av tid som finns för kursmomentet.

<!--more-->

Förkunskaper {#forkunksaper}
---------------------------------

Du har utfört uppgifterna [Sårbarhetsanalys](/uppgift/sarbarhetsanalys) och [OWASP](/uppgift/owasp).

Installation {#installation}
---------------------------------

```bash
# Flytta till kurskatalogen
$ rsync -ravd example/kmom03-app/ me/kmom06/app/
```

**OBS: Tänk på att återställa er databas om ni tagit sönder den i kmom03**

*Det går bra att ta bort applikationen i er kmom03 mapp (om ni har godkänt), så slipper ni att den tar plats på studentservern*

Uppgifter {#uppgifter}
---------------------------------

Utifrån er rapport, välj ut en sårbarhet och lös följande delar. Återupprepa tills ni antingen har löst de sårbarheter ni noterat eller tills tiden för kursmomentet tar slut.

### Skriv testfall

Skriv godtyckligt antal testfall (5+) per sårbarhet som demonstrerar hur man kan utnyttja sårbarheten och hur beteendet borde vara när det det fungerar som det ska. Dessa testfall ska vara gröna när ni åtgärdat sårbarheten.

Det går att använda valfri "testsuite", men rekommendationen ligger på PHPUnit tillsammans med `make test` eller `composer test` (mer om Composer Script [här](https://getcomposer.org/doc/articles/scripts.md#writing-custom-commands)).

### Patch:a problemet

Notera vilka ändringar ni gör och i vilka filer. Skriv även om tiden som ni trodde det skulle ta skiljde sig ifrån den tiden det faktiskt tog. Dubbelkolla att era testfall blir gröna.

Redovisa {#redovisa}
---------------------------------

Svara på följande frågor i en rapport som ni sparar som `me/kmom06/report.pdf`

* Vilka ändringar gjorde ni?
* Hur matchade er estimering gentemot slutresultatet? Hann ni åtgärda samtliga sårbarheter ni hittat?

Publicera er uppgifter:

```bash
# Flytta till kurskatalogen
$ dbwebb publish me
```

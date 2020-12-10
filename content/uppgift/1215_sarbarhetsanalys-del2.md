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

Du har utfört uppgifterna [Sårbarhetsanalys](/uppgift/sarbarhetsanalys).

Installation {#installation}
---------------------------------

[INFO]
**Innan ni börjar**

Tänk på att återställa er databas om ni tagit sönder den i kmom04 (gäller enbart om ni kör applikationen utanför Docker)
[/INFO]

```bash
# Flytta till kurskatalogen
$ rsync -ravd example/bank-app me/kmom05/
```

*Det går bra att ta bort applikationen från er kmom04 mapp, så slipper ni att den tar plats på studentservern*

Uppgifter {#uppgifter}
---------------------------------

Utifrån er rapport, välj ut en sårbarhet och lös följande delar. Återupprepa tills ni antingen har löst de sårbarheter ni noterat eller tills tiden för kursmomentet tar slut.

### Skriv testfall {#testfall}

Skriv godtyckligt antal testfall (3+) per sårbarhet som demonstrerar hur man kan utnyttja sårbarheten och hur beteendet borde vara när det det fungerar som det ska. Dessa testfall ska vara gröna när ni åtgärdat sårbarheten.

Testerna ska gå att köras via `npm test`.

### Åtgärda sårbarheterna {#atgarda}

Börja åtgärda sårbarheten och se till att era tester blir gröna. Om ni märker av att det behövs fler tester så skriver ni dit fler testfall.

Se till att era tester blir gröna med `npm test`.

### Uppdatera rapport {#uppdatera}

Lägg till ett nytt kapitel i er rapport ifrån kmom04 där ni noterar vilka ändringar ni gör och i vilka filer. Skapa en ny tabell som noterar vilka sårbarheter ni åtgärdat, vad er ursprungliga estimation var och hur lång tid det faktiskt tog att åtgärda.

Publicera {#Publicera}
---------------------------------

```bash
# Flytta till kurskatalogen
$ dbwebb publish me
```

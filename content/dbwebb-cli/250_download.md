---
author:
    - mos
revision:
    "2019-11-01": "(B, mos) Genomgången och uppdaterad med mer detaljer."
    "2015-03-23": "(A, mos) Arbetskopia för dbwebb-validate version 2."
...
Ladda ned från servern
==================================

Du kan ladda ned ditt kursrepo, eller delar av det, från studentservern till ditt lokala kursrepo.

Innan du kör kommandot bör du ta en kopia av din lokala katalog. Det är för att undvika att något går fel och dina lokala filer skrivs över på ett felaktigt sätt.

```text
dbwebb download
dbwebb download me
dbwebb download kmom01
dbwebb download lab1
```

Hela kursrepot, eller den valda delen, laddas ned från studentservern.

Om du har redigerat en fil lokalt så skall den inte skrivas över då dess ändringsdatum är senare än det ändringsdatum som finns på studentservern.

Vid överföringen justeras rättigheterna för de kataloger och filer som förs över. Du kan se detaljer för detta genom att lägga till switchen `-v` eller `--verbose` när du kör kommandot.



download -f {#f}
----------------------------------

Du kan forcera en exakt kopia av studentserverns innehåll vid nedladdningen. Det innebär att samtliga filer laddas ned och dina egna filer raderas om de inte finns på studentservern.

Du gör detta genom att lägga till switchen `-f` eller `-force`.



Dela kursrepon {#dela}
----------------------------------

Använd inte download som en metod för att jobba på flera datorer.

Vill du ha möjligheten att dela ett kursrepo mellan flera datorer så skall du se på kursrepot som ett orginal. Lägg detta orginal på ett usb eller en fildelningstjänst och på det sättet kan du använda samma kursrepo på flera olika datorer.



Vanlig användning {#anv}
----------------------------------

Lärarteamet använder download för att hämta dina filer och hjälpa dig med mer avancerad felsökning eller för att rätta dina inlämningar.

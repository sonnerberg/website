---
author: efo
category:
    - webbprogrammering
    - webapp
revision:
  "2018-02-20": (A, efo) Första utgåvan inför kursen webapp-v3.
...
Installera Android utvecklingsmiljö på Linux
==================================

[FIGURE src=/image/webapp/android-robot.png?w=c5 class="right"]

Denna guide visar dig hur du installerar de nödvändiga komponenterna av Android SDK för att kunna köra en Android emulator.

Jag kommer att installera endast det nödvändigaste för att få tillgång till emulatorn. SDK:n kan ta mycket plats på din hårddisk, om du bara installerar de absolut nödvändiga paketen tar det upp mot 6-7 GiB.



<!--more-->



Installera SDK {#sdk}
--------------------------------------
Du kan börja med att läsa översiktligt [om Android SDK och Android Studio](https://developer.android.com/sdk/index.html) som är ett mer komplett utvecklarverktyg.

Du kan behöva [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html), i så fall ladda ner det. Version 7 eller senare. Se till att den finns i din PATH. Du kan testa med `java --version` i terminalen.

För att installera Android SDK:n scrolla ner till [Get just the command line tools](https://developer.android.com/studio/index.html) och ladda ner ett **SDK tools package**. Det är inte meningen att ni ska ladda hem Android studio utan enbart Android SDK.

Extrahera innehållet till valfri plats, en rekommendation är att extrahera innehållet till en katalog `android` i din hemmakatalog.



Avslutningsvis {#avslutning}
--------------------------------------
Nu har du förhoppningsvis kommit igång med Cordova på iOS och har skapat HelloWorld exemplet och har kört exemplet i Simulatorn och på din fysiska enhet.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7311) om denna artikeln.

Du kan även hittar mer info i [Cordovas egna Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/index.html).

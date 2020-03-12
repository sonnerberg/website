---
author: lew
category:
    - webbprogrammering
    - kursen vlinux
revision:
    "2020-03-11": (B, lew) Uppdatering inför HT20
    "2019-04-05": (A, lew) Uppdatering inför HT19
...
Skapa en me-sida till vlinux-kursen
==================================

Skapa en me-sida för redovisningar i kursen vlinux.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har installerat kursens labbmiljö samt installerat kommandot `dbwebb` och du har clonat kursrepot.



Introduktion {#intro}
-----------------------

I din me-sida skall du samla redovisningstexter och du länka till de uppgifter du löst. Det ger dig en samlad plats att utgå ifrån när du vill visa upp vad du gjort i kursen.

Du kan testa hur me-sidan bör fungera, genom att öppna din exempel-katalog i kursrepot under `example/redovisa`.

Du kan bygga en mer avancerad me-sida om du vill, det går bra. Mallen finns med för de som vill ha en enkel me-sida.

Senare i kursen är det valfritt hur man vill göra sin me-sida. Då är det fritt fram att byta språk men för stunden kör vi en enkel html-sida.



Krav {#krav}
-----------------------

I din kurskatalog (repot) för kursen, skall du ta en kopia av exempelkatalogen `example/redovisa` och lägga i din me-katalog under `me/redovisa`.

```bash
# Gå till kurskatalogen
cp -ri example/redovisa me/
```

1. Du har nu en grund för din me-sida i kursen. Modifiera den så den blir "din egen".

1. Uppdatera sidan `me.html` så att den innehåller en kort presentation av dig själv tillsammans med en bild som får representera dig.

1. I sidan `redovisning.html` skall du skriva dina redovisningstexter. Du kan förbereda redovisningstexten för det första kursmomentet.

1. I sidan `om.html` lägger du till en godtycklig bild som du finner representativ för kursen.

1. Leta reda på kursrepot på GitHub och länka till det från din `om.html`.

1. Du kan uppdatera stylesheet och eventuellt JavaScript i katalogerna `me/style` och `me/js`. Det är inte nödvändigt, gör det om du vill och känner att du har tid.

1. Gör en dbwebb publish för att kolla att allt validerar och fungerar.

```text
dbwebb publish redovisa
```



Extrauppgift {#extra}
-----------------------

Om du har tid och kraft.

1. Bygg en snyggare och mer avancerad me-sida.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

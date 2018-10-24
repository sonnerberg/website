---
author: mos
category:
    - kursen design
    - anax flat
    - less
revision:
    "2018-10-15": "(A, mos) Kopia från 'Bygg en ut ditt Anax Flat med eget LESS tema' och omskriven."
...
Bygg ett tema med vertikalt och horisontellt grid
===================================

Du skall bygga ett tema och implementera stöd för ett vertikalt grid och för ett horisontellt grid.

Du bygger temat så att det är responsivt baserat på ditt vertikala grid.

<!--more-->

[WARNING]

**Kursutveckling pågår till kurs design v2**

Dokumentet är under bearbetning inför kursstarten höstn 2018.

[/WARNING]



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom kmom02 i design-kursen.

Du har läst läsanvisningar och har viss förståelse för vad ett vertikalt grid är.

Du har läst läsanvisningar och har viss förståelse för vad ett horisontellt grid är. Andra ord för samma sak är typografiskt grid, baseline grid och vertikal rytm.



Introduktion och förberedelse {#intro}
-----------------------

Gör följande steg för att förbereda dig för uppgiften.

Du kan se hur jag jobbar igenom stegen i videoserien "[Bygg ett tema med vertikalt och horisontellt grid](https://www.youtube.com/playlist?list=PLKtP9l5q3ce9QJnBXk-hLEBZH035xObxS)".

[YOUTUBE src="XXX" list="PLKtP9l5q3ce9QJnBXk-hLEBZH035xObxS" width=700 caption="Videoserie som ger dig en introduktion till de olika delarna i att lösa uppgiften."]



### Skapa tema för kmom03 {#temakmom03}

Börja med att skapa ett nytt tema för detta kursmomentet, döp det till `kmom03` och spara filen i `theme/src/kmom03.less`. Du kan använda grunden från ditt tidigare tema `kmom02`.



### Implementera ett vertikalt grid {#vgrid}

Innan du börjar med detta så blir det enklast om du nollställer alla widths, padding, border och positioneringssätt på dina regioner. Allra enklast är troligen att använda en ny tom `layout/layout_vgrid.less` och implementera integrationen av gridet där. 

Du skall använda dig av ett vertikalt grid i form av modulen [desinax/vertical-grid](https://github.com/desinax/vertical-grid/). I README-filen står det hur du integrerar gridet i ditt eget tema.

Modulen finns redan installerad i ditt repo under `theme/src/@desinax/vertical-grid` så du beheöver inte installera det.

När du börjar integrera så använd de standardinställningar som finns.

Se till att man kan göra showgrid på ditt grid genom att lägga till `?vgrid` på länken till godtycklig sida. Ramverket har stöd för att lägga till klassen `.vgrid` i elementet `<html>`, men du behöver implementera så att gridet verkligen visas.



### Implementera ett horisontellt grid {#hgrid}





### Bekanta dig {#bekanta}

Du kan ta hjälp av videoserien för att kolla in hur man gör ovanstående och hur det kan se ut.

* Hur styla med det vertikala gridet för att få en responsiv webbplats.
* HUr fungerar `?vgrid` och `?hgrid`?



Krav {#krav}
-----------------------

1. Lägg till en stylesheet `theme/src/kmom03.less` (tema för kmom03), återanvänd de moduler du utvecklat i samband med kmom02, eller gör nya.

1. I temat för kmom03, lägg till det vertikala gridet och styla regionerna i din webbplats enbart med gridet. Använd `@desinax/vertical-grid`.

1. I temat för kmom03, lägg till det horisontella gridet. Gör ett medvetet val av typsnitt och eventuellt så stylar du din typgrafi. Använd `@desinax/typografic-grid`.

1. Gör din webbplats responsiv med hjälp av ditt vertikala grid. 

1. Man skall kunna visa ditt grid med `?vgrid` och `?hgrid` på godtycklig sida.

1. Aktivera din style `kmom03` som default stylesheet i styleväljaren.

1. Gör en `dbwebb publishpure redovisa` och kontrollera att allt fungerar på studentservern.

1. Committa alla filer, inklusive temats filer och lägg till en (ny) tagg (2.0.\*).

1. Pusha repot till GitHub, inklusive taggarna.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

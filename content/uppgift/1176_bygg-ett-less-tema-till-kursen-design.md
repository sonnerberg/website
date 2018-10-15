---
author: mos
category:
    - kursen design
    - anax flat
    - less
revision:
    "2018-10-15": "(A, mos) Kopia från 'Bygg en ut ditt Anax Flat med eget LESS tema' och omskriven."
...
Bygg ett LESS-tema till kursen design
===================================

Du skall bygga ett tema till din redovisa-sida och du bygger temats stylesheet med hjälp av LESS.

<!--more-->

[WARNING]

**Kursutveckling pågår till kurs design v2**

Dokumentet är under bearbetning inför kursstarten höstn 2018.

[/WARNING]



Förkunskaper {#forkunskaper}
-----------------------

Du har sedan tidigare en version av din redovisa-sida som är ett eget repo på GitHub och det är taggat i minst version 1.0.0.

Du har en labbmiljö som motsvarar [labbmiljön för kursen design och kmom02](kurser/design-v2/kmom02#labbmiljo).



Introduktion och förberedelse {#intro}
-----------------------

Gör följande steg för att förbereda dig för uppgiften.

Du kan se hur jag jobbar igenom stegen i videoserien "[Bygg ett LESS-tema till kursen design](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-HCkrXAcedUGv14A68Sv57)".

[YOUTUBE src="XXX" list="PLKtP9l5q3ce-HCkrXAcedUGv14A68Sv57" width=700 caption="Videoserie som ger dig en introduktion till de olika delarna i att lösa uppgiften."]



### Kopiera från example/redovisa {#kopiera}

Det finns en katalog som är förberedd för att jobba med ett LESS-tema till din redovisa-sida i design-kursen. Kopiera den och installera sedan det som behövs.

```text
# Stå i rooten av kursrepot
rsync -av example/tema/ me/redovisa/theme/
cd me/redovisa
make install
```

Du har nu en katalog `redovisa/theme` som innehåller en utvecklingsmiljö för LESS-teman kopplade till din redovisa-sida. Kolla snabbt runt i den för att se vad den innehåller.

För att komma igång och börja bygga dina egna LESS-teman så behöver du installera en utvecklingsmiljö.

```text
# Stå i me/redovisa
make install
```

Kommandot make ser till att installera det som behövs.



### Bygg ditt första LESS-tema {#makeless}

Att göra kmom01.css till ett LESS-tema för kmom02.less och visa `make less` och berätta vilka filer som kopieras vart.

Bygg även ett `test.less` som är helt tomt, men går bra att använda för att testa LESS konstruktioner.



### Nollställ stylen med Normalize {#normalize}

Visa hur man lägger till Normalize som en LESS-modul och importerar modulen till sitt eget tema.



### Lägg till Font Awesome {#fontawesome}

Visa hur man lägger till Font Awesome som en LESS-modul och importerar modulen till sitt eget tema, inklusive katalogen för webbfonter.



### Bekanta dig {#bekanta}

Du kan ta hjälp av videoserien för att till exempel kolla in följande.

* Vad är skillnaden mellan temats `src/kmom02.less` och modulerna `src/base/kmom02.less` och `src/layout/kmom02.less`?
* Hur kan man styla innehållskolumnerna för 1, 2 eller 3-kolumners layout?
* Hur stylar man responsivt?

Navbaren, när var och hur kommer den in i flödet?



Krav {#krav}
-----------------------

1. Lägg till en stylesheet `theme/src/kmom02.less` med begränsat av style till webbplatsen. Du får utrymme att jobba vidare med stylen i nästa kmom.

1. Nollställ stylen genom att använda Normalize.

1. Fördela din bas style till modulen `theme/src/base/kmom02.less`.

1. Fördela din layout style till modulen `theme/src/layout/kmom02.less`.

1. Aktivera din style `kmom02.min.css` som default stylesheet i styleväljaren.

1. Skapa ett enklare bastema till din webbplats. Du behöver inte styla jättemycket, det kommer fler möjligheter under kursen. Men, det måste vara ett hyffsat gott grundtema. Inget slarv.

1. Header-delen skall vara stylad och se helt okey ut.

<!--
1. Den style du gör för din meny/navbar skall vara organiserad som en egen LESS-modul i ditt tema.
-->

1. Menyn skall vara väl fungerande och responsiv. Var noga med att lägga dina mediaqueries i slutet av LESS-koden, ordningen är viktig.

1. Du skall använda två menyer, den "vanliga" (navbarTop) och den som är anpassad för små skärmar (navbarMax).

1. Innehållsdelen och eventuella sidokolumner skall se bra och och fungera responsivt.

1. Footer och footerkolumnerna skall se bra ut och fungera responsivt.

1. Gör en `dbwebb publishpure redovisa` och kontroller att allt fungerar på studentservern.

1. Committa alla filer, inklusive temats filer och lägg till en (ny) tagg (2.0.\*).

1. Pusha repot till GitHub, inklusive taggarna.

<!--
1. Se till att ditt tema passerar testerna som körs vid `make test`.
-->

<!--
1. Man kan importera FontAwesome som en LESS-modul. Men det kan vara lite utmanande. Om man gör det så behöver man även ta hand om en font-katalog och kopiera den från FontAwesome till `htdocs`. Ge dig på detta om du känner dig mogen för en utmaning. Det är så jag själv brukar göra i mina teman.
-->



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

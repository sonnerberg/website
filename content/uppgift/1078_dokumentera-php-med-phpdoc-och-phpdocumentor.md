---
author:
    - mos
category:
    - php
    - kurs oophp
    - anax-lite
    - anax
revision:
    "2018-03-20": "(B, mos) Avidentifiera anax-lite."
    "2017-04-21": "(A, mos) Första utgåvan."
...
Dokumentera PHP med phpdoc och phpDocumentor
==================================

[FIGURE src=image/snapvt18/phpdocumentor.png?w=c5 class=right]

Du ska dokumentera ditt projekt med phpdoc och phpDocumenter. Det handlar om att dra nytta av dina docblock kommenterarer när du nu skall automatgenerera din dokumentation.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har tillgång till ett projekt med en Makefile som stödjer att installera phpdoc och generera dokumentation.



Introduktion {#intro}
-----------------------

Låt oss göra det enkelt. Det handlar om att använda [phpDocumenter, aka phpdoc](https://www.phpdoc.org/) för att automatgenerera dokumentation av dina klasser i ditt projekt.

Förbered dig så här.

```bash
# Gå till ditt projekt
$ make help
...
install            - Install all tools
doc                - Generate documentation.
...
```

Du behöver nu installera verktygen och sedan kan du automatgenerera dokumentationen.

```text
make install
mkdir doc
make doc
firefox doc
```

Du behöver en katalog som heter `doc` i ditt projekt, annars genereras inte dokumentationen.

När kommandot phpdoc körs av Makefilen så används konfigurationsfilen `.phpdoc.xml` och den styr vilka kataloger där källkoden hämtas.

Om du saknar en konfigurationsfil så kan du låna en från Anax moduler.

```text
cp vendor/anax/request/.phpdoc.xml .
```

Det som händer är att du använder en av funktionerna som redan finns implementerad i Makefilen. Den installerar verktyget phpdoc i `.bin/phpdoc` och kör det och det genereras dokumentation förutsatt att du har en konfigurationsfil samt en katalog `doc` där dokumentationen kan sparas.

Var nyfiken och kika i konfigurationsfilen `.phpdoc.xml`.



Krav {#krav}
-----------------------

1. Använd phpdoc, via `make doc` för att skapa dokumentation till ditt projekt.

1. Checka in och committa dokumentationen som en del av ditt repo.

1. Validera och publicera.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

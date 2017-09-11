---
author:
    - mos
category:
    - anax
    - php
    - kursen ramverk1
revision:
    "2017-09-11": "(A, mos) Första utgåvan."
...
Skapa en PHP-modul på Packagist och integrera med Anax
==================================

[FIGURE src=image/snapht17/book-update.png?w=c5&cf&a=10,60,20,0 class="right"]

Vi skall se hur vi kan lyfta ut en kodbas som är integrerad i en Anax installation. Vi tar den kodbasen och lägger i ett eget Git-repo som vi publicerar på GitHub. Vi gör en modul av repot och publicerar det på Packagist.

Därefter kan vi åter installera samma kodbas, nu med verktyget composer, in i en installation av Anax.

För att ha en kodbas att jobba på så använder jag mig av REM-servern och skapar en fristående modul som blir enkel att integrera i en godtycklig Anax installation.

<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har god kunskap i REM servern som används i tidigare artiklar som exempelkod. Senaste artikeln som berörde REM servern var "[Att konfigurera routern i Anax](kunskap/att-konfigurera-routern-i-anax)".



En fungerande REM server {#remserver}
--------------------------------------

Dubbelkolla att du har en fungerande REM server i `kmom02/remserver`. Jag kommer att utgå från branchen `route` när jag nu skall skapa ett eget repo för koden.

Nåväl, REM servern ligger redan i ett eget repo. Men där finns också mer saker som gör att det repot är en egen installation av Anax. Precis som en me-sida är en installation av Anax med tillhörande moduler. Jag vill nu lyfta ut enbart de sakerna som är relevanta för en REM server och placera dem i en egen modul. Tanken är inte att man skall kunna hämta det repot och starta upp en REM server, tanken är att man installerar Anax och sedan lägger till REm servern som en fristående modul med hjälp av composer. Precis som man gör med alla andra Anax-moduler.

Skillnaden är att vi får en mer fristående modul för REM servern som kan bli enklare att återanvända när man har behovet av en REM server i sin Anax installation.

Man kan tycka att det är nästan samma sak som det vi har i dag. Men det är inte enkelt att använda composer för att idag installera REM servern som en del i en me-sida, en installation av Anax. Men det skall vi lösa nu.

I vilket fall som så behöver jag ett kodexempel nu när jag skall visa hur du kan jobba med Packagist och REM servern passar bra till det.


**ARBETE PÅGÅR**

<!--stop-->



Avslutningsvis {#avslutning}
--------------------------------------

Vi har gått igenom hur formulärhantering och databashantering med databasdrivna modeller som implementeras via Active Record kan byggas ihop till en samling av klasser och filer som kan scaffoldas fram.

Vi har sett hur vi kan integrera den scaffoldade koden in i vårt eget ramverk och vi får en känsla för hur andra liknande moduler kan scaffoldas fram. Dessutom får vi ett större kodexempel på hur CRUD kan fungera i våra databasdrivna modeller.

Denna artikel har en [egen forumtråd](t/6766) som du kan ställa frågor i, eller bidra med tips och trix.

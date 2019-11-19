---
author:
    - lew
    - nik
category: itsec
revision:
    "2019-10-11": (A, lew, aurora) First edition.
...

Sårbarhetsanalys {#analys}
==================================

Uppgiften går ut på att analysera en applikation efter sårbarheter.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har deltagit i föreläsningarna som tillhör kursmomentet.  


Krav {#krav}
-----------------------

Börja med att kopiera in mappen med applikationen till er me-katalog:

```bash
# Flytta till kurskatalogen
$ rsync -ravd example/kmom03-app/ me/kmom03/app/
```

Starta applikationen med `docker-compose up -d`.

1. Analysera applikationen efter sårbarheter enligt de metoder som nämndes under föreläsningen ([se här](https://bth.instructure.com/files/201806)).

1. Döp analysen till `me/kmom03/analys.pdf`.



```bash
# Flytta till kurskatalogen
$ dbwebb publish kmom03
```

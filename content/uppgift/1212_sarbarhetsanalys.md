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


Analys {#analys}
-----------------------

Er analys ska innehålla en summering, metodbeskrivning av hur ni gjort, en rankad lista över risker, samt en sammanfattning på vilka som är de högst prioriterade sårbarheterna (gärna i tabellform). Listan över risker och sårbarheter ska ni rangordna och er rankning bör även motiveras.

Listan bör innehålla följande egenskaper för varje risk/sårbarhet:

* Risk/sårbarhet (namn)
* Beskrivning
* Allvarlighetsgrad
* Sårbarhetsklassificering
* Prioritet/rank

Metodbeskrivningen bör visa hur ni har gått tillväga, t.ex. om ni använt attackträd, use-cases, eller någon annan metodik. Era eventuella attackträd eller visualiseringar ska också tas med i rapporten.

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

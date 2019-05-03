---
author: lew
revision:
    "2019-04-30": "(A, lew) Första versionen."
...
Radera nätverket
=======================

När vi vill radera nätverket behöver vi först stoppa kontainrarna som använder det. Kommandot `$ docker ps` visar vilka aktiva kontainrar vi har. Använd `$ docker stop <id>` eller `$ docker stop <name>` för att stoppa dem.

Vi kan sedan ta bort nätverket med:

```
$ docker network rm dbwebb
dbwebb
```

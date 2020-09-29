---
author: lew
revision:
    "2019-04-11": (A, lew) Första utgåvan inför HT19.
...
En webbserver i Docker
===================================

Du skall skapa en Docker image och publicera den till Docker Hub.
Imagen ska vara en webbserver som ska kunna svara på en uppsättning routes och returnera JSON.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har läst igenom guiden [Hantera applikationer](guide/docker/hantera-applikationer) och valt ett språk du vill använda. Kika gärna på alla, då det kan göras på olika sätt.

Du har läst kurslitteraturen och skaffat dig grundläggande kunskaper om bash.



Introduktion {#intro}
-----------------------

I exempelmappen finns en [JSON-fil](https://github.com/dbwebb-se/vlinux/tree/master/example/json) som ska servas med hjälp av en router, byggd i språket du valt. Du väljer själv hur du vill sköta "routingen". Om du vill köra med PHP, finns en [minimal router](https://github.com/dbwebb-se/vlinux/tree/master/example/php-router) i exempelmappen du kan utgå ifrån. Tips finns i tillhörande README.md-fil.

Routes som ska stödas är:

| Route                 | Vad skall returneras                            |
|-----------------------|-------------------------------------------------|
| `/`                   | En presentation av de olika routesen.           |
| `/all`                | Hela JSON-filen.                                |
| `/names`              | Namnen på alla växterna.                        |
| `/color/<color>`      | Alla växter som kan ha &lt;color&gt; som färg   |

JSON-filen kopierar du från exempelmappen:

```bash
# Ställ dig i kursroten
$ cp -r example/json/items.json me/kmom04/data/
```

Krav {#krav}
-----------------------

1. Bygg en router som kan svara på "routsen" ovan. Alla svar ska vara JSON.

1. Skapa en Dockerfile `server/Dockerfile` och lägg till din server. Mappen med JSON-filen ska läggas till som en volym.

1. Bygg din image med namnet *username/vlinux-server:latest* där du använder ditt egna användarnamn.

1. Publicera imagen till Docker Hub.

1. Skapa en fil `server/dockerhub.txt` som innehåller två rader.  
```
Porten servern lyssnar på
username/imagename:tag
```

<!-- 1. Skapa ett exekverbart script `script/kmom04.bash` som kör din kontainer med rätt namn och tagg. Tänk på att lägga till volymen här. Servern ska vara nåbar via webbläsaren på porten `8080`. -->



```bash
# Flytta till kurskatalogen
$ dbwebb validate server
$ dbwebb publish server
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.  



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

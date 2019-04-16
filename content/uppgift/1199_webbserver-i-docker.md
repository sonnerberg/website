---
author: lew
revision:
    2019-04-11: (A, lew) Första utgåvan inför HT19.
...
En webbserver i Docker
===================================

Du skall skapa en Docker image och publicera den till Docker Hub.
Imagen ska vara en webbserver som ska kunna svara på en uppsättning routes och returnera JSON.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har läst igenom guiden [Hantera applikationer](guide/docker/hantera-applikationer) och valt ett språk du vill använda.

Du har läst kurslitteraturen och skaffat dig grundläggande kunskaper om bash.



Introduktion {#intro}
-----------------------

I exempelmappen finns en [JSON-fil](https://github.com/dbwebb-se/vlinux/tree/master/example/json) som ska servas med hjälp av en router, byggd i språket du valt. Du väljer själv hur du vill sköta "routingen". Om du vill köra med PHP, finns en [minimal router](https://github.com/dbwebb-se/vlinux/tree/master/example/php-router) i exempelmappen du kan utgå ifrån. Tips finns i README.md-filen



Krav {#krav}
-----------------------

1. Skapa en Dockerfile `script/Dockerfile` som använder sig av imagen `debian:stretch-slim`.

1. Kopiera in ditt egna `commands.bash` in i kontainern, till arbetsmappen `kmom03`.

1. Gör scriptet körbart inuti kontainern.

1. Vid uppstart ska kommandot `commands.bash all` köras.

1. Bygg din image med namnet *username/vlinux:kmom03* där du använder ditt egna användarnamn.

1. Publicera imagen till Docker Hub.

1. Skapa ett script `script/kmom03.bash` som kör din kontainer med rätt namn och tagg.


```bash
# Flytta till kurskatalogen
dbwebb validate kmom03
dbwebb publish kmom03
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.  



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

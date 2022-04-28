---
author: lew
revision:
    "2019-04-11": (A, lew) Första utgåvan inför HT19.
...
Skapa en Docker image
===================================

Du skall skapa en Docker image och publicera den till Docker Hub.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har [installerat Docker](kunskap/installera-virtualiseringsmiljon-docker) som en del av labbmiljön. Du har även skapat ett konto på Docker Hub.

Du har gjort uppgifterna "[Lab1](uppgift/linux-lab-1-introduktion-till-bash)" och [Bash-script med argument options](uppgift/ett-bash-script-med-options-command-arguments).

Du har läst kurslitteraturen och skaffat dig grundläggande kunskaper om bash.



Introduktion {#intro}
-----------------------

Du ska skapa en Docker image där det ska gå att köra scriptet som ligger i mappen `script/`. Imagen ska sedan publiceras på Docker Hub.


[INFO]
**TIPS:**
 Använd [guiden för Docker](guide/docker). Du bör klara dig med informationen fram till och med [Docker Hub](guide/docker/docker-hub).
[/INFO]



Krav {#krav}
-----------------------

1. Skapa en Dockerfile `ex2/Dockerfile` som använder sig av imagen `ubuntu:22.04`.

1. Kopiera in ditt egna `ex1/commands.bash` in i containern, till arbetsmappen `kmom02`.

1. Dubbelkolla så scriptet är körbart inuti kontainern.

1. Vid uppstart ska kommandot `commands.bash all` köras. Dubbelkolla så alla program är installerade.

1. Bygg din image med namnet *username/vlinux-commands:latest* där du använder ditt egna användarnamn.

1. Publicera imagen till Docker Hub och se till så den är publik.

1. Skapa en fil `ex2/dockerhub.txt` som ENDAST innehåller *username/imagename:tag*.

<!-- 1. Skapa ett script `script/kmom03.bash` som kör din kontainer med rätt namn och tagg. -->


```bash
# Flytta till kurskatalogen
$ dbwebb validate kmom02
$ dbwebb publish kmom02
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.  



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

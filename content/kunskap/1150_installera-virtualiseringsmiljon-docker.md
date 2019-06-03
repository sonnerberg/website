---
author: lew
category: labbmiljo
revision:
    "2019-03-08": (A, lew) Första utgåvan.
created: "2019-03-08 10:49:30"
...
Installera virtualiseringsmiljön Docker
==================================

Vi lutar oss mot Dockers egna dokumentation för installationsanvisningar, [https://docs.docker.com/](https://docs.docker.com/). Fortsätt läsa för att se hur du går vidare.

[INFO]
Ett tips för Windows 10 Home är att installera Docker för Linux i din VirtualBox. Det kommer underlätta framöver och vi håller oss kvar i Linuxmiljön. I dagsläget finns det inget stöd för Hyper-V i Windows Home 10.
[/INFO]

<!--more-->



Hämta installationsprogrammet {#download}
---------------------------------

Webbplatsen för Docker innehåller en del där du kan ladda hem och installera Docker. Det finns en Community Edition (CE) versioner för Windows, Mac och Linux. Kör igenom installationen enligt anvisningarna.

* [Windows](https://docs.docker.com/docker-for-windows/install/)

* [MacOs](https://docs.docker.com/docker-for-mac/install/)

* [Linux (Debian)](https://docs.docker.com/install/linux/docker-ce/debian/)

* [Linux (Ubuntu)](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

Docker är en virtualiseringsmiljö så den kräver att din datorn är kapabel att köra vissa virtualiseringstekniker.

Du behöver bekanta dig med [dokumentationen för Docker](https://docs.docker.com/). Det är din vägledare för att komma igång med Docker.



Tips vid installation
---------------------------------

Nu har du förhoppningsvis installerat Docker CE. Det kan såklart krångla med installationen så här samlar vi lite tips och trix når något går snett. Om du inte väljer att installera Docker för Linux kan det vara bra att tänka på följande.



### Windows, VirtualBox och Hyper-V {#win-vb-hyper-v}

Att tänka på är att Docker till Windows använder *Hyper-V* för virtualiseringen, vilket inte VirtualBox gör så det går inte att ha båda teknikerna fungerande samtidigt. Hyper-V är Microsofts egna system för virtualisering av servrar. Antingen får du aktivera Hyper-V. Klicka på startmenyn och skriv "Hyper-v" så dyker det upp ett resultat "Turn Windows features on or off" (eller motsvarigheten på svenska). Däri finns möjligheten att aktivera/avaktivera Hyper-V. Det kräver en omstart.

Ett annat alternativ är att installera Docker i din VM från tidigare kursmoment. Du installerar då Docker för Linux. Om VirtualBox fungerar fint bör det inte vara några problem. Det kommer att kräva en port forward till i kommande kursmoment, men det ger sig nog.

I skrivande stund är Docker i VirtualBox testat på Windows 10 Pro med 8GB RAM.



### Windows, Docker och bcrypt {#dockerbcrypt}


Ibland kan kombinationen av Windows, Docker och npm modulen bcrypt ställa till med stora problem. Ett tips hämtat från [installationsmanualen för bcrypt](https://github.com/kelektiv/node.bcrypt.js/wiki/Installation-Instructions#microsoft-windows) är att installara npm paketet `windows-build-tools` med kommandot nedan. Installera det i kommandotolken (cmd) eller Powershell så Windows har tillgång till det.

```bash
npm install --global --production windows-build-tools
```



Verifiera installationen {#verify}
---------------------------------

Nu är Docker (förhoppningsvis) installerat. Det är lika bra att dubbelkolla...

```bash
$ docker --version
Docker version 17.09.0-ce, build afdb6d4
```

```bash
$ which docker
/usr/bin/docker
```

Bra då vet vi var vi har det installerat och att kommandot `docker` fungerar. Vi kör vår första kontainer:

```bash
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:2557e3c07ed1e38f26e389462d03ed943586f744621577a99efb77324b0fe535
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

Vad som hände ovan är att Docker letar lokalt efter en image `hello-world` med taggen `latest`. Om den inte hittar den lokalt laddas den ned från Docker Hub och kontainern startas. Just den här kontainern är inte så spännande men nu vet vi att det fungerar!



Avslutningsvis {#avslutning}
--------------------------------------

Nu har du förhoppningsvis en fungerande Dockerinstallation.

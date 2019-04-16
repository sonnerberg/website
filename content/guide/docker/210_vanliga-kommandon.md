---
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Några vanliga kommandon
=======================

Vi har provat att starta en kontainer som laddades ned från Docker Hub. Vad Docker Hub är tar vi lite senare i guiden. Hur kan vi se vilka kontainrar som är startade? Vilka images har vi? Docker sparar all information på olika platser beroende på operativsystem.

* Linux: */var/lib/docker/*
* Mac: *~/Library/Containers/com.docker.docker/Data/vms/0/Docker.raw*
* Windows: *C:\Users\Public\Documents\Hyper-V\Virtual Hard Disks\MobyLinuxVM.vhdx*

Vi ska inte gå in i mapparna/filerna och pilla utan vi använder Dockers CLI och hanterar det därifrån.



### Några bra-att-ha-kommandon {#bra-att-ha}

| Kommando                    | Vad gör det?                          |
|-----------------------      |------------------------------------   |
| docker --help               | Hjälp om docker                       |
| docker images               | Listar alla nedladdade images         |
| docker search &lt;image&gt; | Söker efter en image på Docker Hub    |
| docker ps                   | Listar alla kontainrar                |
| docker rm &lt;id&gt;        | Tar bort en eller flera kontainer     |
| docker rmi &lt;id&gt;       | Tar bort en eller flera images        |
| docker start &lt;id&gt;     | Startar en eller flera kontainrar     |
| docker stop &lt;id&gt;      | Stoppar en eller flera kontainrar     |
| docker pull &lt;image&gt;   | laddar ner en image utan att köra den |
| docker run &lt;image&gt;    | Starta en kontainer från en image     |

Istället för ett id kan vi använda namnet på kontainern. Om vi inte har satt det själva autogenereras ett namn. Hur kan man se den informationen då? Först behöver vi en startad kontainer:

`$ docker run --rm -it debian:stretch:slim`

Flaggan `-it` gör att vi får ett interaktivt shell att jobba med. (Se `docker run --help`).  
Flaggan `--rm` rensar automatiskt upp efter oss när vi stänger kontainern.

Öppna sedan en ny terminal och kör `$ docker ps`:

```bash
$ docker ps
CONTAINER ID    IMAGE                COMMAND   CREATED        STATUS          PORTS           NAMES
4802628e331d    debian:stretch-slim  "bash"    5 seconds ago  Up 4 seconds                    distracted_mclean
```

Här får vi fram id, image, givet kommando och vilka namn kontainrarna har. På ovan kontainer kan då köra tex:

```
$ docker stop distracted_mclean
```

Om vi kör `$ docker images` och ser:
```
<none>     <none>     cb3e76fda019     2 weeks ago     87.3MB
```

så har vi lyckats skapa images som inte är kopplade till någon taggad version (vi kommer till taggning senare). Vi kan rensa lite emellanåt med `docker rmi $(docker images -f "dangling=true" -q)`. Det kallas *Prune dangling images*. Vill vi istället rensa helt kör vi `$ docker system prune -a`. **Vi får då bygga om de images som inte har blivit pushade**. 

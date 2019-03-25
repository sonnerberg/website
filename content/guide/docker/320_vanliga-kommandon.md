---
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Några vanliga kommandon
=======================

Vi har provat att starta en kontainer som laddades ned från Docker Hub. Vad Docker Hub är tar vi lite senare i guiden. Hur kan vi se vilka kontainrar som är startade? Vilka images har vi? Docker sparar all information i mappen `/var/lib/docker/` på Linux. Har du Mac så ligger all information i en fil: `~/Library/Containers/com.docker.docker/Data/vms/0/Docker.raw` och på Windows finns informationen i `C:\Users\Public\Documents\Hyper-V\Virtual Hard Disks\MobyLinuxVM.vhdx`. Vi ska inte gå in i mapparna/filerna och pilla utan vi använder Dockers CLI och hanterar det därifrån.



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

Istället för ett id kan vi använda namnet på kontainern. Om vi inte har satt det själva autogenereras ett namn. Hur kan man se den informaitonen då? Först behöver vi en startad kontainer:

`$ docker run -it debian:stretch:slim`

Flaggan `-it` gör att vi får ett interaktivt shell att jobba med. (Se `docker run --help`).

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

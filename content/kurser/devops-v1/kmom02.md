---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom02: Docker
==================================

Vi packar in vår kod i en Docker container för att underlätta utveckling, driftsättning och körning av vår applikation.

<!-- more -->
[FIGURE src="https://pics.me.me/it-works-on-my-machine-then-well-ship-your-machine-62072263.png" caption="Varför docker uppfanns."]

[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]
<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



## Vad är Docker? {#docker}

En snabb översikten av vad Docker är kan vi hitta på [Dockers egna webbsida](https://www.docker.com/resources/what-container). Docker är en container teknologi som liknar en avskalad virtuelle maskin. Vad tillför det till oss som utvecklare?

Docker låter utvecklare att utveckla och driftsätta applikationer i virtuella container miljöer. Detta ska göra att en applikation kan köras på exakt samma sätt utan kompabilitets problem oberoende av vilken dator/server den körs på, så länge Docker är installerat. Att applikationen kan köras oberoende av systemet gör att applikationen blir lättare att använda, utveckla och underhålla och driftsätta.



### Docker terminologi {#terminologi}

- Image: En image är typ ett exekverbart paket som innehåller allt som behövs för att köra applikationen, det inkluderar konfigurationsfiler, miljö variabler och bibliotek.
- Dockerfile: Fil som innehåller instruktionerna för att bygga en Docker image.
- Build: Skapa en image snapshot från Dockerfile.
- Tag: Version av en image. Varje image har ett tag namn.
- Container: Ett lättviktig program paket skapat från en specifik image version. 
- DockerHub: Image repository där vi kan hitta images. Typ GitHub för images.
- Docker Daemon: Körs på host systemet. Användare kan inte jobba direkt mot Docker daemon utan gör det via Docker klienter.
- Docker Engine: Skapar och kör Containers.
- Docker Client: Huvud interfacet för Docker.


Labbmiljön  {#labbmiljo}
---------------------------------

https://dbwebb.se/kunskap/installera-virtualiseringsmiljon-docker
https://dbwebb.se/guide/docker


Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*



### Bok {#bok}

Kolla in följande.



### Artiklar {#artiklar}

Kika igenom följande artiklar.

Docker development vs production.


### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 2xx i namnet.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*


### Övningarr {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna..

1. [Continuous Delivery med Circle CI och Github]()

https://dbwebb.se/uppgift/skapa-docker-image

### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.


1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v2.0.0.



## Lästips {#lastips}

https://docs.docker.com/develop/develop-images/multistage-build/

https://www.wintellect.com/security-best-practices-for-docker-images/

Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

Databas i docker eller ej?
...
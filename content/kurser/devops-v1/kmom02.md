---
author:
    - aar
revision:
    "2019-11-01": "(A, aar) Första versionen."
...
Kmom02: Docker
==================================

Vi packar in vår kod i en Docker container för att underlätta utveckling, driftsättning och körning av vår applikation.

<!-- more -->
[FIGURE src="https://pics.me.me/it-works-on-my-machine-then-well-ship-your-machine-62072263.png"]


[INFO]
Innan ni sätter igång med kursmomentet kolla att ert Microblog repo är synkat med originalet, [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).
[/INFO]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



## Vad är Docker? {#docker}

En snabb översikten av vad Docker är kan vi hitta på [Dockers egna webbsida](https://www.docker.com/resources/what-container). Docker är en container teknologi som liknar en avskalad virtuelle maskin. Vad tillför det till oss som utvecklare?

Docker låter utvecklare att utveckla och driftsätta applikationer i virtuella container miljöer. Detta ska göra att en applikation kan köras på exakt samma sätt utan kompabilitets problem oberoende av vilken dator/server den körs på, så länge Docker är installerat. Att applikationen kan köras oberoende av systemet gör att applikationen blir lättare att använda, utveckla och underhålla och driftsätta.



### Docker terminologi {#terminologi}

- **Image**: En image är typ ett exekverbart paket som innehåller allt som behövs för att köra applikationen, det inkluderar konfigurationsfiler, miljö variabler och bibliotek.
- **Dockerfile**: Fil som innehåller instruktionerna för att bygga en Docker image.
- **Build**: Skapa en image snapshot från Dockerfile.
- **Tag**: Version av en image. Varje image har ett tag namn.
- **Container**: Ett lättviktig program paket skapat från en specifik image version. 
- **DockerHub**: Image repository där vi kan hitta images. Typ GitHub för images.
- **Docker Daemon**: Körs på host systemet. Användare kan inte jobba direkt mot Docker daemon utan gör det via Docker klienter.
- **Docker Engine**: Skapar och kör Containers.
- **Docker Client**: Huvud interfacet för Docker.



### Installera Docker {#installera}

För att få en bättre förståelse för Docker behöver vi använda det och då måste vi installera det. Läs igenom [Installera virtualiseringsmiljön Docker](kunskap/installera-virtualiseringsmiljon-docker). Notera att det kan vara lite svårt med Docker i Windows 10 Home b.la., om ni har en annan miljö ni kan jobba på så rekommenderas det. Lösningen för tillfället är att köra Docker i VirtualBox på Windows 10 Home.



### Öva på Docker {#ova}

Kolla på följande video för en kort introduktion till Docker och hur vi kan använda det.

[YOUTUBE src="6aBsjT5HoGY" caption="Docker Concepts Introduction"]

Gör sen hela guiden [Docker](guide/docker/introduktion) för att lära er skapa egna images och containrar. 

Om ni har tid och känner att ni vill öva lite mer på Docker kan ni testa [Docker på Catacoda](https://katacoda.com/courses/docker).



### Docker i devops {#devops}

Docker är väldigt populärt inom devops världen av många anledningar och ni kan läsa varför i Dockers bloggserie **Docker and the Three Ways of DevOps**.

- [Part 1: The First Way – Systems Thinking](https://www.docker.com/blog/docker-three-ways-devops/)

- [Part 2: The Second Way – Amplify Feedback Loops](https://www.docker.com/blog/docker-three-ways-devops-2/)

- [Part 3: The Third Way – Culture of Continuous Experimentation and Learning](https://www.docker.com/blog/docker-three-ways-devops-3/)



## Skapa egen Docker image för produktion {#file_prod}

Nu när vi har lite kött på benen och vet vad Docker är och hur det fungerar ska ni skapa en egen Dockerfile för microblogen. De som var uppmärksamma förra veckan och kollade i Miguels guide såg kanske att det finns ett kapitel om att skapa en Dockerfile för projektet. Jobba igenom [Deployment on Docker containers](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xix-deployment-on-docker-containers) för att skapa dig en Dockerfile för produktion.  
Skippa avsnittet som heter `Adding a Elasticsearch Container`.  
Ni kan också ignorera saker som rör `translate`, `compile` och `mail`. De används inte i vår microblog. Var uppmärksamma på `boot.sh` filen där ni kan ta bort raden som kör `translate` och `compile`.  
Ni behöver inte heller kopiera `config.py` i Dockerfile, den ligger redan i `app.py` mappen, så vi behöver inte kopiera den.

Döp din Dockerfile till `Dockerfile_prod` och lägg den i mappen `docker`.

Efter att ni skapat er Dockerfile kan läsa vsupalov's review av [Docker Usage in 'The Flask Mega-Tutorial'](https://vsupalov.com/flask-megatutorial-review/). När vi ändå är inne och läser på vsupalov kan ni även läsa [Should Built Docker Images Be Used in a Development Environment?](https://vsupalov.com/dockerfile-in-production-docker-image-in-dev/).



### Databas i Docker {#db_docker}

I Miguels guide fick vi även koden för en continer som kör MySQL. Att köra sin databas i Docker har länge varit debatterat, många är emot men fler och fler börjar tycka att det är OK. Ni kan läsa lite om argumenten i [Should You Run Your Database in Docker?](https://vsupalov.com/database-in-docker/). Jag är för att köra databasen in Docker så länge man lägger data mappen som en volym så att datan inte skrivs över när vi startar om containern.

MySQL sparar sin data i mappen `/var/lib/mysql` så när ni kör er databas container i produktion gör den mappen till en volym på host systemet.



## Skapa en Docker image för testning {#file_test}

Nästa steg är att skapa en till Dockerfile fast en som bara ska användas för testning. Till skillnad från när vi använder Docker för produktion så vill vi inte att containern ska vara igång för evigt. Istället vill vi bara starta upp en container som kör alla tester och sedan stänger ner. Skapa en Dockerfile, döp den till `Dockerfile_test` och lägg den i mappen `docker`.

Om ni vill kan ni ändra så integrationstesterna körs mot MySQL i docker container istället för SQLite i minnet. Testerna kommer troligen köras långsammare men testerna blir mer värdefulla då de körs mot likadant system som körs i produktion. När man kör databasen i en container för testerna brukar man inte göra data mappen till en volym, i och med att vi inte bryr oss om persistent data för tester.



## Spara konfiguration som kod {#konfig_kod}

En viktigt del av det praktiska inom devops är att spara konfiguration som kod och versionshantera den. Detta är för att undvika att tillfällen uppstår där det bara är specifika personer som vet hur man startar/kör/konfigurerar något. Allt ska finnas som kod och versionshanterat så alla kan göra det.

En typisk sån sak är att bygga/köra Docker images. Att bygga/starta en image behöver ofta någon slags konfiguration t.ex. vad ska vara volymer, miljövariabler eller vilken port som ska öppnas. Om detta inte finns som kod blir det svårt för någon annan än för den som skrev koden att göra det.

För Docker använder vi [docker-compose](https://dbwebb.se/guide/docker/installera-compose) i detta syftet. 

Skapa filen `docker-compose.yml` i root mappen av repot. I den, lägg till services för att köra test imagen och prod imagen mot MySQL.

`docker-compose up test` ska starta test containern och köra alla tester.

`docker-compose up prod` ska starta en MySQL container och er prod container.

Updatera `make test` så den kör testerna i Docker.



## CircleCI och Continuous Delivery {#circleci_cd}

Continuous Delivery är förmågan att snabbt, säkert och när som helst kunna göra driftsättning av en applikation manuellt. Ni kan läsa en mer detaljerad förklaring av [Martin Fowler](https://martinfowler.com/bliki/ContinuousDelivery.html), ett av de stora namnen inom Microservices, Software Development och Continuous Integration/Delivery/Deployment.
<!-- https://puppet.com/blog/continuous-delivery-vs-continuous-deployment-what-s-diff -->
Vi ska inte uppnå "riktigt" CD då vi inte har en staging miljö och vi borde testa koden på fler sätt. Men vi jobbar med det vi har. För att vi ska få till CD ska vi testa vår kod på CircleCi, om testerna går igenom bygg en Docker image och publicera den på DockerHub. I nästa kursmoment ska vi ta det ett steg längre och uppnå Continuous Deployment, vilket  lägger till att automatisk driftsätta applikationen efter vi testat och byggt den.

Skapa först ett konto på [DockerHub](https://hub.docker.com/) och skapa sen ett nytt repo där ni kan ladda upp er prod image. När ni gjort det testa ladda upp er första image manuellt. 

Nu vill vi att byggandet och pushandet av nya images ska ske automatiskt när vi uppdaterar koden. Vi gör så att detta sker i CircleCi. Läs [Using CircleCI workflows to replicate Docker Hub automated builds](https://circleci.com/blog/using-circleci-workflows-to-replicate-docker-hub-automated-builds/) för att se hur ni kan skriva er CircleCi config för att bygga och publicera er image till DockerHub. Tänk på att ni vill bara bygga och publisera en ny image om alla tester går igenom.

Gör ett aktivt val mellan att bara publicera ny image för varje ny release eller om det ska ske vid varje commit.

Vi vill inte spara lösenord eller annan känslig information i kod så att det pushas till GitHub. Samtidigt behöver vi använda oss av t.ex. lösenord när vi kör saker i CircleCi. Det kan vi spara som [miljövariabler i CircleCi](https://circleci.com/docs/2.0/env-vars/#setting-an-environment-variable-in-a-container) och sen använda i konfigurationen för CircleCI.

<!-- Hur få exit kod? https://docs.docker.com/compose/reference/up/ --exit code from service, behövs den? -->


## Kör i produktion {#docker_prod}

Sista steget är att köra er prod image på produktionsservern på AWS. Installera Docker på servern och starta prod med mysql container med docker-compose. Bygg inte containerna på servern utan använd den som byggts på CircleCi och laddas upp till DockerHub.

Docker har skrivit lite om att använda [compose i produktion](https://docs.docker.com/compose/production/).

Om ni vill/har tid uppdatera skripten för att deploya appen till att använda Docker istället.



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 2xx i namnet.



Uppgifter {#uppgifter}
-----------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas.
<!-- nginx i docker med https https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71 -->

1. Två Dockerfile's i mappen `docker`, en för produktion som heter `Dockerfile_prod` och en som heter `Dockerfile_test`.

1. docker-compose file för att köra test och starta prod miljön.

1. `make test` kör testerna i Docker.

1. CircleCi testar med docker och bygger produktions image och pushar till DockerHub.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v2.0.0. Om du pushar kmom02 flera gånger kan du öka siffrorna efter 2:an.

1. Inkludera en länk till ditt GitHub repo och din webbsida (domännamn) i din inlämning på Canvas.



## Lästips {#lastips}

[Multistage builds](https://docs.docker.com/develop/develop-images/multistage-build/), för vår app är detta kanske inte nödvändigt men det är väldigt bra att känna till.

[Best practices](https://www.wintellect.com/security-best-practices-for-docker-images/) för Docker.

[Docker latest tag](https://vsupalov.com/docker-latest-tag/), ett annat hett ämne inom Docker är om man ska använda `latest` taggen för att köra images eller ej.

[Building Your Production Tech Stack for Docker Container Platform](https://dockercon2018.hubs.vidyard.com/watch/k3Cv676wmxAwYDxbvcgcgC), video från DockerCon 2018.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Har du använt Docker förut? Gick det bra att använda det nu?

1. Valde du att bygga ny Docker image vid varje commit eller release? Varför?

1. Vad är Continuous Delivery?

1. Uppdaterade du deploy skripten med Docker?

1. Hur var storleken på kursmomentet? Vad tycker du om upplägget på kursmomentet?

1. Veckans TIL?

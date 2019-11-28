---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom05: DevSecOps
==================================

Devops handlar om att brygga kommunikationsbarriärer, det är stort fokus på development och operations teams men även security behöver inkluderas för att det ska bli ett bra resultat. I detta kursmoment ska vi kolla på hur vi kan inkludera säkerhet i hela utvecklingsprocessen, så att alla blir ansvariga för säkerhet i ett projekt.



<!-- more -->

[FIGURE src="img/devops/devops-security.png" caption="Hur det inte ska se ut när man kör devops."]

Vi har redan gjort några saker för att förbättra vår säkerhet, vi har stängt av ssh inloggning som root användare, vi har en ny användare i database bara för microbloggen, vi pushar inte AWS nycklarna till GitHub och vi sparar känslig information som behövs till CircleCi som hemlig miljövariabler. Nu ska vi gå vidare med att aktivt leta efter säkerhetsrisk.



### Vad är DevSecOps {#devsecops}

Målet med DevSecOps är att alla behöver tänka på och är ansvariga för säkerheten hos en produkt. Säkerhet behöver vara en del av hela utvecklingsprocessen. Mycket inom devops handlar om automation och där vill vi även ha med säkerheten, manuell kontroll av säkerhet ska vara ett undantag inte regeln. DevSecOps har fått ett eget namn för att det är först på senare år som man börjat med att få in säkerhetstänket, det var inte riktigt med början av devops. Läs [The “What” “How” and “Why” of DevSecOps](https://www.newcontext.com/what-is-devsecops/) och [What is DevSecOps?](https://www.atlassian.com/continuous-delivery/principles/devsecops) som tar upp lite olika delar av DevSecOps.

Läs också sida 1-17 i [Securing Devops](http://tinyurl.com/usyps42) (länken går till en E-bok version) för en introduktion till Continuous Security.



### Test-driven security {#tds}

Vi ska nu lägga in automatiska säkerhetskontroller i vår CI/CD kedja men vi jobbar ju inte med säkerhets så vi har inte koll på hur vi testar saker för säkerhet. Som tur är för oss finns det många projekt andra människor och företag har gjort som testar säkerhet i olika aspekter på olika system. Ni ska koppla på en mängd olika verktyg på CI/CD kedjan som utför tester på områden som man brukar testa.



#### Docker {#docker}

När det kommer till att göra Docker säkrare finns det väldigt mycket man kan göra, det finns flera olika långa dokument som går igenom vad man kan göra. T.ex. [CIS Docker Benchmark](https://www.cisecurity.org/benchmark/docker/), ett av de längre dokumenten, och [OWASP Container security standard](https://github.com/OWASP/Container-Security-Verification-Standard), som tycker att CIS är för långt dokument. Ni behöver inte sätta er in i dem men om ni är intresserade rekommenderar jag OWASPs standard. Vi nöjer oss med att läsa OSWAP [Docker security cheat sheet](https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html). De har en bra sammanfattning av viktiga saker att tänka på. Vi gör några av sakerna för Microbloggen men de flesta uppfyller vi inte.

Läs också [Container security best practices](https://logz.io/blog/container-security-best-practices/) för en kort översikt av några saker att tänkta på när man jobbar med containrar i produktion. De pratar om Immutable deployment, alltså att bygga ny instance vid varje deploy och ta bort den gamla. Vår infrastructure är inte mogen nog för det. Vår monitoring är för simpel och vi har inte satt upp någon logging monitoring som kan analysera efter säkerhetsintrång.



##### Docker image security scanning {#docker_scan}

Det finns några olika verktyg för att skanna Docker images, Docker runtime och inställningar i Docker host. Tanken var att vi skulle använda oss av något av de verktygen. Tyvärr finns det problem med alla jag testade som gjorde att de blir jobbigare att använda dem än vad vi får ut av det. Jag rekomenderar att läsa [Docker Image Security Scanning: What It Can and Can't Do](https://resources.whitesourcesoftware.com/blog-whitesource/docker-image-security-scanning), den nämner några verktyg för att skanna filer. Den nämner dock inte [Docker Bench Security](https://github.com/docker/docker-bench-security) vilket är Dockers egna verktyg för att skanna olika delar av Docker.

Det är bra att känna till verktygen och om ni jobbar med Docker på fritiden eller senare i arbetslivet rekommenderar jag er att använda något verktyg.

 
<!-- ##### Docker Bench for Security {#bench}

Docker har byggt ihop några skript som kollar basic säkerhet i Docker konfiguration och images. Projektet kallas för [Docker Bench Security](https://github.com/docker/docker-bench-security) och det kollar många av sakerna som tas upp dokumenten jag länkade ovanför. Docker Bench Security är en bra start för säkerhet i Docker men det är inte en fullstädning lösning.

Jobba igenom guiden [Using Docker Bench Security to configure Docker to best practices](https://developers.hp.com/epic-stories/blog/docker-bench-security-container-hardening-and-auditing-host-security) för att fixa basic konfiguration på servrarna för att lösa många av varningarna. Logga in på er AppServer och kör kommandona där när ni jobbar igenom guiden. OBS! Läs igenom nedanstående info innan ni börjar med guiden, det rättar saker som inte funkar för oss, guiden kommer inte lösa alla felen ni har och den är skriven för Alpine os så t.ex. behöver ni skriva `apt-get` istället för `apk` när ni ska installera något.

- När ni ska konfigurera `auditd` ska ni skriva reglerna i filen `/etc/audit/rules.d/audit.rules`.  
- När ni i guiden ska konfigurera Docker Daemon skippa följande två rader:

```
"log-driver": "syslog",
"disable-legacy-registry": true,
"userns-remap": "default"
```

Vi vill inte sätta log-driver för att vi har inte en extern log server att skicka dem till, `disable-legacy-registry` är [deprecated i nyare versioner av Docker](https://docs.docker.com/engine/deprecated/#interacting-with-v1-registries). Efter att ni startat om Docker deamon efter ny config kan det vara så att microblog containern inte startar automatiskt så ni får starta den manuellt.

- Använd `sudo less /var/log/syslog  |  grep docker` för att Docker felmededelande vid restart. kan också tillägga att om man försöker starta om Docker för ofta får man error. Då är det bara att vänta en stund innan man försöker igen.

Jobba igenom guiden nu.

Efter guiden hade jag kvar följande fel:

- 1.1, vi struntar i denna.
- 2.11
- 2.12
- 4.6



https://github.com/freach/docker-image-policy-plugin whitelist docker images för pull -->



#### Dependency Scanning {#dep_scan}

I vårt projekt använder vi oss av många externa paket både i Python koden för Microbloggen men även i Docker imagen. Man kan aldrig riktigt veta om ett paket man installera är säkert eller om det innehåller säkerhetsrisker. Här kommer Dependency scanning in i bilden. Dependency Scanning verktyg har oftast en stor databas som kontinuerligt uppdateras med paket som man vet innehåller kända säkerhetssårbarheter. Vi ska använda oss utav verktyget [Snyk](https://snyk.io/) som kan scanna Python paket men även Docker images.



##### Snyk {#snyk}

<!-- https://circleci.com/blog/adding-application-and-image-scanning-to-your-cicd-pipeline/ -->
Skapa ett konto på [Snyk.io](https://snyk.io/) och koppla det till er Microblog på DockerHub. Ni kan koppla det till GitHub också men Snyk klara tyvärr inte av att hitta requirements filerna som ligger i `requirements` mappen. Snyk kan bara hitta `requirements.txt`. För att Snyk ska klara av att hitta alla paket vi använder i Produktion ska vi skanna i CircleCi istället.

Vi ska använda oss av [Orbs i CircleCi](https://snyk.io/blog/automating-open-source-security-scanning-with-snyk-and-circleci/), mer specifikt [Snyks orb](https://github.com/snyk/snyk-orb) för att skanna både våra Python paket och Docker paketen som ligger i en skapad image. Först behöver ni tillåta 3rd party Orbs i CircleCi. Gå till settings, Secutiry och klicka i `Yes, allow all members of my organization to publish dev orbs... `. Sen behöver ni hämta en API nyckel från Snyk. Gå tlll `settings`, `personal API token` och klicka `click to show`. Kopiera nyckeln och gå till CircleCi och settings för ert Microblog projekt. Skapa en ny miljövariabel som heter `SNYK_TOKEN` och sätt api nyckeln som värde. Nu kan vi uppdatera er CircleCi konfig.

Om ni inte redan kör version 2.1 uppdatera till det och lägg till snyk som en orb.

```
version: 2.1
orbs: 
    snyk: snyk/snyk@0.0.8
```

Vi börjar med att lägga till så att Python paketen skannas. Snyk cli kollar vilka paket som är installerade och klarar egentligen inte av att kolla virtual environment. Men vi kan lurar Snyk. Jag lägger till ett nytt jobb som heter `snyk`.

```
snyk:
    docker:
        - image: circleci/python:3.5
    working_directory: ~/repo
    steps:
        - checkout
        - run:
            name: install dependencies
            command: |
                python3 -m venv venv
                . venv/bin/activate
                make install
        - run: echo "source ~/repo/venv/bin/activate" >> $BASH_ENV # här gör vi så att så att CircleCi automatisk laddar venv och då kollar Snyk har installerat i den.
        - snyk/scan
```

Pusha upp konfigurationen och kolla att det går igenom. Glöm inte att lägga till Snyk i Workflows jobs.

När ni ser att det fungerar ska vi lägga till att skanna Docker imagen. I ert job där ni skapar och pushar docker imagen till DockerHub, lägg till ett nytt steg efter att ni byggt imagen men innan ni publicerar den.

```
- snyk/scan:
    docker-image-name: $IMAGE_NAME
```

Pusha konfigurationen och kolla att det går igenom. Ni borde inte få några varningar eller fel, jag fick i alla fall inte det. Om ni får det försök fixa dem och skriv om det i redovisningstexten.



#### SAST vs. DAST {#sast-dast}

Static Application Security Testing (SAST), eller bara Static Code Analysis, är att analysera källkoden för kända säkerhetsrisker och sårbarheter utan att exekvera programmet. SAST är bra på att fånga upp programmeringsmisstag tidigt i utvecklingsprocessen av en applikation. Vi kommer använda [Bandit](https://github.com/PyCQA/bandit) för att utföra SAST på vår Python kod.

Dynamic Application Security Testing (DAST) letar efter sårbarheter i webbapplikationer genom att skanna och utföra attacker på applikationen. Vi kommer använda [Zap](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) för att utföra DAST på Microbloggen.

Läs [SAST vs. DAST](https://www.synopsys.com/blogs/software-security/sast-vs-dast-difference/) för en jämförelse av de två och vad de är bra på.



##### Bandit {#bandit}

[Bandit](https://github.com/PyCQA/bandit) är ett linting verktyg (som pylint) fast det analyserar istället säkerhet i koden. Ladda ner Bandit och lägg till det i `requirements/test.txt` så att det är en del av paketen för testning. Testa att köra Bandit med `bandit -r app` så att det bara analyserar koden för applikationen, vi behöver inte köra det mot testerna.

Om ni har kodrader som ni anser är false-positivs kan ni lägga `# nosec` som en kommentar i slutet på den raden. Då ignorerar Bandit den raden. Det går även att hoppa över hela tester, ni kan skapa filen `.bandit.yml` och i den skriva:

```
skips: [<'list of tests'>]
```

För att Bandit ska läsa konfigurationen kör Bandit med `bandit -c .bandit.yml -r app`. Om ni får några fel kan ni antingen fixa felet, lägga till `# nosec` eller hoppa över regeln helt. Analysera felet och gör ett aktivt val över vad som är en passande åtgärd på felet.

Lägg till ett `bandit` som ett make target I Makefile som kör Bandit på `app` mappen. Gör sen så att Bandit är en del av testerna som körs i Dockerfile_test och som en del av CircleCi.



##### Zap {#zap}

[Zap](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)/[Zap på Github](https://github.com/zaproxy/zaproxy) är ett verktyg som kan testa väldigt många saker, speciellt från OWASP10. Det går att köra det både automatiskt och manuellt.

Vi kommer att nöja oss med att köra deras [Baseline tester](https://github.com/zaproxy/zaproxy/wiki/ZAP-Baseline-Scan) på Microbloggen, då utförs inga aktiva attacker, den bara skannar websidan. Mozilla har ett [blogginlägg](https://blog.mozilla.org/security/2017/01/25/setting-a-baseline-for-web-security-controls/) där de förklarar hur ni kan köra Zap med baseline testerna. Följ den för att testa köra den mot er Microblog, ni behöver inte lägga till det i CircleCi.

Det går även att köra Zap mot er lokala miljö, men då måste ni sätta nätverk när ni startar containern:

<!-- `docker run -t owasp/zap2docker-stable zap-baseline.py -t https://<domain>` -->
```
docker run --net host owasp/zap2docker-weekly zap-baseline.py -t http://0.0.0.0:8000
```

Fixa minst 5 valfria varningar från Zap, beskriv vilka och vad ni gjorde i redovisningstexten. Det lättaste sättet att fixa dem är att logga in på load balancer instansen och ändra i Nginx konfigurationen, ladda om Nginx och köra Zap igen för att se om varningen försvann.

Egentligen skulle vi lagt till Zap i CircleCi men vi har ingen staging miljö att köra den mot. Så vi får nöja oss med att köra det manuellt innan push. Lägg till ett make target i Makefilen som kör Zap mot er Microblog, döp det till `Zap`.



### Infrastruktur Security  {#infrastruktur}

Produktionsmiljön, CI/CD och molntjänsten vi använder kan vi också göra säkrare. Vi är dock begränsade i vad vi kan göra i och med att vi har studentkonton.



#### AWS {#aws}

När det kommer till att säkra molnmiljön handlar det om att verifiera konfiguration istället för att testa tjänsten.

Vi borde kontrollera följande:

- Att rätt brandväggsregler används i Security Groups.

- Att systemen är up-to-date genom att kolla versionen på bas imagen vi använder som OS på servrarna (AMI, Amazon Machine Image).

- Kontrollera rättigheterna användare har i IAM roller. Vi kan inte göra detta då vi har studentkonton, vi har inte tillgång till [Identity and Access Management (IAM)](https://console.aws.amazon.com/iam/home?#/home). Med det kan vi kontrollera vem som har rättigheter att skapa/ändra/radera resurser på AWS. Vi kan t.ex. skapa en ny användare som används av `gather_aws_instances.yml` playbooken och den användaren har bara rättigheter att läsa data från AWS. Då hade vi inte varit lika sårbara om vi hade råkat läcka AWS nycklarna.

- Om vi använt oss av en RDS instans för databasen, skulle vi kollat att backup är rätt konfigurerat.

Det finns olika verktyg för att verifiera konfigurationer i AWS. AWS har ett eget verktyg som heter [Trusted Advisor](https://console.aws.amazon.com/trustedadvisor/home#/dashboard), men igen är vi begränsade för att vi har studentkonto och inte kan sätta upp IAM roller. Ett annat populärt open-source verktyg är [ScoutSuite](https://github.com/nccgroup/ScoutSuite) men det kräver en read-only IAM roll, så vi kan inte använda det heller.



##### Security Groups {#sg}

Vi ska förbättra våra security groups, som det ser ut nu kan vem som helst koppla upp sig till de olika portarna som är öppna, det är ju onödigt när vi vet vilka IP-addresser alla servrarna har. Vi kan inte göra det på ett bra sätt som det ser ut nu, för att vi kör rollen för SGs före vi skapar servrarna i Ansible. Nu behöver vi skapa servrarna först så att vi kan använda deras IP när vi skapar SGs. Ändra i Ansible så att Security Groups rollen körs efter Provision rollen. Det kan ni göra genom att ta bort `roles/provision/meta` mappen och sen lägga till `security_groups` i `roles` listan efter `provision` i filen `provision.yml`.

I `roles/security_groups/vars/main.yml` hittar ni all security groups, vilka portar som är öppna och vilka IP som kan koppla upp sig mot dem. Nu borde alla IP vara `0.0.0.0/0`, nu vill vi bara att det är SSH portarna och port 80 och 443 på load balancern som ska ha det så. Övriga portar behöver bara specifik servrar koppla upp sig till. T.ex. är det bara load balancern som behöver kunna koppla sig till app serverns port 8000 och det är bara app servern som behöver kunna koppla upp sig till databasens port 3306. Gå igenom filen och byt ut alla `0.0.0.0/0` mot specifika IP addresser (förutom för SSH och port 80 och 443 på LB). Ni kan använda `{{ groups['<host>'][0] }}/32` för att sätta en IP address.

Med detta har vi begränsat var personer kan personer kan utnyttja säkerhetshål för att ta sig in i våra servrar.



#### Produktionsmiljön {#prod_miljo}

Det finns en hel del vi kan göra med servrarna i produktion. SSH är en viktig del i vårt arbetsflöde, Ansible behöver kunna SSH:a in till varje server för att konfigurera dem och vi gör det för att felsöka och testa saker. Dock så är vår SSH setup inte särskilt säker, vi har dock stängt av root och password login vilket är steg 1. I vår struktur kan man SSH:a in till varje server från vilken IP som helst. En säkrar struktur än vad vi har är att ha en deployer/access node som fungerar som ingång till hela produktions infrastrukturen. Då skapar vi en till instans som endast är till för att ge tillgång till resten av servrarna, vi ger den en security group så att man kan SSH:a till den från vilken IP som helst. På övriga servrar sätter vi security groups som bara tillåter SSH kopplingar från deployer nodens IP. Vi kommer inte att skapa en deployer node då vi har begränsat med kredit på AWS men med en större budget hade vi gjort detta.



##### SSH {#ssh}

När vi ändå är inne på SSH kopplingar så kan vi konfigurera säkrare kopplingar SSH på servrarna. Vi börjar med att använda [Mozillas ssh_scan](https://github.com/mozilla/ssh_scan) verktyg för att skanna SSH konfigurationen på våra servrar. Kör följande kommando lokalt på er dator.

```
docker run -it mozilla/ssh_scan /app/bin/ssh_scan -t <domain>
```
Alla servrar borde ha samma SSH konfiguration så det räcker att köra den mot er load balancer. Man får rätt mycket text utskriven men det viktiga är vad den skriver för `recommendation`, jag fick följande:

```
"recommendations": [
  "Remove these key exchange algorithms: diffie-hellman-group16-sha512, diffie-hellman-group18-sha512, diffie-hellman-group14-sha256, diffie-hellman-group14-sha1",
  "Remove these MAC algorithms: umac-64-etm@openssh.com, hmac-sha1-etm@openssh.com, umac-64@openssh.com, hmac-sha1"
],
```

Så scannern tycker att jag borde ta bort gamla algoritmer som inte längre är säkra. Istället för att in och leta efter vilka algoritmer vi använder och hur vi stänger av dem så kan tänker jag att vi använder oss Mozillas openSSH moderna konfigurationer. På [guidelines/openssh](https://infosec.mozilla.org/guidelines/openssh) finns det färdiga konfigurations filer för säkrare SSH.

Kopiera konfigurationen för `Modern (OpenSSH 6.7+)`, SSH:a in på load balancern och ersätt ssh konfigurationen i `/etc/ssh/sshd_config` med den nya. Lägg till raden `AllowUsers deploy` och ändra följande rad `Subsystem sftp  /usr/lib/ssh/sftp-server -f AUTHPRIV -l INFO` till `Subsystem sftp  /usr/lib/openssh/sftp-server -f AUTHPRIV -l INFO`. Filvägen till sftp-servern är fel, och då klagar Ansible om det inte är konfigurerat rätt.

Kör ssh_scan igen och kolla att ni inte har några rekommendationer kvar. Uppdatera Ansible rollen `10-first-minutes` så att den nya SSH konfigurationen sätts på alla servrar.

Det finns givetvis sätt att göra SSH ännu säkrare, det är inget vi ska göra men det kan vara bra att ha på sina egna servrar hemma om man har det. Tjänsten [Duo](https://duo.com/docs/loginduo) har multi-factor authentication för SSH. Så när någon försöker logga in via SSH till er server får ni en notifikation och behöver t.ex. godkänna det i mobilen.



#### Hur säker är vår CI/CD pipeline? {#cicd}

Det är inte bara vår kod som behöver vara säker, även vår CI/CD infrastruktur är en säkerhetsrisk. Någon kan ta sig in i CircleCi's system och komma åt våra olika API nycklar t.ex. och på så sätt få tillgång till vår kod. Läs [How Secure Is Your CICD Pipeline?](https://dzone.com/articles/how-secure-is-your-cicd-pipeline-1) som går igenom vad man ska tänka på när man sätter upp sin CI/CD pipeline och kopplar ihop olika tjänster.



### Lästips {#lastips}

1. [Zapping the top 10](https://www.owasp.org/index.php/ZAPpingTheTop1), hur ni kan använda Zap för att testa OWASP10 sårbarheterna.



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 5xx i namnet.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Skanna Python paketen och Microbloggen Docker image med Snyk på CircleCi. 

1. Skapa make target `bandit`. Lägg till så att det körs med testerna i docker och i CircleCI.

1. Fixa minst 5 varningar från Zap testerna. Glöm inte bort att uppdatera er Nginx konfiguration i Ansible!

1. Uppdatera Security Groups rollen så att bara specifika IP kan koppla upp sig mot de olika portarna.

1. Uppdatera Ansible rollen `10-first-minutes` så att servrarna använder den rekommenderade SSH konfigurationen.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v5.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Varnade Snyk om några paket som ni behövde uppdatera?

1. Ändrade ni något i er kod efter ni kört Bandit? Använder ni `# nosec` för att ignorera någon kod eller skippa något test? Varför?

1. Beskriv vilka Zap varningar ni fixade och hur ni löste dem.

1. Gick det bra med SSH konfigurationen?

1. Hur skulle du definiera DevSecOps och dess roll inom devops?

1. Var skulle du säga att vi har den största säkerhets risken i vårt system och infrastruktur?

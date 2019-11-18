---
author:
    - aar
revision:
    "2019-07-29": "(A, aar) Första versionen."
...
Kmom03: Configuration Management och Continuous Deployment
==================================

Vi fortsätter med att kolla in fler sätt att automatisera flöden. Vi lär oss Ansible för Configuration Management (CM) och Infrastructure as Code (IaC). Tillsammans med Ansible och CircleCI ska vi också utveckla vår Continuous Delivery till Continuous Deployment (också CD).



<!-- more -->

[FIGURE src="https://www.gocd.org/assets/images/blog/continous-delivery-vs-deployment-infographic/continuous-delivery-vs-continuous-deployment-infographic-305dd620.png"]



Nästa steg i vår miljö är att utöka antalet servrar från en till tre. Vi ska bygga en klassisk webbapp struktur, en server för databasen, en för appen och en som load balancer (Nginx, var proxy innan). Med systemet vi har nu, att kopiera bash filer till servern och exekvera manuellt är inte hållbart inom devops. Vi ska utnyttja kraften av Configuration Management verktyget Ansible för att uppnå denna strukturen på att hållbart sätt. Vi flyttar över funktionaliteten från bash skripten till Ansible, som kan utföra samma sak på flera servrar samtidigt. Vi ska skapa och stänga ner servrar med ett kommando, installera och konfigurera dem och tillslut ha ett kommando för att sätta upp hela produktionsmiljön, från zero to hero!



[INFO]
Innan ni sätter igång med kursmomentet kolla att ert Microblog repo är synkat med originalet, [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).
[/INFO]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



## Infrastructure as Code och Configuration Management {#iac-cm}

Infrastructure as Code innebär att behandla sin infrastruktur (servrar) som software, det ska vara definierat i kod och versionshanterat, för ett längre mer djupgående utlägg läs [why use IaC](https://medium.com/cloudnativeinfra/why-use-infrastructure-as-code-881ccd6c4290).

För att få en översikt av vad CM är har Digital Ocean gjort en [bra sammanfattning](https://www.digitalocean.com/community/tutorials/an-introduction-to-configuration-management).

När ni fått lite bättre koll på IaC och CM kan ni läsa om olika verktyg som finns och var de passar in [inom IaC och CM](https://dzone.com/articles/when-to-use-which-infrastructure-as-code-tool).



## Ansible {#ansible}

Ansible är ett verktyg för att automatisera server konfiguration. Läs om [Ansibles grundkoncept](https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html), introduktion till [använda Ansible](https://www.digitalocean.com/community/tutorials/configuration-management-101-writing-ansible-playbooks) och [Best Practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html).



### 10 first minutes on a server i Ansible

[INFO]Om du använder en ssh-nyckel med lösenord behöver du skapa en ny, i slutet av kursmomentet ska ni använda Ansible från CircleCi och CircleCi kan bara använda ssh-nycklar utan lösenord. Ni kan använda [Githubs guide](https://help.github.com/en/enterprise/2.16/user/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) för att skapa en ny nyckel. När ni skapat den, glöm inte att byta ut den på AWS.

Om ni inte skapade en ny nyckel och ni genererade en ssh-nyckel med `.pem` i kmom01 via AWS behöver du göra om den ssh-nyckeln till en `.pub` fil. Använd [Convert AWS pen to pub](https://gist.github.com/zircote/1243501). När du sen ska använda en ssh-nyckel i Ansible använd `.pub` filen.
[/INFO]

Än så länge har vi kopierat skript från `scripts` mappen över till servern och exekverat för att konfigurera servern. Nu ska vi uppgradera oss och göra detta i Ansible istället.

Sen jag filmade videorna har jag uppdaterat hur `provision.yml` fungerar så att det ska bli billigare att använda AWS, vi använder inte längre ElasticIP. Öppna `provision.yml` och ersätt `<subnet-id>` med ett subnet id. På bilden nedanför kan ni se vart ni kan hitta subnet id:t som redan används.

[FIGURE src="img/devops/subnet-id.png" caption="Hitta subnet-id"]

Innan ni fortsätter kan ni stänga ner er gamla server och ta bort den Elastic IP som ni har. Ändra inte i route53.

[WARNING]
Jag har ändrat mer sen jag gjorde videorna. Vi använder inte längre filen `aws_keys.yml` för att lagra AWS credential, istället sparar vi dem som environment variabler. I videon körs `insert_aws_keys_in_config.sh` som ett skript, det gör vi inte längre använda `. insert_aws_keys_in_config.sh` istället. Det är samma som att skriva `source insert_aws_keys_in_config.sh`. Detta gör vi för att underlätta arbetet på CircleCi.

Ni behöver inte längre lägga in sökvägen till er ssh nyckel i `ansible.cfg`. Gör det istället i `Makefile`, i target `add-ssh`. Då kan ni använda `make add-ssh` efter att ni har aktiverat `venv` för att lägga till er ssh-nyckel i ssh-agent. Detta gör att ni inte behöver ha med sökvägen till er ssh-nyckel när ni ska ssh:a till era servrar.
[/WARNING]

Börja med att kolla på videorna med [30x i namnet](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78) för att bekanta er med vad som finns i `ansible` mappen. Jag rekommenderar även att läsa `ansible/README.md` filen efteråt.

Nästa steg är att skapa er egna playbook, kolla på videorna med [31x i namnet](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78) och skapa en playbook för 10-first-minutes skripten.



### Playbooks för app strukturen {#app_structure}

Nu har vi en grund att utgå från, vi har tre servrar som är konfigurerade och installerade som en grund server. Nästa steg är att konf-igurerar varje server för sig. 

Ni ska nu skapa en playbook för att sätta upp databasen på en server, applikationen på en och en load balancer på den sista. När vi bara hade en server använde vi Nginx som en reverse proxy för att skicka vidare requests till Flask appen. Nu ska vi använda Nginx som en load balancer istället. Med Nginx som en load balancer istället för en reverse proxy kan vi lätta utöka antalet applikations servrar när vår hemsida blir populär och besöks antalet ökar. 



#### Database playbook {#database_pb}

Skapa en playbook som startar en Docker container med MySQL på servern som har host namnet `database`.



#### Applikations playbook {#app_pb}

Skapa en playbook som startar en Docker container med den senaste Microblog imagen på servern som har host namnet `appServer`. När ni ska koppla Flask appen till databasen behöver ni dens IP address, ni kan inte längre använda er av Dockers länkning för att de körs på två olika maskiner. I ansible kan ni använda `{{ groups.database[0] }}` för att få ut IP för databas hosten. Tänk också på att supervisor inte behövs längre, nu låter vi Docker se till att en applikation alltid finns körandes.



#### Load balancer playbook {#lb_pb}

Skapa en playbook som installerar Nginx och konfigurerar det som en load balancer och skickar requests till applikations servern. Gör det på servern med host namnet `loadBalancer`. Vi har bara en applikations server än så länge så en load balancer tillför inte direkt något, men det är bra att känna till hur man gör en load balancer.

Läs Nginxs dokumentation om att köra en [load balancer](https://nginx.org/en/docs/http/load_balancing.html). Vad de inte skriver är att vi inte han lägga ett `http` block i ett annat `http` block. Vilket vi gör om vi bara skapar en ny host i `/etc/nginx/sites-available`. Så vi måste ändra på config filen `/etc/nginx/nginx.conf`. Ni kan hitta två config filer för Nginx som load balancer på [Gist](https://gist.github.com/AndreasArne/58374253123a31bb7c32e2b551fe8492).

Det finns flera metoder för att få till HTTPS, vissa svårare än andra. Ni kan se hur jag gör på [Gist](https://gist.github.com/AndreasArne/6b627f15aabeecd435abd1e8e11f96c8). Om ni använder er av den koden se till att det ligger överst i er `main.yml` annars kan det blir problem med config filerna.

Använd [template](https://docs.ansible.com/ansible/latest/modules/template_module.html) modulen i Ansible för att flytta `nginx.conf.j2` till `/etc/nginx/nginx.conf` och `load-balancer.conf.j2` till `/etc/nginx/sites-available/load-balancer.conf`. Notera variablerna i `load-balancer.conf.j2` som ni behöver ha värden till i Ansible.

Ni kan använda [file module](https://docs.ansible.com/ansible/latest/modules/file_module.html?highlight=file) för att länka `load-balancer.conf` till `sites-enabled` mappen.



### Ansible på CircleCi för CD {#cd}

Lägg till ett sista steg i er CircleCi config som kör er playbook för att driftsätta appen.

För att göra detta behöver ni kunna ssh:a från CircleCi till AWS instansen. För det behöver ni lägga till er SSH nyckel på CircleCI. På CircleCi gå till settings för ert projekt, klicka `SSH permissions` och `Add SSH key`. Låt `Hostname` vara tomt och klistra in er SSH nyckel (inte `.pub` filen).

För att slippa behöva aktivera venv i varje gång ni ska köra ett nytt kommando kan ni lägga till `- run: echo "source /path/to/virtualenv/bin/activate" >> $BASH_ENV` som ett steg efter att ni skapat `venv` mappen. Då kommer CircleCi automatiskt aktivera venv i varje steg.

Ni behöver också ha tillgång till era AWS nycklar. Tanken var att de skulle ligga krypterat i `aws_keys.yml` och att ni skulle pusha den till repot. Men jag (eller någon anna vad jag vet) har inte lyckats få Ansible-vault att fungera på CircleCI, problemet är att läsa lösenordet från CircleCi's miljövariabler inte verkar fungera som det ska. Istället behöver ni lägga till AWS nycklarna som miljövariabler i CircleCI. Gå till settings för projektet och sen `Environment Variables`. Lägg nu till en variabel för varje nyckel och döp dem till följande (Viktigt med stora bokstäver).

- `aws_access_key_id` -> `AWS_ACCESS_KEY`
- `aws_secret_access_key` -> `AWS_SECRET_KEY`
- `aws_session_token` -> `AWS_SECURITY_TOKEN`

Det går tyvärr inte att ändra på variablerna efter att man skapat dem, så ni kommer behöva radera dem och lägga till nya när AWS nycklarna har gått ut.

Nu borde ni vara redo att lägga till stegen i er CircleCi konfiguration för att driftsätta den senaste Docker imagen för Microblogen.

Vår Continuous Deployment funkar bara för microbloggen, hur gör vi med ändringar i Nginx eller databasen? Vi nöjer oss med att bara klara av att uppdatera Microbloggen via CD och sköter databasen och Nginx manuellt men vi kan tänka på hur vi skulle gjort. Egentligen borde vi kanske dela upp vårt repo i tre stycken, en för vår load balancer, en för microblog och en för databasen. Då krävs tre separate utvecklings miljöer med Ansible och Makefiler. Men vi hade kunnat få till en bra uppdelning och minskat mängden filer och kod (speciellt i Ansible). En annan lösning är att börja mer "ordentliga" commit meddelanden och ge den en specifik struktur. T.ex. lägga till taggar i dem och beroende på vilken tag som finns i meddelandet kör vi olika jobb på CircleCi. Det sista alternativet är nog det som är lättast för oss och det vi hade valt. Medan om vi jobbade på ett större projekt hade vi i slutändan tjänat på att dela upp repot i flera mindre.

<!-- https://blog.theodo.com/2016/05/straight-to-production-with-docker-ansible-and-circleci/ -->
<!-- https://www.dvlv.co.uk/how-we-use-circleci-and-ansible-to-automate-deploying-flask-applications.html -->



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 3xx i namnet.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Använd Ansible för att skapa och konfigurera tre servrar. En som databas, en till microblogen och en som load-balancer.

1. Utöka CircleCi så att om testerna går igenom och en ny Docker image byggs ska den driftsättas på `appServer`. Med andra ord sätt upp Continuous Deployment.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v3.0.0, om du pushar kmom03 flera gånger kan du öka siffrorna efter 3:an.

<!-- 1. Skriv skript som kollar om service är uppe, om inte kör ansible för att sätta upp annars bara uppdatera. (En deployer node?) -->


### Lästips {#lastips}

1. Hur man kan hantera flera [användare på produktionsservern med Ansible](https://www.cogini.com/blog/managing-user-accounts-with-ansible/). 
<!-- https://dev.iachieved.it/iachievedit/ansible-and-aws-part-5/ -->


Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad är IaC?

1. Vad är CM?

1. Vad är Continuous Deployment?

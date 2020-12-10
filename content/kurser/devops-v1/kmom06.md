---
author:
    - aar
revision:
    "2020-12-04": "(B, aar) Bytt AWS till Minikube."
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom06: Container orchestration
==================================

Er Microblog har fått många nya användare och ni behöver utöka er infrastruktur för att hantera trycket på servrarna. Ni börjar med att utöka hur ni använder Ansible och startar upp fler servrar och containrar på servrarna. Dock märker ni snabbt att det är krångligt och Ansible är inte gjort för att användas till detta. Istället  börjar ni läsa på om container orchestration.



<!-- more -->

[FIGURE src="https://miro.medium.com/max/660/1*Mdj9wylSl0wqJ9sB0ENbRA.png" caption="Hur det är att lära sig kubernetes."]

Vi kommer använda oss utav Kubernetes (K8s) för container orchestration men det är bra att känna till vilka andra verktyg som finns och lite om vad som skiljer dem åt.

Läs [What Is Container Orchestration?](https://blog.newrelic.com/engineering/container-orchestration-explained/)

[INFO]
PS! Stänga ner era andra servrar när ni fått kmom05 rättat!

Innan ni sätter igång med kursmomentet kolla att ert Microblog repo är synkat med originalet, [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).

PS! Stänga ner era andra servrar när ni fått kmom05 rättat!
[/INFO]



### Kubernetes {#k8s}

Börja med en snabb introduktion till Kubernetes begrepp.

[YOUTUBE src="PH-2FfFD2PU" caption="Kubernetes in 5 mins."]

Om det inte var pedagogiskt nog förklaring av Kubernetes kan jag rekommendera följande video där de lär ut Kubernetes som en barnbok.

[YOUTUBE src="Q4W8Z-D-gcQ" caption="The Illustrated Children's Guide to Kubernetes."]

Kubernetes har själva väldigt mycket och bra material för att lära sig Kubernetes och alla dess delar. En bra utgångspunkt är deras [dokumentation](https://kubernetes.io/docs/home/), där finns länkar till det mesta.

- Jobba igenom modul 1-6 i [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/). För att få en bättre förståelse för grunderna i K8s (Kubernetes) och hur man kan interagera med det.



#### Kubernetes yaml {#yaml}

Det finns två sätt att hantera objekt (pods, deployments, etc...) i K8s, imperative och declarative. I imperative kör vi kommandon i terminalen för att jobba mot ett K8s kluster, som ni gjorde i Kubernetes basics, och i declarative skriver vi konfiguration i filer och kör mot klustret.

Läs om deras olika [för och nackdelar](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/).

Vi vill givetvis jobba declarative för att då kan vi spara konfigurationen i Git och vi behöver inte oroa oss för snowflake servrar eller att bara en person har kunskapen om klustret.

[FIGURE src="http://assets.digitalocean.com/articles/comics/imperative-declarative-k8s.jpg" caption="digitalocean förklarar [imperativ vs declarative](https://www.digitalocean.com/community/tutorials/imperative-vs-declarative-kubernetes-management-a-digitalocean-comic)"]

K8s använder yaml filer för att skriva konfigurationen i filer, som Ansible. För en överblick av hur filerna struktureras och vad de kan innehålla. Ska ni läsa en guide men ni behöver inte jobba med i guiden, det räcker om ni läser och förstår.

Läs igenom [Kubernetes deployment tutorial](https://devopscube.com/kubernetes-deployment-tutorial/) 

Gör följande Katakoda för att öva på k8s. [Deploy containers using Yaml](https://www.katacoda.com/courses/kubernetes/creating-kubernetes-yaml-definitions).



#### Stateless applications {#statless}

K8s bygger på virtualisering och containrar, vilket i grunden är stateless. Vi har inte tillgång till persistent data, när vi stänger ner en container så försvinner dess data. K8s och även Docker är i grunden byggt för att köra stateless applikationer, men när populariteten av verktygen har ökat har även användningsområden ökat och de har då lagt till olika lösningar för att få till persistent data (stateful). Men det är inte lika lätt att få till persistent data i K8s som det är i Docker.

Läs [Stateful vs Stateless Applications on Kubernetes](https://linuxhint.com/stateful-vs-stateless-kubernetes/) för en bättre genomgång av skillnaden.

Ni ska börja med att öva på att skapa en stateless applikation och som tur är har K8s själva en bra guide för det. För guiden behöver ni ha tillgång till ett k8s kluster. I guiden finns det länkar till sandbox miljöer både i "Katacoda" och "Play with Kubernetes" som ni kan använda. Jag rekommenderar Katacoda då jag inte fick Play with K8s att fungera. Katacoda har dessutom Nano installerat så ni kan skriva konfigurationen till filer. Allt borde fungera utan problem fram tills steget [Viewing the Frontend Service via NodePort](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/#viewing-the-frontend-service-via-nodeport), Katacoda använder inte minikube för att starta sitt kluster så då kan ni inte använda det för att få en extern ip till ert kluster. Istället kan ni i Katacoda klicka på `+` som finns uppe på er terminal och välja `select port to view on host 1`. Då öppnas en ny tab i webbläsaren med koppling till klustret och där skriver ni in NodePort för er frontend service.

Jobba igenom [Deploying PHP Guestbook application with Redis](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/).

Det finns en mängd olika sätta och verktyg för att köra Kubernetes beroende på vilken miljö man vill köra det i.

Läs [Deploy Kubernetes In Five Different Ways](https://platform9.com/blog/5-methods-deploy-kubernetes/) för en kort överblick av några.



#### Stateful applications {#stateful}

Nu när ni har testat på att köra en stateless applikation i K8s ska ni lära er hur man kan köra en stateful applikation. Börja med att läsa [The sad state of stateful Pods in Kubernetes](https://elastisys.com/sad-state-stateful-pods-kubernetes/) för en förklaring av problemet med stateful applikationer.

Kolla på följande videos om volymer i Kubernetes.

[YOUTUBE src="VB7vI9OT-WQ" caption="Kubernetes Volumes 1: emptydir, NFS, YAML, volumes, and intro to Persistent Volume Claims"]

[YOUTUBE src="OulmwTYTauI" caption="Kubernetes Volumes 2: Understanding Persistent Volume (PV) and Persistent Volume Claim (PVC)"]

Jobba igenom [Persistent volumes](https://www.katacoda.com/mjboxboat/courses/kubernetes-fundamentals-2/persistent-volumes) på Katacoda.

<!-- https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/ -->

<!-- Innan ni stänger ner hela miljön, lägg till webui https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/ för att inspektera K8s infrastrukturen. -->

<!-- https://www.katacoda.com/courses/kubernetes/liveness-readiness-healthchecks -->

<!-- https://www.katacoda.com/javajon/courses/kubernetes-pipelines/helm -->



#### Designa för Kubernetes {#design} 

Ni har nu titta lite på hur en applikations design/arkitektur påverkar hur lätt det är att köra den i K8s. Det finns så klart flera saker som är bra att tänka på när man skapa sin applikation men även hur man sätter upp den i K8s.

Läs [Architecting Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/architecting-applications-for-kubernetes) som tar upp lite om hur man ska tänka runt applikationen men även hur man använder K8s.

Läs [Modernizing Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/modernizing-applications-for-kubernetes) som handlar mer om hur man kan skriva om en applikation för att den ska fungera bättre för K8s.



### Microblog i Kubernetes {#microblog}

Nu ska vi sätta upp Microbloggen i Kubernetes och vi behöver en miljö att köra K8s i. Azure har en managed Kubernetes service kallat [AKS](https://azure.microsoft.com/sv-se/services/kubernetes-service/) men vi har inte tillgång till den. Tanken var att vi skulle installera ett eget kluster på våra VMs på Azure. Tyvärr finns det väldigt lite verktyg som funkar mot VMs i Azure för sätta upp kluster, det verkar som att de som använder Azure och k8s använder AKS. Sen visade det sig att något med hur Azure funkar gör att det inte går att koppla på en load balancer på ett eget kluster i Azure VMs. Vilket gjorde att när vi hade satt upp en applikation i klustret kunde vi inte se den.

Detta gör att vi får nöja oss med att sätta upp ett lokalt kluster på våra egna datorer med verktyget [Minikube](https://minikube.sigs.k8s.io/docs/). Minikube behöver dock en virtualiserings miljö att sätta upp pods i. De stödjer bl.a. VirtualBox, Docker och Hyper-V.



#### Installera verktyg {#install}

Även om Minikube funkar mot docker så behöver Windows och Mac användare köra mot VirtualBox. Load balancern funkar inte mot Docker. Linux användare kan köra i Docker.

##### Windows {#windows}

Jag hade problem med att köra Minikube via WSL (och har inte testat cygwin). Jag rekommenderar att installera saker i Windows och jobba i PowerShell för Kubernetes sakerna.

Det ska gå att köra Minikube i en VirtualBox VM med Linux på windows 10 men jag har inte testat och jag vet inte om load balancern funkar. Om någon vill testa kan ni läsa [Setup minikube on VirtualBox](https://vovaprivalov.medium.com/setup-minikube-on-virtualbox-7cba363ca3bc).



##### VirtualBox {#virtualbox}

Om ni inte redan har det installerat kan ni bara [ladda ner och installera det](https://www.virtualbox.org/wiki/Downloads). Ni behöver inte göra några inställningar.



###### Windows

Om ni har Hyper-V igång behöver ni stänga av det.

Sök på `Turn Windows features on or off` och checka av `Hyper-V`.



##### Minikube {#minikube}

Minikube är inte mycket svårare att installera.

Jobba igenom [Get started](https://minikube.sigs.k8s.io/docs/start/) för att installera och testa Minikube. I del 3 av guiden visar dem hur ni kan använda `kubectl` eller `minikube kubectl --`. Om ni vill installera kubectl hittar ni det [här](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

Om något går fel när ni kör `minikube start` behöver ni köra `minikube delete` för att rensa filer innan ni kör start igen.



#### Ingress som load balancer {#ingress}

Ni ska använda [Ingress-Nginx](https://kubernetes.github.io/ingress-nginx) som load balancer i klustret. Som tur är följer den med i Minikube och ni slipper installera den men den behöver fortfarande aktiveras.

Innan ni ska göra det ska ni läsa om skillnaden mellan [NodePort, load balancer och ingress](https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0).

När ni har läst klart, ska ni jobba igenom en guiden som visar hur ni aktiverar och använder Nginx Ingress. I och med att vi kör allt lokalt kommer det inte kopplas mot er riktiga domän utan ni kan använda vad ni vill. En bit in i guiden visar dem hur ni lägger till en domän i hosts filen och kopplar till klustret. I windows ligger Hosts filen i `C:\Windows\System32\drivers\etc\hosts`, ni behöver öppna den som admin för att ändra i den.

Innan ni jobbar igenom guiden behöver ni rensa klustret så det är tom sen tidigare guide, `minikube delete`.

Jobba nu igenom [aktiver och lära er Nginx Ingress i minikube](https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/). 

När ni är klara med guiden ska ni vara redo för att sätta upp Microblogen. Rensa först klustret och starta ett nytt.

```
minikube delete

minikube start

minikube addons enable ingress
```



#### Mysql i Kubernetes {#mysql}

Jobba igenom [Mysql i Kubernetes](kunskap/mysql_i_kubernetes).

Ni behöver inte köra någon SQL kod då Migrations i Flask sköter det när vi startar Microblogen.



#### Microblog deployment {#microblog}

Nästa steg är att skapa en deployment för Microblogen. Ni borde ha lärt er tillräckligt för att skapa en `service`,  `deployment` och `ingress` för Microblogen. Er microblog deployment ska ha 2 replicas, så att det alltid finns två pods rullande som kan hantera trafik.

Ni behöver skapa en ny Docker image av er Microblog och publicera till DockerHub. Ni kommer inte använda er av statsd i K8s och då kommer er nuvarande image generera fel för att Gunicorn inte kan koppla upp sig mot statsd.

Skapa en ny image utan statsd konfigurationen i Gunicorn och ge den versionen `no-statsd` på DockerHub.

Kolla i er `docker-compose.yml` för vilka env variabler ni behöver för att starta containern. Ni kan använda `mysql` istället för en IP till database i env variabeln `DATABASE_URL`. OBS! starta inte containern med ett specifikt network i er deployment, vi låter K8s hantera nätverk och Gunicorn behöver inte koppla upp sig till statsd.

För att felsöka kan ni använda följande kommandon och `minikube dashboard`.

```
kubectl get po

kubectl describe po

kubectl describe deployment microblog

kubectl logs <pod-name>

kubectl describe ingress
```

Ett tips är att lägga till en `livenessProbe`, på containern i er Deployment. Det används av K8s för att kolla om containern är redo att användas. K8s kommer pinga `/` och kolla vad den får tillbaka för status kod, alla mellan 200 och 399 så tolkas det som att containern mår bra och kan användas.

```
       ...
       livenessProbe:
          httpGet:
            path: /
            port: 5000
        ...
```

När ni kan se er microblog via webbläsaren med ett domännamn är ni klara. Bra jobbat!



### Kubernetes i produktion {#production}

Vårt kluster är väldigt simpelt, det är mer ett utvecklings kluster än något man hade kört i produktion. För att få en inblick i vad som krävs för att lyckas med Kubernetes i produktion ska ni läsa följande artiklar:

- [Kubernetes in production vs. Kubernetes in development: 4 myths](https://enterprisersproject.com/article/2018/11/kubernetes-production-4-myths-debunked)

- [7 Key Considerations for Kubernetes in Production](https://thenewstack.io/7-key-considerations-for-kubernetes-in-production/)

Kolla på "Running Kubernetes in Production: A Million Ways to Crash Your Cluster" där Henning Jacobs från websidan [Zalando.se](https://www.zalando.se/) pratar om hur de använder Kubernetes och vad de lärt sig av att köra det i produktions miljön.

[YOUTUBE src="pKFQuED_2kg" caption="Running Kubernetes in Production: A Million Ways to Crash Your Cluster"]



### Lästips {#lastips}

- Läs [Deploy Kubernetes In Five Different Ways](https://platform9.com/blog/5-methods-deploy-kubernetes/).



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[devops streams ht20](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_MEDc_y12Zxdf3_zgb6YWy)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 6xx i namnet.



Uppgifter  {#uppgifter}
-------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Sätt upp Microbloggen i Kubernetes med Minikube lokalt, skapa alla objekten deklarativt och spara filerna i `kubernetes` mappen.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v6.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad är ert första intryck av Kubernetes? Skulle ni vilja använda det i framtiden?

1. Vad är Container orchestration?

1. Varför är det svårare med stateful applikation jämfört med stateless i k8s?

1. Vad ska vi tänka på när vi designar ett projekt som ska köras i K8s?

1. Vad är viktigt att tänka på när man ska köra K8s i produktion?

1. Hur känns det efter att ni använt K8s, var det lika svårt som alla skriver/säger att det är?

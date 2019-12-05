---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom06: Container orchestration
==================================

Er Microblog har fått många nya användare och ni behöver utöka er infrastruktur för att hantera tycket på servrarna. Ni börjar med att utöka hur ni använder Ansible och startar upp fler servrar och containrar på servrarna. Dock märker ni snabbt att det är krångligt och Ansible är inte gjort för att användas till detta. Istället  börjar ni läsa på om container orchestration.



<!-- more -->
[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]



[FIGURE src="https://miro.medium.com/max/660/1*Mdj9wylSl0wqJ9sB0ENbRA.png" caption="Hur det är att lära sig kubernetes."]

Vi kommer använda oss utav Kubernetes (K8s) för container orchestration men det är bra att känna till vilka andra verktyg som finns och lite om vad som skiljer dem åt. Läs [What Is Container Orchestration?](https://blog.newrelic.com/engineering/container-orchestration-explained/)



### Kubernetes {#k8s}

Börja med en snabb introduktion till Kubernetes begrepp.

[YOUTUBE src="PH-2FfFD2PU" caption="Kubernetes in 5 mins."]

Om det inte var pedagogiskt nog som förklaring av Kubernetes kan jag rekommendera följande video där de lär ut Kubernetes som en barnbok.

[YOUTUBE src="Q4W8Z-D-gcQ" caption="The Illustrated Children's Guide to Kubernetes."]

Kubernetes har själva väldigt mycket och bra material för att lära sig Kubernetes och alla dess delar. En bra utgångspunkt är deras [dokumentation](https://kubernetes.io/docs/home/), där finns länkar till det mesta. För att få en bättre förståelse för grunderna i K8s (Kubernetes) och hur man kan interagera med det ska ni jobba igenom modul 1-6 i [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/).



#### Kubernetes infrastruktur






#### Kubernetes yaml {#yaml}

Det finns två sätt att hantera objekt (pods, deployments, etc...) i K8s imperative och declarative. I imperative kör vi kommandon i terminalen för att jobba mot ett K8s kluster, som ni gjorde i Kubernetes basics, och i declarative skriver vi konfiguration i filer och kör mot klustret. Läs om deras olika [för och nackdelar](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/). Vi vill givetvis jobba declarative för att då kan vi spara konfigurationen i Git och vi behöver inte oroa oss för snowflake servrar eller att bara en person har kunskapen om klustret.

[FIGURE src="https://www.digitalocean.com/community/tutorials/imperative-vs-declarative-kubernetes-management-a-digitalocean-comic" caption="digitalocean förklarar imperativ vs declarative"]

K8s använder yaml filer för att skriva konfigurationen i filer, som Ansible. Läs igenom [Kubernetes deployment tutorial](https://devopscube.com/kubernetes-deployment-tutorial/) för en överblick av hur filerna struktureras och vad de kan innehålla. Ni behöver inte jobba med i guiden, räcker om ni läser och förstår.

Ni kan öva på att använda [konfig filer på katacoda](https://www.katacoda.com/courses/kubernetes/creating-kubernetes-yaml-definitions).



#### Stateless applications {#statless}

K8s bygger på virtualisering och containrar, vilket är i grunden stateless. Vi har inte tillgång till persistent data, när vi stänger ner en container så försvinner dess data. K8s och även Docker är i grunden byggt för att köra stateless applikationer, men när populariteten av verktygen har ökat har även användningsområden ökat och de har då lagt till olika lösningar för att få till persistent data (stateful). Men det är inte lika lätt att få till persistent data i K8s som det är i Docker. Läs [Stateful vs Stateless Applications on Kubernetes](https://linuxhint.com/stateful-vs-stateless-kubernetes/) för en bättre genomgång av skillnaden.

Ni ska börja med att öva på att skapa en stateless applikation och som tur är har K8s själva en bra guide för det. Jobba igenom [Deploying PHP Guestbook application with Redis](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/). Ni behöver ha en miljö att köra K8s klustret i, i guiden finns det länk till sandbox miljöer både i Katacoda och Play with Kubernetes som ni kan använda. Jag rekommenderar Katacoda då jag inte fick Play with K8s att fungera. Katacoda har dessutom Nano installerat så ni kan skriva konfigurationen till filer. Allt borde fungera utan problem fram tills steget [Viewing the Frontend Service via NodePort](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/#viewing-the-frontend-service-via-nodeport), Katacoda kör inte minikube för att starta sitt kluster så ni kan inte använda det för att få en extern ip till ert kluster. Istället kan ni i Katacoda klicka på `+` som finns uppe på er terminal och välja `select port to view on host 1`. Då öppnas en ny tab i webbläsaren med koppling till klustret och där skriver ni in NodePort för er frontend service.



#### Stateful applications {#stateful}

    https://elastisys.com/2018/09/18/sad-state-stateful-pods-kubernetes/ svårigheten med stateful

Innan ni stänger ner hela miljön, lägg till webui https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/ för att inspektera K8s infrastrukturen.


#### Designa för Kubernetes {#design} 

Ni har nu titta lite på hur en applikations design/arkitektur påverkar hur lätt det är att köra den i K8s, det finns så klart flera saker som är bra att tänka på när man skapa sin applikation men även hur man sätter upp den i K8s. Läs [Architecting Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/architecting-applications-for-kubernetes) som tar upp lite om hur man ska tänka runt applikationen men även hur man använder K8s. Läs sen [Modernizing Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/modernizing-applications-for-kubernetes) som handlar mer om hur man kan skriva om en applikation för att den ska fungera bättre för K8s.



### Microblog i Kubernetes {#microblog}

microblog?
    https://www.digitalocean.com/community/tutorials/how-to-migrate-a-docker-compose-workflow-to-kubernetes
- något om alla olika sätt att köra k8s



### Kubernetes i produktion {#production}

Läs följande artiklar som tar upp olika saker man behöver tänka när man ska köra K8s i produktion:

- [Kubernetes in production vs. Kubernetes in development: 4 myths](https://enterprisersproject.com/article/2018/11/kubernetes-production-4-myths-debunked)

- [7 Key Considerations for Kubernetes in Production](https://thenewstack.io/7-key-considerations-for-kubernetes-in-production/)

Kolla på "Running Kubernetes in Production: A Million Ways to Crash Your Cluster" där Henning Jacobs från websidan [Zalando.se](https://www.zalando.se/) pratar om hur de använder Kubernetes och vad de lärt sig av att köra det i produktions miljön.

[YOUTUBE src="pKFQuED_2kg" caption="Running Kubernetes in Production: A Million Ways to Crash Your Cluster"]



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 6xx i namnet.



Uppgifter  {#uppgifter}
-------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v6.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad är Container orchestration?

1. Varför är det svårare med stateful applikation jämfört med stateless i k8s?

1. Vad ska vi tänka på när vi designar ett projekt som ska köras i K8s?

1. Vad är viktigt att tänka på när man ska köra K8s i produktion?

1. Hur känns det efter att ni använt K8s, var det lika svårt som alla skriver att det är?

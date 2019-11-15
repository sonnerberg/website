---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom04: Monitoring
==================================

Nu när vi har ett system upper och rullande behöver vi veta när något går fel, vi ska övervaka hela produktionsmiljön och alla dess delar.



<!-- more -->

[FIGURE src="https://upload.wikimedia.org/wikipedia/commons/d/d2/IoT_environmental_monitoring_system_solution_-_Overview.jpg" caption="Överblick av olika delar som kan ingå i ett system med övervakning."]


[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]
<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>




<!-- https://old.reddit.com/r/devops/comments/afqye3/whats_your_monitoring_and_alerting_stack_look_like/
https://itnext.io/deploy-elk-stack-in-docker-to-monitor-containers-c647d7e2bfcd
 -->
 
<!-- Elastic stack
https://logz.io/blog/10-elasticsearch-concepts/
https://github.com/nickjj/ansible-docker
https://www.guru99.com/elk-stack-tutorial.html
    Ny instance med t2.small
    Ny SG
    RP i LB nod för ELK
    Installera Beats på övriga instancer
    +1 app instance?
    Om de kör provision igen för att bara få upp ELK kommer det även starta upp en till av varje annan!!
    load balancer - https://galaxy.ansible.com/entercloudsuite/filebeat
        https -> http, enabled -> started?
    galaxy https://blog.ktz.me/getting-started-with-ansible-galaxy/
 -->


### Monitoring {#monitoring}

https://docs.microsoft.com/en-us/azure/devops/learn/what-is-monitoring
https://pandorafms.com/blog/why-you-need-a-monitoring-system/
https://queue.acm.org/detail.cfm?id=3178371



### Log management {#log}

Log management är processen av att samla in, lagra, hantera och analysera loggar från infrastruktur, system och applikation. Det är ett väldigt brett ämne då typ allt genererar loggar av något slag och systemet för att sköta log hantering är väldigt avancerade. Läs [What is log management](https://www.tripwire.com/state-of-security/security-data-protection/security-controls/what-is-log-management/) för att få en överblick av delarna som ingår i log management. Läs sen om vilken användning olika roller har av log management i [Why is log management important](https://www.graylog.org/post/why-is-log-management-important).

Läs igenom [ELK stack tutorial](https://www.guru99.com/elk-stack-tutorial.html)för en överblick av ett av de mest populära systemen för Log management.



### Application performance monitoring (APM) {#apm}

APM kan även kallas Application Performance Management (också APM), enligt vissa är det skillnad. APM är att övervaka, hantera och diagnosera prestanda, tillgänglighet och användare upplevelse av applikationer. Avancerade program används för att göra om data till "business value". Läs [What is application performace monitoring](https://www.eginnovations.com/blog/what-is-application-performance-monitoring/).



### Observability {#observability}

På senare år har det även börjat talas mycket om Observability vilket hänger ihop med monitoring. Vi kan se monitoring som att ha kolla på hälsan av våra system medan observability är att ha djup insikt i hur våra system beter sig. Observability ska hjälpa oss hitta fel och problem. Läs [Observability sv. Monitoring](https://dzone.com/articles/observability-vs-monitoring).

Om ni vill kan ni även kolla på [What Does the Future Hold for Observability?](https://www.youtube.com/watch?v=MkSdvPdS1oA).



### Prometheus och Grafana {#prometheus}

Vi ska använda oss av [Prometheus](https://prometheus.io/), ett väldigt populärt verktyg för att lagra tidsserie data, visualisera data samt att sätta upp larm/notifikation vid events. Prometheus har inbyggt att visa simpla grafer för data men det är vanligt att använda sig utav verktyget [Grafana](https://grafana.com/) för att bygga dashboards med grafer och diagram över data.

Börja med att läsa [Prometheus Monitoring : The Definitive Guide in 2019](https://devconnected.com/the-definitive-guide-to-prometheus-in-2019/) för en överblick av vad Prometheus är och vad det innehåller.

När ni sen har lite kolla på hur Prometheus fungerar ska ni testa installera Prometheus, Grafana och koppla ihop dem. Först behöver ni någonstans att kör verktygen, kolla på följande video för att uppdatera Ansible skripten för att skapa servrar på AWS:

[YOUTUBE video med skapa en till small server]

Följ nu guiden [Complete Node Exporter Mastery with Prometheus](https://devconnected.com/complete-node-exporter-mastery-with-prometheus/) som visar hur ni kan övervaka resurserna på AWS instansen som ni installerar Prometheus på. OBS! När ni sätter `scrape_interval` sätta inte mindre än 30 sekunder, era AWS instanser har begränsat med resurser, vi kan inte gå helt Crazy!  
Ni ska senare göra en Ansible playbook för att sätta upp Prometheus och Grafana, då kan ni installera det hur ni vill. Men börja med att följa guiden för att lära er verktygen först. 


Nginx

Docker

Gunicorn

MySQL
Finns det färdiga dashboards för dessa?

Alerting

Om finns tid, kolla hur skriva om ansible skript utan elastic ip!



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 4xx i namnet.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Ni har lagt till en till instans i er AWS infrastruktur och den nya instansen kör Prometheus. Lägg till en Reverse Proxy i er Nginx konfiguration som leder till Prometheus interfacet, om ni även kör Grafan lägg till en reverse proxy till den också. Länka dem i er redovisningstext.

1. Prometheus ska övervaka Nginx, MySQL databasen, Docker containrarna för microblog och databasen och AWS instanserna. För instanserna är det intressant att se hur mycket minne som är kvar på hårddisken, CPU och RAM användning. Skapa en dashboard för varje ..... Om ni använder Grafana gör era dashboards där istället för i Prometheus.

1. Skapa larm i Prometheus som varnar om någon Docker container, Nginx eller instans inte längre är igång. Skapa även ett larm som varnar om minnet på hårddisken på Prometheus instansen har mindre än 5G kvar.
Hitta ett sätt som kan användas för att temporärt tar plats på hårddisken så larmet kan testas.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v4.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Beskriv vad som menas med Monitoring, olika saker som brukar övervakas och vad det används till.

1. Beskriv Log management och vad det används till.

1. Beskriv APM vad det används till.

1. Beskriv Observability och vad det används till.

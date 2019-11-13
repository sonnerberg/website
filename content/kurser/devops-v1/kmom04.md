---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom04: Monitoring
==================================

Nu när vi har ett system upper och rullande behöver vi veta när något går fel, vi ska börja övervaka systemet och kolla olika sätta/saker man brukar övervaka.



<!-- more -->
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


### Monitoring

https://docs.microsoft.com/en-us/azure/devops/learn/what-is-monitoring
https://pandorafms.com/blog/why-you-need-a-monitoring-system/
https://queue.acm.org/detail.cfm?id=3178371

### Log management

#### ELK?

### Application monitoring

### Observability

https://medium.com/@copyconstruct/monitoring-and-observability-8417d1952e1c

1. Kolla på [What Does the Future Hold for Observability?](https://www.youtube.com/watch?v=MkSdvPdS1oA).

### Prometheus

https://devconnected.com/the-definitive-guide-to-prometheus-in-2019/
https://prometheus.io/docs/introduction/overview/


### Grafana?

### Bok {#bok}

Kolla in följande.



### Artiklar {#artiklar}

Kika igenom följande artiklar.



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 4xx i namnet.

### Lästips {#lastips}





Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*


### Övningarr {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna..



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.


1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v4.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

...
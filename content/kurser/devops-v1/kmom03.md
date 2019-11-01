---
author:
    - aar
revision:
    "2019-07-29": "(A, aar) Första versionen."
...
Kmom03: Configuration Management och Continuous Deployment
==================================

Vi fortsätter med att kolla in fler sätt att automatisera flöden. Vi lär oss Ansible för Configuration Management (CM) och även för Infrastructure as Code. Tillsammans med Ansible och CircleCI ska vi också utveckla vår Continuous Delivery till Continuous deployment (också CD).



<!-- more -->

[FIGURE src="https://www.gocd.org/assets/images/blog/continous-delivery-vs-deployment-infographic/continuous-delivery-vs-continuous-deployment-infographic-305dd620.png"]


[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]
<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



## Infrastructure as Code och Configuration Management {#iasc-cm}



## Ansible {#ansible}



### Hur fungerar Ansible? {#funkar-ansible}



### Göra

10-första minuter https://ryaneschinger.com/blog/securing-a-server-with-ansible/

3 servrar

nginx role

app role (docker)

databas role (docker)



### Ansible på CircleCi för CD {#cd}




### Bok {#bok}

Kolla in följande.



### Artiklar {#artiklar}

Kika igenom följande artiklar.

1. CD vs CD

1. https://blog.theodo.com/2016/05/straight-to-production-with-docker-ansible-and-circleci/

### Lästips {#lastips}

1. Hantera användare på produktionsservern https://www.cogini.com/blog/managing-user-accounts-with-ansible/.


### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 3xx i namnet.





### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Utöka projektet med Ansible och CD. (Gör om skripten till ansible kod med 3 servrar istället för 1)
Om jobbar tillsammans ska de ha varsin användare. https://dev.iachieved.it/iachievedit/ansible-and-aws-part-5/
1. Skriv skript som kollar om service är uppe, om inte kör ansible för att sätta upp annars bara uppdatera. (En deployer node?)

<!-- 1. Lägg till något i koden. -->

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v3.0.0, om du pushar kmom02 flera gånger kan du öka siffrorna efter 3:an.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

...
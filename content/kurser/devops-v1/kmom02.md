---
author:
    - aar
revision:
    "2019-07-29": "(A, aar) Första versionen."
...
Kmom02: Configuration Management och Continuous Deployment
==================================

Vi fortsätter med att kolla in fler sätt att automatisera flöden. Vi lär oss Ansible för Configuration Management (CM) och kollar på hur vi automatisk kan driftsätta (CD) projektet när vi släpper en ny release. 



<!-- more -->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **40 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

Ingen labbmiljö än så länge!



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*



### Bok {#bok}

Kolla in följande.



### Artiklar {#artiklar}

Kika igenom följande artiklar.

1. CD vs CD


### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller genomgångar och föreläsningar som spelas in (streamas) och därefter läggs i en spellista. Du kan nå spellistan på "[Devops streams]()".



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*


### Övningarr {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna..

ansible linter

1. [Configuration Management med Ansible]()

1. [Continuous Delivery med Circle CI och Github]()



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Utöka projektet med Ansible och CD. (Gör om skripten till ansible kod med 3 servrar istället för 1)
Om jobbar tillsammans ska de ha varsin användare. https://dev.iachieved.it/iachievedit/ansible-and-aws-part-5/
1. Skriv skript som kollar om service är uppe, om inte kör ansible för att sätta upp annars bara uppdatera. (En deployer node?)

<!-- 1. Lägg till något i koden. -->

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v2.0.0, om du pushar kmom02 flera gånger kan du öka siffrorna efter 2:an.


extra: fixa vpc för servrarna


Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

...
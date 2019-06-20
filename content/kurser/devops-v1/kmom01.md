---
author:
    - aar
revision:
    "2019-04-17": "(A, aar) Första versionen släppt."
...
Kmom01: Introduktion till DevOps
==================================

Det är en fullspäckat kurs där vi ska lära oss många ny verktyg och koncept. Vi börjar kursen med att ni ska bestämma er för ett projekt att utveckla under kursensgång. Vi tar en grundlig introduktion till konceptet DevOps som vi kommer fördjupas oss mer i längre fram i kursen.
Ni ska börja koda på projektet direkt, skriva tester, skapa github repo och koppla det till ett Continues Integration verktyg som Travis eller Circle Ci.



<!-- more -->
Skriv enhetstester från början, tips att testa på TDD. Jag rekomenderar boken Clean Architecture för en intro till TDD och annat bra.

Loggin från start?

Lämna in vad ni planerar för projekt och länk till github repot.

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

Ingen labbmiljö än så länge!



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*



### Bok {#bok}

Kolla in följande.

....



### Artiklar {#artiklar}

Kika igenom följande artiklar.

1. https://12factor.net/logs


### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller genomgångar och föreläsningar som spelas in (streamas) och därefter läggs i en spellista. Du kan nå spellistan på "[Devops streams]()".



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-12 studietimmar)*


### Övningarr {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna..

1. Om du inte redan har en virtuell server och domännamn jobba igenom artikeln ["GitHub Education Pack och en server på Digital Ocean"](kunskap/github-education-pack-och-en-server-pa-digital-ocean) där vi använder Github Education Pack för att skaffa en egen Virtuell Server med ett eget domännamn. Du kan skippa steget "Installera nodejs och npm". Om du behöver sätta upp servern på nytt men inte vill göra allt manuellt finns det skripts i [iac/10-first-minutes](github.com/dbwebb-se/devops-proj/infrastructure-as-code/10-first-minutes).

1. Sätt upp Continuous integration med CircleCi ["Continuous Integration With Python: An Introduction"](https://realpython.com/python-continuous-integration/#overview-of-continuous-integration-services)

# Använd exemplet från ovanför?
1. Driftsätta ett Python Flask projekt ["Driftsätt en Flask app"](kunskap/dirftsätt-en-flask-flask-app). 



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Forka och bekanta dig med koden i projektet, CI och driftsätt [Ett proj](uppgift/).

1. Skriv egna tests/fixa bugg och driftsätt nya versionen [Uppdatera och driftsätt manuellt](uppgift/uppdatera-och-driftsätt-manuellt) 

1. Försäkra dig om att du har gjort `dbwebb publish redovisa` och taggat din inlämning med version 1.0.0 (eller högre) samt pushat repot inklusive taggarna till GitHub.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

...
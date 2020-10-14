---
author:
    - aar
revision:
    "2019-04-17": "(A, aar) Första versionen släppt."
...
Kmom01: Introduktion till DevOps
==================================

[WARNING]
**Utveckling pågår**

Detta kmom är under uppdatering, påbörja inte förrän denna gula rutan är borttagen.

[/WARNING]

Det är en fullspäckat kurs där vi ska lära oss många ny verktyg och koncept. I kursen ska vi lära oss både om det kulturella inom devops men även det praktiska. Vi börjar med att skaffa en produktionsmiljö och bekantar oss med ett påbörjat projekt som ska kopplas till en CI kedja och driftsätta manuellt.


<!-- more -->



## Vad är devops? {#devops}

Kolla på följande video för att få en introduktion till ämnet devops. Devops är ett brett ämne med många olika defenitioner, här försöker skaparen av CM verktyget [Chef](https://www.chef.io) beskriva konceptet och komma fram till en rimlig definition.

[YOUTUBE src="_DEToXsgrPc" caption="Chef Style DevOps Kungfu - Adam Jacob Keynote - ChefConf 2015."]


<!-- Ny video https://www.youtube.com/watch?v=Me3ea4nUt0U kortare och med om arbetsflödet -->

För de som vill gräva ner sig i den teoretiska delen och företagskulturen av devops rekommenderar jag boken [Effective Devops](http://tinyurl.com/yyuw7a9w). Läs kapitel 1-6.



## Miljö {#miljo}

Tanken är att vi ska jobba med ett projekt igenom hela kursen och då behöver vi verktyg och program för att jobba med koden. Vi kommer ha både en lokal utvecklingsmiljö och en produktionsmiljö. Vi börjar med utvecklingsmiljön, som vi brukar kalla labbmiljö.



### Labbmiljön  {#labbmiljo}

Vi kommer att utöka vad som ingår i labbmiljön under kursen. Till en början behöver vi programmen som finns i [installera labbmiljön](./../labbmiljo).



### Produktionsmiljö {#produktionsmiljo}

När man jobbar enligt devops ska saker ofta gå snabbt och automatiskt, då underlättar det om man snabbt och enkelt kan starta upp och stänga ner servrar. Därför ska vi använda oss av en molntjänst, mer specifikt [Amason Web Services (AWS)](https://aws.amazon.com/).



#### AWS {#aws}

För att få en introduktion till vad AWS är kan ni kolla in "AWS in 10 minutes".

[YOUTUBE src="r4YIdn2eTm4" caption="AWS in 10 minutes."]

Sen behöver du skaffa ett konto på AWS, som student kan man skapa ett gratiskonto och få 100$ i kredit gör till och med steg 10 i [AWS Educate starter account](https://www.instructables.com/id/Guide-to-AWS-Educate-Starter-Account/). Om du redan har ett konto på AWS kan du få 75$ i kredit på det. Gör då sida 4 och 5 i [Creating an aws account for students...](http://holowczak.com/creating-an-aws-account-for-student-use-with-aws-educate/4/).

Skapa en server på AWS.

[YOUTUBE src="fA_4k8vJp7I" caption="101 Skapa server på AWS."]


#### Domännamn {#domain}

Det underlättar dessutom om vi har ett domännamn som vi kan länka till en server. Om du inte redan har ett kolla in artikeln ["GitHub Education Pack och en server på Digital Ocean"](kunskap/github-education-pack-och-en-server-pa-digital-ocean). I den görs mer saker än vad vi behöver göra så kolla bara på delen [GitHub Education Pack](kunskap/github-education-pack-och-en-server-pa-digital-ocean#gep) och [En domän till din server](kunskap/github-education-pack-och-en-server-pa-digital-ocean#domain) (Du kan sluta läsa när det börjar handla om Digital ocean).

<!-- Möjlig alternativ till namecheap, http://www.dot.tk/en/index.html?lang=en -->

Koppla ditt domän namn till servern.

[YOUTUBE src="diuYaLN1ius" caption="102 Koppla domän till AWS."]



#### 10 första minuterna {#10first}

Gör sen [Första 10 minuter på en server](kunskap/github-education-pack-och-en-server-pa-digital-ocean#first10) delen. Tänk på att logga in med användaren `admin` istället för `root`. När du har loggat in vill du däremot byta till root användaren innan du fortsätter, gör det med `sudo su`. Du kan skippa följande kommandon:
```bash
apt-get remove --purge unscd
userdel -r debian
```
Brandväggsdelen är frivillig i och med att vi kommer använda oss av security groups i AWS för att kontrollera kopplingar till servern.



### Appen {#appen}

Nästa steg är att bekanta oss med appen som du ska jobba på i kursen. Läs igenom och följ [Introduktion till Devops appen](kunskap/introduktion_till_devops_appen).



#### Driftsätt appen {#driftsatt}

Vi har en server och vi har en app, då måste vi lära oss ["Driftsätta en Flask app"](kunskap/driftsatta-en-flask-app). Om något blir fel och du inte riktigt vet hur du ska ångra det, skapa om servern i AWS och använd dig av [skripten i repot](https://github.com/dbwebb-se/microblog/tree/master/scripts) för att snabbt göra de 10 första minuterna på en server och börja om med driftsättningen.

<!-- https://askubuntu.com/questions/879437/ensurepip-is-disabled-in-debian-ubuntu-for-the-system-python -->



### Continues Integration {#ci}

Vi vill ha en CI-kedja till repot så att testerna automatiskt körs när du gör push. I kursen har jag valt att använda [CircleCi](https://circleci.com/). Läs igenom ["Continuous Integration With Python: An Introduction"](https://realpython.com/python-continuous-integration/) för att se hur man kan sätta upp CircleCi för ett Python projekt och gör det sen för ditt forkade repo.  
När du pushar din kod ska CircleCi köra alla unittester, integrationtester och validera koden.





### Video {#video}

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 1xx i namnet.



### Lästips {#lastips}

1. [The 12 Factor App](https://12factor.net/) är en populär "standard" för att bygga Software-as-a-service och  används mycket i devops sammanhang.

1. [DevOps Roadmap](https://roadmap.sh/devops) Visar upp vanligaste verktygen man behöver kunna för att jobba med de tekniska delarna av devops.

    - Här kan ni se vilka av verktygen vi kommer använda oss i kursen, [i fylld devops roadmap](image/devops/devops-roadmap-filled.png)



Uppgifter  {#uppgifter}
-------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas.

1. Lägg till funktionaliteten att följa andras blogginlägg. Jobba igenom [Miguels guide för att följa andra](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-viii-followers) OBS! koden kommer inte fungera rakt av, t.ex. när Miguel skapar routes skriver han `app` men ni behöver använda `bp`. Se till att de nya testerna går igenom och driftsätt den nya versionen på din server. Testerna kommer  inte heller fungera rakt av, Miguel använder sig av `unittest` modulen medan vår microblog använder `pytest`. Ni behöver skicka med `test_app` som parameter för att kunna använda databasen i testerna.

1. Lägg till en CircleCi badge i README filen för repot.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v1.0.0. Om du pushar kmom01 flera gånger kan du öka siffrorna efter 1:an.

1. Inkludera en länk till ditt GitHub repo och din webbsida (domännamn) i din inlämning på Canvas.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad var din uppfattning av devops för en vecka sen?

1. Har det ändrats efter denna veckan?

1. Hur skulle du definiera devops?

1. Finns det något speciellt du vill lära dig i denna kursen?

1. Vad tycker du om kmom01's upplägg och storlek?

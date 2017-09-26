---
author:
    - mos
category:
    - anax
    - php
    - kursen ramverk1
revision:
    "2017-09-25": "(A, mos) Första utgåvan."
...
Integrera din packagist modul med verktyg för autmatisk test och validering
==================================

[FIGURE src=image/snapht17/packagist-submitted.png?w=c5&cf&a=10,50,50,0 class="right"]

Vi utgår från en modul som vi tidigare publicerade på GitHub och Packagist. Modulen innehåller rutiner för enhetstester och kodvalidering. Vi skall nu integrera modulen med externa tjänster som utför dessa tester varje gång vi committar ändringar eller gör pull requests till repot.

Vi integrerar med en handfull tjänster såsom Travis, CircleCI, Scrutinizer och SensioLab samt knyter in några av dem till en Gitter-kanal för utvecklare av modulen. Vi får ett flöde för automatiserade tester som skapar grunden för begreppet CI, _Continuous Integration_. Varje commit kickar igång ett flöde där vår modul integreras och testas mot beroenden i ett antal miljöer och system.

<!--more-->

Jag väljer att jobba vidare med min REM server som nu är modulariserad och publicerad på GitHub och Packagist.

**ARBETE PÅGÅR**
<!--stop-->



Förutsättning {#pre}
--------------------------------------

Du har jobbat igenom artikeln "[Skapa en PHP-modul på Packagist och integrera med Anax](kunskap/skapa-en-php-modul-pa-packagist-och-integrera-med-anax)".



En REM server {#remserver}
--------------------------------------

För att visa hur det fungerar så behöver vi en modul. Jag väljer att jobba med modulen REM server som finns på [GitHub under `canax/remserver`](https://github.com/canax/remserver/) och på [Packagist som `anax/remserver`](https://packagist.org/packages/anax/remserver).

Det vi nu kommer att göra handlar mest om att konfigurera kopplingar mellan GitHub och externa tjänster för automatiserade tester och kodvalidering.

Du kommer behöva skaffa konton på respektive tjänst. Men på de flesta kan du använda ditt konto från GitHub för att logga in.



Automatisera tester {#maketest}
--------------------------------------

Vi pratar om autmatiserade tester och det förutsätter att jag har enhetstester och validering på mitt repo.

Det fungerar nu på följande sätt.

```text
make install
make check
make test
```

Vid `make install` installeras en lokal utvecklingsmiljö i repot. Du kan se vilken exekverbar som används och dess version via `make check`. Testerna körs när du gör `make test`. 

Som det är nu så är det bara phpunit som kan göra att `make test` misslyckas. Verktygen phpcs och phpmd körs men även om de hittar fel så avbryts inte testerna. Det är så makefilen är konfigurerad i sitt utgångsläge. Vill man vara hårdare och avbryta testerna när phpcs/phpmd misslyckas så kan man konfigurera om makefilen.

Makefilen och installationen av en lokal utvecklingsmiljö och möjligheten att köra hela testsuiten är central för automatiserade tester. Detta innebär att godtyckligt system kan checka ut repot och köra `make install test` för att köra hela testsuiten.

Vill jag se hur bra kodtäckning jag har på mina enhetstester så ligger den informationen under `build/coverage` och kan inspekteras i en webbläsare.



Travis {#travis}
--------------------------------------

Vi börjar med att integrera mot tjänsten [Travis](https://travis-ci.org/). bekanta dig med webbplatsen och kika kort i dess dokumentation.

Du kan sedan studera [Travis statusen för GitHub organisationen CAnax](https://travis-ci.org/canax) och alla dess moduler som omfattas av automatiserade tester. Klicka dig in på en av modulerna för att se status på dess senaste bygge. 

[FIGURE src=image/snapht17/travis.png?w=w2 caption="Travis har koll på hur modulerna i Anax klarar sina automatiserade tester."]

I min modul finns redan en konfigurationsfil `.travis.yml` för Travis och det gör det enkelt för mig att lägga till denna nya modul.

Du kan titta på denna video hur jag går tillväga för att lägga till modulen på Travis.

**VIDEO**

När du är klar får du en badge.



CircleCI {#circleci}
--------------------------------------

Nästa tjänst är [CircleCI](https://circleci.com/). Bekanta dig med webbplatsen och logga in.

Likt Travis det en byggtjänst som kan köra automatiserade tester genom att checka ut repon från GitHub. Egentligen räcker det men en tjänst, men vi tar och integrerar vårt repo mot CircleCI också.

Via CircleCI kan du se status för de [senaste byggena för modulen `anax/di`](https://circleci.com/gh/canax/remserver).

[FIGURE src=image/snapht17/circleci.png?w=w2 caption="CircleCI är en byggmiljö likt Travis."]

I mitt modul-repo finns en konfigurationsfil `circle.yml` och med den kan jag lägga upp mitt repo så att CircleCI checkar ut det och kör mina tester.

Så här kan det se ut.

**VIDEO**

När du är klar får du en badge.



Scrutinizer {#scrutinizer}
--------------------------------------

[Scrutinizer](https://scrutinizer-ci.com/) är nästa byggtjänst. Logga in och bekanta dig med tjänsten.

Du kan se hur detaljer om [modulen `anax/di` presenteras](https://scrutinizer-ci.com/g/canax/di/). Srutinizer gör sin egen bedömning om kodens kvalitet och utger ett omdöme om modulens delar samt ger bas för förbättringdsförslag för koden. Man ser även hur mycket kodtäckning enhetstesterna har och man kan se vilka delar av koden som är täckta eller ej.

Ett verktyg likt Scrutinizer kan ge dig indikationer på kodens kvalitet.

[FIGURE src=image/snapht17/scrutinizer.png?w=w2 caption="Via Scrutinizer kan du få mer detaljerad information om din kod via statiskt kodanalys."]

I mitt repo finns en konfigurationsfil `.scrutinizer.yml` och med den kan jag integrera mitt repo med Scrutinizer.

Så här kan det se ut när jag lägger till Scrutinizer.

**VIDEO**

När du är klar får du en badge.



Sensiolabs {#sensiolabs}
--------------------------------------

Tjänsten [SensioLabsInsight](https://insight.sensiolabs.com/) är kopplad till företaget bakom Symfony. Logga in och bekanta dig med tjänsten.

Du kan se status för [senaste bygget för `anax/di`](https://insight.sensiolabs.com/projects/850a0607-ad17-4dcc-924c-ad0bb6ae8d63). 

Så här kan det se ut när jag lägger till SensioLabs.

**VIDEO**

När du är klar får du en badge.



Gitter {#gitter}
--------------------------------------

Via chatt tjänsten Gitter kan du skapa en egen chattkanal för ditt repo. Du kan också koppla Git repot till kanalen så att man ser alla commits och taggar mot repot.

Det går också att koppla upp status för när Travis och CircleCI checkar ut och testar din kod. Om någon av dem misslyckas så syns det i chatt-kanalen.

När man jobbar i team om att utveckla mjukvara kan detta vara ett sätt att hålla sig ajour med senaste status för en modul.

Så här kan det se ut när jag skapar Gitter-kanalen och konfigurerar den.

**VIDEO**



https://gitter.im/canax/remserver

Notifikationer från Travis, CircleCI.

När du är klar får du en badge.



Avslutningsvis {#avslutning}
--------------------------------------

Vi har gått igenom hur man skapar en fristående modul, hur man kan jobba med den och hur man kan publicera den på GitHub och Packagist och hur den kan hanteras med composer.

Denna artikel har en [egen forumtråd](t/6840) som du kan ställa frågor i, eller bidra med tips och trix.

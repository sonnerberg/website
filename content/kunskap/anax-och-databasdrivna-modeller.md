---
author:
    - mos
category:
    - anax
    - remserver
    - php
    - kursen ramverk1
revision:
    "2017-08-15": "(A, mos) Första utgåvan."
...
Anax och databasdrivna modeller
==================================

[FIGURE src=image/snapht17/anax-route-config.png?w=c5&cf&a=10,50,40,0 class="right"]




<!--more-->

Som vanligt funderar vi och utvärderar efter hand.

Vi fortsätter att använda REM servern som exempelkod.



Förutsättning {#pre}
--------------------------------------

Du har läst artikeln "[Anax med Dependency Injection](kunskap/anax-med-dependency-injection)".



Glöm inte `.htaccess` {#htaccess}
--------------------------------------

Glöm inte att redigera din `.htaccess` när du publicerar till studentservern.











<!--stop-->



En tom Anax {#initanax}
--------------------------------------

När jag jobbar i denna artikeln vill jag ha en tom webbplats att leka med så jag använder kommandot `anax` för att scaffolda en grundstruktur som bygger på Anax och DI.

```bash
# Gå till kursrepot
cd me/kmom03/
anax create anaxr/ ramverk1-di
cd anaxr
```

Öpnna din webbläsare mot `htdocs` för att kontrollera att webbplatsen fungerar. Kontrollera att routen `htdocs/debug/info` också fungerar.





Avslutningsvis {#avslutning}
--------------------------------------

Vi har återgien gjort en övning i refaktoring av ramverkets kod för att studera olika alternativ till strukturer. Nu var det routern som fick en genomgång och förändring i hur konfigurationen sker.

Denna artikel har en [egen forumtråd](t/6619) som du kan ställa frågor i, eller bidra med tips och trix.

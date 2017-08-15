---
author:
    - mos
category:
    - anax
    - php
    - kursen ramverk1
revision:
    "2017-08-15": "(A, mos) Första utgåvan."
...
Anax och formulärhantering
==================================

[FIGURE src=image/snapht17/anax-route-config.png?w=c5&cf&a=10,50,40,0 class="right"]

Vi skall se om vi kan anänvda externa klasser för att göra vår ramverkskod mer potent att lösa avancerade saker med mindre rader kod. Troligen blir det inte mindre rader kod som helhet dock, men förhoppningsvis blir det färre rader som vi själva behöver skriva.

Vi tar och tittar på formulärhantering och CRUD för att se en variant på hur det kan ske och på hur koden kan struktureras.


<!--more-->

Som vanligt funderar vi och utvärderar efter hand.



Förutsättning {#pre}
--------------------------------------

Du har läst artikeln "[Anax med Dependency Injection](kunskap/anax-med-dependency-injection)" och artikeln "[Att konfigurera routern i Anax](kunskap/att-konfigurera-routern-i-anax)".



Glöm inte `.htaccess` {#htaccess}
--------------------------------------

Glöm inte att redigera din `.htaccess` när du publicerar till studentservern.



En tom Anax {#initanax}
--------------------------------------

När jag jobbar i denna artikeln vill jag ha en tom webbplats att leka med så jag använder kommandot `anax` för att scaffolda en grundstruktur som bygger på Anax och DI tillsammans med de uppgraderade router-konfigurationen.

```bash
# Gå till kursrepot
cd me/kmom04/
anax create anax4/ ramverk1-route
cd anax4
```

Öppna din webbläsare mot `htdocs` för att kontrollera att webbplatsen fungerar. Kontrollera att routen `htdocs/debug/info` också fungerar.



Ett formulärexempel {#formularex}
--------------------------------------

Jag tänkte att vi gör ett par enkla formulärexempel som skapar en användare, redigerar den och raderar den.

Det första vi behöver är Anax modul för HTML formulär, `anax/htmlform` och vi installerar den så här.

```bash
composer require anax/htmlform
```

För att bekanta oss med modulen så öppnar vi webbläsaren mot modulens katalog `vendor/anax/htmlform/htdoc` och vi testar exemplen i `htdoc/formmodel`.

Modulen hjälper oss att skapa HTML formulär och hanterar postning av formulär, validering och ompostning vid valideringsfel. Modulen ger en bestämd struktur i hur man jobbar med formulär. Tanken är att det kan tjäna tid och programmeringsrader, när man väl lärt sig att använda en sådan modul.

I modulen är det flexibelt hur man väljer att skapa sina formulär, man kan använda arrayer tillsammans med callbacks eller klasser med metoder. Vi skall titta närmare på de exempel som använder klasser.






<!--stop-->





Avslutningsvis {#avslutning}
--------------------------------------

Vi har återigen gjort en övning i refaktoring av ramverkets kod för att studera olika alternativ till strukturer. Nu var det routern som fick en genomgång och förändring i hur konfigurationen sker.

Denna artikel har en [egen forumtråd](t/6619) som du kan ställa frågor i, eller bidra med tips och trix.

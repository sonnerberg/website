8---
author:
    - mos
category:
    - anax
    - php
    - kursen ramverk1
revision:
    "2017-08-15": "(A, mos) Första utgåvan."
...
Anax och databasdrivna modeller
==================================

[FIGURE src=image/snapht17/anax-route-config.png?w=c5&cf&a=10,50,40,0 class="right"]

Vi bygger vidare på ett exempel med formulärhantering i Anax och integrerar med en extern modul för databashantering.



<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har läst artikeln "[Anax och formulärhantering](kunskap/anax-och-formularhantering)". Denna artikel om databashantering tar vid där formulärartikeln slutade.



Glöm inte `.htaccess` {#htaccess}
--------------------------------------

Glöm inte att redigera din `.htaccess` när du publicerar till studentservern.



Bygg vidare på formulärexemplet {#initanax}
--------------------------------------

Vi jobbar vidare i samma katalog `anax4` där vi gjorde formulärexemplet. Du bör alltså ha tre routes som fungerar, nämligen `user`, `user/login` och `user/create`.

Tanken är att vi skall implementera så att vi kan skapa en användare och logga in som en användare. Vi vill visa på ett flöde som omfattar delar av formulär och CRUD mot en databas.

Testa även att öppna din webbläsare mot `htdocs` för att kontrollera att index-sidan för webbplatsen fungerar tillsammans med routen `htdocs/debug/info`.

Om du av någon anledning vill starta på nytt och utgå från koden som fanns i formulärartikeln så kan du scaffolda fram den. Se det som ett alternativ.

```bash
# Ställ dig i kursrepot me/kmom04 
anax create anax4f ramverk1-form
cd anax4f
```

Om du väljer att skapa nytt behöver du kontrollera att de olika routerna fungerar som tänkt.

Oavsett vad så bör vi nu ha en liknande kodbas att utgå ifrån. Jag jobbar vidare i min katalog `anax4`.



Installera modul för databas {#instdb}
--------------------------------------

Vi skall installera en Anax modul som hjälper oss med databashanteringen.

```bash
# Gå till anax4
composer require anax/database
```



Öppna din webbläsare mot `htdocs` för att kontrollera att webbplatsen fungerar. Kontrollera att routen `htdocs/debug/info` också fungerar.








<!--stop-->








Avslutningsvis {#avslutning}
--------------------------------------

Vi har återgien gjort en övning i refaktoring av ramverkets kod för att studera olika alternativ till strukturer. Nu var det routern som fick en genomgång och förändring i hur konfigurationen sker.

Denna artikel har en [egen forumtråd](t/6619) som du kan ställa frågor i, eller bidra med tips och trix.

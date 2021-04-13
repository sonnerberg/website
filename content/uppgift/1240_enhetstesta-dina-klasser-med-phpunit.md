---
author: mos
category:
    - kurs mvc
revision:
    "2021-04-13": "(A, mos) Första utgåvan."
...
Enhetstesta dina klasser med PHPUnit
===================================

Du har sedan tidigare ett antal klasser i PHP som du nu skall skapa en test suite för.

Din test suite innehåller enhetstester som körs med PHPUnit.

Du skall försöka att nå så hög kodtäckning som möjligt.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har PHP i din path i terminalen och du har installerat composer.

Du kan grunderna i enhetstestning med phpunit.

Du har installerat Xdebug och kan mäta kodtäckning med phpunit.



Introduktion och förberedelse {#intro}
-----------------------

Gör följande steg för att förbereda dig för uppgiften.



### Spara filerna i me {#me}

Alla filerna sparar du i ditt kursrepo under `me/game/`.

Alla referenser till filer och kataloger du nu skall skapa förutsätter att de ligger under denna katalogen.



### Kopiera en test suite för dina controllers {#testsuite}

I katalogen `example/game/phpunit` ligger ett antal filer som ger dig en komplett uppsättning av testfall för att täcka de controllers som fanns med i förra kursmomentets exempelkod.

Du kan kopiera in den katalogstrukturen till din `me/game`, antingen som den är eller fil för fil. Du bör dubbelkolla vilka filer som ligger i katalogen innan du börjar kopiera, för att undvika att du skriver över någon av dina egna filer.

Om du väljer så kan du kopiera alla filerna på en gång, så här.

```text
# Gå till roten av ditt kursrepo
rsync -av example/game/phpunit/ me/game/
```

Du har nu en komplett test suite för de controller som fanns i exempelkoden.



### Kör enhetstesterna {#runner}

Du kan nu köra enhetstesterna.



Krav {#krav}
-----------------------

Kraven är uppdelade i sektioner.



### Skapa en test suite för dina klasser {#testsuit}

1. Din Makefile skall stödja `make phpunit` och `make test` så som exempelkoden använder det.

1. Din test suite skall placeras i katalogen `test/` och den katalogen skall innehålla en konfigurationsfil `config.php`.

1. Du får gärna skriva om dina klasser för att göra dem mer testbara, om det känns rimligt. Snygg och ren kod är ofta testbar kod.

1. Skriv enhetstester för att testa dina egna klasser och funktioner.

1. Försök även få med kod i `config/` och `view/` så att den omfattas av din kodtäckning och du kan visuellt se hur väl dina testfall täcker även de filerna.

1. Försök nå 100% kodtäckning av din kod. Om du inte lyckas med det så försöker du nå så hög kodtäckning som du anser vara rimligt med skäliga medel.



### Publicera {#publicera}

1. När du är klar, kör `make test` för att köra alla testerna mot ditt repo. När man kör `make test` så bör det passera utan allvarliga felmeddelanden.

1. Dubbelkolla att webbplatsen fungerar på studentservern genom att göra en `dbwebb publishpure me` och testköra den.

1. Committa alla filer till ditt repo och lägg till en ny tagg (3.0.\*). Öka versionnumret om du lägger till ändringar (3.0.1, 3.0.2 och så vidare). Rättaren kommer normalt sett att använda din senaste tagg som är >= 3.0.0 och < 4.0.0.

1. Pusha upp repot till GitHub/GitLab, inklusive taggarna.



<!--
Extrauppgift {#extra}
-----------------------

Lös följande extrauppgifter om du har tid och lust.

-->



Tips från coachen {#tips}
-----------------------

Gör små commits och committa ofta. Använd tydliga committ-meddelanden så att historiken ser bra ut.

Kör ofta `make test` för att dubbelkolla att inga valideringsfel smyger sig in i koden.

Lycka till och hojta till i chatt och forum om du behöver hjälp!

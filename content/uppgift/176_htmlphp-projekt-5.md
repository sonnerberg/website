---
author: mos
category:
    - webbprogrammering
    - databas
    - sqlite
    - php pdo
revision:
    "2018-09-24": "(C, mos) Genomgång i samband med uppdatering av databasen för jetty."
    "2015-08-26": "(B, mos) La till krav om att integrera multisidan från `jetty.php`."
    "2015-06-15": "(A, mos) Första utgåvan i samband med kursen htmlphp v2."
...
Bygg ut din htmlphp me-sida till version 5
==================================

Bygg in en sökmotor i din me-sida, en sökmotor som söker i din egen-konstruerade databas.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har utfört uppgiften "[Bygg ut din htmlphp me-sida till version 4](uppgift/bygg-ut-din-me-sida-till-version-4)".

Du har utfört uppgiften "[Bygg en multisida för att söka i en databas](uppgift/bygg-en-multisida-for-att-soka-i-en-databas)".



Introduktion {#intro}
-----------------------

Du skall uppdatera din me-sida och samtidigt integrera den med kod för att söka i en databas.



### Börja med att kopiera me-sidan {#copyme}

Börja med att ta en kopia från föregående uppgift `me4`, och bygg vidare på den.

```bash
# Ställ dig i rooten av kursrepot
cd me
cp -ri kmom04/me4/* kmom05/me5/
```

Nu har du din bas du kan utgå ifrån. Din resulterande sida skall finnas i katalogen `me/kmom05/me5`.

Skapa katalogen `me/kmom05/me5/db` och lägg databasen i den.

Ett tips är att kopiera kod från uppgiften *kmom05/jetty*. Där finns funktioner som du kan modifiera och använda i denna uppgiften. 

De funktioner du skapar kan du lägga i filen `src/functions.php`, så blir de tillgängliga för alla sidor.

Så här kan det se ut när du är klar.

[YOUTUBE src=0WbqYVGy9nI width=630 caption="En sökmotor för dinosaurier på Mikaels me-sida."]



Krav {#krav}
-----------------------

1. Börja med att integegrera (kopiera) multisidan `jetty.php` från föregående övning, in i din me-sida och skapa ett menyval för sidan.

1. Skapa en ny SQLite databas med minst tre rader där varje rad har minst tre kolumner. Om du inte kommer på nåt eget så gör du en databas för dinosaurier.

1. Skapa en ny sida, `search.php`. Lägg den som en del av navbaren och döp till "Sök".

1. I din sida `search.php`, skapa ett formulär som gör att du kan söka i din databas.

1. Spara din DSN till databasen i din fil `config.php`.

1. Använd egna funktioner för att koppla dig till databasen och för att visa resultatet. Spara funktionerna i filen `src/functions.php`.

1. I sidan, presentera en länk som användaren kan klicka på för att se allt innehåll i databastabellen, presenterat i en HTML-tabell.

1. Validera och publicera din kod enligt följande.

```bash
# Ställ dig i kursrepot
#dbwebb validate me5
dbwebb publish me5
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar. 



Extrauppgift {#extra}
-----------------------

* Kan du göra så din sökmotor liknar Bing eller Googles sökmotor?



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

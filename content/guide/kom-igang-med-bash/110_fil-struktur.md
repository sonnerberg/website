---
author: lew
revision:
    "": "(A, lew) Första versionen."
...
Filstruktur
=======================

Det finns många olika sätt att strukturera filer, inte bara inom bash-programmering, utan i de flesta fall. Vi sätter här en standard som vi använder oss utav genom kursen.



### Filändelse {#filandelse}

Då Bash är skrivet utifrån sh kan vi välja vilken filändelse vi vill använda, script.bash eller script.sh. Egentligen behöver vi inte ha någon filändelse alls men det är nog självförklarande varför vi använder det ändå. I guiden och kursen använder vi filändelsen `.bash`.



### Shebang {#shebang}

En *shebang* (även kallad hashbang) är en rad överst i scriptfilerna som talar om var interpretatorn är lokaliserad som ska användas för att exekvera scriptet.

Då olika unix-system placerar Bash på olika ställen är `#!/usr/bin/env bash` att föredra. Då behöver man inte veta i förväg var interpretatorn är installerad. Shebangen ser till att den första interpretatorn som påträffas i användarens `$PATH` används, oavsett om den ligger i `/bin`, `/usr/bin` eller `/usr/local/bin`.

Vi har alltid shebangen överst i filen:
```bash
#!/usr/bin/env bash


```



### Gör filen exekverbar {#exekverbar}

För att kunna köra filen behöver vi göra den exekverbar. När vi ändå ska hålla oss vid terminalen gör vi det med hjälp av kommandot `chmod`. Vi tar för vana redan nu att ta en titt i manualen:

`man chmod`

> chmod -- change file modes or Access Control Lists

Scrollar vi ner där så kan vi hitta att:

> x       The execute/search bits.

Det handlar om rättighetsbitarna och vi kan använda det med: `chmod +x filnamn` för att göra en fil exekverbar. Hade vi använt `-x` så hade vi tagit bort rättigheterna att exekvera filen.

<!-- Var tar vi upp rättigheter och manualen?? -->

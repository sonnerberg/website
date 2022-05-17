---
author: lew
category: linux
revision:
    "2022-05-10": (A, lew) Ny inför HT22.
...

Skapa en webbplats på en Apache Virtual Host
==================================

Fixa iordning en webbplats med en Apache Virtual Host. Du får dels konfigurera upp en Named Apache Virtual Host och dels får du använda volymer och portar för att hantera filer på din lokala arbetsstation i servern som kör webbplatsen. Du ska leverera en image som kan serva en lokal mapp med en webbsida på en viss adress.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Kom igång med Apache](kunskap/kom-igang-med-apache)" och du har koll på guiden "[Docker](guide/docker)".



Introduktion {#intro}
-----------------------

De filer du skapar och använder i denna uppgiften skall du spara i ditt kursrepo i katalogen `me/kmom03/vhosts`. De används för att redovisa uppgiften.



Krav {#krav}
-----------------------

1. Skapa `me.vlinux.se.conf`. Filen ska använda sig av variabler och peka mot en namngiven virtuell host `me.vlinux.se`.

1. Skapa en `Dockerfile` enligt guiden som kör Apache2 och använder sig utav din egna configfil.

1. Ta en skärmdump på terminalen som visar när du använder `w3m` för att komma åt webbplatsen inifrån containern med hjälp av ett host-namn. Spara den som `dump.png`. Spara bilden i formatet .png och använd små bokstäver i filnamnet.

1. Skapa ett Bash-script, `dockerhub.bash` som kör din publicerade image och servar filer via en volym på sökvägen `$(pwd)/mysite` som mappas mot din valda sökväg i config-filen. Kika i guiden om [Apache Virtual Hosts](docker/apache-vh) för inspiration.

1. Publicera dina svar enligt följande.

```bash
# Ställ dig i kurskatalogen
dbwebb publish vhosts
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. Lägg till fler virtuella hostar via följande lokala mappar: `mysite1, mysite2 etc`.



Tips från coachen {#tips}
-----------------------

Stressa inte. Kör det ihop sig så är det en bra taktik att börja om från början och göra om. Det går snabbare andra gången, och ännu snabbare tredje gången.

Lycka till och hojta till i chatten om du behöver hjälp!

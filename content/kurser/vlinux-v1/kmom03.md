---
author:
    - lew
revision:
    "2022-05-09": (B, lew) Uppdaterad inför HT22.
    "2019-03-25": (A, lew) Ny inför HT19.
...
Kmom03: Virtual Hosts
==================================

[WARNING]
Kursen uppdateras inför HT22. Är "gula rutan" borta är det fritt fram att börja.
[/WARNING]

Nu kan vi enkelt snurra igång en Linuxmiljö så låt oss se hur vi kan använda containern som en server och installera ett par webbplatser på den. Det låter som en vettig syssla för en webbprogrammerare.

Ett bra sätt att installera många webbplatser på en och samma maskin är Apache Virtual Hosts och det är något vi skall bekanta oss med. Vi ska skapa namnbaserade webbplatser som ligger på samma domän med hjälp av webbservern Apache.

<!-- Nu har vi en Linux-server och en webbserver. Låt oss nu bekanta oss med en annan teknik för virtualisering: Docker. Vi kommer även bekanta oss med skriptprogrammering i Bash.

Mycket handlar om att förenkla vardagen, som programmerare, genom att automatisera de processer och rutiner man utför. En hel del av det vi gör kan automatiseras via skript, till exempel Bash-skript med kommandon. Men för att göra det behöver vi ha koll på hur man skapar skript och hur man programmerar i bash.

Man behöver också ha en rätt bra koll på vanliga kommandon i Linux-terminalen. Det finns kommandon som är kraftfulla och om vi bara lära oss ett par av dessa kommandon så kan de spara en hel del tid åt oss. -->

<!--more-->

[FIGURE src=/image/vlinux/apache.svg.png caption="Apache2."]


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 8-12 studietimmar)*


### Kurslitteratur  {#kurslitteratur}

Läs följande:

<!-- 1. [The Linux Command Line](kunskap/boken-the-linux-command-line)
    * Kapitel 6 Redirection
    * Kapitel 24 Writing Your First Script -->



### Artiklar {#artiklar}

<!-- 1. Boken "The Linux Command Line" har en webbplats där det finns [ett stycke med fokus på att skriva shell scripts](http://linuxcommand.org/lc3_writing_shell_scripts.php). Ta det som ett komplement till boken. -->



### Video  {#video}

Titta på följande:

1. Till kursen finns en videoserie, "[vlinux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_oeXQlDtKv51tVM4Y8UtkF)", kika på de videor som börjar på 3.

<!-- 1. Kris Occhipinti har en serie om [skriptprogrammering med Bash på YouTube](https://www.youtube.com/playlist?list=PLcUid3OP_4OXOUqYTDGjq-iEwtBf-3l2E). Det är många avsnitt och du kan välja vilka du vill titta på. Videorna ger dig bra bas-kunskaper i Bash. -->



<!-- ### Lästips {#lastips} -->

<!-- 1. Det finns en [referensmanual till Bash](http://www.gnu.org/software/bash/manual/bashref.html). Kika gärna i den.

1. Det finns en populär guide för att [komma igång med Bash och programmering i Bash](http://mywiki.wooledge.org/BashGuide). Samma webbplats har en [FAQ om Bash](http://mywiki.wooledge.org/BashFAQ).

1. Bekanta dig med dokumentationen [för Docker](https://docs.docker.com/).

1. [Reddit har en kanal om Bash](https://www.reddit.com/r/bash/) där man kan se både nybörjare och erfarna prata om Bash. Det kan vara intressant att läsa igenom ett par inlägg i kanalen för att få en känsla om vad Bash handlar om. -->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 4-10 studietimmar)*



### Övningar {#ovningar}

Genomför följande övningar.

1. Jobba igenom guiden om "[Apache Name-based Virtual Hosts](guide/unix-tools/apache)".

<!-- 1. Jobba igenom guiden "[Kom igång med SSH-nycklar](guide/unix-tools/kom-igang-med-ssh-nycklar)".

1. Jobba igenom guiden om "[rsync](guide/unix-tools/rsync)".

1. Jobba igenom guiden om "[tmux](guide/unix-tools/tmux)". -->



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

Gör uppgiften "[Skapa en webbplats på en Apache Virtual Host](uppgift/skapa-en-webbplats-pa-en-apache-virtual-host)".

1. Lägg till redovisningstexten i din me-sida.



### Testa din inlämning {#test}

Du kan köra vissa tester på din inlämning och se om de delarna uppfyller kraven. Rättningen kommer endast genomföras om testerna går igenom.

```console
$ dbwebb test kmom03
```



### Extra {#extra}

Det finns inga extra uppgifter.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Är detta din första bekantskap med skriptprogrammering i Bash?
* Berätta om din uppfattning om Bash som programmeringsmiljö, relatera till andra programspråk du kan.
* Vilka möjligheter/utmaningar ser du med denna typen av skriptprogrammering?
* Var det något som var extra svårt eller utmanande i uppgifterna?
* Har du arbetat med Docker innan?
* Anser du att det är någon fördel/nackdel med Docker om du jämför med VirtualBox?
<!-- från kmom02 -->
* Hur känns konceptet med Apache name-based Virtual Hosts? Känner du igen det sedan tidigare?
* Det blir allt fler kommandon i terminalen, hur känns det med terminalen och dess kommandon?
* Gick det bra med ssh-nycklar och rsync över ssh?
* Hur kändes det att jobba med tmux?
* Reflektera över hur du känner inför Unix som operativsystem så här långt?

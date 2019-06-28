---
author:
    - lew
revision:
    "2019-03-26": (A, lew) Ny inför HT19.
...
Kmom05: Docker network
==================================

[WARNING]

**Kursutveckling pågår**

Kursen ges hösten 2019 läsperiod 1.

[/WARNING]

Nu har vi kontroll på hur vi kan hantera en webbserver i Docker. Vi tar ett steg till in i Bashprogrammeringen och bygger ett script som kan prata med en server.

Du kommer få en färdig server, skriven i Node.js, och ett RESTful API till servern. Servern implementerar en [*maze*](https://en.wikipedia.org/wiki/Maze). Servern är färdig och du kan testköra den via kommandot curl.

Din uppgift är att bygga en bash-klient till servern, enligt en kravspecifikation. Din klient skall använda servern för att lösa mazen. Vi lägger in klienten och servern i Docker-kontainrar och låter de prata med varandra med hjälp av "Docker network", där vi låter Docker skapa ett eget nätverk.

Så är upplägget. Låt se hur bra vingarna bär. Upplägget på detta kursmomentet är "lite friare", så vi går nästan rakt på själva uppgiften.

<!--more-->

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 0 studietimmar)*


### Kurslitteratur  {#kurslitteratur}

Det finns ingen läsanvisning i kurslitteraturen.




<!--
### Artiklar {#artiklar}

TBD -->

<!-- 1. Läs igenom hur du med Bash kan skapa ett mer avancerat kommandoradsprogram som tar argument. Artikeln ["Skapa Bash-skript med options, command och arguments"](kunskap/skapa-bash-skript-med-options-command-och-arguments) ger dig en struktur till hur du kan skapa mer avancerade och större Bash-skript. -->



### Video  {#video}

Titta på följande:

Det finns inga videos kopplade till kursmomentet.

<!-- 1. Till kursen finns en videoserie, "[vlinux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce__96JmUrXLdfgGiXy_OQ_m)", kika på de videor som börjar på 05. -->



### Lästips {#lastips}

Läs lite om [Docker network](https://docs.docker.com/network/).



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-14 studietimmar)*



### Övningar {#ovningar}

1. Läs om [Docker network](guide/docker/docker-network) i guiden.

1. Luta dig mot guiden [kom igång med Bash](guide/kom-igang-med-bash).



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Mazerunner i bash](uppgift/mazerunner-i-bash)". Du sparar ditt arbete under mappen `kmom05/maze/`.

1. Lägg till redovisningstexten i din me-sida.



### Extra {#extra}

Det finns inga extra uppgifter.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.


* Hur kändes det att skriva ett litet större bash-skript? Var det något som var mer eller mindre utmanande och tidskrävande?
* Kikade du på källkoden till maze-servern? Har du några reflektioner kring den?
* Gjorde du nåt speciellt i din mazerunner som du vill lyfta fram?

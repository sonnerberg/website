---
author: mos
category:
    - php
revision:
    "2018-03-26": "(E, mos) Uppdaterad inför oophp-v4."
    "2017-03-17": "(D, lew) Ny version för oophp-v3."
    "2014-03-19": "(C, mos) Förtydligande om lite kod i sidkontrollern."
    "2013-08-16": "(B, mos) Gjorde valbara krav till obligatoriska."
    "2013-08-14": "(A, mos) Första utgåvan i samband med oophp version 2."
...
Tärningsspel 100
==================================

Tärningsspelet 100 är ett enkelt och roligt tärningsspel. Spelet spelas med en eller flera tärningar och det gäller att samla ihop poäng för att komma först till 100.

I varje omgång kastar en spelare tärningarna tills hon väljer att stanna och spara poängen, eller tills det dyker upp en 1:a och hon förlorar alla poäng som samlats in i rundan. Rundan går då över till nästa spelare. Det gäller att komma först till 100.

I uppgiften får du möjlighet att bygga klasser för tärning, tärningshand, spelrunda och själva spelet. Du väljer själv vilken struktur du vill ha på klasserna och hur de skall samverka.

<!--more-->


<!--
Ett tärningsspel i Anax kan se ut så här.

[FIGURE src=/image/oophp/v3/dice100.png?w=w1&q=70 caption="Ett tärningsspel i Anax."]
-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom delen med "Arv och Komposition" i guiden I guiden "[Kom igång med Objektorienterad programmering i PHP](guide/kom-igang-med-objektorienterad-programmering-i-php)".



Spelregler tärningsspelet 100 {#regler}
-----------------------

Följande är generella regler för tärningsspelet 100.

Man kan vara två eller fler spelare. Man kan spela med en eller flera tärningar.

Alla spelare kastar en tärning och den som får högst börjar spelet med en spelrunda.

Notera alla spelare på ett papper, protokollet, det gäller att först samla på sig 100 poäng.



### Spelrunda {#spelrunda}

En spelrunda inleds av en spelare genom att den kastar alla tärningar.

Alla tärningar med ögon 2-6 summeras och adderas till totalen för nuvarande spelrunda. En tvåa är värd 2 poäng och en sexa är värd 6 poäng, och så vidare.

Spelaren bestämmer om ett nytt kast skall göras inom samma spelrunda för att försöka samla mer poäng. Eller så väljer spelaren att avbryta spelrundan och föra över de insamlade poängen till säkerhet i protokollet.

Om spelaren kastar en etta så avbryts spelrundan och turen går över till nästa spelare. Nuvarande spelare förlorar alla poäng som samlats in i nuvaranade spelrunda.



Krav {#krav}
-----------------------

1. Gör så att en spelare kan spela tärningsspelet 100 via en webbsida där motspelaren är datorn.

1. Bygg ditt spel med klasser som samverkar. Du kan själv välja vilka klasser du skapar och hur de samverkar.

1. Skissa på ett UML-diagram för klasserna, ett klassidagram. Rita i ett verktyg (dia, draw.io, etc) eller rita på ett papper (och scanna in/fotografera). Spara ditt diagram i filen `doc/guess/class.pdf`.

1. Se till att du har minimalt med kod i routens hanterare, flytta spelets logik till klasserna.

1. När du är klar så gör du `make doc test` samt `dbwebb publish`.



Extrauppgift {#extra}
-----------------------

Gör följande extrauppgifter om du har tid och lust.

1. Försök göra datorn mer intelligent när den spelare spelet. Försök göra så att datorn tar olika beslut i spelet, beroende av motspelarens poäng.

1. Gör det flexibelt så man kan använda valbart antal tärningar när man spelar spelet.



Tips från coachen {#tips}
-----------------------

**Lycka till och hojta till i forumet om du behöver hjälp!**

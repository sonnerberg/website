---
author: efo
category: javascript
revision:
  "2018-03-01": (A, efo) Första utgåvan i samband med kursen webapp v3.
...
Lager appen del 6
==================================
[FIGURE src=image/webapp/money.jpeg?w=c5 class="right"]

I kursmoment 5 skapade vi en native app baserad på vår webapp med hjälp av Cordova. I denna uppgift ska vi använda mobila enheters styrkor och lägga till funktionalitet för GPS och kartor.



<!--more-->



Förkunskaper {#forkunskaper}
-----------------------
Du har gjort uppgiften [Lager appen del 5](uppgift/lager-appen-del-3). Du har jobbat dig igenom övningarna "[Animationer och övergångar](kunskap/animationer-och-overgangar)" och "[GPS och karta](kunskap/gps-och-karta)".


Introduktion {#intro}
-----------------------
Börja med att kopiera din lager app från kmom05 så har du nått att utgå ifrån.

```bash
# stå i me-katalogen
cp kmom05/lager5/* kmom06/lager6/
```

Använd lager [API:t](https://lager.dbwebb.se) dokumentationen och speciellt sektionen om invoices. Här kan du hämta ut alla invoices och skapa nya.



Krav {#krav}
-----------------------
1. Använd animationer och övergånger för att efterlikna native applikationer.

1. Skapa en vy i din app med de ordrar som är redo att skickas. Dvs. ordrar med status större än .

1. När man klickar in på ordern får man al information om ordern och en karta där paketet ska levereras.

1. Använd GPS för att visa nuvarande position på kartan.

1. Validera och publicera din kod enligt följande.

```bash
# Ställ dig i kurskatalogen
dbwebb validate lager6
dbwebb publish lager6
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------
Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Validera och publicera ofta. Så slipper du en massa validerings- och publiceringsfel i slutet av övningen.

När du gör *publish* så körs även *validate*. Blir det för mycket fel när du kör *publish* så kan det bli enklare att bara göra *validate* till att börja med.

Lycka till och hojta till i forumet om du behöver hjälp!

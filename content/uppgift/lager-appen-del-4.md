---
author: efo
category: javascript
revision:
  "2018-02-12": (A, efo) Första utgåvan i samband med kursen webapp v3.
...
Lager appen del 4
==================================
[FIGURE src=image/webapp/money.jpeg?w=c5 class="right"]

I kursmoment 3 arbetade vi med formulär och JavaScript ramverket mithril. Vi ska i denna uppgift skapa delar av appen som är skyddad med hjälp av JWT. I den skyddade delen ska det vara möjligt att se tidigare fakturor och skicka nya.



<!--more-->



Förkunskaper {#forkunskaper}
-----------------------
Du har gjort uppgiften [Lager appen del 3](uppgift/lager-appen-del-3). Du har jobbat dig igenom övningarna [Tabeller i mobila enheter](kunskap/tabeller-mobila-enheter) och [Login med JWT](kunskap/login-med-jwt).


Introduktion {#intro}
-----------------------
Börja med att kopiera din lager app från kmom03, om du inte gjorde det i övningen, så har du nått att utgå ifrån.

<strong>OBS! Gör bara detta om du inte gjorde det i övningen.</strong>

```bash
# stå i me-katalogen
cp kmom03/lager3/* kmom04/lager4/
```

Använd lager [API:t](https://lager.dbwebb.se) dokumentationen och speciellt sektionen om invoices. Här kan du hämta ut alla invoices och skapa nya.



Krav {#krav}
-----------------------
1. Skapa möjlighet för att logga in i Lager appen.

1. Bakom de skyddade delarna ska faktura sidan ligga.

1. Skapa en tabell med information om tidigare fakturor.

1. Skapa ett formulär för att göra om en order till en faktura.

1. Navigationen ska tydligt visa vilken vy användaren är i.

1. Validera och publicera din kod enligt följande.

```bash
# Ställ dig i kurskatalogen
dbwebb validate lager4
dbwebb publish lager4
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------
* Om tid och lust finns portera Lager appen del 1 och Lager appen del 2 till mithril. Så vi har en stor Lager app istället för två mindre.



Tips från coachen {#tips}
-----------------------

Validera och publicera ofta. Så slipper du en massa validerings- och publiceringsfel i slutet av övningen.

När du gör *publish* så körs även *validate*. Blir det för mycket fel när du kör *publish* så kan det bli enklare att bara göra *validate* till att börja med.

Lycka till och hojta till i forumet om du behöver hjälp!

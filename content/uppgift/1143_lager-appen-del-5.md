---
author: efo
category: javascript
revision:
  "2018-02-28": (A, efo) Första utgåvan i samband med kursen webapp v3.
...
Lager appen del 5
==================================
[FIGURE src=image/webapp/money.jpeg?w=c5 class="right"]

I tidigare kursmoment har vi jobbat med vår lager app i webbläsaren. Nu är det dags att skapa en app på 'riktigt', som går att installera på en mobil-enhet och använda sig av både splashscreen och en riktig ikon.



<!--more-->



Förkunskaper {#forkunskaper}
-----------------------
Du har gjort uppgiften [Lager appen del 4](uppgift/lager-appen-del-4). Du har installerat sista delen av labbmiljön för webapp-v3. Du har jobbat dig igenom övningarna [Kom igång med Cordova](kunskap/kom-igang-med-cordova) och [Lägg till en Splash screen och ändra ikon](kunskap/splash-screen-och-ikon).


Introduktion {#intro}
-----------------------
Börja med att skapa ett Cordova projekt



kopiera din lager app från kmom04 så har du nått att utgå ifrån.

```bash
# stå i me-katalogen
cp kmom03/lager3/* kmom04/lager4/
```

Använd lager [API:t](https://lager.dbwebb.se) dokumentationen och speciellt sektionen om invoices. Här kan du hämta ut alla invoices och skapa nya.



Krav {#krav}
-----------------------
1. Skapa ett formulär för att registrera sig som användare i Lager appen.

1. Skapa ett formulär för att logga in i Lager appen med en registrerad användare.

1. Bakom de skyddade delarna ska faktura vyerna ligga.

1. Skapa ett formulär för att göra om en order till en faktura. Ändra orderns status till 'fakturerad' enligt API:t.

1. Det ska inte gå att fakturera en order två gånger.

1. Skapa en tabell med information om befintliga fakturor.

1. Tabellen ska fungera på alla enheter, gör ett medvetet val av design.

1. Från tabellen ska man kunna ta sig till en faktura där all information från fakturan visas.

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
* Användaren ska automatisk loggas in efter registrering.

* Om tid och lust finns portera Lager appen del 1 och del 2 till mithril. Så du har en stor Lager app istället för två mindre.



Tips från coachen {#tips}
-----------------------

Validera och publicera ofta. Så slipper du en massa validerings- och publiceringsfel i slutet av övningen.

När du gör *publish* så körs även *validate*. Blir det för mycket fel när du kör *publish* så kan det bli enklare att bara göra *validate* till att börja med.

Lycka till och hojta till i forumet om du behöver hjälp!

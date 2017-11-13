---
author: mos
category:
    - javascript
    - websocket
    - kurs ramverk2
revision:
    "2017-11-13": (A, mos) Första utgåvan.
...
Bygg en chatt med WebSocket
==================================

Du skall bygga en chatt med WebSocket och lägga till i din redovisa sida. När du bygger chatten så bygger du ditt eget applikationsspecifika protokoll.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Kom igång med realtidsprogrammering i JavaScript](kunskap/kom-igang-med-realtidsprogrammering-i-javascript)".



Introduktion {#intro}
-----------------------

Du bygger vidare på de kunskaper du fick i artikeln, främst i sammanhanget av broadcast servern.

Tänk på att bygga en kodstruktur som kan vara återanvändbar när du eventuellt bygger andra implementationer ovanpå websockets. Skall du lägga din egen server i en modul, en klass, eller hur bygger du grunden i kodstrukturen?

Organisera koden i egna moduler så den blir enkel att återanvända i andra sammanhang.

Du kan välja godtyckligt teknikval för uppgiften, välj teknik som användes i artikeln eller välj annan modul som bygger på websockets, till exempel socket.io.

Om du tänker återanvända chatten i din applikation så vill du kanske redan nu organisera koden i ett eget repo?

Det finns ett kommande kursmoment som handlar om att göra en npm-modul av godtycklig kod. Kanske är denna chatt ett alternativ till lösning.



Krav {#krav}
-----------------------

1. Skapa en klient och en server för chatt. Välj en teknik som grundar sig på websockets. Visa att chatten fungerar genom att integrera den i din redovisa-sida.

1. Bygg ett eget applikationsprotokoll ovanpå websockets. Förslagsvis använder du JSON (eller annat du väljer).

1. Använd subprotkoll i din lösning, på så vis är du förberedd om du behöver göra en ny version av ditt applikationsprotokoll.

1. När man kopplar upp sig så identifierar man sig med ett nick, ett smeknamn.

1. Flera klienter kan koppla sig till chatten. När någon skriver något ser alla andra det. Man ser nicket tillsammans med meddelandet.

1. Committa, tagga (v4.x.x) och pusha relevanta repon samt ladda upp på studentservern.



Extrauppgift {#extra}
-----------------------

Gör följande extrauppgift om du har tid och lust.

1. Lös så att din server upptäcker när klienter försvinner utan att höra av sig. Du behöver någon form av teknik för att upptäcka och städa upp när klienten försvinner utan att koppla ned sig på ett korrekt sätt.

1. Dubbelkolla om din chatt är öppen för XSS eller ej.

1. Gör så man kan skicka ett meddelande till en specifik användare.

1. Gör så man kan lista alla användare som är inloggade på servern.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

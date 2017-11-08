---
author:
    - mos
category:
    - labbmiljo
    - kursen ramverk2
    - test
revision:
    "2017-10-03": (PA1, mos) Första utgåvan.
...
Kom igång med realtidsprogrammering i JavaScript
==================================

[FIGURE src=image/snapht17/mocha-nyc-codecoverage.png?w=c5 class="right"]

Vi skall se hur JavaScript och Websockets kan kombineras till något som motsvarar realtidsprogrammering i webbsammanhanget.

Vi ser koden som krävs för att sätta upp en klient och en server som utför echo och broadcast. Det ger oss en grund att stå på. Som server använder vi Express, även om vi kan göra detta utan Express.

<!--more-->

[WARNING]
**Kursutveckling pågår**
[/WARNING]
<!--stop-->



Förkunskaper {#forkunskaper}
--------------------------------------------------------------------

Du kan grunderna i JavaScript på klient och server samt har tillgång till en labbmiljö med Node, npm och Express.



Websockets {#websocket}
--------------------------------------------------------------------

HTML5 Websockets skapar nya möjligheter där webbläsaren kan ha en konstant uppkoppling mot en server där meddelanden både kan skickas och tas emot med minimal overhead. Möjligheten öppnar sig för att bättre bygga webbapplikationer som agerar i realtid.

Det finns en W3C standard för [The Websocket API](https://www.w3.org/TR/websockets/), det ger grunden till vad utvecklare av webbläsare och liknande behöver förhålla sig till. Detta berör både klienten och servern så de behöver ett sätt att prata.



En echo-server {#echo}
--------------------------------------------------------------------

Det finns ett exempel av en [echo-server](http://demos.kaazing.com/echo/) som använder sig av websockets. Pröva den så ser du grunderna i att klienten behöver koppla upp sig till servern och sedan kan man skicka ett meddelande. Servern skickar bara tillbaka samma meddelande, som en ekande-server, en echo-server.

[FIGURE src=image/snapht17/kaazing-echo-server.png?w=w2 caption="Testa konceptet av en echo-server med websockets."]

Du kan även pröva att koppla upp dig mot en annan echo-server som finns på `ws://dbwebb.se:1337/`. Pröva att det fungerar på samma sätt och att klienten du använder fungerar även mot en annan server.



En klient i webbläsaren {#clientweb}
--------------------------------------------------------------------

Låt se vilken kod som behövs för att sätta upp en server och en klient. Vi börjar med klienten i webbläsaren. I kursrepot under `example/websocket/client` finns sidan `client.html` som är grunden till en klient.

[FIGURE src=image/snapht17/websocket-client.png?w=w2 caption="En klient som kan koppla upp sig mot en server via websocket."]

Då skall vi använda klienten.



Klient websocket connect {#clientconnect}
--------------------------------------------------------------------

För att se vad som händer när du trycker på "Connect" så öppnar du devtools och kikar i flikarna "Console" och "Networks".

Bekanta dig med hur det ser ut i olika webbläsare. Här ser du Firefox och Chrome.

[FIGURE src=image/snapht17/websocket-connect-firefox.png?w=w2 caption="Firefox visar detaljer i Console när uppkopplingen sker för websockets."]

[FIGURE src=image/snapht17/websocket-connect-chrome.png?w=w2 caption="Chrome visar detaljer i Console när uppkopplingen sker för websockets."]

DU kan också se hur uppkopplingen för en websocket ser ut under fliken "Networks".

[FIGURE src=image/snapht17/websocket-connect-firefox-network.png?w=w2 caption="Firefox i fliken Networks vid uppkoppling för websockets."]

[FIGURE src=image/snapht17/websocket-connect-chrome-network.png?w=w2 caption="Chrome i fliken Networks vid uppkoppling för websockets."]

Det du ser är status 101 för själva requesten som görs vid uppkopplingen av websocken.

Om du klickar på den requesten så ser du dess header information. Det du ser är att webbläsaren gör en request header för att uppgradera protokollet mot servern till "websocket". Webbläsaren, eller servern, svarar om hen accepterar uppgraderingen. I dessa fallen gick det bra.

[FIGURE src=image/snapht17/websocket-upgrade-firefox.png?w=w2 caption="Firefox visar hur request och response header innehåller detaljer om uppgradering till protokoll websocket."]

[FIGURE src=image/snapht17/websocket-upgrade-chrome.png?w=w2 caption="Chrome visar hur request och response header innehåller detaljer om uppgradering till protokoll websocket."]



Koden för klienten {#clientconnectcode}
--------------------------------------------------------------------

Det handlar inte om så mycket kod som behövs i klienten för att utföra själva uppkopplingen.

HTML-sidan `client.html` innehåller endast en knapp och ett inputfält.

```html
<!doctype html>
<meta charset="utf-8">
<title>HTML5 websockets</title>

<h1>Websockets</h1>
<h2>Connect</h2>
<p>You may connect to any server out there, try any of these:</p>
<ul>
    <li><code>ws://dbwebb.se:1337/echo</code></li>
    <li><code>ws://demos.kaazing.com/echo</code></li>
    <li><code>ws://localhost:1337/</code> (if you have your own server)</li>
</ul>
<p>Open up devtools and see the output in the console and network tab.</p>

<input id="url" value="ws://dbwebb.se:1337/echo" style="width: 30em;"/>
<button id="connect">Connect</button>

<script src="client.js"></script>
```

Själva koden för att sätta igång kopplingen och hålla den levande finns i filen `client.js`.

```javascript
/**
 * To setup a websocket connection, and nothing more.
 */
(function () {
    "use strict";

    let websocket;
    let url     = document.getElementById("url");
    let connect = document.getElementById("connect");

    connect.addEventListener("click", function(/*event*/) {
        console.log("Connecting to: " + url.value);
        websocket = new WebSocket(url.value);

        websocket.onopen = function() {
            console.log("The websocket is now open.");
        };
    }, false);
})();
```

Det viktiga i koden rör `new WebSocket()` där vi skapar ett nytt objekt för vår websocket-koppling. Till detta objekt kopplar vi en eventhanterare som anropas när uppkopplingen är utförd.



Klient skicka och ta emot {#clientsendrecieve}
--------------------------------------------------------------------

Vi bygger vidare på vår klient så att den kan koppla upp sig, koppla ned sig och skicka samt ta emot meddelanden från en echo-server. Det finns ett färdigt exempelprogram i `example/websocket/echo` där `client.html` är klienten för webbläsaren. Formuläret är utökat och själva koden bakom finns i `client.js`.

_Visa hur den fungerar_



En server för connect {#serverconnect}
--------------------------------------------------------------------

Då kikar vi på hur server-delen kan se ut. För att bygga servern tar vi hjälp av en npm modul som heter socket.io. Du kan läsa om modulen på dess webbplats [socket.io](https://socket.io/) och [modulen socket.io](https://www.npmjs.com/package/socket.io) finns på npm.

Så här kan du installera modulen.

```text
npm install --save socket.io
```

I katalogen `example/websocket/connect` ligger en minimal servern som 


https://socket.io/


https://developer.mozilla.org/sv-SE/docs/Web/API/WebSockets_API

https://www.websocket.org
http://demos.kaazing.com/echo/













Avslutningvis {#avslutning}
--------------------------------------------------------------------

Vi har gått igenom testning och hur man kan bygga upp grunden till en testmiljö med verktyg för enhtstestning, kodtäckning, Docker och valideringsverktyg samt byggt samman alla delar i en CI-kedja med externa verktyg för kodkvalitet.

Det finns en [forumtråd kopplad till denna artikeln](t/7007). Där kan du ställa frågor eller bidra med tips och trix.

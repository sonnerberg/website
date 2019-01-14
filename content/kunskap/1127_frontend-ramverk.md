---
author: efo
category:
    - ramverk2
    - verktyg
revision:
    "2018-12-03": "(A, efo) Första utgåvan för ramverk2 version 2 av kursen."
...
Frontend ramverk
==================================

[FIGURE src=image/webapp/javascript-logo.png?w=c5 class="right"]

Vi ska i denna artikel titta på ett antal koncept, som används för att bygga webbapplikationer med hjälp av JavaScript. I artikeln går vi igenom koncepten med hjälp av tre exempel program, som är implementerad i JavaScript ramverken Angular, Mithril, React och Vue, samt i vanilla JavaScript ES5.



<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har bra kunskap om JavaScript och vilka möjligheter som finns i programmeringsspråket.



Introduktion {#intro}
--------------------------------------

Anledningen till att ovanstående tekniker har valts ut är att Angular, React och Vue i 2018 har setts som "The Big Three". Dessa tre ramverk är de tre mest nerladdade JavaScript ramverken under året enligt [npm trends](https://jsreport.io/javascript-frameworks-by-the-numbers-winter-2018/). För att jämföra med tidigare kända tekniker har vi även valt att inkludera JavaScript ramverket mithril som användes i [kursen webapp](https://dbwebb.se/kurser/webapp-v3) och JavaScript ES5, som vi har använt tidigare i bland annat [kursen javascript 1](https://dbwebb.se/kurser/javascript1-v2/).



Exempelprogram {#example}
--------------------------------------

I kursrepots exempel katalog finns två olika exempel program skrivna med hjälp av de fem ovannämnda teknikerna. I `example/tic-tac-toe` finns ett luffarschack implementerad med möjlighet att hoppa tillbaka i spelets historik. I `example/calculator` är en simpel miniräknare implementerad.

Dessutom finns det samma Me-sida som konsumerar me-api:t från tidigare kursmoment implementerad i de 5 olika teknikerna. [GitHub repon](https://github.com/emilfolino?utf8=%E2%9C%93&tab=repositories&q=me-&type=&language=) för dessa 5 Me-sidor samt me-api:t finns tillgängligt. Dessa är även driftsatta på `me-{angular,mithril,react,vanilla,vue}.jsramverk.me`.

Först tar vi en titt på antal rader som utvecklaren behöver skriva i dessa små exempelprogram och hur stora produktionsfilerna för dessa exempelprogram är.



#### Rader skriven kod i exempelprogrammen {#loc}

I nedanstående tabell listas de rader kod som utvecklaren har skrivit för att implementera exempelprogrammen. De rader som är räknade är enbart de rader som innehåller källkod, så rader med kommentarer och tomma rader är borttagna.

|  | Angular | Mithril | React | Vue | Vanilla JS |
|-----|--------|--------|--------|---------|--------|
| calculator  | 112 | 103 | 133 | 98 | 118 |
| me   | 166 | 107 | 117 | 134 | 92 |
| tic-tac-toe | 196 | 136 | 146 | 172 | 126 |



#### Storlek produktionsfil(er) {#filesize}

I nedanstående tabell listas storleken på produktionsfilerna som skapas av antingen bygg verktyget i ramverket, webpack eller uglify. Filstorlekar är utskrivna med hjälp av kommandot `ls -lh` i ett bash-skal.

|  | Angular | Mithril | React | Vue | Vanilla JS |
|-----|--------|--------|--------|---------|--------|
| calculator  | 217K | 30K | 115K | 83K | 2.6K |
| me   | 329K | 29K | 134K | 106K | 2.2K |
| tic-tac-toe | 222K | 29K | 37K | 87K | 2.8K |



Tekniska koncept {#concepts}
--------------------------------------

Vi tittar i denna del av artikeln på några tekniska koncept som används i de olika ramverken. Vi tittar på hur man har vald att implementera dessa koncept i de olika ramverken och utvärderar vilka fördelar och nackdelar som finns med att göra på det viset.


### Komponenter {#komponenter}

De fyra ramverk som har valts ut i denna artikel är alla byggda runt komponenter. Komponenter är återanvändbara delar av koden, som i bästa fall inte har några externa beroenden.

I mithril och React är allt JavaScript och komponenterna definieras i JavaScript filer. I mithril är enda kravet att det ska finnas en `view` funktion som returnerar noder. I React heter funktionen `render` och funktionen returnerar JSX. I Vue finns varje komponent i en fil men är uppdelade i tre delar `template`, `script` och `style`, som motsvarar de tre lagren vi känner till från tidigare med struktur (HTML), stil (CSS) och dynamik (JavaScript). I angular har man tagit det ett steg längre med tre olika filer för dessa tre lager.



### Länkning av data {#linking}

Vi vill i många applikationer och speciellt i applikationer där data uppdateras ofta länka data i våra modeller till representationen i en vy. I vanilla JavaScript hade vi gjort det genom att varje gång data uppdateras sätta ett nytt värde för ett specifikt element i DOM'en.

```javascript
var data = 42;

document.getElementById("element").textContent = data;
```

I många ramverk är detta nått man försöker förenkla genom att uppdatera vyn direkt varje gång data ändras. Detta är en av de magiska sakerna med JavaScript ramverk och vi ska nedan se exempel på hur detta kan göras. I de flesta ramverken definierar vi medlemsvariabler i komponenter och vi kan sedan använda dessa medlemsvariabler i templates. I nedanstående exempel ser vi hur vi använder medlemsvariabler i Vue.

```
<template>
    <div class="calculator">
        <div class="display">{{ current || 0 }}</div>
        ...
    </div>
</template>

<script>
export default {
    data() {
        return {
            current: 0,
        }
    },
    ...
```

Om medlemsvariabeln `current` får ett nytt värde ändras den direkt i den kopplade template. I vanilla JavaScript gör vi en explicit koppling och uppdatering av data och i de ramverk som har valts ut är det en implicit koppling och uppdatering.



### Routing {#routing}

### Eventhantering och delegering {#event}

### HTTP-anrop {#http}

### Arkitektur {#architecture}




RealWorld {#realworld}
--------------------------------------

För att ytterligare utvärdera våra valda ramverk tar vi en titt i GitHub repot [RealWorld Example](https://github.com/gothinkster/realworld).



John Papa's Heroes {#heroes}
--------------------------------------

Under dotJS konferensen pratade John Papa om att välja ett frontend ramverk. Som förberedelse för presentationen hade han skapat samma app i "The Big Three" och de tre apparna ligger som open source kod på GitHub. [heroes-angular](https://github.com/johnpapa/heroes-angular), [heroes-react](https://github.com/johnpapa/heroes-react) och [heroes-vue](https://github.com/johnpapa/heroes-vue) är de tre repon som innehåller koden och det finns länkar till en publik driftsatt version från GitHub.



Driftsättning {#deploy}
--------------------------------------

I denna del av artikeln ska vi titta på hur vi driftsätter appar vi har skapat med hjälp av dessa ramverk på vår server.



### Domän {#deploy-domain}

Vi vill i de flesta fall lägga våra alster på en domän eller subdomän. Vi har redan pekat al trafik från registratorn namecheap till vårt Cloud i Digital Ocean. Vi behöver därför bara skapa en subdomän i Digital Ocean. Vi gör det på samma sätt som i "[Node.js API med Express](kunskap/nodejs-api-med-express)". Gå till Networking och välj din domän skriv sedan in din subdomän välj din droplet och skapa subdomänen.

[FIGURE src=image/ramverk2/do-subdomain.png?w=w3 caption="Digital Ocean subdomän"]

Ibland kan det ta en liten stund innan subdomäner kommer på plats, så avvakta lite grann om det inte syns direkt.



### Angular {#angular}

För att driftsätta en Angular app krävs att vi har en statisk fil webbserver (static file web server) till exempel nginx. Om appen är skapat med hjälp av `ng` kan vi skapa produktionsfilerna med hjälp av kommandot `ng build --prod`. Vi har då en `dist/` katalog som innehåller en katalog med applikationens namn och där finns filerna som ska användas när vi vill driftsätta.

Vi skapar en site i nginx med följande konfiguration, där du byter ut `[SERVER_NAME]` med det server namn du vill använda. Vi skapar även root katalogen `/var/www/[SERVER_NAME]/html` med kommandot `sudo mkdir -p /var/www/[SERVER_NAME]/html`.

```bash
server {

        root /var/www/[SERVER_NAME]/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name [SERVER_NAME];

        charset utf-8;

        error_page 404 /index.html;

        location / {
        }
}
```

Skapa en symbolisk länk från `/etc/nginx/sites-enabled` katalogen till din konfigurations-fil i `sites-available`. Kör sedan kommandot `sudo nginx -t` för att testa konfigurationen och `sudo service nginx restart` för att starta om nginx.

Då jag inte vill installera och bygga applikationer på servern väljer jag att använda `rsync` för att överföra filer till servern. Först behöver dock `deploy`-användaren äga och få skriva till katalogen `/var/www/[SERVER_NAME]/html`. Det gör vi med följande kommandon.

```bash
sudo chown deploy:deploy /var/www/[SERVER_NAME]/html
sudo chmod 775 /var/www/[SERVER_NAME]/html
```

Jag väljer att använda möjligheten för att skapa npm-scripts i `package.json` och skapar ett deploy script på följande sätt. I nedanstående är `[SERVER]` din domän och `[SERVER_NAME]` samma som tidigare, `[APP_NAME]` är namnet på din applikation.

```json
"scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e",
    "deploy": "ng build --prod && rsync -av dist/[APP_NAME]/* deploy@[SERVER]:/var/www/[SERVER_NAME]/html/"
},
```

Vi kan nu köra kommandot `npm run deploy` och applikationen byggas för produktion samt överföras till rätt katalog på servern.



### Mithril {#mithril}

Då vi i mithril använder webpack för att bygga våra JavaScript fil skapar vi ytterligare ett npm script för att göra en produktionsfil.

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "webpack -d",
  "production": "webpack -p"
},
```

Vi kan nu köra kommandot med `npm run production` och då skapas en ny `bundle.js` fil, som är redo för produktion. På samma sätt som för vanilla JavaScript appen använder vi rsync för att föra över de tre filerna till servern. Jag utgår från fil och katalog strukturen som finns exempel katalogen.

```bash
rsync -av index.html ../style.css dist/bundle.js deploy@[SERVER]:/var/www/[SERVER_NAME]/html/
```

På servern skapar vi en likadan nginx konfigurationsfil, som för ramverken.



### React {#react}

För att driftsätta en React app krävs att vi har en statisk fil webbserver (static file web server) till exempel nginx. Om appen är skapat med hjälp av `create.react-app` kan vi skapa produktionsfilerna med hjälp av kommandot `npm run build`. Vi har då en `build/` katalog som är de filerna som ska användas när vi vill driftsätta.

Vi skapar en site i nginx med följande konfiguration, där du byter ut `[SERVER_NAME]` med det server namn du vill använda. Vi skapar även root katalogen `/var/www/[SERVER_NAME]/html` med kommandot `sudo mkdir -p /var/www/[SERVER_NAME]/html`.

```bash
server {

        root /var/www/[SERVER_NAME]/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name [SERVER_NAME];

        charset utf-8;

        error_page 404 /index.html;

        location / {
        }
}
```

Skapa en symbolisk länk från `/etc/nginx/sites-enabled` katalogen till din konfigurations-fil i `sites-available`. Kör sedan kommandot `sudo nginx -t` för att testa konfigurationen och `sudo service nginx restart` för att starta om nginx.

Då jag inte vill installera och bygga applikationer på servern väljer jag att använda `rsync` för att överföra filer till servern. Först behöver dock `deploy`-användaren äga och få skriva till katalogen `/var/www/[SERVER_NAME]/html`. Det gör vi med följande kommandon.

```bash
sudo chown deploy:deploy /var/www/[SERVER_NAME]/html
sudo chmod 775 /var/www/[SERVER_NAME]/html
```

Jag väljer att använda möjligheten för att skapa npm-scripts i `package.json` och skapar ett deploy script på följande sätt. I nedanstående är `[SERVER]` din domän och `[SERVER_NAME]` samma som tidigare.

```json
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
  "deploy": "npm run build && rsync -av build/* deploy@[SERVER]:/var/www/[SERVER_NAME]/html/"
},
```

Vi kan nu köra kommandot `npm run deploy` och applikationen byggas för produktion samt överföras till rätt katalog på servern.



### Vanilla JavaScript {#vanilla}

För att driftsätta vanilla JavaScript applikationen använde jag uglifyjs för att minifiera koden. Sedan är det ett liknande `rsync` kommando som för de andra apparna. Jag utgår från fil och katalog strukturen som finns exempel katalogen.

```bash
uglifyjs main.js -o bundle.min.js
rsync -av index.html ../style.css bundle.min.js deploy@[SERVER]:/var/www/[SERVER_NAME]/html/
```

På servern skapar vi en likadan nginx konfigurationsfil, som för ramverken.



### Vue {#vue}

För att driftsätta en Vue app krävs att vi har en statisk fil webbserver (static file web server) till exempel nginx. Om appen är skapat med hjälp av `vue-cli` kan vi skapa produktionsfilerna med hjälp av kommandot `npm run build`. Vi har då en `dist/` katalog som är de filerna som ska användas när vi vill driftsätta.

Vi skapar en site i nginx med följande konfiguration, där du byter ut `[SERVER_NAME]` med det server namn du vill använda. Vi skapar även root katalogen `/var/www/[SERVER_NAME]/html` med kommandot `sudo mkdir -p /var/www/[SERVER_NAME]/html`.

```bash
server {

        root /var/www/[SERVER_NAME]/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name [SERVER_NAME];

        charset utf-8;

        error_page 404 /index.html;

        location / {
        }
}
```

Skapa en symbolisk länk från `/etc/nginx/sites-enabled` katalogen till din konfigurations-fil i `sites-available`. Kör sedan kommandot `sudo nginx -t` för att testa konfigurationen och `sudo service nginx restart` för att starta om nginx.

Då jag inte vill installera och bygga applikationer på servern väljer jag att använda `rsync` för att överföra filer till servern. Först behöver dock `deploy`-användaren äga och få skriva till katalogen `/var/www/[SERVER_NAME]/html`. Det gör vi med följande kommandon.

```bash
sudo chown deploy:deploy /var/www/[SERVER_NAME]/html
sudo chmod 775 /var/www/[SERVER_NAME]/html
```

Jag väljer att använda möjligheten för att skapa npm-scripts i `package.json` och skapar ett deploy script på följande sätt. I nedanstående är `[SERVER]` din domän och `[SERVER_NAME]` samma som tidigare.

```json
"scripts": {
  "serve": "vue-cli-service serve",
  "build": "vue-cli-service build",
  "lint": "vue-cli-service lint",
  "deploy": "npm run build && rsync -av dist/* deploy@[SERVER]:/var/www/[SERVER_NAME]/html/"
},
```

Vi kan nu köra kommandot `npm run deploy` och applikationen byggas för produktion samt överföras till rätt katalog på servern.



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna artikel skrapat ytan på JavaScript ramverken Angular, Mithril, React och Vue, samt jämfört ramverken med vanilla JavaScript. Vi har även tittat på hur vi kan driftsätta en applikation skapat i det valda ramverket på vår cloud-server.

Vi avslutar denna artikel med en video där den tidigare BDFL för [django](https://www.djangoproject.com/) pratar om hur vi inte alltid behöver ett JavaScript ramverk.

[YOUTUBE src=k7n2xnOiWI8 caption="A Framework Author's Case Against Frameworks - Adrian Holovaty - dotJS"]

---
author: efo
category: javascript
revision:
  "2017-03-15": (A, efo) Första utgåvan inför kursen webapp v2.
...
Ett mobilanpassad formulär
==================================

[FIGURE src="/image/webapp/form.jpeg?w=c5" class="right"]

Vi ska i denna övning titta på hur vi med hjälp av HTML5 input gör våra mobila appar mer användarvänliga och säkra. Vi skapar även formulär komponenter till vårt GUI komponent ramverk. I slutet av övningen tittar vi på hur vi skapar ett formulär i mithril.



<!--more-->



HTML5 input typer {#html5}
--------------------------------------

I och med introduktionen av HTML5 introducerades även ett antal nya [input typer](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input). Dessa typer specificerar vilken sorts data som inputfältet kan ta som indata. Detta gör det möjligt att hindra användaren från att fylla i fel sorts data, men även att anpassa användargränssnittet till det data som användaren skall fylla i. Nedan finns en listning av 6 input typer och hur den mobila enheten anpassas för input typen. Inputfälten visas i Android emulatorns webbläsare.

Det helt vanliga text input fältet ger ett vanligt tangentbord och ingen klient validering av vilka värden som fylls i.

```html
<input type="text">
```

[FIGURE src="/image/webapp/input-screenshot/input-text.png?w=200" caption="Text input"]



Om man har ett fält där användaren bara ska ange siffror kan man använda sig av `number`. Detta gör att tangentbordet på mobila enheter bytts ut mot ett numerisk och att det inte går att fylla i annat än karaktärer relaterade till siffror.

```html
<input type="number">
```

[FIGURE src="/image/webapp/input-screenshot/input-number.png?w=200" caption="Number input"]



Om användaren skall fylla i sin e-postadress kan det vara bra med et input av typen `email`. Det underlättar för användaren när man skall använda @.

```html
<input type="email">
```

[FIGURE src="/image/webapp/input-screenshot/input-email.png?w=200" caption="Email input"]



Vid ifyllning av telefonnummer kan det vara fördelaktigt att använda input av typen `tel`. Där får användaren upp ett numerisk tangentbord, som ser ut som det man använder när man skall ringa från en telefon.

```html
<input type="tel">
```

[FIGURE src="/image/webapp/input-screenshot/input-tel.png?w=200" caption="Telephone input"]



När vi har datumfält finns input av typen `date`. Med `date` får användaren av en mobil enhet upp en datum väljare. På desktop skiljer det mellan de olika webbläsare, men Chrome och Firefox ger användaren möjlighet för att välja datum formaterat enligt användarens inställningar. Det värde som skickas med när vi skickar formuläret är alltid formaterat enligt 'YYYY-MM-DD'.

```html
<input type="date">
```

[FIGURE src="/image/webapp/input-screenshot/input-date.png?w=200" caption="Date input"]



För fält där vi vill skriva in lösenord använder vi naturligtvis `password`.

```html
<input type="password">
```

[FIGURE src="/image/webapp/input-screenshot/input-password.png?w=200" caption="Password input"]


Styling av formulär {#styling}
--------------------------------------
När vi designade våra knappar i förra kursmomentet ville vi att de tre olika elementen `button`, `a` och `input[type=submit]` skulle se likadana ut. När vi designar formulärfält vill vi att de olika fälten ser likadana ut. Vi ska i denna del av övningen titta på hur vi kan designa formulärfält som är enhetligt designade i olika webbläsare. Hur vi ligger till genomtänkta förifyllda värden och hur vi tydligt visar för användaren vilket fält som är i fokus.

Vi börjar med den enhetliga stylingen. Vi börjar med att definiera klassen `.input` då kan vi använda klassen när vi vill ge styling till element. Vi vill som för knapparna ha ett mjukt utseende och rundar därför hörnen på samma sätt som för knapparna. Vi vill ha samma tunna ram runt knappen och vi vill ha samma typsnitt i formulärfälten som på resten av sidan. Vi vill även ha samma bredd på alla formulärfält trots de olika typer och vi specificerar bredden i `rem`. Vi ökar den inre marginalen (padding) så att fälten blir lättare att klicka på. Vi vill även ha ett avstånd mellan formulärfältet och sätter det som `margin-bottom`.

```scss
.input {
    font-size: $body-font-size;
    line-height: $line-height;
    font-family: $font-body;
    display: block;
    border: 1px solid #ccc;
    border-radius: 0.2rem;
    padding: 0.6rem 0.6rem;
    box-sizing: border-box;
    width: 32rem;
    margin-bottom: 1.4rem;
}
```

För små mobila enheter vill vi inte att fälten har en fast bredd utan då ska de fylla ut hela bredden på skärmen. Då vi i grunddefinitionen har satt `box-sizing: border-box;`. Gör vi detta enkelt med nedanstående kod.

```scss
@media (max-width: 667px) {
    .input {
        width: 100%;
    }
}
```

En viktig del av formulärfälten är texten vi har som beskriver fälten med (label). Vi vill designa våra label och formulärfältet så det är tydligt vilka som hänger ihop. Igen börjar vi med att skapa en klass `.input-label` och ger bara style till den. Det enda vi gör är att använda `display: block;` och sätta typsnittet att det ska vara `bold`. Vi ökar upp marginal ovanför våra element för att klumpa ihop `label` och `input`.

```scss
.input-label {
    font-weight: bold;
    margin: 2rem 0 0 0;
    display: block;
}
```

Om man vill ha lite mindre marginal på första elementet med klassen `.input-label` kan man använda pseudo-klassen `:first-of-type` enligt nedan.

```scss
.input-label:first-of-type {
    margin: 1rem 0 0 0;
}
```

Om man alltid vill ha ett kolon (:) efter `.input-label` kan man använda pseudo-elementet `::after`.

```scss
.input-label::after {
    content: ":";
}
```

Ett annat bra sätt att förtydliga för användaren vad som ska fyllas i är att använda sig av `placeholder` attributet. Detta görs i HTML på detta sättet `<input type="text" placeholder="Fyll i text">`. I mithril exemplet nedan finns exempel på hur man använder en placeholder i mithril.

Våra formulärfält ser nu ut enligt nedan och vi har nu samma styling trots olika webbläsare och olika typer av formulärfält.

[FIGURE src="/image/webapp/screenshot-inputs-chrome.png?w=c7" class="right" caption="Formulärfält i Chrome med ifylld data."]
[FIGURE src="/image/webapp/screenshot-inputs-firefox.png?w=c7" caption="Formulärfält i Firefox med placeholders."]



Ett formulär i mithril {#mithril}
--------------------------------------
Formuläret nedan gör det möjligt att redigera en dator. Det finns en `Computer` modell som tar hand om data när det skickas från formuläret. När vi skapar formulär i mithril använder vi oss som vanligt av `m` för att skapa våra virtuella noder. Längst ut lägger vi ett formulär element och inuti formulär elementet våra formulärfält. För att de ändringar vi gör i formulärfältet ska sparas använder vi oss av livscykel metoden `oninput` och funktionen `m.withAttr` ([Dokumentation](http://mithril.js.org/withAttr.html)). `oninput` och `m.withAttr` sätter värdet på den nuvarande dator (`Computer.current`) varje gång vi ändrar i fältet.

Vi använder oss av en livscykel metod `onsubmit` för formuläret för att förhindra att formuläret laddar om sidan när vi trycker på spara-knappen. Vi anropar dessutom modellens `save` funktion och då vi har redan satt värdet på den nuvarande dator kan vi helt enkelt bara spara den med hjälp av `m.request` och API:t som ligger i bakgrunden för appen.

```javascript
import m from 'mithril';
import computer from "../models/computer";

let computerForm = {
    oninit: function(vnode) {
        computer.load(vnode.attrs.id);
    },
    view: function() {
        return m("form", {
                onsubmit: function(event) {
                    event.preventDefault();
                    computer.save();
                } }, [
            m("label.input-label", "Name"),
            m("input.input[type=text][placeholder=Name]", {
                oninput: m.withAttr("value", function(value) { computer.current.name = value }),
                value: computer.current.name
            }),
            m("label.input-label", "Year"),
            m("input.input[type=number][placeholder=Year]", {
                oninput: m.withAttr("value", function(value) { computer.current.year = value }),
                value: computer.current.year
            }),
            m("label.input-label", "Operating System"),
            m("select.input", {
                onchange: m.withAttr("value", function(value) { computer.current.os = parseInt(value) })
            }, computer.operatingSystems.map(function(os) {
                return m("option", { value: os.id }, os.name);
            })),
            m("input[type=submit][value=Save].button", "Save")
        ]);
    }
};

export { computerForm };
```

Modellen `computer` som används för att hämta ut den specifika datorn som ska redigeras (`load`) och spara datorn (`save`) ser ut enligt nedan. Först definierar vi `computer.operatingSystems` och  `computer.current`. De används för att visa upp operativsystem och `current` används för att spara data vi hämtar från vårt låtsas API. När vi sedan ska spara datorn anropar vi en `PUT` route och skickar med `computer.current` som data objekt.

```javascript
var m = require("mithril");

var computer = {
    operatingSystems: [
        { id: 1, name: "Windows 10" },
        { id: 2, name: "Windows 7" },
        { id: 3, name: "MacOS" },
        { id: 4, name: "Debian" },
        { id: 4, name: "Ubuntu" }
    ],
    current: {},
    load: function(id) {
        return m.request({
            method: "GET",
            url: "www.api-url.com/load/" + id
        }).then(function(result) {
            computer.current = result;
        });
    },
    save: function() {
        return m.request({
            method: "PUT",
            url: "www.api-url.com/save",
            data: computer.current
        }).then(function() {
            m.route.set("/computers");
        });
    }
};

export { computer };
```

För ytterligare exempel på formulär hantering i mithril titta i [tutorial](https://mithril.js.org/simple-application.html).



Avslutningsvis {#avslutning}
--------------------------------------
Detta var en genomgång av ett antal olika input typer i HTML5, som ger bättre användbarhet speciellt på mobila enheter. Genom att tala om vilken sorts data, som varje formulärfält är gjort för, kan den mobila enhet anpassa tangentbord och användargränssnitt för den specifika användningen.

Vi har även tittat på formulärhantering i mithril både själva formuläret i en vy och hur den bakomliggande modellen för att hämta och spara data ser ut.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7317) om denna artikeln.

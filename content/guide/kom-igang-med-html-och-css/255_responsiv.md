---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Responsiv webbplats {#responsiv}
=======================

Det pratas mycket om responsiva webbplatser, responsiv webbdesign och *mobile first*. Den typen av tänkande blir allt mer viktigt då webbplatserna används av både desktop-datorer, läsplattor och mindre mobila enheter.

Ni ska vi inte fördjupa oss i detta, men låt oss ändå använda en enkel princip för att uppnå att webbplatsen kan fungera bra även på mindre enheter.

Först berättar vi för enheten som besöker vår webbplats att den skall använda sin egen bredd för att visa sidan, den skall inte låtsas att den är större än den verkligen är.

```html
    <meta name="viewport" content="width=device-width; initial-scale=1.0; maximum-scale=2.0;">
</head>
```

I annat fall kan en mobil låtsas att ha en mycket större skärm än den egentligen har, för att simulera att den är en desktop-skärm.

Nästa steg är att lägga till en media-fråga, en *media-query*, för att ändra sidans utseende på små skärmar.

```css
/**
 * responsive
 */
@media (max-width: 980px) {
    body {
        width: auto;
        background-color: yellow;
    }
}
```

Media-frågan säger att om bredden på webbläsaren är mindre än 980 pixlar så skall CSS-konstruktionen som följer gälla. Du kan testa om det fungerar, på din egen webbplats, genom att ändra storleken på webbläsaren. När bredden blir mindre än 980 pixlar så kommer den att få samma bredd som webbläsaren, det är det som `auto` innebär.

Att färgen blir gul är bara för att göra det enklare att se att stylen verkligen ändras.

I de flesta webbläsare kan man simulera hur en sida ser ut i en uppsätting mobila enheter. Antingen kan man högerklicka, och välja "inspektera element" eller helt enkelt trycka på tangenten `F12`. Överst i rutan som dyker upp hittar man en knapp, "Responsive design mode" eller liknande. Testa, lek och lär. Lägg `F12` på minnet då det är ett väldigt kraftfullt verktyg vid utveckling mot både webbläsaren och mobila enheter.

Så här ser det ut när webbplatsen visas i en iPhone i porträttläge i Firefox.

[FIGURE src=/image/htmlphp/guide/murphy/iphone-portrait1.png?w=w2 caption="index.html visas i porträttläge för iPhone 6s."]

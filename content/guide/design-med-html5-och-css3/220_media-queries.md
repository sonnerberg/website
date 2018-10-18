---
author: efo
revision:
    "2018-10-17": "(A, efo) Första versionen."
...
Media queries
=======================

När vi vill anpassa en webbplats till skärmar av olika storlekar är ett sätt att använda media queries. Media queries kan bland annat användas för att vid olika storlekar av skärmar applicera andra CSS regler. Låt oss titta på ett exempel där vi definierar ett element och sedan ger det en annan styling när skärmen är mindre än 980 pixlar.

```css
.big-box {
    width: 960px;
    margin: 0 auto;
}

@media (max-width: 980px) {
    .big-box {
        width: 98%;
    }
}
```

Vi observerar ovan att vi lägger vår media query efter den ursprungliga definitionen av elementet då vi vill att den skrivs över när skärmen är liten.

För mer om media queries och andra användningsområden än responsiva webbplatser se MDN web docs [Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) dokument.

I exempel katalogen finns ett exempel program med media queries. Exempelprogrammet finns i `example/media-queries` eller på [GitHub](https://github.com/dbwebb-se/design/tree/master/example/media-queries).

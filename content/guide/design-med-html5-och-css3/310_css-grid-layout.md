---
author: efo
revision:
    "2018-10-12": "(A, efo) Första versionen."
...
CSS Grid Layout
=======================

I moderna webbläsare finns det ett nytt sätt för att skapa grid layouts, istället för sätten man har gjort tidigare med tabeller, floats, flexbox osv. Detta nya moderna och tyvärr inte riktigt supporterade sätt kallas CSS Grid Layout eller kort och gott CSS Grid. Vi ska i denna artikel kort titta på hur man kan använda CSS Grid för att skapa en enkel sida med en header, två kolumner och en footer. För mer information om CSS Grid kan [A Complete Guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) rekommenderas.

Vi börjar med lite HTML där vi skapar en `container` samt 4 stycken `items` som vi sedan vill placera ut i ett grid.

```html
<div class="container">
    <div class="header">header</div>
    <div class="column-left">column-left</div>
    <div class="column-right">column-right</div>
    <div class="footer">footer</div>
</div>
```

För att webbläsaren ska veta om att vi vill använda CSS Grid definierar vi att `container` ska vara en grid `container` med följande kod.

```css
.container {
    display: grid;
}
```

Vi vill sedan definiera hur vi vill ha våra rader och kolumner i vår grid. Vi kommer ha en rad för header, en där kolumnerna ligger och en för footer, sedan vill vi ha en kolumn för den vänstra kolumnen och en för den högra. Vi definierar det med följande kod, där vi även centrerar `container` och sätter storlekarna både `container` samt för våra rader och kolumner.

```css
.container {
    width: 960px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: auto 200px;
    grid-template-rows: 200px 600px 200px;
}
```

I ovanstående exempel sätter vi att vi att första kolumnen automatisk ska anpassa sig och ta upp resten av utrymmet som finns tillgängligt och att kolumn två ska vara 200 pixlar bred. Sedan definierar vi vår tre rader som 200 pixlar, 600 pixlar och 200 pixlar höga.

Det som återstår nu är att placera ut våra `items` på rader och kolumner i vårt grid. Vi gör detta med det som kallas `short-hand syntax` så vi definierar på vilken linje mellan rader eller kolumner våra element ska starta och sluta. För header delen vill vi att den ska starta på 1:a kolumn-linjen och sluta på 3:e kolumn-linjen, dvs hela översta raden. Detta gör vi med följande kod.

```css
.header {
    grid-column: 1 / 3;
    grid-row: 1 / 1;
}
```

För de andra element blir det följande kod med de två kolumner och en footer som tar upp hela bredden.

```css
.column-left {
    grid-column: 1 / 1;
    grid-row: 2 / 2;
}

.column-right {
    grid-column: 2 / 2;
    grid-row: 2 / 2;
}

.footer {
    grid-column: 1 / 3;
    grid-row: 3 / 3;
}
```

I exempel-katalogen och på [github](https://github.com/dbwebb-se/design/tree/master/example/css-grid-layout) finns koden från detta exempel i katalogen `css-grid-layout` med möjlighet att leka runt med de olika värdena för att testa hur CSS Grid fungerar.

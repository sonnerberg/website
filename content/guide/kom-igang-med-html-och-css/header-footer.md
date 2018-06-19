---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Header och footer {#header-footer}
=======================

Det finns ett flertal element som kan hjälpa oss med strukturen. Två viktiga element är &lt;header&gt; och &lt;footer&gt;. Tanken med dem är att de ska hantera innehållet högst upp på sidan respektive längst ner. Du får själv lista ut vilket element som hanterar vad. Vi lägger till dem och ger dem varsin bakgrundsfärg. Vi kan även passa på att titta på olika rubrik-element och en paragraf.

index.html:

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>Stormtrooper Murphy</title>
    <link rel="stylesheet" href="style/style.css">
</head>
<body>
    <header>
        header
    </header>
    <h1>Det här är en rubrik i elementet h1</h1>
    <h2>Det här är en rubrik i elementet h2</h2>
    <h3>Det här är en rubrik i elementet h3</h3>
    <h4>Det här är en rubrik i elementet h4</h4>
    <h5>Det här är en rubrik i elementet h5</h5>
    <h6>Det här är en rubrik i elementet h6</h6>
    <p>Den här texten är i en paragraf</p>
    <footer>
        footer
    </footer>
</body>
</html>
```
Taggarna h1-h6 representerar rubriker i fallande storlek. Både rubriker och paragrafer (&lt;p&gt;) har en default-style kopplad till sig. Man får automatiskt lite luft över och under dem. Bra att ha koll på. I headern och footern är texten inte omsluten av några taggar, så där sker ingen formattering.

För att se våra nya element behöver vi ge dem lite färg och en storlek. Följande lägger jag in i style.css:

```css
body {
    background-color: #ddd;
    width: 1000px;
    margin: 0 auto;
}

header {
    width: 1000px;
    height: 100px;
    background-color: red;
}

footer {
    width: 1000px;
    height: 70px;
    background-color: green;
}
```

**background-color** sätter som bekant en bakgrundsfärg på elementet. Här använder jag ett *hexadecimalt* värde. En färg kan representeras av en eller två siffror enligt RGB(Red, Green, Blue) alternativt som tidigare, av färgens namn. Det finns många färger med fördefinierade namn. Testa och lek!  

**width** sätter en bredd på elementet. Här använder jag `px` (pixlar).  

**margin** talar om hur mycket marginal runt elementet som ska finnas. Värdet `0 auto` är en fix för att få det att hamna i mitten. 0 pixlar uppåt och nedåt samt beräkna vänster och höger automatiskt. Mer om det senare, nu tittar vi hur det ser ut.

[FIGURE src=/image/htmlphp/guide/murphy/steg1.png?w=w2 caption="En grundstruktur för en webbsida."]

Testa exemplet på [Codepen](https://codepen.io/dbwebb/pen/aKErbo).

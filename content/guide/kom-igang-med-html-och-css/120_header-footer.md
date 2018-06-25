---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Header och footer {#header-footer}
=======================

Det finns ett flertal element som kan hjälpa oss med strukturen. Två viktiga element är &lt;header&gt; och &lt;footer&gt;. Tanken med dem är att de ska hantera innehållet högst upp på sidan respektive längst ner. Du får själv lista ut vilket element som hanterar vad. Vi lägger till dem och ger dem varsin bakgrundsfärg. Samtidigt kan vi ta bort rubrikerna och paragraferna.

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
    <header></header>
    <h1>I am Stormtrooper Murphy!</h1>
    <p>This is my website.</p>
    <footer></footer>
</body>
</html>
```
Vi lämnar lite text på sidan så länge så se vi vart det hamnar.

För att se våra nya element behöver vi ge dem lite färg och en storlek. Följande lägger jag in i style.css:

```css
html {
    background-color: white;
}

body {
    background-color: #ddd;
    width: 1000px;
    margin: 8px auto;
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

**background-color** sätter som bekant en bakgrundsfärg på elementet. I `body` använder jag ett *hexadecimalt* värde. En färg kan representeras av en eller två siffror enligt RGB(Red, Green, Blue) eller som tidigare, av färgens namn. Det finns många färger med fördefinierade namn. Läs gärna mer om [color keywords](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value).  

**width** sätter en bredd på elementet. Här använder jag `px` (pixlar).  

**margin** talar om hur mycket marginal runt elementet som ska finnas. Värdet `8px auto` är en fix för att få det att hamna i mitten. 8 pixlar uppåt och nedåt samt beräkna vänster och höger automatiskt. Mer om det senare, nu tittar vi hur det ser ut.

[FIGURE src=/image/htmlphp/guide/murphy/grund-2.png?w=w2 caption="Röd header och grön footer."]

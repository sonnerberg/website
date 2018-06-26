---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Styla navbar för nuvarande sida {#current}
=======================

Det är vanligt att navbaren visar, markerar, valet för nuvarande sida. När man klickat på valet för sidan "About" så skall det menyvalet vara aktivt, eller valt, och detta visas med en annorlunda style av menyvalet.

Här finns olika tekniker att jobba med, men då jag bara har två sidor, kör jag på CSS. Om det är nuvarande sida så sätter vi en CSS-klass på HTML-elementet och kan därmed styra dess utseende.

Vi har följande navbar att utgå ifrån.

```html
<nav class="navbar">
    <a href="index.html">Home</a>
    <a href="about.html">About</a>
</nav>
```

Tanken är att skapa en struktur som lägger till en klass i menyvalet, om man besöker just denna sidan. Vi vill att det skall se ut så här i HTML-koden, när man till exempel besöker sidan "About".

```html
<nav class="navbar">
    <a href="index.html">Home</a>
    <a href="about.html" class="selected">About</a>
</nav>
```

Lägger vi nu till CSS-kod så kan vi styla klassen för att ge just detta menyval ett speciellt utseende.

```css
...
.navbar .selected {
    background-color: #ccc;
}
```

---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
`<main>` och `<article>` {#main-article}
=======================

Det handlar om att strukturera sidans innehåll i *rätt* HTML-element. Vad som är rätt och inte är inte alltid tydligt, men det finns grundstrukturer som är tydliga. HTML-elementen har en *semantisk* mening, de berättar vilken typ av innehåll de har. Det underlättar när man läser sidans källkod, man ser tydligare vilken betydelse de olika elementen har.

Så här gjorde jag. Jag tillförde ett element som heter `<main>` som wrappar sidans huvudsakliga innehåll. Jag samlade webbsidans huvudsakliga innehåll inom ett element `<article>`.

Artikeln fick en egen `<header>` och en `<footer>` där bylinen ligger. Strukturen ser ut så här.

```html
<main>
    <article>
        <header>
            <h1>Article header</h1>
            <p class="author">Updated <time datetime="2018-06-25 11:17:43">25th june 2018</time> by Murphy</p>    
        </header>

        <p>Article content, images etc.</p>

        <footer class="byline">
            <p>Content for a byline, images etc.</p>
        </footer>
    </article>
</main>
```

Man kan lägga till CSS-klasser där det behövs, det gör det enklare att styla elementen. Det är inget man behöver göra från början, man kan fylla på med CSS-klasser efter hand, när man känner att det behövs. Som du kan se av koden ovan har jag valt klasserna `author` och `byline`, mest för jag tycker det är enklare att styla de HTML-block som avses.

HTML handlar mycket om att märka upp orden, det är viktigt att man använder en god struktur för uppmärkningen. Iallafall om man vill bli proffs på detta. Men, det finns inget exakt facit för hur man ska göra. Men genom att läsa specifikationerna och se hur andra gör, så lär man sig vad som fungerar och inte. Dessutom, om det ser bra ut i webbläsaren, då kan det ju inte vara fel, eller hur?

En första ansats kan se ut så här:

[FIGURE src=/image/htmlphp/guide/murphy/after-article.png?w=w2 caption="Indelning i main, article"]

Vi lägger även in innehåll i about.html och delar in det i `main` och `article`. 

Du kan studera koden på [Codepen](https://codepen.io/dbwebb/pen/VdBMVo).

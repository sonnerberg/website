---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Navbar {#navbar}
=======================

Vi ska såklart inte bara ha en sida. Murphy vill ju ha en sida till! Vi skapar en sida som tar upp lite om Murphys förflutna, så en potentiell arbetsgivare får en känsla för vem detta är.  

Elementet `<nav>` definierar en uppsättning navigeringslänkar, vilket passar bra till ändamålet. Följande kod hamnar i `index.html` precis under slut-taggen `</header>`:

```html
...
<nav class="navbar">
    <a href="index.html">Home</a>
    <a href="about.html">About</a>
</nav>
...
```

**&lt;a&gt;** definierar en länk. Atttributet `href` talar om vad länken ska peka mot.

Sedan måste vi ha en sidan det länkas till. Jag väljer att kopiera `index.html` och döper kopian till `about.html`. Den nya filen får en ny title `<title>` och bilden städas undan. Låt oss ladda om webbläsaren och se hur `<nav>` skapar länkarna per default:

[FIGURE src=/image/htmlphp/guide/murphy/navbar-right.png?w=c8 class="right" caption="about.html"]
[FIGURE src=/image/htmlphp/guide/murphy/navbar-left.png?w=c8 caption="index.html"]



Fint, det går att navigera mellan sidorna. Det ser dock inte ut som en navigeringsmeny så vi gör ett tappert försök till snyggare style.

style.css:

```css
.navbar {
    padding: 1em;
    background-color: #fff;
    border-top: 1px solid #9c9;
}

.navbar a {
    display: inline-block;
    padding: 0.5em 1em;
    border: 1px solid #999;
    text-decoration: none;
}

.navbar a:hover {
    background-color: #eee;
    text-decoration: underline;
}
```

**text-decoration** möljliggör style av länkar och värdet `none` ser till så länkarna inte har kvar sitt grundutseende. Läs gärna mer om egenskapen [text-decoration](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration).

När vi nu tittar i webbläsaren börjar det se proffsigt ut:

[FIGURE src=/image/htmlphp/guide/murphy/navbar1.png?w=w2 caption="Bra start!"]

---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Validering {#validering}
=======================

Hur vet man att man skriver bra kod? Ett sätt är att validera koden med hjälp av en så kallad *Markup Validation Service*. W3C tillhandahåller en sådan, både för HTML och CSS. Man kan antingen validera med hjälp av en länk, filuppladdning eller direkt inmatning. För att det ska fungera med en länk måste sidan ligga på en publik server, vilket den inte gör än. Vi går in på [https://validator.w3.org/](https://validator.w3.org/) och klickar på *Validate by Direct Input* och klistrar in vår HTML-kod från index.html.

[FIGURE src=/image/htmlphp/guide/murphy/validate-html.png?w=w2 caption="Grönt = bra."]

Det finns som sagt även en validator för CSS-koden. Vi gör likadant med den. Glid in på [https://jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator/) och *By Direct Input*. Klistra in och kör!

[FIGURE src=/image/htmlphp/guide/murphy/validate-css.png?w=w2 caption="Grönt = bra."]

Nu vet vi att vi följer standarden för hur språken ska struktureras. Vi jobbar vidare med footern och lägger in länkar till validatorerna så vi kan validera sidan med ett klick. Följande kod löser det i slutet av index.html.

```html
    <footer>
        <hr>
        <a href="http://validator.w3.org/check/referer">HTML5</a>
        <a href="http://jigsaw.w3.org/css-validator/check/referer">CSS</a>
    </footer>
</body>
```

Så här blev det för mig:

[FIGURE src=/image/htmlphp/guide/murphy/validatelinks.png?w=w2 caption="Två länkar till validatorerna."]



###Unicorn, ett valideringsverktyg för flera tekniker {#unicorn}

Som om inte detta räcker finns verktyget *Unicorn* som är ett valideringsverktyg som kör både HTML och CSS i ett svep. Dessutom kan det köra ytterligare kompletterande tester. Vi lägger till en länk till det med:

```html
<a href="http://validator.w3.org/unicorn/check?ucn_uri=referer&amp;ucn_task=conformance">Unicorn</a>
```



###Om HTML-entiteter {#htmlentities}

Varför används `&amp;` istället för tecknet `&` när vi länkar till Unicorn ovan?
Du kan testa att ändra din kod och enbart skriva `&`. Validera den sedan i Unicorn. Du får då ett felmeddelande som säger:

> **`&` did not start a character reference. (`&` probably should have been escaped as `&amp;`.)**

Tecknet `&` har en speciell betydelse i HTML och därför kan det ibland behöva ersättas med sin motsvarande HTML entitet `&amp;`. Annars validerar inte HTML-koden, den är inte helt korrekt.

I tabellen nedan är ett par tecken som är reserverade i HTML, de har speciell betydelse. Om man vill att respektive tecken skall skrivas ut i text, eller vara en del av en länk, så behöver man byta ut tecknet mot dess _entity_, eller HTML entitet som det också kallas.

| Tecken | Entity   | Kommentar |
|--------|--------  |-----------|
| `&`    | `&amp;`  | Början på en entitet eller teckensekvens. |
| `<`    | `&lt;`   | Start på en HTML-tagg. |
| `>`    | `&gt;`   | Slut på en HTML-tagg. |
| `"`    | `&quot;` | Start och slut på ett attributs värde. |

Det finns fler tecken som kan konstrueras med HTML entiter. Du kan till exempel skapa ett copyright-tecken &copy; `&copy;` eller ett euro-tecken &euro; `&euro;` med dem.

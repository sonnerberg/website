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

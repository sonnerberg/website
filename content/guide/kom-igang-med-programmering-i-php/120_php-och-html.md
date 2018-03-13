---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
PHP och HTML
=======================



Först en vanlig html-sida {#html-mall}
-----------------------

Låt oss göra ett exempel. Vi börjar med en vanlig enkel html-sida och vi gör sedan om den till en dynamisk php-sida. Det ger oss en känsla av skillnaden mellan dem. **Jag visar hur jag gör och du gör likadant på din egen server.**

*Kod: En enkel mall-sida för testprogram, mall.html*

```html
<!doctype html>
<html lang="sv"> 
<head>
<meta charset="utf-8"/>
<title>php20</title>
</head>
<body>
<h1>Mallsida i HTML</h1>
<p>Hello World!</p>
<hr>
<a href="http://validator.w3.org/unicorn/check?ucn_uri=referer&amp;ucn_task=conformance">Unicorn</a>
<a href="source.php">Källkod</a>
</body>
</html>
```

Skapa en sida `mall.html` som innehåller koden ovan. Du kan testa min variant av [`mall.html`](kod-exempel/guiden-php-20/2/mall.html). Kolla att den går igenom validatorn.

Klicka sedan på länken källkod och leta reda på sidan `mall.html` och studera dess källkod. Det som du ser är källkoden som den ser ut på server-sidan. Vi kan kalla det för orginal-koden. Här är en [direktlänk till källkoden för `mall.html`](kod-exempel/guiden-php-20/2/source.php?dir=&file=mall.html#file) som den visas med skriptet `source.php`.

[INFO]
**Visa källkod med `source.php`**

Du kan [ladda ned en egen kopia av `source.php`](source). Ta en kopia av koden och lägg i en fil som du döper till `source.php`. Lägg filen i samma katalog som filen `mall.html`.
[/INFO]

Gå tillbaka och visa sidan `mall.html` i din webbläsare. Ta musen och högerklicka på webbsidan, välj menyvalet "Visa källkod". Nu visas den källkod upp som webbläsaren har laddat. 

[FIGURE src=/image/snapshot/guiden-php-20-kallkod-mall-html.png?w=w1 caption="Högerklicka och visa källkod för att se vad webbläsaren ser."]

Det är detta som är källkoden ur webbläsarens perspektiv. När vi nu börjar jobba med PHP så måste vi skilja på hur källkoden ser ut på serversidan och hur den ser ut i webbläsaren. Det är två skilda saker och vid felsökning så har man nytta av båda varianterna.




Nu en php-sida {#php-mall}
-----------------------

Bra. Ta nu en kopia av sidan `mall.html` och döp den till `mall.php`, öppna den i din webbläsare och kontrollera att den visar exakt samma resultat som `mall.html`. Det enda jag ändrar så långt är sidans rubrik.

Nu lägger vi till lite PHP-kod i mall-sidan. Vi tar en enkel konstruktion som bara skriver ut "Hello World".

*Kod för att skriva ut "Hello World from PHP".*

```php
<?php echo "<p>Hello World from PHP.</p>"; ?>
```

Se hur min [`mall.php`](kod-exempel/guiden-php-20/2/mall.php) ser ut. Studera källkoden för sidan, dels på serversidan och dels i webbläsaren. Kan du se skillnaden mellan dem? Server-sidan innehåller PHP-konstruktionen och när webbläsaren ser sidan så finns det bara HTML-kod. Det är bra att ha koll på dessa två varianter av källkod, dels på serversidan och dels i webbläsaren.

Skillnaden mellan `mall.html` och `mall.php` är att sidan som slutar på ändelsen `.php` körs genom PHP's preprocessor. När preprocessorn hittar PHP-taggar, det vill säga `<?php` (starttag) och `?>` (sluttag), så tolkas detta som PHP-kod och exekveras. Allt som man då skriver ut i sin PHP-kod hamnar i den slutliga HTML-koden och skickas till webbläsaren.

*PHP starttag och sluttag.*

```php
<?php
// PHP starttag, efter denna så kommer PHPkod.
// Här skriver man sin PHP-kod.
// Nu kommer PHP sluttag.
?>
```

Nu har vi grunderna till ett testprogram för PHP. Då går vi vidare.

---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Dela upp i filer och inkludera
=======================

När du börjar skriva mycket PHP-kod så vill du dela in din kod i olika delar. Det är enklare att underhålla mindre väl avgränsade delar än en stor klump av kod. Ett sätt att organisera koden är att dela in den i filer och inkludera filerna när det behövs med [`include()`](http://php.net/manual/en/function.include.php) eller [`require()`](http://php.net/manual/en/function.require.php).



Inkludera för att strukturera en webbsida {#include-webb}
-----------------------

Ett vanligt användningsområde för `include()` är att dela in webbplatsens sidor i olika delar. Till exempel så används ofta en och samma header och footer på samtliga sidor i en webbplats. Då kan man strukturera sin kod så att man har headern i en egen fil, `header.php`, footern i en egen fil, `footer.php` och sedan inkluderas dessa i varje ny sida som skapas.

**Ett exempel med include av `header.php` och `footer.php` i en `new-page.php`.** 

```php
<?php 
$title = "Titel på min nya sida";
include("header.php"); 
?>
 
<h1>Här är en ny sida</h1>
<p>Lång fin text på min nya sida.</p>
 
<?php include("footer.php"); ?>
```

I detta fallet kan filen `header.php` se ut som följer. Notera hur variabeln `$title` används för att skriva ut sidans titel. Variabeln sätts i den nya sidan, men används i `header.php`. På det sättet kan du definiera variabler på en plats och använda dem i en annan fil. Är du osäker på vad en variabel innehåller så skriver du helt enkelt ut dess innehåll för att dubbelkolla, antingen med `echo` eller med `var_dump()`.

**Innehållet i `header.php`.**

```php
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title><?= $title ?></title>
</head>
<body>
```

På liknande sätt så innehåller filen `footer.php` avslutningen av sidan.

**Innehållet i `footer.php`.**

```php
<hr>
<footer>Denna sidans footer</footer>
</body>
</html>
```

Du kan testa mitt [exempel för webbsida med `include()`](kod-exempel/guiden-php-20/7/new-page.php).

Om du kör exemplet och sedan högerklickar för att visa sidans källkod så ser du det sammanfogade resultatet.

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Titel på min nya sida</title>
</head>
<body>
 
<h1>Här är en ny sida</h1>
<p>Lång fin text på min nya sida.</p>
 
<hr>
<footer>Denna sidans footer</footer>
</body>
</html>
```



Include eller require? {#require}
-----------------------

Skillnaden på `include()` och `require()` är felhanteringen. Om filen saknas så *avbryter* `require()` exekveringen med ett felmeddelande medan `include()` ger ett felmeddelande men *fortsätter exekveringen*. Vilket som är bäst att använda beror på sammanhanget och du kan själv välja vilket du tycker passar bäst.

Här kan du se exempel på felmeddelanden där filen som skall inkluderas saknas, först ett [exempel med `include()`](kod-exempel/guiden-php-20/7/include_error.php) och sedan ett [exempel med `require()`](kod-exempel/guiden-php-20/7/require_error.php).

Det finns två varianter som heter [`include_once()`](http://php.net/manual/en/function.include-once.php) och [`require_once()`](http://php.net/manual/en/function.require-once.php). Skillnaden är att de kontrollerar att filen endast inkluderas en gång. 



Konstanter `__FILE__` och `__DIR__` för absolut sökväg {#sokvag}
-----------------------

När man inkluderar filer så vill man ibland använda absolut sökvägen till filerna. Då har man användning av konstanterna `__FILE__` och `__DIR__`. Dessa konstanter ger sökvägen till den filen som nu exekveras, eller till den katalog som filen finns i. Se följande exempel på hur du använder dessa konstanter tillsammans med `require()`.
  
```php
<?php
echo "<p>Constant __DIR__ (available from PHP 5.3) is: " . __DIR__ . "</p>";
echo "<p>Constant __FILE__ is: " . __FILE__ . "</p>";
echo "<p>Filename-part of __FILE__ is: " . basename(__FILE__) . "</p>";
echo "<p>Directory-part of __FILE__ is: " . dirname(__FILE__) . "</p>";

echo "<p>Lets include a file by using __FILE__ and __DIR__ to create the absolute path.</p>";
include(dirname(__FILE__) . "/empty_file.php");
include(__DIR__ . "/empty_file.php");
?>
```

Här kan du testa mitt [exempel på absolut sökväg](kod-exempel/guiden-php-20/7/constants.php).

Dessa konstanter är exempel på magiska konstanter som är fördefinerade i PHP. Se vilka fler [magiska konstanter som finns i PHP](http://php.net/manual/en/language.constants.predefined.php).



PHP korta taggar, "short tags" {#short-tags}
-----------------------

Det finns flera varianter på PHP-taggar. Du har kanske noterat att jag mixar två varianter.

```php
<?php $title = "Titel på min nya sida"; ?> <!-- Den "vanliga" PHP-taggen  -->

<?= $title ?>  <!-- Den korta varianten som är samma sak som <?php echo $title; ?> -->
```

Den korta varianten lämpar sig för användning tillsammans med HTML-kod. Det är en kortare variant för att skriva `<?php echo $title; ?>`. Du sparar ett par tecken och koden blir lättare att läsa.

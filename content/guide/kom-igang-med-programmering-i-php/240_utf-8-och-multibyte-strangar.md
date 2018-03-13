---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
UTF-8 och multibyte strängar
=======================

När du jobbar med multibyte-strängar, och teckenkodning enligt UTF-8, så finns en speciell del i manualen som beskriver ["Multibyte String"](http://php.net/manual/en/book.mbstring.php) och de funktioner som finns tillgängliga. Ofta föregås dessa funktioner av `mb_`. Det är numer nästan standard att enbart hantera UTF-8 och multibyte men det finns fortfarande många webbplatser och applikationer som inte hanterar UTF-8. Se till att du har läst översikten av tillgängliga [funktioner för multibyte strängar](http://php.net/manual/en/ref.mbstring.php).

Ett enkelt sätt att visa på skillnaden mellan multibyte strängar och icke multibyte, tex ISO-8859-1, är att räkna hur lång strängen "åäö" är. Om teckenkodningen är IS-O8859-1 så är det enkelt, alla ser att strängen innehåller tre tecken och det är också svaret som funktionen `strlen('åäö')` skulle ge. Här är kod så att du kan testa det själv.

```php
<!doctype html>
<html lang="sv"> 
<head>
<meta charset="iso-8859-1"/>
<title>php20</title>
</head>
<body>
<h1>Hur lång är en sträng, strlen('åäö') i ISO-8859-1</h1>

<p>Teckenkodningen på denna filen (1) och på webbsidan (2) är ISO-8859-1.</p>

<p>Längden på strängen 'åäö' är strlen('åäö') = <?=strlen('åäö')?> (skall vara 3).</p>
```

Gör en egen fil, se till att den sparas på disk med teckenkodning enligt ISO-8859-1, öppna den sedan i en webbläsare och resultatet skall bli den korrekta stränglängden på `åäö`.

[Testa exemplet här](kod-exempel/guiden-php-20/strangar/iso88591.php).


Men, när vi pratar UTF-8 och multibyte så blir svaret ett helt annat, `strlen('åäö')` ger svaret 6 när vi använder UTF-8 som teckenkodning. Det är för att det krävs två byten för att lagra dessa tecken. I multibyte strängar så används ett, två eller flera byten för att lagra ett tecken. Därför måste vi använda funktioner som är skräddarsydda till att hantera multibyte strängar. Funktionen `mb_strlen('åäö')` ger oss det förväntade svaret 3. Här är ett exempel som du kan testa och leka med.

```php
<!doctype html>
<html lang="sv"> 
<head>
<meta charset="utf-8"/>
<title>php20</title>
</head>
<body>
<h1>Hur lång är en sträng, strlen('åäö') i UTF-8</h1>

<p>Teckenkodningen på denna filen (1) och på webbsidan (2) är UTF-8. Den interna kodningen för PHP-installationen (3) är <?=mb_internal_encoding()?>.</p>

<p>För att vara säker på att PHP betraktar alla strängar som UTF-8 så sätter jag mb_internal_encoding('utf-8').</p>

<?php mb_internal_encoding('utf-8'); ?>

<p>PHP's interna kodning är nu: <?=mb_internal_encoding()?></p>

<p>Längden på strängen 'åäö' är strlen('åäö') = <?=strlen('åäö')?> (skall vara 6).</p>

<p>Längden på strängen 'åäö' är mb_strlen('åäö') = <?=mb_strlen('åäö')?> (skall vara 3).</p>
```

Lägg koden i en egen fil, spara filen med teckenkodning enligt UTF-8, öppna den i en webbläsare och se vad som händer.

[Testa min variant av exemplet här](kod-exempel/guiden-php-20/strangar/utf8nobom.php).

När det gäller hantering av UTF-8 och multibyte tecken krävs alltså lite mer hantering. Framförallt finns det `mb_` funktioner vi kan använda då det krävs att man tar hänsyn till multibyte-tecken. Men det krävs också att man har koll på vilken default encoding som PHP-installationen har för stränghantering. I exemplet sätter jag den explicit till att vara UTF-8. 

Teckenkodning kan vara jobbigt i början. Men när man fått ordning på det så är det inte så svårt. Det handlar i grund och botten om att datorprogram kan inte upptäcka vilken encoding man har på en sträng. Det går inte att gissa sig till vilken encoding som skall användas. Därför måste vi som programmerare ha koll, i varje programsekvens, att korrekt teckenkodning används. I vårt fall som webbprogrammerare innebär det följande:

1. Vilket format använder texteditorn för att spara filen?
2. Vilken teckenkodning säger webbsidan att den är i (`<meta charset/>`)?
3. Vilken teckenkodning använder PHP-installationen som default?

När vi kopplar in databaser så kan gäller även teckenkodning för databasen, hur data lagras i kolumnen. Det kan också vara vilken teckenkodning som används på kopplingen mellan PHP och databasmotorn. Det är många delar som kan krångla men tar man dem i ordning så brukar det gå bra. 

Övning ger färdighet. Börja med att få dessa båda exempel att fungera ovan, då har du kommit ett steg in i den underbara världen av teckenkodning.

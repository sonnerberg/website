---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Styla nuvarande länk i en navbar
=======================

Det mesta du skriver i PHP är ett *uttryck*, eller *[expression](http://php.net/manual/en/language.expressions.php)*, konstruktionerna `$a = 5` och `$a++` är exempel på uttryck. Ett uttryck är helt enkelt en liten byggstenar som formar ett större PHP-skript. Ett enkelt sätt att se på ett uttryck är att **ett uttryck har ett värde**.
  
Du kan utföra beräkningar med vanliga *[operatorer](http://php.net/manual/en/language.operators.php)* såsom `+ - / * =`. Detta är operatorer som jobbar med siffror. Det finns också operatorer för att jobba med strängar och mer komplexa variabler. 



Matematiska operatorer och *operator precedence* {#math-op}
-----------------------

Först ett exempel med [matematiska operatorer](http://php.net/manual/en/language.operators.arithmetic.php), det fungerar precis som i matematiken.

```php
<?php
echo (5 + 37) . "<br>";
echo (43 - 1) . "<br>";
echo (2 * 10 + 27 - 10 / 2) . "<br>";
echo (-42 * -1) . "<br>";
echo (9 % 5) . "<br>";
echo (5 % 3) . "<br>";
```

I vissa exempel kan det vara klurigt att se hur PHP väljer att räkna ut värdet på uttrycket. Men det är samma regler som gäller i matematiken. Det finns en viss förbestämd ordning, *operator precendece*, hur ett uttryck skall beräknas. Är man osäker på ordningen så använder man paranteser. Paranteser är bra för det underlättar också läsbarheten för den som tittar på din kod. Läs mer om [förbestämd ordning på Wikipedia](http://en.wikipedia.org/wiki/Order_of_operations) eller om [operator precedence fungerar i PHP](http://php.net/manual/en/language.operators.precedence.php).

[Testa exemplet här](kod-exempel/guiden-php-20/operatorer/matematiska.php).



Strängoperator för konkatenering {#strang-op}
-----------------------

I exemplet ovan använder vi punkt som är en strängoperator som adderar strängar, *konkatenerar*. Så här fungerar den.

```php
<?php
echo "<p>Ge mig ett slumpmässigt tal: " . rand() .  "<br><br>Ladda om sidan för att se ett nytt tal</p>";
```

Punkten är alltså en konkateneringsoperator för strängar.

[Testa exemplet här](kod-exempel/guiden-php-20/operatorer/konkatenering.php).



Tilldelningsoperator {#tilldelning-op}
-----------------------

När du vill använda tilldela ett värde till en variabel så använder du tilldelningsoperatorn `=`. Så här ser det ut.

```php
<?php
$a = 42;     // Tilldela talet 42 till en variabel

$a = $a + 7; // Värdet på variabeln $a + 7 tilldelas $a
$a += 7;     // Samma sak igen fast ett kortare sätt att skriva.

$a = $a - 7; // Värdet på variabeln $a - 7 tilldelas $a
$a -= 7;     // Samma sak igen fast ett kortare sätt att skriva.

$a = "<p>Det magiska talet är: " . $a;
$a .= "</p>";
echo $a;
```

[Testa exemplet här](kod-exempel/guiden-php-20/operatorer/tilldelning.php).



Operatorer för `++` och `--` {#inkrement-op}
-----------------------

Ibland har man en variabel och vill öka eller minska värdet med 1. Då kan man använda operatorer för inkrementering `++` eller dekrementering `--`. Du kan använda dem före eller efter en variabel. Så här fungerar det.


```php
<?php
$a = 42;

echo $a++ . "<br>";  // Skriv ut värdet på variabeln och öka det sedan med 1

echo --$a . "<br>";  // Skriv ut värdet på variabeln men minska det med 1 innan du tar dess värde.
```

Det är alltså **skillnad** på om du sätter operatorn innan eller efter variabeln. I första fallet så läses variabelns värde av innan den ökas. I det andra fallet så minskas variabelns värde innan det avläses och skrivs ut.

[Testa exemplet här](kod-exempel/guiden-php-20/operatorer/inkrement.php).



Operatorer för jämförelse {#jamforelse-op}
-----------------------

Operatorer för jämförelse är som i matematiken när du vill jämföra två tal. Du kan jämföra och se om talen är lika med varandra, om det ena talet är större eller mindre än det andra.

```php
<?php
$a = 42;
$b = 1337;

echo "<p>$a == $a<br>";
var_dump($a == $a); 

echo "<p>$a != $a<br>";
var_dump($a != $a); 

echo "<p>$b >= $a<br>";
var_dump($b >= $a);

echo "<p>$b < $a<br>";
var_dump($b <= $a); 
```

I PHP finns ett koncept som kallas *type juggling*. Det är när man jämför värden som enligt PHP är av olika typer. Det går bra att jämföra en sträng med en siffra, men resultatet är inte alltid uppenbart. De regler som ligger bakom går alltså att läsa om i begreppet [type juggling](http://php.net/manual/en/language.types.type-juggling.php). 

Ibland vill man undvika att PHP skall tolka och göra dessa "lösa" jämförelser, då använder man tre `===` istället för två `==`. Då görs en jämförelse både på värdet och på dess typ. Värdena är inte bara lika med varandra, de är identiska och har samma typ. Så här fungerar det.

```php
<?php
$a = 42;
$b = "42";
$c = "1337 små grisar";

echo "<p>$a === $a<br>";
var_dump($a); 
var_dump($a); 
var_dump($a === $a); 

echo "<p>$b !== $a<br>";
var_dump($b); 
var_dump($a); 
var_dump($b !== $a); 

echo "<p>$c > $a<br>";
var_dump($c); 
var_dump($a); 
var_dump($c > $a); 

echo "<p>$a + $b<br>";
var_dump($a); 
var_dump($b); 
var_dump($a + $b); 

echo "<p>$c + $a<br>";
var_dump($c); 
var_dump($a); 
var_dump($c + $a); 
```

[Testa exemplet här](kod-exempel/guiden-php-20/operatorer/jamforelse.php).

---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Kort if-sats med ternary operator
=======================

Det finns ett kortare sätt att skriva vissa if-satser. Sättet är egentligen en operator som kallas [ternary operator](http://php.net/manual/en/language.operators.comparison.php#language.operators.comparison.ternary). Det är en konstruktion som återfinns även i andra programmeringsspråk. Det är inte en konstruktion som ersätter alla if-satser, men i vissa fall är den behändig. Speciellt bra är den när man vill ge en variabel ett värde beroende på ett villkor. 

Så här fungerar principen för ternary operatorn.

```php
(villkor) ? (värde om villkoret är sant) : (värde om villkoret är falskt)
```

Här är ett vanligt exempel där du vill tilldela en variabel ett värde beroende på om en annan variabel är definierad eller ej. I exemplet vill vi tilldela variabeln `$a` värdet `$b + 1`, men bara om `$b` har ett värde, annars skall `$a` bli `null`.

```php
<?php
// Så här gör du med en if-sats
$a = null;
if(isset($b)) {
  $a = $b + 1;
}

// Så här gör du med ternary operatorn
$a = isset($b) ? $b + 1 : null; 
```

Som du ser så blir det mindre kod när du använder ternary operatorn i detta fallet. Det är ett smidigt sätt att tilldela variabler beroende på ett villkor.

Jag gjorde ett lite utökat exempelprogram för att visa hur ternary operatorn fungerar. [Testa mitt exempel här](kod-exempel/guiden-php-20/villkor/ternary.php).

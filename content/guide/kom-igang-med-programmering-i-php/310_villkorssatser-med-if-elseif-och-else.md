---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Villkorssatser med if, elseif och else
=======================

Villkorssatser med `if` är en del av det som kallas [kontrollstrukturer] i PHP. Det är programkonstruktioner som används för att styra exekveringen av ett program. Kika snabbt på översikten av de [kontrollstrukturer som finns i PHP](http://php.net/manual/en/language.control-structures.php).



if-satser {#if-satser}
-----------------------

Villkor och villkorsatser används för att exekvera olika programkod beroende på ett villkor. Villkoret kan vara enkelt som att testa om en variabel innehåller värder 42, eller mer komplext där man testar många olika variablers värden tillsammans med operatorer som AND (`&&`) och OR (`||`).

Låt oss kika på ett exempel med [`if`-satser](http://php.net/manual/en/control-structures.if.php), [`else`](http://php.net/manual/en/control-structures.else.php) och [`else if`](http://php.net/manual/en/control-structures.elseif.php).

```php
<?php

$a = 42;
$b = 1337;

if($a < $b) {
  echo "<p>$a is less than $b</p>";
}

if($a > $b) {
  echo "<p>$a is greater than $b</p>";
} 
else {
  echo "<p>$a is less than (or equal to) $b</p>";
}

if($a > $b) {
  echo "<p>$a is greater than $b</p>";
} 
else if($a == $b) {
  echo "<p>$a is equal to $b</p>";
} 
else {
  echo "<p>$a is indeed less than $b</p>";
}

if($a == 42 && $b == 1337) {
  echo "<p>$a = 42 OCH $b = 1337</p>"
}
else {
  echo "<p>Någon har mixtrat med filen och ändrat värdena i \$a och eller \$b. Bra gjort.";
}
```

Testa själv att skapa ett testprogram med ovan kod, Vad behöver du göra för att följande rad skall skrivas ut av programmet? Testa så att du får det att fungera.

> *Någon har mixtrat med filen och ändrat värdena i $a och eller $b. Bra gjort.*

[Testa mitt exempel här](kod-exempel/guiden-php-20/villkor/if.php).

Man kan skriva en if-sats utan att ha måsvingar runt den, förutsatt att det bara är en kodrad som skall exekveras inom if-satsen. Men det är god sed att alltid använda måsvingar oavsett. Så gör det.

```php
// Gör inte så här
if($a)
  echo "hej";

// Skriv alltid med måsvingar
if($a) {
  echo "hej";
}
```

Vill du läsa mer om hur man bör skriva sin kod så kan du läsa [artikeln om kodningsstandarder för webbprogrammeraren](kunskap/kodstandarder-for-webbprogrammeraren).

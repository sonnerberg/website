---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Villkorssatser med switch-case
=======================

Villkorssatsen [`switch-case`](http://php.net/manual/en/control-structures.switch.php) kan jämföras med en serie av if-satser. När det blir **många tester på ett och samma villkor** så är detta en konstruktion att föredra framför upprepade satser av `if`, `else if`. Koden blir mer läsbar och det är bra. Låt oss studera ett exempel.
  
```php
<?php
//$a = 42;
//$a = 1337;
$a = "Hello World";

// As if-statements
echo "<p>As if.</p>";
if($a == 42) {
  echo '<p>$a is equal to 42</p>';
} 
else if ($a == 1337) {
  echo '<p>$a is equal to 42</p>';
} 
else if ($a == "Hello World") {
  echo '<p>$a is equal to 42</p>';
} 
else {
  echo '<p>$a is NOT an known value.</p>';
}

// As switch/case
echo "<p>As switch.</p>";
switch($a) {
  case 42:
    echo '<p>$a is equal to 42</p>';
    break;
  
  case 1337:
    echo '<p>$a is equal to 42</p>';
    break;
    
  case "Hello World":
    echo '<p>$a is equal to 42</p>';
    break;
    
  default:
    echo '<p>$a is NOT an known value.</p>';
}
```

[Testa mitt exempel här](kod-exempel/guiden-php-20/villkor/switch.php).

Du är inte begränsad till en rad i varje `case:`, du kan skriva flera rader av kod i varje `case:`. Du kan använda måsvingar för att omsluta kodraderna i varje `case:`, men det är inget krav.

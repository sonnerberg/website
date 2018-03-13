---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Loopar med for och while
=======================

Det finns flera varianter av loop-konstruktioner i PHP. En loop-konstruktion används för att återupprepa exekveringen av ett och samma kodstycke ett visst antal gånger eller tills ett villkor är uppfyllt. Låt oss titta på loop-konstruktionerna [`while()`](http://php.net/manual/en/control-structures.while.php), [`do-while()`](http://php.net/manual/en/control-structures.do.while.php) och [`for()`](http://php.net/manual/en/control-structures.for.php). 

```php
<?php
echo "<p>Count to ten using a while-loop.</p>";
$i = 0;
while($i <= 10) {
  echo "$i<br>";
  $i++;
}

echo "<p>Count to ten using a do-while-loop.</p>";
$i = 0;
do {
  echo "$i<br>";
  $i++;
} while($i <= 10);

echo "<p>Count to ten using a for-loop.</p>";
for($i = 0; $i <= 10; $i++) {
  echo "$i<br>";
}
```

Du kan alltså göra samma sak med de olika loop-konstruktionerna, vilken du väljer är upp till dig. Efterhand kommer du att märka att de olika loop-konstruktionerna lämpar sig olika väl till olika uppgifter. Loopen `while` testar alltid villkoret innan den kör en runda medans `do-while` alltid gör en runda och testar villkoret i slutet av rundan. I loopen `for` kan du tilldela variabler i själva uttrycket och lämpar sig bra för loopar som skall utföras ett bestämt antal gånger. Lär dig alla tre konstruktionerna så är du på den säkra sidan.

[Testa mitt exempel här](kod-exempel/guiden-php-20/loop/while-for.php).

Det finns ytterligare en loop-konstruktion som heter [`foreach()`](http://php.net/manual/en/control-structures.foreach.php) som används för att loopa runt elementen i en array. Se exempel på denna loopen i [stycket om arrayer](#array-foreach).

---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Arrayer och arrayhantering
=======================

Arrayer är en kraftfull och användbar PHP-konstruktion. En array är en lista av värden. Varje värde kan ha en nyckel kopplad till sig.


bodyClass();


Valid pages in array, map to filename.

array i array.

foreach 

??

htmlentities

GET, querysträng
SERVER



Skapa, skriv ut och läs en array {#array-skrivut}
-----------------------

Du definierar och läser från en array på array på följande sätt:

```php
// En tom array
$a = array();  

// Läs ett värde från position 1 i arrayen, ger felmeddelande eftersom det inte finns något i position 0
echo "<i>Här kommer ett felmeddelande med flit!<i>";
echo "Position 1 i arrayen innehåller " . $a[1];

// Sätt värden i arrayen
$a[1] = 42;
$a['name'] = "Mumintrollet";


// En array med värden
$a = array("1337", 42, 13.37, true, false, null);

// Läs ett värde från position 1 i arrayen, ger 42
echo "Position 1 i arrayen innehåller " . $a[1];


// array med både värden och nycklar
$a = array(
  'answer'  => 42, 
  'name'    => "Mumintrollet",
  'elite'   => 1337, 
);

// Läs det värde som är kopplat till nyckeln 'name'
echo "Värdet som är kopplat till array-nyckeln 'name' är " . $a['name'];
```

Som du ser så räknas arrayens innehåll med start på 0 när du inte tilldelar en nyckel.

När man jobbar med arrayer så är det ibland bra att skriva ut hela dess innehåll. Man är kanske osäker på dess innehåll, struktur eller nycklar. Följande två sätt är bra för att skriva ut arrayer.

```php
<?php
echo "<pre>" . print_r($a, true) . "</pre>";
echo "<pre>" , var_dump($a) , "</pre>";
```

[Testa exemplet här](kod-exempel/guiden-php-20/array/array.php).

[INFO]
**Vilket språk skall man använda i kommentarer och variabelnamn?**

I guiden mixar jag svenska och engelska på kommentarer och variabelnamn. Normalt använder jag alltid engelska när jag skriver kod. Både i kommentarer och i variabelnamn. Alltid. Utan undantag.
[/INFO]



Arrayer och funktioner {#array-funktion}
-----------------------

Det finns inbyggda funktioner som gör det enkelt att jobba med arrayer. Här ser du exempel på ett par av dessa funktioner.

```php
<?php
$a = array(
  'answer'  => 42, 
  'name'    => "Mumintrollet",
  'elite'   => 1337, 
);

echo "<hr><p>Arrayen innehåller " . count($a) . " element.</p>";

ksort($a);
echo "<hr><p>Sortera arrayen baserat på nycklarna:<pre>" . print_r($a, true) . "</pre></p>";

shuffle($a);
echo "<hr><p>Kasta om värden i arrayen, ignorera nycklarna:<pre>" . print_r($a, true) . "</pre></p>";
```

[Testa exemplet här](kod-exempel/guiden-php-20/array/funktioner.php).

Läs mer om de [funktioner som finns för arrayer](http://php.net/manual/en/book.array.php). Testa några av dem, du behöver bli kompis med dem. Du kan spara mycket tid på att lära dig vilka funktioner som finns. Genom att använda funktionerna sparar du tid och slipper skriva egen kod.



Loopa runt alla element i en array {#array-foreach}
-----------------------

Med loop-konstruktionen `foreach()` kan du iterera, loopa, runt alla elementen i en array. Det finns två varianter där du väljer om du vill ta hänsyn till nycklarna eller ej.

```php
<?php
$a = array(
  'answer'  => 42, 
  'name'    => "Mumintrollet",
  'elite'   => 1337, 
);

foreach($a as $value) {
  echo "Arrayen innehåller värdet '$value'.<br>";
}

foreach($a as $key => $value) {
  echo "Värdet på nyckel '$key' är '$value'.<br>";
}
```

[Testa exemplet här](kod-exempel/guiden-php-20/array/foreach.php).

Läs om [loop-konstruktionen `foreach()` i manualen](http://php.net/manual/en/control-structures.foreach.php).

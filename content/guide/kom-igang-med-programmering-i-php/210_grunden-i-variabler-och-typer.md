---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Grunden i variabler och typer
=======================



Deklaration av variabler {#dekl-variabel}
-----------------------

En variabel i PHP föregås av ett dollar-tecken, `$`, som i `$val` eller `$text`. Variabelnamnet startar med en bokstav eller "underscore" `_` och följs sedan av en mix av bokstäver, siffror och `_`. Variabelnamn gör skillnad på stora och små bokstäver, det betyder att `$text` och `$Text` är två olika variabler.

En variabel kan defineras och användas utan att fördeklarera den med ett värde. Det är inget fel i sig, men det kan ställa till problem med odefinerade variabler. Gör det därför till en vana att alltid deklarera ett värde i dina variabler. Gör dem tomma om de skall vara tomma, du kan tilldela dem specialvärdet `NULL` som innebär att variabeln inte har ett värde, den är bara `NULL`.

```php
<?php
// En variabel, deklarerad men den har inget värde, 
// det rekommenderas att alltid ge variabeln ett värde eller null.
$var;

// Heltal som läggs i en variabel.
$heltal1 = 42;
$heltal2 = 1337;

// Flyttal med punkt för decimalerna.
$flyttal1 = 3.141592654;
$flyttal2 = 1.4142;

// Strängvariabeler omsluts av enkelfnutt '' eller dubbelfnutt "".
$text1 = "Jag kan 10 decimaler på pi: "; 
$text2 = "Roten ur 2 är: ";
$text3 = "Svaret på frågan om allting och universum?";
$text4 = "Elit ";

// boolska variabler har värdet true eller false.
$sant = true;
$falskt = false;

// Värdet null är ett specialvärde som innebär null, ingenting.
$inget = null;
?>
```



Att använda variablernas värde {#anvand-variabel}
-----------------------

När du har deklarerat variablerna kan du använda dem. Här är ett exempel där värdet på variablerna skrivs ut tillsammans med lite text.

```php
<?php
echo "<p>", $text1, $flyttal1, "</p>";    // Separated by ,
echo "<p>" . $text2 . $flyttal2 . "</p>"; // Concatinated with . 
echo "<p>$text3 $heltal1</p>";            // Print out variables within "
echo "<p>{$text4} {$heltal2}</p>";        // Separate variables within string with {}

// Notice that the values for false and null is not visible on the webpage.
echo "<p>Sant=$sant<br>falskt=$falskt<br>inget=$inget</p>";
?>
```

Som du ser så finns det olika varianter på att skriva ut variabler i en text. 


Variabler och typ {#typer}
-----------------------

En variabel är av en typ som bestäms av PHP. Det bestäms av variabelns värde. De enklare typerna som stöds är strängar och siffror (heltal eller flyttal). Det finns också boolska variabler som innehåller värdet sant eller falskt. Dessutom finns värdet `null`.

```php
<?php
echo "<pre>";
var_dump($heltal1);
var_dump($flyttal1);
var_dump($text1);
var_dump($sant);
var_dump($falskt);
var_dump($inget);
echo "</pre>";
?>
```

Funktionen `var_dump()` är en ypperlig funktion för felsökning. Den skriver ut variabelns innehåll och dess typ, så som det uppfattas av PHP.



Testsida för variabler och typer {#test}
-----------------------

Jag gjorde en [testsida för variabler och typer](kod-exempel/guiden-php-20/5/variables.php). Det är ett bra arbetssätt att alltid göra små testsidor så fort man får problem eller undrar hur något fungerar. Det är alltid lättare och snabbare att felsöka ett litet testprogram än ett större program, det är också lättare att be om hjälp om man kan referera till ett litet exempelprogram.

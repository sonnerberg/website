---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Inbyggda funktioner
=======================



Inledning {#inledning-6}
-----------------------

PHP har ett stort antal inbyggda funktioner som underlättar livet som PHP-programmerare. Finns det funktioner så använder man dem istället för att skriva egna. Det är viktigt att lära sig hur man slår upp och letar reda på funktioner. Manualens sökfunktionen hjälper dig på vägen.
  
Varje funktion har en egen sida i PHP-manualen, slå upp de två funktioner vi använt så här långt, [`echo()`](http://php.net/manual/en/function.echo.php) och [`var_dump()`](http://php.net/manual/en/function.var_dump.php), läs om dem och studera upplägget för manualsidan. Använda sökfunktionen på manualsidan för att hitta de funktioner du letar efter.
 
Det finns en stor mängd inbyggda funktioner, det finns funktioner för datum och tid, matematiska funktioner, funktioner för stränghantering, kryptering, funktioner för att hämta information från andra webbplatser, för att komma åt databaser och så vidare.



Matematiska funktioner {#matte-funktioner}
-----------------------

Vi tittar på den matematiska funktionen som beräknar kvadratroten ur ett tal, [`sqrt()`](http://php.net/manual/en/function.sqrt.php), samt funktionen som skriver ut talet PI, [`pi()`](http://php.net/manual/en/function.pi.php).

Så här kan det se ut när vi använder funktionerna.

```php
<?php
echo "<p>Talet PI är lika med: " . pi() . "</p>";
echo "<p>Kvadratroten ur talet 2 är lika med: " . sqrt(2) . "</p>";
?>
```

Kika på [översikten av de matematiska funktionerna](http://php.net/manual/en/ref.math.php) för att få en känsla för vilka funktioner som finns tillgängliga.
 


Funktioner för datum och tid {#datum-funk}
-----------------------

Det finns funktioner för datum och tid. Titta på funktionen [`date()`](http://php.net/manual/en/function.date.php) som hjälper dig att skriva ut dagens datum. Studera även funktionen [`time()`](http://php.net/manual/en/function.time.php) som ger dig antalet sekunder sedan den första januari 1970. 

Så här kan du använda funktionerna.

```php
<?php
echo "<p>Dagens datum och tid är nu " . date('r') . "</p>";
echo "<p>Så här många sekunder har det gått sedan den förste januari 1970: " . time() . "</p>";
?>
```

Kika på [översikten av funktioner för datum och tid](http://php.net/manual/en/ref.datetime.php) för att få en känsla för vilka funktioner som finns tillgängliga.



Funktioner för stränghantering {#strang-funk}
-----------------------

Det finns funktioner för bearbetning av strängar, det kan vara jämförelse, modifiera strängar och delsträngar, räkna antalet tecken i en sträng och så vidare.

Ett par av de vanligaste funktionerna är [`strlen()`](http://php.net/manual/en/function.strlen.php) som räknar antalet tecken i en sträng och [`strcmp()`](http://php.net/manual/en/function.strcmp.php) för att jämföra två strängar.

Det finns också funktioner som hjälper dig med kryptering och liknande funktioner. Två sådana funktioner är [`str_rot13()`](http://php.net/manual/en/function.str_rot13.php) och [`md5()`](http://php.net/manual/en/function.md5.php).

Så här kan det se ut när dessa funktioner används.

```php
<?php
echo "<p>Hur många tecken finns det i strängen 'Mumintrollet'? Svar: " . strlen('Mumintrollet') . "</p>";
echo "<p>Är strängen 'Hello' samma som 'hello'? Svar: </p>";
var_dump(strcmp('Hello', 'hello'));

echo "<p>Koda strängen 'moped' enligt ROT13: " . str_rot13('moped') . "</p>";
echo "<p>Hur ser en md5-hash av strängen 'MegaMic' ut? Svar: " . md5('MegaMic') . "</p>";
?>
```

När det gäller strängar så är det viktigt att ha koll på vilket teckenkodning man använder. När man hanterar unicode och UTF-8 så finns det varianter av funktionerna, precis så som jag använde funktionerna `strlen()` och [`mb_strlen()`](http://php.net/manual/en/function.mb_strlen.php), där prefixet `mb_` står för multibyte variant av funktionen. I de svenska tecknen för `åäö` består varje tecken av två byten i UTF-8, därför fungerar inte den vanliga funktionen `strlen()`, därför behövs det anpassade funktioner då man jobbar med Unicode och UTF-8.

Kika på [översikten av funktioner för stränghantering](http://php.net/manual/en/ref.strings.php) för att få en känsla för vilka funktioner som finns tillgängliga. Titta även på [översikten av funktioner för multibyte strängar](http://php.net/manual/en/ref.mbstring.php), det är bra att ha en uppfattning om att multibyte strängar kräver anpassade funktioner. 



Exempel för att testa inbyggda funktioner {#test-funk}
-----------------------

Testa mitt [kodexempel där jag använder inbyggda funktioner](kod-exempel/guiden-php-20/6/builtin.php). Pröva gärna ytterligare funktioner som du hittar. Öva dig i att läsa manualen så du kan använda funktionen utifrån som den beskrivs.

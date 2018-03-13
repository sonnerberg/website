---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Instruktioner och kommentarer
=======================



PHP starttag och sluttag {#php-taggar}
-----------------------

Man går in i "PHP-läge" med *starttaggen* `<?php`, därefter tolkas allt som PHP-kod. PHP-läget avslutas med en PHP *sluttag* `?>`. Därefter kan man skriva vanlig HTML-kod igen. På detta sätt kan man växla mellan HTML och PHP.

```php
<?php 

// Everything between the PHP tags is considered to be PHP-code.

?>
```


Instruktioner och semikolon {#instruktioner}
-----------------------

Det som finns mellan PHP-taggarna är *instruktioner*. Man kan ange flera instruktioner och separera dem med semikolon `;`. Ett annat ord för en instruktion är *uttryck* (på engelska blir det *statement*).

Här är ett exempel på PHP-kod fördelat på instruktioner som skriver ut en textsträng.

```php
<?php 
echo "<p>Hello World!</p>";
echo "<p>Hello PHP!</p>";
echo "<p>My name is Mikael...</p>";
?>
```



Kommentarer {#kommentarer}
-----------------------

Du kan ange *kommentarer* i din PHP-kod på ett antal olika sätt. Använd kommentarer för att dokumentera och strukturera din kod. Se följande exempel på ett par varianter för att ange kommentarer i PHP.


```php
 <?php
/* Here is a multi-line comment, just as i CSS or C/C++
second line of comment.
third line.
*/
echo "<p>Hello World!</p>"; // One line comment, comment to end of line
echo "<p>Hello PHP!</p>";
echo "<p>My name is Mikael...</p>"; # Comment as shell-style

// Another one liner comment.
echo "<p>Hello PHP again!</p>";

?>
```

Det finns alltså olika sätt att kommentera sin kod. PHP har också stöd för en kommentarstyp som kan hjälpa dig att bättre dokumentera din kod, denna kommentarstyp brukar kallas [PHPDoc](http://en.wikipedia.org/wiki/PHPDoc). Det är egentligen en variant av kommentaren `/* *` men mcyket mer kraftfull eftersom informationen i kommentaren går att använda för att skapa dokumentation av koden.

```php
 <?php
/** 
 * Here is a PHPDoc comment.
 *
 * @author Mikael Roos <me@mikaelroos.se>
 */
?>
```

Du kan alltså uppnå både struktur av din kod och bättre förståelse för den, genom att kommentera den. Använd kommentarer där det behövs, främst för din egen del. Bra kod är självdokumenterande tillsammans med kommentarerna.



Felsök med kommentarer {#felsok-kommentar}
-----------------------

Ett bra sätt att felsöka är att använda kommentarerna `/* */`. Med dem kan du kommentera bort stora delar av koden medans du felsöker. Säg att du får ett felmeddelande som du inte lyckas rätta, då kan du kommentera bort kod tills felmeddelandet försvinner. När det är borta så aktiverar du koden genom att ta bort kommentarerna. Gör du det stegvis så kan du felsöka och avgränsa felet till precis den rad där det inträffar. Det är en bra felsöknings-metod för fel som du inte lyckas rätta med hjälp av felmeddelandet enbart.



Testprogram med kommentarer {#test-kommentar}
-----------------------

Här är ett [testprogram med kommentarer i](kod-exempel/guiden-php-20/4/comments.php). Kika och se källkoden för programmet (på serversidan), kika sedan på den källkod som genererats, den som du ser när du högerkligar och visar källkod i webbläsaren. Kan de du skillnaden mellan serversidan och det som hamnar i webbläsaren?


[INFO]
**Ta bort sluttaggen `?>`**

När du har en fil med enbart PHP-kod så skall du inte avsluta den med PHP-sluttag. Du kan, och bör, ignorera sluttaggen. Använder man sluttaggen så måste man se till att det inte finns några tomma rader eller tecken efter den, annars får man problem när man använder sessioner.

Det rekommenderas därför, att inte använda sluttaggen i de filer där du enbart har PHP-kod.
[/INFO]

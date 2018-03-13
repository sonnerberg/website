---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Strängar och stränghantering
=======================



Enkelfnuttar, dubbelfnuttar och heredoc {#fnuttar}
-----------------------

I PHP blir det en del hantering av [strängar](http://php.net/manual/en/language.types.string.php). Strängar omsluts av [enkelfnuttar](http://php.net/manual/en/language.types.string.php#language.types.string.syntax.single) och [dubbelfnuttar](http://php.net/manual/en/language.types.string.php#language.types.string.syntax.double). Skillnaden mellan de två varianterna är att variabler expanderar när de står inom dubbelfnuttar men *inte* när de finns inom enkelfnuttar. Behöver du escapa ett specialtecken så sätter du en backslash framför tecknet. Du kan ha en sträng som sträcker sig över flera rader och det finns en specialkonstruktion för strängar som kallas [heredoc](http://php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc) där allt betraktas som en sträng tills ett avslutande token. Låt oss se på ett par olika sätt att hantera strängar och skriva ut dem.
  

```php
<?php
$tal = 1337;

// Enkel fnutt
$str01 = '<p>En enkel sträng inom "enkelfnuttar" med en variabel som INTE expanderas till sitt värde $tal.</p>';
$str02 = '<p>En
sträng inom 
enkelfnuttar (\') som sträcker sig över flera rader.
Men variabler såsom \$tal ($tal) expanderas inte till sitt värde.
</p>';

// Dubbel fnutt
$str11 = "<p>En enkel sträng inom 'dubbelfnuttar' med en variabel som expanderas till sitt värde $tal.</p>";
$str12 = "<p>En
sträng inom 
dubbelfnuttar (\") som sträcker sig över flera rader.
Här expanderas variabler såsom \$tal ($tal) till sitt värde.
</p>";

$str21 = <<<EOD
<p>Här kan man skriva text tills slutmarkören EOD dyker upp. Men det är oerhört viktigt att slutmarkören står ensam på raden och att den inte finns tomma tecken, som mellanslag eller tabbar, varken före eller efter slutmarkören. <b>Kom ihåg det!</b> Slutmarkör och tomma tecken ger dig problem.

<p>Variabler expanderar till sitt rätta värde och \$tal = $tal.
EOD;

// Ouput
echo <<<EOD
$str01
$str11
<hr>
<pre>$str02</pre>
$str02
<hr>
<pre>$str12</pre>
$str12
<hr>
<pre>$str21</pre>
$str21;
EOD;
```

[Testa exemplet här](kod-exempel/guiden-php-20/strangar/strangar.php).

Det finns en mängd [funktioner för att jobba med strängar](http://php.net/manual/en/ref.strings.php). Det är bra att ha en god översikt över dem, så du vet var de finns när du behöver dem. Tidigare i denna guiden såg du ett par [exempel på hur man använder strängfunktioner](#strang-funk).

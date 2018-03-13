---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Alternativ syntax för kontrollstrukturer
=======================

I ovanstående exempel med villkorssatser och loopar så används den normala syntaxen för kontrollstrukturer där blocken omsluts med måsvingar `{}`. Det är samma syntax som en C eller C++ programmerare är van vid. Det finns också en [alternativ syntax](http://php.net/manual/en/control-structures.alternative-syntax.php) som kan användas. Den alternativa syntaxen kan bibehålla läsbarheten i koden, även när man blandar PHP och HTML. Skriver man ren PHP-kod så finns det ingen anledning att använda den alternativa syntaxen.

**Exempel på alternativ syntax för `if`.**

```php
<?php
$a = 42;
//$a = 1337;
?>

<?php if($a == 42): ?>
  <p>Jag har svaret på frågan om allting.</p>
<?php elseif($a == 1337): ?>
  <p>Jag är ett pro!</p>
<?php endif; ?>
```

Som du kan se så byts måsvingarna ut mot ett kolon `:`. Det är en liten ändring men när man är i en fil som i huvudsak är HTML-kod och vill blanda upp den med lite PHP-sekvenser, då är faktiskt denna alternativa syntax att föredra.

**Exempel på alternativ syntax med `foreach`.**

```php
<?php
$b = array(
  'Namn' => 'Mumitrollet',
  'Bor'  => 'Mumindalen',
);
?>

<p>Nedan tabell visar namn och adressdetaljer.</p>
<table>

<?php foreach($b as $key => $val): ?>
  <tr>
    <th><?=$key?></th>
    <td><?=$val?></td>
  </tr>
<?php endforeach; ?>

</table>
```

[Testa mitt exempel här](kod-exempel/guiden-php-20/alternative/alternative.php). Studera min källkod för exemplet och se vad du anser om kodens struktur och om den alternativa syntaxen gör HTML-delen av koden mer läsbar.

Det är god programmeringssed att försöka separera HTML och PHP så mycket det går. En fil som innehåller en blandning av traditionell PHP-kod, uppblandad med HTML, blir snabbt oöverskådlig. Jag försöker följa ett par enkla regler när jag skriver min kod.

1. Är det bara PHP-kod så skriver jag PHP-kod som vilket programmeringsspråk som helst. I en sådan fil undviker jag HTML-kod och HTML-sekvenser.
2. Är det blandat HTML och PHP så utgår jag från HTML som struktur och använder shorttags och alternativ struktur för att minimera PHP-inslagen. Filen skall vara läsbar som en HTML-kod och innehålla utskrifter av variabler och loopar.
3. Krävs det ett inslag av PHP-kod i den blandade HTML/PHP-filen så lägger jag det stycket överst i filen och lagrar undan information i variabler som sedan skrivs ut längst ned i filen.

På dessa sätt får jag en god grundstruktur som fungerar för mig och som ger läsbar kod.

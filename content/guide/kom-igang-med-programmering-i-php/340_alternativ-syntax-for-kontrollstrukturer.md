---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Alternativ syntax för kontrollstrukturer
=======================

Det finns en alternativ syntax för hur man skriver kontrollstrukturer. Den variant vi sett hittills är lämpad för när man skriver PHP som ett vanligt programmeringsspråk. Men när man blandar HTML-kod och PHP-kod, vilket händer när man skriver kod i vyer, template-filer, så kan den alternativa syntaxen vara att föredra, den passar bättre ihop med HTML.



Varför alternativ struktur? {#varfor}
------------------------

När PHP skapades så var tanken att vara ett skriptspråk för att ge dynamik till HTML och webbsidor. Tanken var att blanda PHP-kod med HTML-kod. Numer är PHP ett vanligt traditionellt programmeringsspråk som också används som skript/templatespråk för HTML och webbsidor.

Någonstans i den logiken finns anledningen till att det kan vara bra att ha två olika sätt att skriva koden på.

Låt oss se hur vi kan använda den alternativa strukturen i våre vyer, i våra template-filer, där vi mixar HTML och PHP.

Bara en not innan vi fortsätter, man vill helst inte mixa kod av olika syften, man vill dela upp saker så att "var sak har sin plats" och inte blandas ihop. När man blandar kod av olika typer blir det lätt rörigt. Speciellt i webbsammanhang där vi utan problem kan skriva både HTML, CSS, PHP och JavaScript i en och samma fil. Det blir lätt rörigt det.



Vad är en vy, en template fil? {#templatefil}
------------------------

En fil som likt `header.php` och `footer.php` har till syfte att generera den resulterande webbsidan, kan vi också kalla templatefiler. Det kan hjälpa oss att tydliggöra deras syften.

En god filstruktur kan vara att spara den typen av filer i en underkatalog `view/`. Det är lite med tanke på framtiden, när vi senare programmerar i störra ramverk så kommer denna typen av filer att namnges som template-filer och ofta lagras i kataloger som döps till `view/`.

Men, innan vi går vidare så kan vi se hur de alternativa strukturerna ser ut.



Short echo tag {#short-echo-tag}
------------------------

Vi börjar med en variant som egentligen inte är en kontrollstruktur, det är bara en variant av hur man kan kan skriva ut ett värde i en template fil.

I exemplet använder vi filen `header.php` och vi skiver ut variabeln `$title` som sidans titel.

Först skriver vi ut variabeln som en vanlig php-konstruktion.

```php
<!doctype html>
<html lang="en">
<title><?php echo $title ?></title>
```

Det är alltså konstruktionen `<?php echo $title ?>` som skriver ut sidans titel inom html elementet `<title>`.

Med en short echo tag kan vi få ned koden lite genom att skriva `<?= $echo ?>` som ett alternativ till `<?php echo $title ?>`.

Koden i templatefilen `header.php` ser alltså ut så här.

```php
<!doctype html>
<html lang="en">
<title><?= $title ?></title>
```

Man kan tycka att det är små saker, men när kodbasen växer så är det små saker som kan göra att koden blir lättläst.



Alternativa kontrollstrukturer {#altstruktur}
------------------------

Det finns alternativa kontrollstrukturer för if, switch, while, do while och for. De ser ut så här.

Först en if-sats som skriver ut sidans titel, förutsatt att `$title` har ett värde.

```php
<title>
<?php if ($title) : ?>
    <?= $title ?>
<?php else : ?>
    No title was defined.
<?php endif; ?>
</title>
```

Den alternativa strukturen ger alltså en möjlighet att blanda html och php på ett någorlunda läsbart sätt.

Om vi skriver en while loop med den alternativa syntaxen så kan det se ut så här.

```php
<?php while ($number <= 10) : ?>
    <p><?= $number++ ?></p>
<?php endwhile; ?>
```

Ovan loop räknar till 10 och skriver ut varje siffra inom ett html element.



Mer {#mer}
------------------------

Kika gärna i manualen om [alternativ syntax för kontrollstrukturer](http://php.net/manual/en/control-structures.alternative-syntax.php).

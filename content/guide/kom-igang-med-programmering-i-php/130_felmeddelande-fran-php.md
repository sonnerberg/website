---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Felmeddelanden från PHP
=======================

Låt oss se hur vi sätter på felmeddelanden så att de visas. Vi skapar en mallsida som vi kan använda för våra testprogram.



En mall för testprogram {#mall}
-----------------------

Skapa en ny fil som du döper till `template.php` och fyll den med följande innehåll.

```php
<pre>
<?php

$sum = 1 + 1;

echo "Hello World\n";
echo "\n";
echo "Sum of 1 + 1 is: $sum\n";

?>
</pre>
```

Om du kör koden ovan så kan din webbsida se ut så här.

[FIGURE src=image/snapht18/template-php.png?w=w3 caption="En mallsida med ett testprogram."]

Tanken med strukturen ovan är att skriva ut allt inom html-elementet `<pre>` som ger förformatterad text och som tar hänsyn till radbrytningen `\n`. Det gör att vi slipper blanda in allt för mycket html-element i vårt kodande.



Sätt på felutskrifter {#felutskrift}
-----------------------

Det första vi gör är att se till att php visar felmeddelande när vi skriver felaktig kod.

Om felmeddelanden skall visas är en inställning i webbserverns konfiguration för php. Vissa delar av den kan vi påverka direkt i vårt skript. På följande sätt kan vi slå på utskrifter av felmeddelanden. Uppdatera din `template.php` så att följande kod finns överst i filen.

```php
<?php
error_reporting(-1);              // Report all type of errors
ini_set("display_errors", 1);     // Display all errors 
?>
```

Det första raden är en php-funktion som anropas för att göra en inställning om att alla typer av felmeddelande skall visas. Du kan slå upp funktionen [`error_reporting()`](http://php.net/manual/en/function.error-reporting.php) i manualen för att se vad den gör.

Du kommer ihåg att manualen är din bästa vän? Lär dig hantera den. Alla funktioner beskrivs på samma sätt och när du lärt dig uppbyggnaden så ligger hela språket öppet för dig att lära.

Den andra raden anropar en funktion `ini_set()` som ber PHP att skriva ut felmeddelanden och inte dölja dem. I vissa installationer av webbserver och php så är standardinställningen att inte visa felmeddelanden. Det är en bra inställning för system som är i drift, men inte så bra när man utvecklar eller vill lära sig. I produktionssystem vill vi inte att felmeddelanden skall visas, men när vi utvecklar så behöver vi se dem.

Nu bör felmeddelande visas i all sin tydlighet.



Provocera fram ett felmeddelande {#provocera}
-----------------------

Du kan nu tvinga fram ett felmeddelande genom att lägga till en php-rad enligt följande.

```php
echo $unknown;
```

Min kompletta testfil `unknown.php` ser ut så här.

```php
<?php
error_reporting(-1);              // Report all type of errors
ini_set("display_errors", 1);     // Display all errors 
?>

<pre>
<?php
echo $unknown;
?>
</pre>
```

Koden ovan försöker alltså skriva ut en variabel som inte är definierad, den finns inte. Det skall ge ett felmeddelande.

Resultatet blir så här när man kör den i webbläsaren.

[FIGURE src=image/snapht18/unknown.png?w=w3 caption="Felmeddelande som visar när man använder en variabel som inte är definierad."]

Exakt hur felmeddelandet skrivs ut kan skilja beroende på hur din webbläsare är konfigurerad.



Exempelprogram med felutskrifter {#felutskrifter}
-----------------------

Typer av felmeddelanden, NOTICE, WARNING, ERROR?



Jag gjorde ett exempelprogram för att visa hur felmeddelanden kan se ut. Pröva [mitt testprogram med felmeddelande](kod-exempel/guiden-php-20/3/error.php).

Så här kan det se ut när du kör det.

[FIGURE src=/img/snapshot/guiden-php20-felmeddelande.png caption="Vanliga felmeddelande i PHP av typen NOTICE och WARNING."]

Följande felmeddelande visas, se hur de säger vad felet är och att de hänvisar till raden där felet finns.

 > Notice: Undefined variable: var in /usr/home/mos/htdocs/dbwebb.se/kod-exempel/guiden-php-20/3/error.php on line 18

Felet säger att vi har en odefinerad variabel. I detta fallet är det en variabel som jag läser värdet på, men variabeln har inte tilldelats något värde.

 > Notice: Use of undefined constant I_AM_NOT_DEFINED - assumed 'I_AM_NOT_DEFINED' in /usr/home/mos/htdocs/dbwebb.se/kod-exempel/guiden-php-20/3/error.php on line 22

Felet säger att vi använder en odefinerad konstant, en konstant som inte har definerats.

 > Warning: floor() expects exactly 1 parameter, 0 given in /usr/home/mos/htdocs/dbwebb.se/kod-exempel/guiden-php-20/3/error.php on line 26

Här försöker jag anropa en funktion `floor()` men jag missar att skicka med ett argument, därav varningen.

Öva dig i att läsa felmeddelandena, de innehåller alla ledtrådar du behöver för att rätta till dem, de säger vilken fil och radnummer som du skall börja leta på. Det är en övningssak att rätta felen när de dyker upp, **börja alltid med det översta felet och rätta det först**. Ibland är en del av resterande fel så kallade följdfel, de beror av det första felet och försvinner när du rättat det.
  

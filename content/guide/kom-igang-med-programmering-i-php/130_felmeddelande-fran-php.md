---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Felmeddelanden från PHP
=======================



Sätt på felutskrifter {#felutskrift}
-----------------------

Innan vi skriver mer PHP-kod så är det bäst att sätta på utskriften av felmeddelanden. Utan felmeddelande blir det svårt att koda PHP. Lägg följande kod överst i din sida `mall.php`.

*Kod för att sätta på visning av felmeddelande.*

```php
<?php
error_reporting(-1);              // Report all type of errors
ini_set('display_errors', 1);     // Display all errors 
ini_set('output_buffering', 0);   // Do not buffer outputs, write directly
?>
```

Det första raden är en PHP-funktion som säger att alla typer av felmeddelande skall visas. Slå upp funktionen [`error_reporting()` i manualen](http://php.net/manual/en/function.error-reporting.php). Du kommer ihåg att manualen är din bästa vän? Lär dig hantera den. Alla funktioner beskrivs på samma sätt och när du lärt dig uppbyggnaden så ligger hela språket öppet för dig att lära.

Den andra raden anropar en funktion som ber PHP att skriva ut felmeddelanden och inte dölja dem. I vissa installationer (MAMP) så är standardinställningen att inte visa felmeddelanden. Det är en bra inställning för system som är i drift, men inte så bra när man utvecklar eller vill lära sig.

Den tredje raden säger till PHP att inte buffra svaret (lagra informationen och skriva ut senare) utan skriva ut delarna av resultatsidan  så fort som möjligt. En del installationer har buffrad utskrivning som på, det kan undvika ett par problem, men, när du kommer till en server som inte buffrar utskriften så dyker dessa problem upp. Det är bättre att alltid ha koll på felen så att de inte dyker upp när du laddar upp ditt program på en annan server.

Du kan pröva min uppdaterade [`mall.php` med stöd för felutskrifter](kod-exempel/guiden-php-20/3/mall.php) och se var jag lade koden genom att studera sidans källkod.



Exempelprogram med felutskrifter {#felutskrifter}
-----------------------

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
  

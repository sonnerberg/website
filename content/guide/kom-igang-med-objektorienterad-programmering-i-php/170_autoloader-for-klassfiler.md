---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Autoload för klassfiler
==================================

När antalet klasser växer blir det till slut krångligt att inkludera alla klassfilerna, i rätt ordning, där de behövs. Med hjälp av PHP's [automatiska laddning av klassfiler](http://php.net/manual/en/language.oop5.autoload.php) så blir det mycket lättare, och dessutom snyggare kod.



###Om autoload {#omautoload}

Autoload är en funktion som vi själva skriver och som anropas första gången som ett objekt skapas av en klass. Tanken är då att funktionen laddar in klassfilen, så att vi slipper hantera inkluderingen av klassfilerna. Autoload har alltså koll på var klassfilerna finns någonstans och inkluderar dem vid behov.

I PHP finns det en variant där man skapar funktionen [`__autoload()`](http://php.net/manual/en/function.autoload.php), men ett bättre sätt är att använda [`spl_autoload_register()`](http://php.net/manual/en/function.spl-autoload-register.php).

Fördelen med spl_autoload_register är att man kan ha flera funktioner för autoloading, det är bra när man använder någon annans kod som kan ha en annorlunda struktur för att lagra och namnge klassfilerna.



###En autoloader {#enautoloader}

Låt oss skapa en autoladdare för våra klassfiler, implementationen förutsätter att klassfilerna ligger i samma katalog som det anropande skriptet.

Lägg följande kod i filen `autoload.php`.

```php
<?php
/**
 * Autoloader for classes.
 *
 * @param string $class the name of the class.
 */
spl_autoload_register(function ($class) {
    $path = "{$class}.php";
    if (is_file($path)) {
        include($path);
    }
});
```

Konstruktionen är att jag bifogar en funktion som kan hitta den klassfil som efterfrågas, och inkludera den.



###Var inkludera autoloadern? {#includeauto}

I dina skript kan du nu ta bort alla require av klasserna och ersätta den med din autoloader.

Om du vill så kan du anropa autoloadern i din config.php.

Eller så inkluderar du den i varje testskript. Båda varianterna fungerar.



###Övning autoloader {#ovning-3}

Ta en kopia av ditt exempelprogram med histogrammet och skriv om det så att autoloadern används.

1. För att förstå hur autoloadern anropas så kan du lägga till en utskrift i den. Gör en `echo "Autoloading: $class<br>";` för att skriva ut klassens namn, varje gång autoloadern anropas.

Så här kan det se ut.

[FIGURE src=/image/snapvt17/oophp20-7.png?w=w2 caption="Autoloadern skriver ut klassernas namn."]

En autoloader är en väldigt viktig komponent i PHPs infrastruktur. Det finns en standard som heter [PSR-4](http://www.php-fig.org/psr/psr-4/) som anger hur autoloading skall fungera. Men vår hemmasnickrade autoloader gör ju också sitt jobb, i all enkelhet.

På PHP-FIGs hemsida finner du även standarder för hur vi skriver kod, i form av [PSR-1](http://www.php-fig.org/psr/psr-1/) och [PSR-2](http://www.php-fig.org/psr/psr-2/). Det är de kodstandarder som vi normalt använder då vi validerar vår kod med validatorer som phpcs och phpmd.

---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
En klass för en tärning
==================================


Jag behöver ett exempelprogram och känner för att göra en tärning. Det blir ett bra exempel på hur en klass kan byggas upp. Jag tänkte bygga upp den steg för steg så att den fungerar som ett exempel på olika objektorienterade konstruktioner i PHP.


###En tärningssida med PHP och HTML {#dicepage}

För att simulera en tärning så räcker det gott med följande traditionella kod som rullar en tärning sex gånger och visar upp resultatet.

Jag lägger fölande kod i filen `test_dice1.php`.

```php
<?php
require "config.php";
?><!doctype html>
<meta charset="utf-8">
<title>Tärning</title>
<h1>En tärning</h1>
<p>Tärningen kastas 6 gånger, här är resultatet.</p>

<?php
// To save the outcome of each dice roll
$rolls = [];

// Roll the dice
$times = 6;
for ($i = 0; $i < $times; $i++) {
  $rolls[] = rand(1, 6);
}

// Print out the results
$html = "<ul>";
foreach ($rolls as $val) {
  $html .= "<li>{$val}</li>";
}
$html .= "</ul>";
?>
<?= $html ?>
```

Koden skapar en HTML-sida steg för steg och blandar med PHP-kod som simulerar en tärning.

Om man kör exemplet kan man få följande resultat.

[FIGURE src=image/snapvt17/oophp20-3.png?w=w2 caption="Tärningen slås sex gånger, ladda om sidan för en ny runda."]

Så, det var grunden för en tärning.



###Skapa en tärningsklass {#diceclass}

Låt oss nu göra om delar av koden, till en klass, steg för steg. Vi ser i koden att vi har en array där vi lagrar alla tärningskast och en loop där vi kastar tärningen och slutligen skrivs resultatet ut. Nu är det fritt fram hur du kan organisera din kod för att göra den objektorienterad med klasser och objekt.

Jag gör så här, först en klass som jag döper till `Dice` och sparar i filen `Dice.php`.

```php
<?php
/**
 * A Dice class to play around with a dice.
 */
class Dice
{

  // Here comes properties & methods

}
```

Detta är grunden till klassen.


###Klass med properties och metoder {#diceprop}

Nu kan jag stoppa in arrayen som en medlemsvariabel och koden som kastar tärningen blir en metod. 

Jag uppdaterar min kod.

```php
class Dice
{
    /**
     * Properties
     */
    public $rolls = [];


    /**
     * Roll the dice
     *
     * @param integer $times number of times to roll the dice.
     *
     * @return void
     */
    public function roll($times)
    {
        $this->rolls = [];

        for ($i = 0; $i < $times; $i++) {
            $this->rolls[] = rand(1, 6);
        }
    }
}
```

När du är i en metod och vill peka ut en medlemsvariabel så använder du `$this` som är en referens till nuvarande objekt, det objekt som användes för att anropa metoden. Vi har alltså en medlemsvariabel `$rolls` och för att komma åt den i en metod så använder vi `$this->rolls`. Det är så det funkar.

Du kan läsa om medlemsvariabler, eller [properties](http://php.net/manual/en/language.oop5.properties.php), i manualen.



###Exempelprogram som använder Dice {#usedice}

Så, det får räcka, jag tar en kopia av mitt gamla exempelprogram och skriver om det så att det använder klassen istället. Jag sparar det som `test_Dice2.php`.

Poängen är att skapa ett objekt av klassen och använda det. Så här ser min uppdatering ut.

```php
<?php
require "config.php";
require "Dice.php";
?><!doctype html>
<meta charset="utf-8">
<title>Tärning</title>
<h1>En tärning</h1>
<p>Tärningen kastas 6 gånger, här är resultatet.</p>

<?php
// Create an instance of the class
$dice = new Dice();

// Roll the dice
$times = 6;
$dice->roll($times);
$rolls = $dice->rolls;

// Print out the results
$html = "<ul>";
foreach ($rolls as $val) {
  $html .= "<li>{$val}</li>";
}
$html .= "</ul>";
?>
<?= $html ?>
```

Kärnan i uppdateringen är att skapa ett objekt av klassen och använda det.

```php
// Create an instance of the class
$dice = new Dice();

// Roll the dice
$times = 6;
$dice->roll($times);
$rolls = $dice->rolls;
```

Utskriften av resultatet kunde jag återanvända. Det var bra.



###Summan av tärningsslagen {#dicetotal}

Visst vore det trevligt om tärningen själv kunde räkna ut summan av alla slagen? Det innebär att vi bygger ut klassen med en metod som gör beräkningen. 

Metoden `Dice::getTotal()` kan se ut så här.

```php
    /**
     * Get the total from the last roll(s).
     *
     * @return integer as sum of rolled dices.
     */
    public function getTotal()
    {
        return array_sum($this->rolls);
    }
```

Smidigt med inbyggda funktioner.

Visst kan jag lägga koden utanför klassen, men nu är tanken att tänka objektorienterat och kapsla in all kod som har med tärningen att göra. Jag får all kod som är relaterad till en tärning i en klass. Koden blir enkel att återanvända. Klasser är en bra struktur som underlättar återanvändning av kod.

Du kan nu uppdatera ditt testprogram för att skriva ut summan av alla tärningsskasten.

```php
<p>Summan av alla tärningar är: <?= $dice->getTotal() ?></p>
```

Resultatet kan se ut så här.

[FIGURE src=image/snapvt17/oophp20-4.png?w=w2 caption="Nu summeras alla tärningsslagen."]

Nu kan du grunderna med klasser och objekt och hur de används. Nu är du redo för en övning.



###Övning Dice {#ovning-1}

Fortsätt nu själv att bygga ut din klass. Här är ett par förslag på funktioner som gör exempelprogrammet lite mer avancerat.

1. Skicka in en parameter till sidan, via querystringen `?roll=6`, som säger hur många slag du skall slå.
1. Lägg in en metod i klassen som returnerar antalet slag som slagits.
1. Skriv ut hur många slags som gjordes.
1. Skriv ut summan och medelvärdet (ny metod) av alla tärningsslagen.

Så här kan det se ut.

[FIGURE src=image/snapvt17/oophp20-5.png?w=w2 caption="Tärningar med valfritt antal snittvärdet."]

Bra, nu kan du både skapa en klass, använda den och bygga ut den med nya metoder.

---
author: mos
category:
    - kurs webtec
revision:
    "2021-06-15": "(A, mos) Första utgåvan."
...
Programmera med PHP
===================================

Du skall träna dig på grunderna i PHP genom att utföra ett antal mindre programmeringsövningar.

Det handlar om grunder såsom problemlösning och programmering med variabler, if-satser, loopar, arrayer, funktioner och att dela upp koden i olika filer.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap om att programmera med PHP.

Du har PHP i din PATH och kan exekvera kommandot `php` i terminalen.

Du har installerat en utvecklingsmiljö med validatorer som testkör din kod via statisk kodanalys.



<!--
Genomgång {#genom}
------------------------

Här är en video som "pratar" dig igenom uppgiftens upplägg och visar hur du kommer igång.

[YOUTUBE src="gKzwQTG9eCI" width=700 caption="Kurs mvc kmom03 tisdagsgenomgång, del 3/3 uppgiften (Zoom med Mikael)."]
-->



Introduktion och förberedelse {#intro}
-----------------------

Uppgifterna löser du genom att skriva kod i filer som du exekverar via terminalen.

Spara alla filerna under `me/php`.

Du skall ha ett main-program och den koden sparar du i filen `main.php`. Main-programmet skriver ut menyn och läser input från användaren och utför sedan en uppgift.

Lösningen på varje uppgift skall kodas som en funktion med ett bestämt namn. Samtliga funktioner placeras i filen `src/functions.php` som inkluderas i `main.php`. När koden växer blir det troligen fler funktioner som delas upp i olika filer och då är det bra att samla dem i en underkatalog och `src` är ett vanligt namn på en sådan katalog.

Så här kan det se ut när de första menyvalen är implementerade.

[ASCIINEMA src="421936" caption="De första menyvalen är implementerade."]



### Strikta type i PHP {#strict}

Se till att alla dina filer inleds med att använda strikta typer.

```text
<?php

declare(strict_types=1);
```



### Konfigurationsfil och felutskrifter {#error}

Skapa en fil `config.php` och lägg dit följande kod som sätter på felutskrifter. Detta gör att det blir tydligt om något är fel i din kod. När man utvecklar sin kod vill man att dessa felmeddelanden syns. När man har levererat sin kod till "produktionsläge" vill man dock stänga av dem som en säkerhetsåtgärd.

Sätt på felutskrifter i `config.php`.

```php
error_reporting(-1);              // Report all type of errors
ini_set("display_errors", "1");   // Display all errors
```

Se till att denna filen inkluderas som den första filen i din `main.php`.



### DocBlock kommentarer {#docblock}

Ovanför varje funktion skall du skriva en DockBlock kommentar och ge en kort introduktion till vad funktionen gör. Dessa kommentarer gör att vi senare kan automatgenerera dokumentation för koden.

Det är mest lämpligt att använda engelska när man skriver kod och kommentarer.

```php
/**
 * Prints details about this program.
 */
function about() : void {
    // some code
}
```

När funktionerna växer kan man även dokumentera inkommande parametrar till funktionen, vad den returnerar och om den kastar exception.



### Utvecklingsmiljö med validatorer {#validate}

Du bör sedan tidigare ha installerat en utvecklingsmiljö för PHP under katalogen `me/` där du via composer kan köra verktyg för statisk kodvalidering.

Glöm inte att köra dessa verktyg kontinuerligt.

Denna uppgift skall passera följande verktyg.

* `composer phpcs`
* `composer phpmd`

Du kan köra båda verktygen direkt via `composer test`.

Du måste stå i katalogen `me/` när du kör ovan kommandon.



Uppgift 1: Ett menydrivet program i terminalen {#u1}
-----------------------

Skapa grunden för ditt menydrivna program. Följande menyval skall finnas.

```
1. Skriv ut detaljer om programmet
9. Avsluta
```

Om användaren skriver in `1` så skall programmet skriva ut en kort beskrivning av programmet samt vem som skrivit det. Koden för att utföra utskriften skall skrivas i en funktion `about()` som placeras i filen `functions.php`

Om användaren skriver in `9` så skall programmet avslutas via funktionen `exitProgram()` samt skriva ut ett avslutningsmeddelande.

När programmet startar skall du skriva ut en välkomsttext och en ascii-bild (välj själv motiv på bilden).

Om användaren skriver in ett val som inte finns så anropas en funktion `notValidChoice()` som skriver ut ett meddelande att det var ett felaktigt menyval.

När det valda menyvalet är utfört så visas menyn och ascii-bilden igen.

För tips, leta i manualen.

* [`readline()`](https://www.php.net/manual/en/function.readline.php)
* [`require()`](https://www.php.net/manual/en/function.require.php)



Uppgift 2: Detaljer om din PHP installation {#u2}
-----------------------

Om du använde if-sats i uppgift 1, så byt ut din if-sats till en switch-sats.

Lägg till menyvalet "2. Detaljer om PHP" som gör enligt följande.

* Skriv ut versionen av PHP.
* Skriv ut vilket operativsystem som ligger i botten av PHP-installationen.
* Sökväg till PHP binären.
* Visa värdet för konfigurationen av `display_errors` via `ini_get()`.
* Visa värdet för konfigurationen av `display_startup_errors` via `ini_get()`.

Döp funktionen till `printPhpVersion()`.

För tips, leta i manualen.

* [Predefined Constants](https://www.php.net/manual/en/reserved.constants.php)
* [`ini_get()`](https://www.php.net/manual/en/function.ini-get.php)



Uppgift 3: Tid och datum {#u3}
-----------------------

[WARNING]

**Arbete pågår**.

[/WARNING]

Lägg till menyvalet "3. Dagen tid och datum" som gör följande.

* Skriv ut dagens datum, enligt formatet ÅÅÅÅ-MM-DD.
* Skriv ut dagens veckodag på engelska.
* Skriv ut dagens datum och tid, enligt ISO 8601.
* Skriv ut dagens tid (svensk tidszon), enligt TT:MM:SS
* Skriv en dagens tid (tidszon i Los Angeles, USA), enligt TT:MM:SS

Döp funktionen till `printCurrentDateAndTime()`.

För tips, leta i manualen.

* [DateTime::format](https://www.php.net/manual/en/datetime.format.php)

Uppgift 4: Stränghantering {#u4}
-----------------------

Lägg till menyvalet "4. Stränghantering" som gör följande.

* Kolla ordet "skärgårdsö" med strlen() och med mb_strlen(). Skriv ut svaren separerade med komma och mellanslag.
* Skriv ut positionen för bokstaven "l" i meningen "Hello world!".
* Byt ut ordet "world" mot "Sweden" i meningen "Hello world!" och skriv ut den.
* Gör om meningen "Hello world!" till stora bokstäver och skriv ut.
* Dela upp meningen "Hello world!" i två strängar och skriv ut första strängen.

Döp funktionen till `printStringTests()`. Lägg gärna ordet och meningen i variabler.

För tips, leta i manualen.

* [strlen()](https://www.php.net/manual/en/function.strlen)
* [explode()](https://www.php.net/manual/en/function.explode.php)



Uppgift 5: Fibonaccitalföljd {#u5}
-----------------------

Skapa en funktion som använder Fibonaccital, som ser ut så här 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 etc. Räkna ut summan av alla udda tal under 1.000.000 i funktionen och returnera summan.
Skriv sedan ut svaret i menyn.

Lägg till menyvalet "5. Fibonaccital.

* Skriv ut talföljden upp till och med 55 samt summan av alla udda tal under 1.000.000 på en ny rad.

Döp funktionen till `fibonacci()`.



Uppgift 6: Arrayer med strängar {#u6}
-----------------------

Skapa en array med länderna Sverige, Norge och Danmark och kalla den `$countries`. Använd konstruktionen [].
Skapa ännu en array med städerna Stockholm, Oslo Köpenhamn och kalla den `$capitals`. Använd array().

Lägg till menyvalet "6. Arrayer med strängar" och gör följande.

* Skriv ut innehållet i $countries. Använd en for-sats.
* Skriv ut innehållet i första elementet i $countries och det fjärde. Du får en varning när du skriver ut det fjärde elementet för det finns inte fyra element i arrayen. Gör en enkel felhantering för arrayer; en if-else-sats som kollar antalet element i arrayen innan du skriver ut antingen fjärde elementet eller ett felmeddelande.
* Skapa en ny array `$atlas`, där första elementet ser ut så här: "Sverige - Stockholm", andra innehåller "Norge - Oslo" och så vidare. Utgå ifrån `$countries` och `$capitals`. Använd array_push()
Skriv ut arrayen `$atlas` med kommatecken och mellanslag mellan. Använd foreach och implode().
* Skapa en key/value array `$keyArray` där landet är key (nyckel) och huvudstaden value (värde). Skriv ut huvudstaden i Norge. Tips använd `$keyArray["Norge"]`. Lägg till array_key_exists() för att kontrollera att nyckeln "Norge" finns.
* Lägg till Finland och Helsingfors. Skriv ut vilket land som Helsingfors är huvudstad i.

Döp funktionen till `printStringArrays()`.

För tips, leta i manualen.

* [array_push()](https://www.php.net/manual/en/function.array-push.php)
* [implode()](https://www.php.net/manual/en/function.implode.php)



Uppgift 7: Arrayer med siffror {#u7}
-----------------------

Skapa en array med siffrorna [285, 11, 9.75, 9, 2216] och kalla den `$numbers1`.
Skapa ännu en array med siffrorna [324, 36, 20.02, 8, 4998, 0, 11] och kalla den `$numbers2`.

Lägg till menyvalet "7. Arrayer med siffror" och gör följande.

* Skriv ut medelvärdet för `$numbers1`, avrundat till 2 decimaler.
* Lägg till den minsta siffran från `$numbers1` först i `$numbers2` samt summan av det sista och första elementet i `$numbers` sist i `$numbers2`. Skriv ut `$numbers2` med " - " emellan.
* Sortera `$numbers2` i sjunkande (decending) ordning och skriv ut resultatet. Vilket metod skulle du använt om du hade haft en key/value array? Skriv ut det också.

Döp funktionen till `printNumberArrays()`.

För tips, leta i manualen.

* [array_sum()](https://www.php.net/manual/en/function.array-sum.php)
* [round()](https://www.php.net/manual/en/function.round.php)
* [array_unshift()](https://www.php.net/manual/en/function.array-unshift.php)



Uppgift 8: Filhantering {#u8}
-----------------------

Det finns två filer under katalogen files; sherlock.txt och serialized.txt. Skapa två variabler med filnamnen i och kalla dem `$file1` och `$file2`. Titta på innehållet i filerna.

Lägg till menyvalet "8. Filhantering" och gör följande.

* Kolla om filen `$file1` finns. Skriv ut "Filen files\sherlock.txt finns.". Använd print() och $file1 i strängen du skriver ut.
* Läs innehållet i sherlock.txt och lägg i en sträng. Skriv ut strängen.
* Läs innehållet i sherlock.txt från tecken 12 och 20 tecken framåt och lägg informationen i en sträng. Skriv ner strängen på en ny fil `test.txt` och skriv ut innehållet i filen `test.txt`.
* Gör unserialize på filen `$file2` (serialized.txt) och skriv ut innehållet.

Döp funktionen till `printFileTests()`.

För tips, leta i manualen.

* [file_get_contents()](https://www.php.net/manual/en/function.file-get-contents)
* [serialize()](https://www.php.net/manual/en/function.serialize.php)



Extrauppgift match()  {#u10}
---------------------

Byt ut din switch-sats i menyn till match().

För tips, leta i manualen.

* [`match()`](https://www.php.net/manual/en/control-structures.match.php)



Extrauppgift password  {#u12}
---------------------

Skapa en varibel som är ditt lösenord med innehållet "Hello2world!".

Lägg till menyvalet "A. Password" och gör följande.

* Beräkna md5 hash av din variabel och skriv ut den.
* Skapa en hash av ditt lösenord och verifiera det. Skriv ut "Lösenord är ok!" om verifieringen gick igenom.
* Här är en sträng "Pvaqreryyn, Ynql naq gur Genzc, Byq Lryyre, Gernfher Vfynaq, Gur Whatyr Obbx". Vad innehåller den för information? Skriv ut informationen. Tips: formatet är rot13.

Döp funktionen till `printPasswordTests()`.

För tips, leta i manualen.

* [`password_hash()`](https://www.php.net/manual/en/function.password-hash)



Extrauppgift datum och tid  {#u12}
---------------------

Lägg till menyvalet "B. Mer om datum och tid" och gör följande.

* Skapa ett DateTime objekt med dagens datum och skriv ut det på formatet "år-månad-dag timmar:minuter:sekunder".
* Vilken metod används för att sätta en tidszon? Skriv ut det.
* Skapa ett DateTime objekt med ett gammalt datum "2021-05-12 11:15:17", ta bort 2 månader och lägg till 3 timmar. Skriv ut resultatet.

Döp funktionen till `printDateAndTimeExtra()`.

För tips, leta i manualen.

* [`DateTime()`](https://www.php.net/manual/en/class.datetime.php)



<!-- Extrauppgift : Riskornen på schackbrädet {#u11}
-----------------------

Känner du till problemet "Riskornen på schackbrädet" (‘chessboard and rice grain problem’ på engelska)?

Tänk dig ett vanligt schackbräde och lägg ett riskorn på den första rutan. Sedan lägger du två riskorn på andra rutan, och därefter en fördubbling på varje ruta, det vill säga, fyra på tredje åtta på fjärde och så vidare. Hur många riskorn ligger det på schackbrädet när samtliga rutor fyllts med riskorn?

Lägg till menyvalet "C. Riskornen på schackbrädet" som gör följande.

* Skriv ut antalet riskorn. Lägg märke till att php inte är bra på att hantera stora tal.

Tips: Tänk 1 + 2*1 + .... etc. -->



Redovisning {#redovisa}
-----------------------

Besvara följande frågor i din redovisningstext.

* Berätta hur det gick att lösa uppgiften, var något extra svårt, lurigt, krångligt eller flöt det på smidigt?
* Är det något som du är extra nöjd med i ditt resultat från uppgifterna?



Publicera {#publicera}
-----------------------

Avsluta uppgiften så här.

1. Testa att din kod validerar genom att ställa dig i katalogen `me/` och köra dem via `composer test`.

1. Testa ditt resultat så att det passera de automatiska testerna med `dbwebb test php`.

1. När du är klar kan du publicera resultatet med `dbwebb publish php`.

---
author: mos
category:
    - php
    - phpunit
    - kursen oophp
revision:
    "2018-04-03": "(A, mos) Första utgåvan i samband med oophp version 2."
...
Kom igång med PHPUnit
==================================

[FIGURE src=image/snapvt18/phpunit-terminal.png?w=c5&a=0,64,70,0&cf class="right"]

Du skall komma igång med enhetstestning i PHP via verktyget PHPUnit. Det finns ett färdig exempel som du skall jobba igenom för att bekanta dig med strukturen, vilka filer som är inblandade och du skall skriva ditt allra första testfall.

Du skall skriva testklasser och tester som testar 100% av koden och du skall verifiera att all kod testas genom att studera kodtäckningen för din kompletta test suite.

<!--more-->

Så här kan det se ut när du utför uppgiften.

[FIGURE src=image/snapvt18/phpunit-terminal.png?w=w3 caption="Enhetstestning med PHPUnit via en Makefile."]

[FIGURE src=image/snapvt18/code-coverage-overview.png?w=w3 caption="Kodtäckning vid enhetstestning, en översikt av enheterna (klasserna)."]

[FIGURE src=image/snapvt18/code-coverage-detail.png?w=w3 caption="Detaljerad kodtäckning rad för rad i en enhet (klass)."]



Förkunskaper {#forkunskaper}
-----------------------

Du har installerat [PHPUnit](labbmiljo/phpunit) och [Xdebug](labbmiljo/xdebug).

Du har tillgång till kursrepot och exempelkoden som ligger under `example/phpunit`.



Introduktion och förberedelse {#intro}
-----------------------

Gå igenom följande steg för att förbereda dig inför samt jobba igenom större delen av uppgiften.

<!--
[YOUTUBE src="XXX" playlist="PLKtP9l5q3ce-LjAqv50bj_bCyYivKafPW" class=700 caption="Mikael visar hur du jobbar igenom övningen."]
-->



### Kopiera exempelkoden {#exempelkod}

Börja med att kopiera exempelkoden.

```text
# Ställ dig i rooten av kursrepot
rsync -av example/phpunit me/kmom03
```

Det kan se ut så här när katalogen är kopierad.

```text
$ tree me/kmom03/phpunit
me/kmom03/phpunit
├── Makefile
├── README.md
├── composer.json
├── htdocs
│   ├── config.php
│   └── index.php
├── src
│   └── Guess
│       ├── Guess.php
│       └── GuessException.php
└── test
    ├── Guess
    │   └── GuessTest.php
    └── config.php

5 directories, 9 files
```



### Läs och gör enligt README.md {#readme}

I katalogen finns en [README.md](https://github.com/dbwebb-se/oophp/tree/master/example/phpunit), läs den och utför de delar som där står, när du är klar har du nästan gjort hela uppgiften. Filen innehåller beskrivning av hur du kör de enhetstesterna som ligger i exemplet och visar grunderna i hur enhetstester fungerar tillsammans med PHPUnit.



### Vad testar enhetstester? {#vad-testa}

De enheter du testar är de klasser som finns i din src-katalog. I vårt fall är alltså enheten lika med klassen. Enhetstestning blir testning av våra klasser.

Tänk på att det finns en hel del kod som (normalt) inte omfattas av enhetstester. Det kan vara kod du skriver i frontkontroller, sidkontrollers, konfigurationsfiler och templatefiler för vyer. I en perfekt värld vill man testa all kod, men enhetstestning löser inte allt. 



### Bra struktur bland testklasserna {#struktur}

Ge dina testklasser namn som syftar på vad de testar. Ha gärna många testklasser som inte är så stora. I längden blir det enklare att ha koll på vad de olika testklasserna gör.

Skapa gärna katalogstrukturer om du har många testklasser.

Gör dina testmetoder små och låt dem bara testa en sak. Ge dem tydliga namn till vad de testar och lägg en kommentar ovanför som gör det enkelt för dig att i efterhand komma ihåg syftet med varje testmetod.

```php
/**
 * Construct object and verify that the object has the expected
 * properties. Use no arguments.
 */
public function testCreateObjectNoArguments()
{
    $guess = new Guess();
    $this->assertInstanceOf("\Mos\Guess\Guess", $guess);

    $res = $guess->tries();
    $exp = 6;
    $this->assertEquals($exp, $res);
}
```

När du gör negativa tester och framkallar exceptions, lägg dem i egna testklasser och döp dem till relevanta namn. Det är en bra idé att dela upp negativa tester och separera dem från övriga tester. Allt för att komma ihåg vad man har testat och inte, i ett senare skede.



### Använd dina egna klasser {#egna}

Du kan lösa uppgiften genom att använda den koden som bifogas. Det är en tillräcklig utmaning. Men du får gärna ta din egen kod från Guess och använda den som testobjekt istället.

Jag gissar att dina egna versioner av spelet (GET, POST, SESSION) delar koden för klasserna, det vill säga att spelkärnan finns i samma klasser som delas mellan index-filerna för GET, POST och SESSION. Oavsett vad, se om du kan göra alla dina klasser testbara. Förhoppningsvis innehåller inte dina klasser några spår av de globala variablerna `$_GET, $_POST, $_SESSION`, det gör dem svårare att testa. Den koden bör du lägga i index-filerna.

Om du vill ha mer kod att öva att skriva testfall mot så kan du använda de klasserna som rör tärningen, antingen från guiden eller från uppgiften om 100-spelet.

Skriv om koden för att göra den mer testbar? Om du stöter på saker i din egna kod som inte är testbara så kan du överväga att göra refaktorering på de delarna i din klass, eller iallafall allvarligt fundera över varför de delarna inte är testbara.




Krav {#krav}
-----------------------

1. Skriv testfall så att du når 100% kodtäckning, exklusive de kodrader som kastar exception.

1. Gör en ny testklass `test/Guess/GuessExceptionTest.php` för att testa att exception kastas. När du är klar bör du ha 100% kodtäckning på alla filer i src-katalogen.

1. När du är klar så gör du `make test` för att kontrollera att din test suite fungerar och sedan gör du en `dbwebb publish`.



Extrauppgift {#extra}
-----------------------

Gör följande extrauppgifter om du har tid och lust.

1. Använd din egen Guess-kod som bas för uppgiften.

1. Kopiera in klasserna för `Dice*` och skriv testfall för dem.



Tips från coachen {#tips}
-----------------------

**Lycka till och hojta till i forumet om du behöver hjälp!**

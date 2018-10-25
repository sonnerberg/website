---
author: mos
category:
    - labbmiljo
    - make
revision:
    "2018-10-25": (C, mos) Genomgång och smärre justeringar.
    "2016-10-28": (B, mos) Ändrade install --mode till -m på Mac.
    "2016-10-13": (A, mos) Första utgåvan.
...
Installera Composer för pakethantering med PHP
===================================

[FIGURE src=/image/snapvt16/logo-composer.png?w=c5 class="right"]

Vi skall installera verktyget Composer som är en pakethanterare för PHP.

Composer är ett kommandoradsprogram som låter dig installera paket och moduler som andra utvecklare har gjort och publicerat. Composer håller koll på vilka versioner som är installerade och att paketen installeras effektivt och kan hållas uppgraderade.


<!--more-->



Läs mer {#mer}
-------------------------------

Du kan läsa mer om [Composer på webbplatsen](https://getcomposer.org/).

Du kan se vilka [PHP-paket som finns publicerade på Packagist](https://packagist.org/).



Förutsättning {#pre}
-------------------------------

Du har [PHP i din path](labbmiljo/php-i-pathen).



Installera på Windows XAMPP {#windows}
-------------------------------

Denna instruktion är för dig som har Cygwin och XAMPP. Om du använder Windows 10 med Bash så följer du istället instruktionen för [Linux](#linux).

Öppna Cygwin. Gå till katalogen där din exekverbara PHP ligger.

```text
cd $( dirname $( which php ))
```

Hämta hem composer enligt de stegen som beskrivs i [Download Composer](https://getcomposer.org/download/).

Kontrollera att du har laddat ned filen.

```text
ls -l composer.phar
```

Provkör composer.

```text
php composer.phar --version
```

Då lägger vi till så att du kan köra composer som ett kommando, utan att behöva ange php framför. Vi gör det via två skript ([`composer`](https://gist.github.com/mosbth/ae5437cfe01d14b9707c) samt [`composer.bat`](https://gist.github.com/mosbth/bba3e71b5f86394a0d44)) som du kan hämta från GitHub.

```text
wget -O composer https://gist.githubusercontent.com/mosbth/ae5437cfe01d14b9707c/raw/
wget -O composer.bat https://gist.githubusercontent.com/mosbth/bba3e71b5f86394a0d44/raw/
chmod 755 composer
```

Kontrollera att filerna ligger på plats och har rätt rättigheter.

```text
$ ls -l composer*
-rwxr-xr-x+ 1 mikae mikae    1008 Oct 13 14:15 composer
-rwxrw-r--+ 1 mikae mikae     384 Oct 13 14:15 composer.bat
-rwxrwx---+ 1 mikae mikae 1704783 Oct 13 13:49 composer.phar
```

Dessa båda skript, som du nu laddat ned, gör så att du kan köra kommandot genom att bara ange kommandot `composer`, oavsett om du är i Cygwin (via `composer`) eller i `cmd.exe` (via `composer.bat`).

De båda filerna `composer` och `composer.bar` exekverar slutligen filen `composer.phar`.

Testa att det fungerar.

```text
composer --version
```



Installera på Mac OS {#macos}
-------------------------------

Följ instruktionen om hur man [laddar ned och installerar composer](https://getcomposer.org/download/).

När filen är nedladdad, gör följande.

Kontrollera att filen finns på plats.

```text
$ ls -l composer.phar 
-rwxr-xr-x 1 mos mos 1.7M Oct 13 14:33 composer.phar*
```

Provkör kommandot.

```text
php composer.phar --version
```

Bra, nu vet du att den nedladdade filen fungerar. Placera den nu i en katalog som ligger i din path. Nedan förutsätter att du har en egen katalog `$HOME/bin` som ligger i din PATH.

```bash
sudo install -m 0755 composer.phar $HOME/bin/composer
```

Verifiera att filen ligger på plats och att den går att köra.

```bash
ls -l $HOME/bin/composer
composer --version
```

Om det sista kommandot gick bra och visade nuvarande version för composer så är allt okey.



Installera på Linux och Windows 10 Bash {#linux}
-------------------------------

Följ instruktionen om hur man [laddar ned och installerar composer](https://getcomposer.org/download/).

När filen är nedladdad, gör följande.

Kontrollera att filen finns på plats.

```text
$ ls -l composer.phar 
-rwxr-xr-x 1 mos mos 1.7M Oct 13 14:33 composer.phar*
```

Provkör kommandot.

```text
php composer.phar --version
```

Bra, nu vet du att den nedladdade filen fungerar. Placera den nu i en katalog som ligger i din path.

```text
sudo install --mode=0755 composer.phar /usr/local/bin/composer
```

Verifiera att filen ligger på plats och att kommandot går att köra.

```text
ls -l /usr/local/bin/composer
composer --version
```

Om det sista kommandot gick bra och visade nuvarande version för composer så är allt okey.



Verifiera att Composer fungerar {#test}
-------------------------------

Följande två kommandon kan hjälpa dig att dubbelkolla vilken installation av composer som du använder.

```text
whereis composer
which composer
```

Kör följande för att se att composer fungerar.

```text
composer --version
composer
```



Bra att veta om Composer {#bra}
-------------------------------

Ibland får du ett meddelande om att uppdatera `composer`. Du kan hjälpa `composer` att uppdatera sig själv.

```text
composer selfupdate
```

Du kan göra fler saker med `composer`. Använd hjälptexten för att snabbt få en översikt av vad du kan göra.

```text
composer
```



Avslutningsvis {#avslutning}
------------------------------

Det finns en [forumtråd om Composer](t/5795), ställ dina frågor där och tipsa gärna om hur du använder det.

---
author: lew
revision:
    2019-04-16: (A, lew) Första utgåvan inför HT19.
...
Bash-script som testar serverns routes
===================================

Du skall skapa ett Bash-script som testar de olika routesen hos din server. Som hjälp använder vi programmet [curl](https://curl.haxx.se/) i scriptet. Du kan säkert redan ha det installerat, annars är det bara att installera det med pakethanteraren.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har genomfört uppgiften "[Webbserver i Docker](uppgift/webbserver-i-docker)".

Du har genomfört uppgiften "[Bash-script med argument options](uppgift/ett-bash-script-med-options-command-arguments)" från kursmoment 03.

Du har läst kurslitteraturen och skaffat dig grundläggande kunskaper om bash.



Introduktion {#intro}
-----------------------

Du ska skapa, likt förra kursmomentet, ett Bash script som med argument kan ge svar från din server. Du kan med andra ord återanvända en hel del från kursmoment 03.



Krav {#krav}
-----------------------

1. Skapa ett bash-script `client/client.bash` som kan ta emot options och argument. Anropas ditt script utan options eller argument, skall scriptet skriva ut att man kan få hjälp genom att använda `--help, -h`.

1. Ändra rättigheter för scriptet genom kommandot `chmod 755 client/client.bash`

1. Ditt script skall avslutas med korrekt exit värde.

1. Använd en main-funktion för att starta programmet.

1. Strukturera koden i olika funktioner.

1. Följande *options* ska fungera:

| Option                | Vad skall hända |
|-----------------------|-----------------|
| `-h, --help`          | Skriv ut en hjälptext om hur programmet används. |
| `-v, --version`       | Visar nuvarande version av programmet. |
| `-s, --save`          | Spara den returnerade datan till fil. Det ska fungera för alla argument.|


7. Följande *argument* ska fungera:

| Argument&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Vad skall hända |
|---------------------------|-----------------|
| `all`                     | anropa `/all`. |
| `names`                   | anropa `/names`.|
| `color <color>`           | anropa `color/<color>`. |
| `test <url>`        | Skriv ut information om serverns status, om den är nåbar eller ej. Om &lt;url&gt; är satt ska den anropas, annars localhost:port |



Validera ditt `client.bash` script genom att göra följande kommandon i kurskatalogen i terminalen.

```bash
# Flytta till kurskatalogen
$ dbwebb validate client
$ dbwebb publish client
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.  



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lycka till och hojta till i forumet om du behöver hjälp!

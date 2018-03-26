---
author: mos
category:
    - kurs oophp
    - anax
revision:
    "2018-03-19": "(A, mos) Första utgåvan."
...
Bygg en me-sida för oophp med Anax
===================================

Du skall skapa en me-sida för kursen oophp. Du får en mall, baserat på Anax, som du kan använda och du skall sedan gå in och redigera sidorna så att de passar dig i kursen.

Du skall göra ett Git-repo av din me-sida. När du är klar så publicerar du och taggar ditt repo på GitHub.

Allt eftersom kursen går så kommer du att fylla på innehåll i din me-sida.

Inledningsvis finns inga krav på att du behöver bemästra katalogstrukturen i Anax. Du kommer steg för steg att introduceras i strukturen som används. 

<!--more-->

Så här kan det se ut när det du har koll på mallen för me-sidan.

[FIGURE src=image/snapvt18/oophp-me.png?w=w3 caption="Mallen för me-sidan i oophp."]



Förkunskaper {#forkunskaper}
-----------------------

Du har tidigare (i design-kursen) sett den övergripande katalogstrukturen för ramverket Anax.

Du kan grunderna i Git och GitHub.

Du har PHP i din path och du har installerat composer.



Introduktion och förberedelse {#intro}
-----------------------

Gör följande steg för att förbereda dig för uppgiften.

Du kan se hur jag jobbar igenom stegen i videoserien "[En me-sida med Anax i kursen oophp](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_RQMga3qbZzvpzvH-gW3gv)".

[YOUTUBE src="p3RlMVjwhmE&t" list="PLKtP9l5q3ce_RQMga3qbZzvpzvH-gW3gv" width=700 caption="Videoserie som ger dig en introduktion till de olika delarna i redovisa-sidan."]



### Kopiera från example/redovisa {#kopiera}

Det finns en installation av Anax som är specifik för oophp-kursen och dess redovisningssida. Kopiera den och installera det som behövs med composer.

```text
# Stå i rooten av kursrepot
rsync -av example/redovisa me
cd me/redovisa
composer install
```

Nu kan du öppna en webbläsare och peka mot katalogen `redovisa/htdocs`.



### Make {#make}

Om du får problem med detta stycket så kan du hoppa över det, men gör ett foruminlägg så att det som "är sönder" kan lagas, du behöver det senare i kursen. Det kan finnas saker i Makefilen som skiljer sig mellan olika plattformar.

Dubbelkolla att du har Make installerat och att det fungerar.

Börja med att få en översikt över de kommandon du kan köra med make.

```text
make
```

Installera sedan en lokal utvecklingsmiljö i repot.

```text
make install
```

Du kan nu testa vilka verktyg som finns installerade via följande kommando.

```text
make check
```

Du kan testköra testsuiten som finns.

```text
make test
```

Du kommer använda kommandot make för att jobba med dina enhetstester, längre fram i kursen.



### Git & GitHub {#git}

Gör ett git-repo av katalogen.

```text
git init
git add .
git commit -m "First commit"
```

Gå till GitHub och skapa ett nytt repository dit du kan ladda upp git-repot.

Ladda upp ditt git-repo till GitHub (byt ut git@github.com:mosbth/oophpv4.git mot länken till ditt eget repo). Använd SSH-nycklar för att identifiera dig, det blir så mycket enklare att slippa skriva lösenord varje gång man laddar upp repot.

```text
git remote add origin git@github.com:mosbth/oophpv4.git
git push -u origin master
```

Nu har du publicerat din me-sida på GitHub.



### Publicera studentservern {#publicera}

Publicera till studentservern för att se att allt fungerar.

```text
dbwebb publish redovisa
```

Du behöver ändra sökvägarna i `htdocs/.htaccess`, annars får du 404 på länkar och 500 på bilderna. Det är samma struktur som fanns i design-kursen.

Glöm inte att det finns `dbwebb publishfast` och `dbwebb publishpure` som låter dig publicera snabbt och utan minifiering (nödvändigt vid felsökning). 



### Bekanta dig {#bekanta}

Bekanta dig med strukturen och vad som finns i ramverket.

Kolla in videoserien för en guidning i ramverkets struktur och filer.



Krav {#krav}
-----------------------

1. Uppdatera första sidan där du ger en presentation av dig tillsammans med en bild.

1. Uppdatera om-sidan där du skriver en rad om denna kursen samt uppdaterar de länkar som finns, så att de går till rätt ställen. Komplettera med en bild som du själv väljer.

1. Uppdatera redovisningssidan så att den blir som du vill, här samlas dina redovisningstexter för kursen.

1. Håll din navbar uppdaterad så man kan navigera mellan sidorna.

1. Uppdatera header och footer så de passar din personliga me-sida.

1. Styla sidan så som du finner bäst. Använd LESS/SASS/CSS, återanvänd kunskaper från design-kursen eller använd något ramverk liknande Bootstrap, välj själv.

1. När du är klar, kör `make test` för att köra en testsuite på ditt repo. Det gör inget om du får fel, men fråga gärna i forumet för att få rätt på eventuella problem. När man kör `make test` så bör det passera utan problem, men det är inget krav i nuläget.

1. Gör en `dbwebb publish redovisa` för att kolla att allt validerar och fungerar på studentservern.

1. Committa alla filer och lägg till en ny tagg (1.0.\*).

1. Pusha upp repot till GitHub, inklusive taggarna.



Extrauppgift {#extra}
-----------------------

Lös följande extrauppgifter om du har tid och lust.

1. Snygga till din me-sida lite extra med style. Det är alltid trevliga om det ser snyggt och ordningsamt ut.

1. Skapa en egen testsida för att leka runt med olika konstruktioner. Det kan vara bra att ha.



Tips från coachen {#tips}
-----------------------

Gör små commits och committa ofta, när du väl har din bas. Använd tydliga committ-meddelanden så att historiken ser bra ut.

Var försiktig att använda stora bilder, de tar mycket quota (begränsning av lagringsutrymme) från ditt konto på studentservern.

Lycka till och hojta till i forumet om du behöver hjälp!

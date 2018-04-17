---
author: mos
category:
    - php
    - anax
    - kursen oophp
revision:
    "2018-04-16": "(B, mos) Uppdaterade stycket om enhetstester."
    "2018-04-16": "(A, mos) Första utgåvan i samband med oophp version 4."
...
Bygg CRUD filmdatabas med MySQL
==================================

[FIGURE src=image/snapvt17/movie-paginate-1.png?w=c5&a=25,50,32,0&cf class="right"]

Du har ett färdigt exempel att utgå ifrån, exemplet innehåller kod som löser CRUD kring en filmdatabas. Din uppgift är att föra över den koden, refaktorera den, så att den passar in i ramverket kring din redovisa-sida.

Du skall lägga in koden som en del i din redovisa-sida och visa upp filmer, eller någon annan typ av produktliknande information, välj själv fokus för vad du vill visa upp.

<!--more-->

[WARNING]
**Utveckling pågår.**

Dokumentet är under bearbetning och ännu icke klart.

[/WARNING]

Så här ser exemplet ut som du har att utgå ifrån.

[FIGURE src=image/snapvt17/movie-paginate-1.png?w=w3 caption="Första sidan visas med två träffar av filmer."]

<!--
Så här kan det se ut när du är klar.

[FIGURE src=image/snapvt17/movie-paginate-1.png?w=w3 caption="Första sidan visas med två träffar av filmer."]
-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom Jobba igenom guiden "[Kom igång med PHP PDO och MySQL (v2)](kunskap/kom-igang-med-php-pdo-och-mysql-v2)". 

Du har en redovisa-sida.



Introduktion och förberedelse {#intro}
-----------------------

Gå igenom följande steg för att förbereda dig inför uppgiften.

<!--
[YOUTUBE src="XXX" playlist="PLKtP9l5q3ce8dXaJytGWt3usKsqpXT9E-" width=700 caption="Mikael visar hur du jobbar igenom övningen."]
-->



### Kom igång utifrån exempelkoden {#exempelkoden}

Kopiera in koden in i ramverkets struktur, avvakta att integrera.
Få exemplet att fungera.

```text
# Stå i me/redovisa
rsync -av ../../example/php-pdo-mysql htdocs
```



### Strukturera kring SQL-koden {#sql}

Var noga med vilka filer som finns och var de placeras. Det behövs återskapas av rättaren.



### Hur integrera en route {#introute}

Visa hur man integrerar en route, en första sida.



### Använd Anax\\Database {#anaxdatabase}

Visa hur man sätter igång modulen `Anax\Database`.
Databas as service in di.



### Lokal databas kontra produktionsserver {#server}

Konfigurera databasen för både lokal och produktionsservern.
Visa publicera och hur man skapar databasen på produktsservern.



### Vanliga funktioner {#funktioner}

Visa hur man kan inkludera vanliga funktioner i autoloadern.





Krav {#krav}
-----------------------

1. Filer för att återskapa databasen.

1. Visa filmer (eller något annat, välj fritt), minst fem stycken, dock inte de som finns med i exemplet.

1. Inloggning?


1. När du är klar så gör du `make test` för att kontrollera att din testsvit fungerar och sedan gör du en `dbwebb publish`.



Extrauppgift {#extra}
-----------------------

Gör följande extrauppgifter om du har tid och lust.

1. Inloggning. (registrera användare, admin av användare)

1. Enhetstestning databas



Tips från coachen {#tips}
-----------------------

**Lycka till och hojta till i forumet om du behöver hjälp!**

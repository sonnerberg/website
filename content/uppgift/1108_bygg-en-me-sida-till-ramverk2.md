---
author:
    - mos
category:
    - javascript
    - nodejs
    - kurs ramverk2
revision:
    "2017-10-14": "(A, mos) Första utgåvan."
...
Bygg en me-sida till ramverk2
===================================

Du skall sätta samman en me-sida baserat på Express.

Du skall lägga all kod i ett repo på GitHub. 

När du är klar så publicerar du och taggar ditt repo på GitHub.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom artikeln "[Node.js webbserver med Express](kunskap/nodejs-webbserver-med-express)".



Introduktion {#intro}
-----------------------

Spara allt du gör i ditt kursrepo under katalogen `me/redovisa`.

Skapa ett repo på GitHub som är taggat i minst version 1.0.0.

Om du vill använda annan teknik än Express och Pug för att bygga din webbplats så kan det vara okey. Men diskutera först i forumet.



###Utgå från mall-filer {#mall}

Det finns en mall i `example/redovisa` som du skall utgå ifrån. Den innehåller bland annat en makefile som är förberedd för att köra `make install test` samt filer som är förberedda för att integrera ditt repo mot byggtjänster och kodkvalitetstjänster.

Kopiera filerna från mallen så här.

```bash
# Gå till kursrepot
rsync -av example/redovisa me
```



###Tänk till om kodstrukturen {#strukturen}

Tänk till en extra gång när du nu organiserar ditt repo. Tänk vilken katalogstruktur du vill ha och hur du skall organisera din kod i filer och moduler.

Tänk det som att du vore en systemarkitekt på ett företag, du måste bestämma den struktur som företagets programmerare skall jobba i så det är viktigt att du gör ett bra beslut som fungerar för många individer som jobbar i teamet.

Tänk på att koden skall vara testbar. Du kan lita på att vi kommer införa enhetstester.

Tips. Det kan vara klokt att kika på Express app generator som scaffoldar fram en app till dig. Ibland är det bra att ha kompletta kodexempel framför sig.



Krav {#krav}
-----------------------

1. Använd Express och Pug för att skapa en webbplats.

1. Se till att det finns en `package.json` i katalogen. Filen skall innehålla alla beroenden som krävs.

1. Skapa en första sida där du ger en presentation av dig tillsammans med en bild.

1. Skapa en about-sida där du skriver en rad om denna kursen samt länkar till ditt repo på GitHub. Lägg även till en godtycklig bild som du anser kompletterar sidans innehåll.

1. Skapa en report-sida som du förbereder för att innehålla alla dina redovisningstexter för kursen.

1. Skapa en navbar så att man kan navigera mellan dina sidor.

1. Lägg till en header och footer som syns på alla relevanta sidor.

1. Styla sidan så som du finner bäst. Använd LESS/SASS/CSS, återanvänd kunskaper från tidigare kurser eller använd ramverk liknande Bootstrap, välj själv.

1. Kör `make install test` för att kolla att du inte har några valideringsfel.

1. Integrera repot med en byggtjänst motsvarande Travis eller CircleCI. Lägg till badgen i din `README.md`.

1. Committa alla filer och lägg till en tagg (1.0.\*).

1. Pusha upp repot till GitHub, inklusive taggarna.

<!--
1. Integrera repot med en tjänst för kodkvalitet (och kodtäckning) motsvarande Scrutinizer. Lägg till badgen i din `README.md`.
-->



Extrauppgift {#extra}
-----------------------

Lös följande om du har tid och finner det nyttigt.

1. Gör en route som låter dig hantera innehåll i `content/index.md` och `content/about/me.md`. Skapa alltså en liknande struktur du hade i kursen ramverk1 där du hanterade innehåll i markdown-filer.



Tips från coachen {#tips}
-----------------------

Kolla in app-generatorn som finns till Express, den kan ge dig tips till kodstruktur och innehåll i din app.

Lycka till och hojta till i forumet om du behöver hjälp!

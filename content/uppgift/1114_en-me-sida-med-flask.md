---
author: lew
revision:
    "2017-11-10": (A, lew) Updated version for VT18.
category:
    - oopython
...
Skapa en me-sida med Python och Flask
===================================

Använd ett microramverk för att skapa en webbapplikation (alt. me-sida).

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom övningen "[Kom igång med Flask](kunskap/kom-igang-med-flask)".

Du har jobbat igenom övningen "[Flask och Jinja2](kunskap/jinja2)".

Du har också gjort din [Flask applikation körbar via CGI](coachen/flask-som-cgi-script).

Har du gjort övningarna har du nästan kommit i mål med uppgiften.



Introduktion {#intro}
-----------------------

Vi ska skapa en me-sida som vi senare kommer bygga vidare på genom kursen. Utgå ifrån övningen.



Krav {#krav}
-----------------------

Startfilen ska heta `app.py` och ska ligga i mappen `me/flask` och vara körbar via `app.cgi`.

1. Applikationen ska använda Bootstrap.

1. Applikationen ska ha minst tre sidor, index.html, about.html och redovisning.html.

1. header.html och footer.html ska inkluderas med Jinja2.

1. index.html ska innehålla minst
    * en bild
    * Någon form av välkomsttext

1. redovisning.html ska innehålla
    * Dina redovisningstexter för kursmomenten

1. about.html kan innehålla något om kursen och vilka tekniker du jobbar i, det kan vara bra att visa upp när du är klar med kursen.

1. Validera och publicera applikationen på studentservern.


<!-- 5. Applikationen ska använda port 5000 -->

```bash
# Ställ dig i kurskatalogen
#dbwebb validate flask
dbwebb publish flask
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------

Lär dig felsöka med debuggern, använd den när du får problem. Komplettera med utskrifter av `print()`.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

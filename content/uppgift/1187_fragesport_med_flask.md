---
author: lew
revision:
    "2018-11-29": (A, aar) First version.
category:
    - oopython
...
Skapa former
===================================

[FIGURE src=/image/oopython/kmom02/skapa-former.png?w=c5 class="right"]

Uppgiften går ut på att med hjälp av klasser, Flask, jinja2 och CSS, skapa former som visas i applikationen. Formerna ska skapas med hjälp av ett formulär och ritas ut i en annan route.

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har gått introduktionskursen i Python.  
Du har läst artikeln "[GET, POST i Flask](kunskap/flask-get-post)".  
Du har läst artikeln "[Klass relationer](kunskap/klass-relationer)".  



Introduktion {#intro}
-----------------------    




Krav {#krav}
-----------------------

Börja med att skapa routes för uppgiften, en för att skapa former och en för att visa upp dem.

Arbeta i mappen kmom02/flask.

```bash
# Ställ dig i kurskatalogen
cd me/kmom02/flask
```

1. kopierade app.py och app.cgi från flask/cgi övning

1. fixade mapp struktur från flask/jinja intro övning

1. Fixa index.html

```bash
# Ställ dig i kurskatalogen
dbwebb validate flask
dbwebb publish flask
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. Lägg till fler former, tex en [cylinder](https://sv.wikipedia.org/wiki/Cylinder) eller [hyptagon](https://sv.wikipedia.org/wiki/Heptagon).



Tips från coachen {#tips}
-----------------------

Tänk på att det går att använda inline style, tex: `<div style="posistion:absolute;top:10;left:50;">`.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

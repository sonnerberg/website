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

Uppgiften går ut på att med hjälp av klasser, Flask, jinja2 och CSS, skapa en webbsida för att ställa frågor med tre olika typer av svarsalternativ.

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har gått introduktionskursen i Python.  
Du har läst artikeln "[GET, POST i Flask](kunskap/flask-get-post)".  
Du har läst guiden "[Klass relationer](guide/kom-igang-med-objektorienterad-programmering-i-python)".  



Introduktion {#intro}
-----------------------    

Du jobbar vid sidan om dina studier och din kund vill att du gör klart en webbsida som redan är påbörjad. Gränssnittet och routes är redan klart, du ska bara skapa klasserna för backend:en till webbsidan. Dina klasser behöver uppfylla abstraktionskraven som finns utspridd i koden. Med det menas att dina klasser behöver ha vissa metoder och attribut med rätt namn, annars kommer inte frontend fungera med din backend. I klassdiagrammet nedanför kan du se vilket gränssnitt din klasser måste uppfylla.

Du ska implementera klasserna för de olika frågetyperna och handlern som app.py jobbar mot som i sin tur använder fråge-klasserna. Samma struktur som i övningen. I den färdiga koden som du får finns redan anrop till objekt av de klasser som du ska implementera, det betyder att dina klasser måste uppfylla de beroenden.



Krav {#krav}
-----------------------

Börja med att kopiera frontend:en till ditt uppgift.

```bash
# Ställ dig i kurskatalogen
cp -ri example/flask/questions me/kmom02/flask
cd me/kmom02/flask
```

1. Bekanta dig med koden, kolla igeom app.py för att se vilka routes som finns och vilka html filer som används till vad. Leta efter alla anrop som görs till klasserna du ska skapa för att få en bild av vilka metod som behövs och vad de används till.

1. Implementera klasserna som behövs i filerna `handler.py` och `questions.py`, en handler klass som heter `QuesionManager` och tre klasser för frågorna. Typerna är fritext svar, flervalsfrågor med flera rätt (checkboxes) och flervalsfrågor med ett rätt svar (radiobuttons). Välj ut en av dem som basklass som de andra två ska ärva från. I mappen `templates/answer_types` finns en html template för varje typ av klass. 

1. Du ska inte behöva ändra i några av de andra filerna, förutom style.css, men om du känner att du vill/behöver det skriv varför i din redovisningstext.

1. Webbsidan ska fungera på studentservern med hjälp av session.

1. Hårdkoda minst tre frågor för varje Question klass.

```bash
# Ställ dig i kurskatalogen
dbwebb validate flask
dbwebb publish flask
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns inga extrauppgifter.



Tips från coachen {#tips}
-----------------------


Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

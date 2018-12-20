---
author: aar
revision:
    "2018-11-29": (A, aar) First version.
category:
    - oopython
...
Frågesport med Flask
===================================

[FIGURE src=/image/oopython/kmom02/fragesport.png?w=c5 class="right"]

Uppgiften går ut på att med hjälp av klasser, Flask, jinja2 och CSS, skapa en webbsida med tre olika typer av frågor.

<!--more-->


Förkunskaper {#forkunskaper}
-----------------------

Du har gått introduktionskursen i Python.  
Du har läst artikeln "[GET, POST i Flask](kunskap/flask-get-post)".  
Du har läst guiden "[Klass relationer](guide/kom-igang-med-objektorienterad-programmering-i-python)".  



Introduktion {#intro}
-----------------------    

Du jobbar vid sidan om dina studier och din kund vill att du gör klart en webbsida som redan är påbörjad. Gränssnittet och routes för sidan är redan klart, du ska skapa klasserna för backend:en till webbsidan. I och med att frontend redan är klar och innehåller anrop till koden du ska skapa behöver dina klasser uppfylla abstraktionskraven som det medför. Med det menas att i dina klasser behöver det finnas vissa metoder och attribut med rätt namn, annars kommer inte frontend fungera med din backend. I klassdiagrammet nedanför kan du se vilket gränssnitt din klasser måste uppfylla. Men gränssnitt menas existerande publika metoder.

[YOUTUBE src=PCGwx_wpzME width=630 caption="Så här kan det se ut när det är färdigt."]

Du ska implementera klasserna för de tre frågetyperna och handlern som app.py jobbar mot som i sin tur använder fråge-klasserna. Samma struktur som i övningen.

[FIGURE src=/image/oopython/kmom02/fragesport_uml.png caption="Klassdiagram för uppgiften."]

Attributen och metoderna som är **bold** markerad används av den färdiga kod ni får och måste därför implementeras och med de namnen. Övriga är bara exempel på vad man kan ha med. `QuestionType2` och `QuestionType3` innehåller bara ett statisk attribut som ett måste men du kommer också behöva överlagra några av metoderna från `Question` för att det ska bli bra. Vilka metoder beror på vilken klass du väljer som basklass. Jag hade även bytt namn på Question klasserna så det inte bara är type2 eller 3. Förhoppningen är att metodnamnen är beskrivande nog över vad de ska göra men om du är osäker är det bara att fråga.



Krav {#krav}
-----------------------

Börja med att kopiera frontend:en till ditt uppgift.

```bash
# Ställ dig i kurskatalogen
cp -ri example/flask/questions me/kmom02/questions
cd me/kmom02/questions
```

1. Kolla på youtube-klippet ovanför för att få en översyn av vad du ska göra.

1. Bekanta dig med koden, kolla igeom app.py för att se vilka routes som finns och vilka html filer som används till vad. Leta efter alla anrop som görs till klasserna du ska skapa så att du får en bild av vilka metod som behövs och vad de används till.

1. Implementera klasserna som behövs i filerna `handler.py` och `questions.py`, en handler klass som heter `QuesionManager` och tre klasser för frågorna. Typerna av frågor är fritext svar, flervalsfrågor med flera rätt (checkboxes) och flervalsfrågor med ett rätt svar (radiobuttons). Välj ut en av dem som basklass och låt de andra två ärva från basklassen. I mappen `templates/answer_types` finns en html template för varje frågetyp.

1. Frågeklasserna behöver innehålla en fråga, svaret och svarslternativen, om det finns några. De behöver ha metoder för att hämta värdena och en metod för att kolla om användarens svar är rätt. 

1. Handlern ska äga alla tillgängliga frågor, hålla reda på hur många poäng spelaren har, vilken fråga man är på och vad max poängen är. Det ska finnas metoder för att hämta antalet poäng, max poäng, kolla om det finns fler frågor, hämta nästa fråga, läsa från session, skriva till session, återställa spelet och kolla om användarens input är rätt svar på nuvarande frågan.

1. Använd dig av `print()` i metoderna du skapar, kolla klassdiagrammet och kolla där anrop görs för att ta reda på vad som skickas som argument till dina metoder.

1. Session ska användas för att hålla kolla på hur många poäng spelaren har och vilken fråga spelaren är på.

1. Du ska inte behöva ändra i några av de andra filerna, förutom style.css, men om du känner att du vill/behöver det skriv varför i din redovisningstext.

1. Hårdkoda minst tre frågor för varje Question klass. Tips att skapa dessa i `QuestionManager`.

```bash
# Ställ dig i kurskatalogen
dbwebb validate questions
dbwebb publish questions
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

1. För de frågor med checkboxes ge poäng för varje rätt alternativ. Om det är två alternativ som är rätt på frågan ska den vara värd två poäng.



Tips från coachen {#tips}
-----------------------


Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

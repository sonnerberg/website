---
author: mos
revision:
    "2017-10-10": (B, mos) Genomgången inför ht17.
    "2015-10-15": (A, mos) Första utgåvan för kursen.
...
Kmom01: JavaScript och WebGL
==================================

Du kommer igång med en labb- och utvecklingsmiljö som stödjer utveckling av HTML, CSS och JavaScript tillsammans med WebGL. Du testar på programmering i JavaScript, bygger en sandbox för dina tester och du skapar dina första WebGL-ritningar i webbläsaren.

<!--more-->


Så här långt kommer du när du läst boken och testat dess exempel.

[FIGURE src=/image/snapht15/webgl-sandbox2-point-random-color.png?w=w2 caption="Placera ut punkter på canvasen i olika färger."]



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Kursens labbmiljö  {#labbmiljo}
---------------------------------

*(ca: 2-6 studietimmar)*

Du behöver installera kursens labbmiljö samt ha tillgång till verktyget `dbwebb` som du installerar på terminalen. När du är klar kan du klona kursrepot där du finner en del av kursens material.



###Labbmiljön {#kurslabbmiljo}

Det första du behöver göra är att installera en labbmiljö för kursen. Om detta är din första dbwebb-kurs så kan det innebära en hel del jobb och en del nya tekniker. Se till att du har gott om tid när du gör detta.

1. [Installera labbmiljön](./../labbmiljo) som behövs för kursen. 



###Installera/uppdatera kommandot dbwebb {#dbwebbcli}

Om du redan har installerat kommandot dbwebb så gör du en selfupdate för att vara säker på att du har senaste versionen. Sedan kan du fortsätta till nästa stycke.

```text
dbwebb selfupdate
```

Om du vill ha en introduktion till installationen av dbwebb-kommandot så kikar du på videon "[Mikael installerar dbwebb-cli som en del av labbmiljön](https://www.youtube.com/watch?v=vlZRW2OZamE)".

Utför följande steg för att installera kommandot dbwebb.

1. [Installera kommandot `dbwebb`](dbwebb-cli/kom-igang-och-installera). Kommandot används under hela kursen för att jobba med kursmaterialet.

1. När du har installerat kommandot så fortsätter du med sektionen för att [konfigurera kommandot `dbwebb`](dbwebb-cli/konfiguration).



###Klona kursrepot {#clona}

Kursrepot innehåller en viss del av kursmaterialet och det ger en struktur där du skriver kod för att lösa övningar och uppgifter i kursen. Du hämter det med hjälp av kommandot dbwebb. Vi kallar det för att du klonar ditt kursrepo. Klona är ett begrepp som används i versionshanteringssystemet Git.

1. Läs om hur du [laddar ned (klona) ditt lokala kursrepo](dbwebb-cli/clone) som innehåller kursmaterial för kursen.

Den snabba vägen.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb clone webgl
```

Bra, det var inledningen och vissa nödvändiga saker. Nu kan du sätta igång "på riktigt" med det första kursmomentet.



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-8 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [WebGL Programming Guide](kunskap/boken-webgl-programming-guide).
    * Ch 1: Overview of WebGL
    * Ch 2: Your first step with WebGL

I kapitel 2 finns en del exempelprogram som du kan testa direkt i ditt kursrepo `example/webgl/theBook/Chapter2/`, eller via [dbwebb's kopia av kursrepot](webgl/repo/example/webgl/theBook/Chapter2/).

1. Bekanta dig med boken [Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript) genom att läsa igenom det första kapitlet [Ch1 Basic JavaScript](http://speakingjs.com/es5/ch01.html) (läs till och med stycket om "Strict Mode") som ger dig en introduktion till grundkonstruktioner i programmeringsspråket JavaScript.



###MDN {#mdn}

I kursen används Mozilla Developers Network (MDN) som en resurs generellt för webbresurser och specifikt för referensmanual till programmeringsspråket JavaScript.

Vill du hamna på rätt manualsida så lägger du alltid till "mdn" till din googling. Det finns många versioner av JavaScript och du vill gå tillbaka till källan i referensmanualen för att veta vad som är rätt (eller fel).

Gör följande:

1. Bekanta dig kort med översikten på [MDN: Web technology for developers](https://developer.mozilla.org/en-US/docs/Web). Där ser du generellt material om webbteknologier.

1. Bekanta dig specifikt med det som finns under rubriken "JavaScript". Använd minst 10 minuter av din tid för att kika runt och läsa någon av de inledande artiklarna om JavaScript.

1. För en snabb introduktion till konstruktionerna i språket JavaScript kan jag rekommendera dokumentet "[MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)" och de inledande kapitlen som kompletterar det du läst i kurslitteraturen.
    * Introduction
    * Grammar and types
    * Expressions and operators



###Artiklar {#artiklar}

Läs följande:

1. I kursen används validatorer och en kodstandard för att testa att du skriver kod på ett, enligt kodstandarden, acceptabelt sätt. Du kan läsa om dbwebb-kodstandarden på [npm javascript-code-style](https://www.npmjs.com/package/javascript-style-guide). Du kan diskutera [kodstandarden i forumet](t/6327).



###Video  {#video}

Kika på följande videor.

1. Videon "[The Future of WebGL and Gaming](https://www.youtube.com/watch?v=6lnEmAYVziA)" ger dig en inblick i en möjlig framtid för 3D-spel på webben.



###Föreläsningsmaterial {#slide}

Föreläsningsmaterial finner du i kursrepot under [`slide/01.*`](webgl/repo/slide).



###Lästips {#lastips}

Följande källor är relevanta och ger dig en orientering i WebGL och det som krävs för att jobba med WebGL.

1. Webbplatsen [WebGL Fundamentals](http://webglfundamentals.org/) innehåller en samling artiklar som riktar sig till den som precis börjat koda WebGL. Det kan vara bra att använda sig av de artiklarna som komplement till boken. 

1. Webbplatsen [Learning WebGL](http://learningwebgl.com/blog/?page_id=1217) innehåller ett antal lektioner om hur man kommer igång med WebGL. De kan komplettera boken.

1. [Khronos Group](https://www.khronos.org/) driver standardisering och utveckling inom OpenGL och WebGL. Vänd dig till deras webbplats för referensmaterial.

1. Du bör redan vara mycket väl insatt i vektorer, matriser och hur de relaterar till 3D-grafik. Vill du fräscha upp minnet så finns det bra resurser i artikelserien om "[Vector Math for 3D Computer Graphics](http://www.dickbaldwin.com/KjellTutorial/KjellVectorTutorialIndex.htm)".



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 10-12 studietimmar)*



###Övningar {#ovningar}

Börja med att kika på följande introduktionsartiklar om HTML, CSS och JavaScript. Beroende på dina förkunskaper så får du välja hur mycket tid du spenderar på dem. De innehåller grunder och ger dig en introduktion i de olika teknikerna.

* HTML - [Gör din första sida med HTML5](coachen/gor-din-forsta-sida-med-html5)
* CSS - [Styla din sida med CSS och en extern stylesheet](coachen/styla-din-sida-med-css-och-en-extern-stylesheet)
* JavaScript - [Kom igång med JavaScript och skriv din första kod](coachen/kom-igang-med-javascript-och-skriv-din-forsta-kod)



När du är klar med ovanstående introduktionsartiklar så genomför du följande övning.

1. Kom igång och gör ditt första program i JavaScript tillsammans med artikeln "[Kom i gång med HTML, CSS, JavaScript och Canvas](kunskap/kom-i-gang-med-html-css-javascript-och-canvas)".

2. Uppgradera din sandbox till att rita med 3D-kontext och WebGL tillsammans med artikeln "[Kom igång och rita med WebGL på en Canvas](kunskap/kom-igang-och-rita-med-webgl-pa-en-canvas)".



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Rita punkter med WebGL](uppgift/rita-punkter-med-webgl)".

1. Gör uppgiften "[Skapa en me-sida till webgl-kursen](uppgift/skapa-en-me-sida-till-webgl-kursen)".



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Vilken utvecklingsmiljö sitter du på?
* Hur väl känner du dig hemma i webbtekniker som JavaScript, HTML och CSS?
* Hur väl känner du dig hemma i 3D programmering med OpenGL, WebGL eller motsvarande?
* Gick det bra att skapa me-sidan? Var det någon som var svårt att hantera i me-sidan?
* Vad tycker du om kursboken så här långt?
* Berätta lite om hur du löste uppgiften med punkterna. Var det något som var svårt, lurigt eller utmanande?

---
author:
    - mos
revision:
    "2017-05-29": (PI1, mos) Omarbetning inför ht17.
    "2016-03-15": (H, mos) Tog bort videoserie MonkeyLords och NewBoston.
    "2016-02-22": (G, mos) Lade till videoserien "Lär dig Python".
    "2015-08-25": (F, mos) Ändrar till hur labbmiljön installeras samt dbwebb-cli v2.
    "2015-01-08": (E, mos) Bort blå ruta med kursutveckling pågår.
    "2014-10-01": (D, mos) Ändrade länken till redovisa-instruktionen.
    "2014-08-30": (C, mos) Publicerades för första gången officiellt.
    "2014-08-25": (B, mos) Cgi fungerar som tänkt med python3 på webbservern.
    "2014-08-21": (A, mos) Första utgåvan för python kursen.
...
Kmom01: Kom i gång med Python
==================================

[WARNING]
Arbete pågår med uppdatering inför HT2017.
[/WARNING]

<!-- Why learn python? -->

Det första vi skall göra är att skaffa oss en utvecklingsmiljö och kika i kurslitteraturen. Python fungerar på många miljöer och i olika varianter. Vi börjar skriva de första enkla programmen för att komma underfund med hur Python kan användas.

[FIGURE src=/image/snapht14/python-mos-me-page.png?w=w2 caption="Mikaels me-sida i Python som cgi-skript."]

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Det första du behöver göra är att installera en labbmiljö för kursen. Om detta är din första dbwebb-kurs så kan det innebära en hel del jobb och en del nya tekniker. Se till att du har gott om tid när du gör detta.

1. Du kan börja med att [installera labbmiljön](kurser/python/labbmiljo) som behövs för kursen. 

1. Fortsätt med sektionen för att [installera kommandot `dbwebb`](dbwebb-cli/kom-igang-och-installera). Kommandot används under hela kursen för att jobba med kursmaterialet.

1. När du har installerat kommandot så fortsätter du med sektionen för att [konfigurera kommandot `dbwebb`](dbwebb-cli/konfiguration) så att det blir enkelt att jobba med det.

1. Du kan nu [ladda ned (klona) ditt lokala kursrepo](dbwebb-cli/clone) som innehåller kursmaterial för kursen. Här kommer du att skriva all kod till övningar och uppgifter.



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*


###Kurslitteratur  {#kurslitteratur}

Läs följande:

Kursens huvudbok ger förståelse och bakgrunden till att klara övningar och uppgifter.

1. [Python for Everybody: Exploring data in Python3](kunskap/boken-python-for-everybody-exploring-data-using-python3)
    * Ch1 Why should you learn to write programs?
    * Ch2 Variables, expressions and statements

<!--
1. [Think Python: How to Think Like a Computer Scientist](kunskap/boken-think-python-how-to-think-like-a-computer-scientist).
    * Ch1 The way of the program
    * Ch2 Variables, expressions and statements
-->



###Artiklar {#artiklar}

Efterhand som du lär dig Python kommer du att märka att du referensmanualen är en bra källa till kunskap. Bekanta dig därför med strukturen som finns på Pythons webbplats och gå igenom följande.

1. Bekanta dig översiktligt med [dokumentationen som finns på Pythons webbplats](https://www.python.org/doc/). Kika runt och orientera dig. Vi använder Python 3.

1. Se översikten av referensdokumentation för [Python 3.x Doc](https://docs.python.org/3/). Bekanta dig med strukturen och se vilken typ av information som du kan hitta samt hur 

1. Läs första kapitlet i [The Python Tutorial](https://docs.python.org/3/tutorial/index.html). Det är mest för att du skall se vilken typ av information som finns i tutorialen och för att bekanta dig med den typen av material.



###Video  {#video}

Titta på följande:

1. Följande videor som följer med och kompletterar kurslitteraturen. Det är författaren som har föreläsningar kopplade till bokens kapitel.
    * [Python for Informatics: Chapter 1 - Introduction](https://www.youtube.com/watch?v=G721cooZXgs)
    * [Python for Informatics: Chapter 2 - Expressions](https://www.youtube.com/watch?v=IXXHH6ztsSA)

1. Här är en videoserie [Lär dig Python](https://www.youtube.com/playlist?list=PLKtP9l5q3ce93pTlN_dnDpsTwGLCXJEpd) som är tätt kopplad till kursmaterialet. Kika på de videor som börjar med 0 och 1. Det är korta videor som tar upp delar som är relevanta i respektive kursmoment.



###Lästips {#lastips}

Det finns inga extra lästips.

<!-- Om du känner att du har tid och lust. -->



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 6-8 studietimmar)*



###Övningar {#ovningar}

Genomför följande övning för att träna dig och förbereda inför uppgifterna.

1. Kom igång och gör ditt första program i Python tillsammans med artikeln "[Kom igång med ditt första program i Python](kunskap/kom-igang-med-ditt-forsta-program-i-python)".



###Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[En me-sida i Python som cgi-skript](uppgift/en-me-sida-i-python-som-cgi-skript)".

2. Gör uppgiften "[Ditt första Python-skript](uppgift/ditt-forsta-python-skript)".




###Extra {#extra}

Det finns inga extra uppgifter.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](kurser/python/redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Vilken utvecklingsmiljö använder du?
* Är du bekant med programmering och problemlösning och/eller Python sedan tidigare?
* Är du bekant med terminalen och Unix-kommandon sedan tidigare?
* Gick det bra att komma i gång med kursmomentet, fanns det svårigheter som du fastnade på?
* Vilken del av kursmaterialet (böcker, artiklar, videor, etc) uppskattade du mest, använde du dem alla?

---
author: mos
category:
    - kurs webtec
revision:
    "2021-06-15": "(A, mos) Första utgåvan."
...
Bygg en webbplats med PHP
===================================

Du skall utgå från en webbplats du byggt tidigare i kursen och strukturera om den så att den blir byggt med hjälp av PHP.

Du skall även utveckla nya webbsidor till din webbplats för att pröva konstruktioner såsom GET, POST, SESSION och COOKIE.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har utfört uppgiften "Skapa en responsiv webbplats med HTML och CSS".

Du har grundläggande kunskap om hur man bygger webbplatser med PHP.



<!--
Genomgång {#genom}
------------------------

Här är en video som "pratar" dig igenom uppgiftens upplägg och visar hur du kommer igång.

[YOUTUBE src="gKzwQTG9eCI" width=700 caption="Kurs mvc kmom03 tisdagsgenomgång, del 3/3 uppgiften (Zoom med Mikael)."]
-->



Introduktion och förberedelse {#intro}
-----------------------

Du har sedan tidigare utvecklat en webbplats i `me/htmlcss`. Du kan utgå från den och dess innehåll för att nu tillföra PHP för att bygga din webbplats och kod mer dynamiskt.



Krav {#krav}
-----------------------

Utför följande krav.

1. Spara alla filerna i ditt kursrepo under `me/session`.

1. Bygg om webbplatsen så att den körs som PHP-sidor. Första sidan skall heta `index.php`.

1. Organisera din PHP-kod i filer och funktioner där det är lämpligt.

1. Organisera webbplatsen enligt konceptet sidkontroller och vyer.

1. Skapa en webbsida som sparar ett datum för senaste tillfället då du besökte sidan. Visa upp datumet, om det finns, annars skriv ut "du har inte besökt denna webbsidan tidigare". Avsluta med att spara tiden för det senaste besöket i din cookie.

1. Skapa en webbsida som kan radera/förstöra din cookie.

1. Skapa en webbsida som sparar information i sessionen och visar upp det. Varje gång man laddar om sidan skall det synas att informationen i sessionen ökas, till exempel en variabel som ökas med +1.

1. Skapa en webbsida som kan radera/förstöra sessionen.

1. Skapa en webbsida med ett formulär som ser ut som en sökmotor. Använd GET och i resultatsidan skriver du ut innehållet i söksträngen.

1. Skapa en webbsida med ett formulär där du skall registrera dig själv som kund (eller liknande). Använd POST med en processingsida som sparar till sessionen och gör redirect till en resultatsidan där du skriver ut innehållet från det postade formuläret i en HTML tabell.

1. Kontrollera att din webbplats är fortsatt responsiv för olika bredder på webbläsaren.

1. Besvara följande frågor i din redovisningstext.

    * Berätta hur det gick att lösa uppgiften, var något extra svårt, lurigt, krångligt eller flöt det på smidigt?
    * Är det något som du är extra nöjd med i ditt resultat från uppgiften?

<!--
Överkurs drag & drop för att ladda upp en bild.
-->



Publicera {#publicera}
-----------------------

Avsluta uppgiften så här.

1. Testa ditt resultat så att det passera de automatiska testerna med `dbwebb test session`.

1. När du är klar kan du publicera resultatet med `dbwebb publish session`.

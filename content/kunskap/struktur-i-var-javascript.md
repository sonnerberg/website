---
author: efo
category: javascript
revision:
  "2018-01-18": (A, efo) Första utgåvan inför kursen linux V18.
...
Struktur i JavaScript
==================================
[FIGURE src=image/webapp/backpack.jpg?w=c4 class="right"]

Vi har nu bra struktur på vår CSS/SASS kod och tiden har nu kommit för att ta ett steg i rätt riktning även för JavaScript koden. Sista delen av kursmoment 1 var att dela upp koden för Me-appen i olika filer för att få en bättre struktur på koden. Vi ska i denna övning titta på verktyg för att strukturera vår JavaScript kod. Målet är att vi bara importerar en JavaScript-fil i `index.html` och att vi använder modulerna på ett bättre sätt än vi har gjort tidigare.



webpack {#webpack}
--------------------------------------
I koden vi skrev i kmom01 avslutade vi med att dela upp JavaScript koden i ett flertal `.js`-filer, som vi importerade i `index.html`. När vi använder en modul som finns i en annan JavaScript fil förlitar vi oss på att den har laddats i `index.html`. För att komma bort från detta kan vi använda webpack. webpack används för att kompilera JavaScript moduler och gör det möjligt att dela upp vår JavaScript kod i ett flertal moduler. Vi kan även hämta in externa moduler och på samma sätt som egna modulerna kompilera ner det till en enda fil.

Låt oss titta på ett exempel för att konkretisera detta.



Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna övning tittat på hur vi kan skapa en bättre struktur för vår JavaScript och hur vi explicit definerar vilka JavaScript moduler vi vill använda.

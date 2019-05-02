---
author: lew
category: unix
revision:
    "2019-05-02": (A, lew) Ny inför HT19.

...
Uppdatera mazen med en loop
==================================

Du ska utgå ifrån mazerunnern du skapade i kursmoment 05. Tanken är att skriptet ska kunna köras med kommandot `./mazerunner.bash loop` och hålla sig i spelet tills man avslutar eller nått sista rummet.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har gått igenom delen i guiden som handlar om [Docker compose](guide/docker/docker-compose).  
Du har färdigställt uppgiften [mazerunner i Bash](uppgift/mazerunner-i-bash).  
Du har koll på [Bash-guiden](guide/kom-igang-med-bash).



Introduktion {#intro}
-----------------------

TBD



Krav {#krav}
-----------------------

Kraven består av två delar. Först skapar vi ett Bash-skript som körs mot servern. Sedan bygger vi in både servern och klienten i varsin kontainer som pratar med varandra via ett eget nätverk.




### Bashscript i loop {#bash-loop}

1. Utöka funktionaliteten i `mazerunner.bash` så att allt sker i en loop när man startar programmet med `./mazerunner loop`. Skriptet skall börja med att initiera ett nytt spel och visa vilka kartor som finns. Spelaren kan då välja en karta varpå spelaren träder in i första rummet. Därefter fortsätter loopen och väntar på att spelaren skriver in riktningen north, south, east, west, eller help för en hjälptext eller quit för att avsluta.

Så här kan det se ut, ungefär.

[ASCIINEMA src=23368]


<!--
###Lös mazen {#solution}

1. Utöka funktionaliteten i `mazerunner.bash` så att den automatiskt går igenom mazen på ett effektivt sätt som leder till sista rummet. Du startar detta genom att ange `./mazerunner solve`.



###Buggfix {#bugg}

1. Det finns en felrapport på maze-servern, [issue 8](https://github.com/dbwebb-se/linux/issues/8), som behöver lagas. Gör först ett testfall `issue.bash` som återskapar och påvisar felet. Laga sedan felet i din maze server.

-->



### Validera och publicera {#publish}

Validera och publicera din kod enligt följande.

```bash
# Ställ dig i kurskatalogen
dbwebb validate maze
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns ingen extrauppgift.



Tips från coachen {#tips}
-----------------------

Strukturera din kod med funktioner i bash. Då får du en bra struktur i första delen och i andra delen så kan du återanvända funktionerna.

Lycka till och hojta till i forumet om du behöver hjälp!

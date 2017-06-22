---
author: efo
category: python
revision:
    "2017-06-21": (A, efo) Första utgåvan i samband med uppdatering av kmom05 i kursen python.
...
Analysera text och ord
==================================

[FIGURE src=image/python/old-book.jpg?w=c5 class="right"]

Vi har i Marvin byggt ett program bestående av två moduler och ett antal funktioner som samverkar för att Marvin kan svara på frågor. Vi har även bekantat oss med `dictionary` där vi kan spara nyckel-värde par. Vi har även bekantat oss med CLI med hjälp av modulen `argparse`. Vi ska i denna uppgift skapa ett CLI-program som tar emot argument och kan analysera en text.

<!--more-->




Förkunskaper {#forkunskaper}
-----------------------

Du har en bra förståelse för `dictionary` och har jobbat igenom "[Python med dictionaries och tupler](uppgift/python-med-dictionaries-och-tupler)". Du har även jobbat med CLI-program i "[Modulen argparse](kunskap/argparse)".



Introduktion {#intro}
-----------------------

I kursrepot finns en del av "Phil, the Fiddler", [`example/text/phil.txt`](https://github.com/mosbth/python/blob/master/example/text/phil.txt). Du skall använda den texten och låta ditt CLI-program analysera den.

Vill du lära dig mer om vad textanalys kan innebära "på riktigt" så läser du lite om [text analys och text mining på Wikipedia](https://en.wikipedia.org/wiki/Text_mining).

Du kommer göra en övning med ordfrekvens, läs gärna om det på [Wikipedia Letter Frequency](https://en.wikipedia.org/wiki/Letter_frequency) och studera bilden som visar bokstävernas procentuella förekomst i det engelska språket.

För samtliga uppgifter gäller att ett ord består av bokstäverna [a-Z]. Ett tips är att konvertera alla ord till enbart små bokstäver [a-z], det kan göra uppgiften enklare.

Googla "online word counter" eller "online letter counter" så hittar du verktyg som gör precis det du skall göra. Testa att köra in  texten i ett av dem och se hur det ser ut. Då får du en referens och mental bild som kan hjälpa dig att se om du är på rätt väg eller ej.

Du ska i uppgiften göra ett CLI-program som analyserar en text från en fil. Det kan se ut på detta sättet när vi kör programmet:

```bash
# Generell använding av vårt text analys verktyg
$ python3 main.py [options] filename [command]

# Visa hjälp text
$ python3 main.py --help

# Kör alla analyser för phil.txt
$ python3 main.py phil.txt lines

# Visa antal rader i texten phil.txt
$ python3 main.py phil.txt lines

# Visa ordfrekvensen i texten phil.txt
$ python3 main.py phil.txt word_frequency

# Visa bokstavsfrekvensen i texten phil.txt med extra utskrift
$ python3 main.py --verbose phil.txt letter_frequency
```



Krav {#krav}
-----------------------

Börja med att kopiera koden från övningen "[Modulen argparse](kunskap/argparse)".

```bash
# Ställ dig i kursmoment katalogen
cp -ri argparse/*.py analyzer/
cp -ri ../../example/text/phil.txt analyzer/
cd analyzer
```

Se till att din katalog `analyzer` innehåller filen `phil.txt`.

1. Ditt program ska bestå av tre moduler: `main.py`, `cli_parser.py` och `analyzer.py`.

1. Ditt program ska ha följande options: `-h, --help`, `-s, --silent`, `-v, --version` och `--verbose`.

1. Ditt program ska ta emot ett filnamn som första kommando och analysera texten i den filen.

1. Som andra kommando ska ditt program ta emot ett sätt att analysera texten på och enbart analysera texten på det sättet.

1. Analysera antal rader, ord och bokstäver med kommandon `lines`, `words` och `letters`.

1. Analysera även ord- och bokstavsfrekvensen och skriv ut de sju mest förekommande orden och bokstäverna. Ange frekvensen i % av totala mängden ord eller bokstäver. Använd kommandon `word_frequency` och `letter_frequency`.

1. Validera ditt program genom att göra följande kommando i kurskatalogen i terminalen.

```bash
# Ställ dig i kurskatalogen
dbwebb validate analyzer
```

Rätta eventuella fel som dyker upp och validera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------

Det finns inga extra uppgifter.



Tips från coachen {#tips}
-----------------------

Lär dig felsöka med debuggern, använd den när du får problem. Komplettera med utskrifter av `print()`.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

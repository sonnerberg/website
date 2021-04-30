---
author:
  - moc
  - aar
category: python
revision:
  "2021-03-30": (A, moc) Ny version för att introducerar automaträttning.
created: "2021-03-30 11:19"
...
Din egen chattbot - Marvin - steg 2
==================================

Programmering och problemlösning i Python. Strukturera koden i egna funktioner.

<!--more-->


<!-- Introduktion {#intro}
-----------------------

-->


Förkunskaper {#forkunskaper}
-----------------------

Du kan grunderna i Pythons stränghantering och du har gjort den [första delen](uppgift/din-egen-chattbot-marvin-steg-1-v3) av Marvin.



Krav {#krav}
-----------------------
[INFO]
Taggarna för varje uppgift motsvarar själva menyvalet. För att testa Menyval **8** kan man då använda `--tags=8`, för Menyval **b1** `--tags=b1` osv.
[/INFO]


1. Kopiera din Marvin från föregående kursmoment och utgå från den koden.

```bash
# Flytta till kurskatalogen
cd me
cp -ri kmom02/marvin1/marvin.py kmom03/marvin2/
cd kmom03/marvin2
```

2. Skapa filen `main.py`, den skall innehålla koden för att starta ditt program. Skapa **funktionen** `main` som innehåller koden för din while-loop. Din main fil skall sedan kalla på `main` funktion i blocket för villkoret `if __name__ == "__main__"` som du lägger längst ner i main.py.

3. Koden för dina menyval ska nu ligga i `marvin.py`. Flytta all kod för dina nuvarande menyval till `marvin.py`, dessa skall sparas i funktioner som du kallar på när ett menyval ha gjorts i programmet. Importera `marvin.py` i `main.py` och strukturera om koden för de gamla menyvalen så att de läggs i en varsin funktion, med **följande namn**. Dessa funktionerna har utöver sitt menyval som tag också "marvin1" som tag.
  * Menyval 1 - `greet`
  * Menyval 2 - `celcius_to_farenheit`
  * Menyval 3 - `word_manipulation` * Tips, gör denna i samband med menyval **11**, (krav 7).
  * Menyval 4 - `sum_and_average`
  * Menyval 5 - `compare_numbers`
  * Menyval 6 - `hyphen_string`
  * Menyval 7 - `is_isogram`

Om du har gjort några av extrauppgifterna från föregående kursmoment så kan du döpa dem till ett valfritt namn.

**Alla** `input()` och `print()` som används i menyvalen skall ligga i funktionen för menyvalet och inte i main programmet.  
Det är OK att bryta ut din kod till flera mindre funktioner så länge de används i funktionen som efterfrågas.


- Tags: `struct`. Kör tester som kollar att "marvin.py" och "main.py" finns och att funktionen "main()" finns i "main.py"

4. Menyval **8** - `randomize_string`: Kasta om bokstäver. Marvin ska be dig skriva in ett ord som sedan slumpmässigt kastas om. Det omkastade ordet ska sedan skrivas ut i formatet `<orginal sträng> --> <slumpad sträng>`. Lösningen ska vara case-sensitive, med andra ord `A != a`. Tips [random modulen](https://docs.python.org/3.8/library/random.html).
```python
input: "Hej"                        output: "Hej --> jHe"
input: "Borde inte bli samma igen"  output: "Borde inte bli samma igen --> eel gn rtm dBmibo saiiane"
```


5. Menyval **9** - `anagram`: Anagram. Skapa ett val där marvin ber om två strängar och kollar om de är anagram. Ett anagram är när man kan få fram samma sträng genom att kasta om bokstäverna i den andra. Lösningen ska inte vara case-sensitive, med andra ord `A == a`. Tips, [sorted()](https://docs.python.org/3/howto/sorting.html) och [lower()](https://docs.python.org/3/library/stdtypes.html#str.lower). Exempel:
```python
input: "Anagram", "Magarna"     output: "Match"
input: "Paris", "sirap"         output: "Match"
input: "Nope", "note"           output: "No Match"
```

6. Menyval **10** - `get_acronym`: Akronym skapare. Marvin ska be om en sträng och skapa en akronym för den genom att plocka ut alla stora bokstäver och sätta ihop till en ny sträng. Tips, [isupper()](https://docs.python.org/3/library/stdtypes.html#str.isupper). Exempel:
```python
input: "BRöderna Ivarsson Osby"             output: "BRIO"
input: "Ingvar Kamprad Elmtaryd Agunnaryd"  output: "IKEA"
```

7. Menyval **11** - `mask_string`: Sträng maskering. Skapa ett nytt val där Marvin ber om en sträng och ersätter alla utom de fyra sista karaktärerna med “#”. Exempel:
```python
input: "4556364607935616"     output: "############5616"
input: "64607935616"          output: "#######5616"
```

Till detta menyvalet ska du också skapa funktionen `multiply_str`. `multiply_str` funktionen ska ta emot två argument, det första ska vara en sträng och det andra ett heltal. Funktionen ska multiplicera strängen med heltalet och returnera strängen som skapas.

Skriv koden i `mask_string` så att `multiply_str` används för att skapa delen av strängen med `#`.

Använd också `multiply_str` i funktionen för menyval **3**.



8. Testa, validera och publicera din kod enligt följande.

```bash
# Flytta till kurskatalogen
dbwebb test marvin2
dbwebb validate marvin2
dbwebb publish marvin2
```

Rätta eventuella fel som dyker upp och publicera igen. När det ser grönt ut så är du klar.



Extrauppgift {#extra}
-----------------------
[INFO]
För att inkludera dina extrauppgifter i testerna behöver du skicka med option `-e` eller `--extra`.
[/INFO]


* Menyval **b1** - `points_to_grade`: Poäng till betyg, Marvin ska fråga efter maxpoäng samt dina poäng och sedan ska Marvin skriva ut vilket betyg dina poäng motsvarade. Använd betygsskalan:
```
Score   Grade
>= 90%    A
>= 80%    B
>= 70%    C
>= 60%    D
<  60%    F
```
Formatera output enligt `score: <betyg>`.
```python
input: "100", "59"     output: "score: F"
input: "70", "50"     output: "score: C"
```

* Menyval **b2** - `has_strings`: Gör så Marvin kan ta emot fyra strängar, den första strängen ska jämföras med de andra tre. Kolla om den första strängen börjar med den andra, innehåller den tredje och slutar med den sista. Lösningen ska vara case-sensitive, med andra ord `A != a`. Tips, [startswith()](https://docs.python.org/3/library/stdtypes.html#str.startswith), [endswith()](https://docs.python.org/3/library/stdtypes.html#str.endswith) Exempel:
```python
input: "anagram", "ana", "agr", "am"        output: "Match"
input: "isogram", "is", "gra", "m"          output: "Match"
input: "Palindrom", "par", "ind", "rom"     output: "No match"
```


Tips från coachen {#tips}
-----------------------

Felsöka med debuggern/Thonny och komplettera med utskrifter av `print()`.

Validera ofta. Så slipper du en massa valideringsfel i slutet av övningen.

Lycka till och hojta till i forumet om du behöver hjälp!

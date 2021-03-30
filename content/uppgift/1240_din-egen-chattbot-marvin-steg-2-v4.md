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

Du kan grunderna i Pythons stränghantering och du har gjort den [första delen](uppgift/din-egen-chattbot-marvin-steg-1-v4) av Marvin.



Krav {#krav}
-----------------------
[INFO]
Taggarna för varje uppgift motsvarar själva menyvalet. För att testa Menyval **28** kan man då använda `--tags=8`, för Menyval **b1** `--tags=b1` osv.
[/INFO]


1. Kopiera din Marvin från föregående kursmoment och utgå från den koden.

```bash
# Flytta till kurskatalogen
cd me
cp -ri kmom02/marvin1/marvin.py kmom03/marvin2/
cd kmom03/marvin2
```

2. Skapa en ny fil `main.py`, den ska innehålla koden för while-loopen och vilket val som görs. marvin.py ska innehålla all kod som körs när ett val är gjort, alltså varje enskilt vals kod. Importera marvin.py i main.py.

3. Skriv om koden så att menyn och varje menyval finns i en egen funktion. All kod ska ligga i funktioner, den enda koden som inte ska ligga i en funktioner är `if __name__ == "__main__":` i slutet av main.py.

4. Menyval **8**: Kasta om bokstäver. Marvin ska be dig skriva in ett ord som sedan slumpmässigt kastas om. Det omkastade ordet ska sedan skrivas ut.

5. Menyval **9**: Anagram. Skapa ett val där marvin ber om två strängar och kollar om de är anagram. Ett anagram är när man kan få fram samma sträng genom att kasta om bokstäverna i den andra. Tips, [sorted()](https://docs.python.org/3/howto/sorting.html) och [lower()](https://docs.python.org/3/library/stdtypes.html#str.lower). Exempel:
```python
input: "Anagram", "Magarna"     output: "Match"
input: "Paris", "sirap"         output: "Match"
input: "Nope", "note"           output: "No Match"
```

6. Menyval **10**: Akronym skapare. Marvin ska be om en sträng och skapa en akronym för den genom att plocka ut alla stora bokstäver och sätta ihop till en ny sträng. Tips, [isupper()](https://docs.python.org/3/library/stdtypes.html#str.isupper). Exempel:
```python
input: "BRöderna Ivarsson Osby"             output: "BRIO"
input: "Ingvar Kamprad Elmtaryd Agunnaryd"  output: "IKEA"
```

7. Menyval **11**: Sträng maskering. Skapa ett nytt val där Marvin ber om en sträng och ersätter alla utom de fyra sista karaktärerna med “#”. Exempel:
```python
input: "4556364607935616"     output: "############5616"
input: "64607935616"          output: "#######5616"
```

8. Validera och publicera Marvin genom att göra följande kommandon i kurskatalogen i terminalen.

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
För att inkludera dina extrauppgifter i testerna behöver du skicka med argumentet `-e` eller `--extra`.
[/INFO]


* Menyval **b1**: Poäng till betyg, Marvin ska fråga efter maxpoäng samt dina poäng och sedan ska Marvin skriva ut vilket betyg dina poäng motsvarade. Kika på övning 3.3 i boken [Python for Informatics](kunskap/boken-python-for-informatics-exploring-information).

* Menyval **b2**: Gör så Marvin kan ta emot fyra strängar, den första strängen ska jämföras med de andra tre. Kolla om den första strängen börjar med den andra, innehåller den tredje och slutar med den sista. Tips, [startswith()](https://docs.python.org/3/library/stdtypes.html#str.startswith), [endswith()](https://docs.python.org/3/library/stdtypes.html#str.endswith) Exempel:
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

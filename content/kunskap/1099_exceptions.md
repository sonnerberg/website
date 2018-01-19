---
author: lew
revision:
    "2018-01-09": (A, lew) First version.
category:
    - oopython
...
Exceptions i Python
===================================

[FIGURE src=/image/oopython/kmom04/exceptions_top.png?w=c8 class="right"]

Det finns två vanliga fel, eller *errors*, som man kan snubbla över i Python. Det är *syntax errors* och *exceptions*. Vi ska titta närmare på exceptions och hur vi kan jobba med dem.

<!--more-->  



Intro {#intro}
-------------------------------

En stor fördel med exceptions är att de tvingar fram en utskrift när något går fel. Med egna exceptions kan vi tvinga fram egna uaölkjgjsdgjafdsjkgdfg


Errors {#errors}
-------------------------------

###Syntax Errors {#syntax-errors}

Det vanligaste felet är syntax errors (ibland parsing errors). Det uppstår när syntaxen är fel och programmet inte kan köras. Ett exempel är följande kod:

```
>>> if 100 < 5 print("Oj då...")
  File "<stdin>", line 1
    if 100 < 5 print("Oj då...")
                   ^
SyntaxError: invalid syntax
```

Felet visar oss vilken fil det handlar om (i detta fallet interpretatorn). Den lilla pilen pekar på den tidigaste gången felet upptäcktes på raden och vanligen är den felaktiga koden i delen före pilen. Här handlar det om att if-satsen inte startar med `:`.



###Built-in Exceptions {#built-in-exceptions}

Även om syntaxen är korrekt så finns det fel som bara hittas när programmet exekveras. Då handlar det om exceptions. Det kan handla om att en variabel inte är definierad eller att man adderar en siffra med en sträng. Ett exempel på ImportError:

```
>>> from Nangijala import Skorpan
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
ImportError: No module named 'Nangijala'

```

Här kastas felet *ImportError* och vi får information om var i filen felet uppstår och ett meddelande: "No module named 'Nangijala'". Hjälpsamt och trivsamt.

Det finns många inbyggda exceptions som hjälper oss att se vad som blivit fel. Några av de vanligaste är:

| Exception     | Meddelande                             |
| ------------- | :--------------------------------      |
| ImportError   |  No module named 'something'           |
| IndexError    |  list index out of range               |
| KeyError      |  *the_key* (tex my_dict["the_key"])    |
| NameError     |  name '*variable name*' is not defined |

Kika i [dokumentationen](https://docs.python.org/3/library/exceptions.html) för fler exceptions.



###try except {#try-och-except}

När man pratar om felhantering stöter man på termer som att *kasta ett exception* (throw exception) och *fånga ett exception* (catch exception). När man kastar ett exception så talar man om att det har blivit ett fel och definierar vilket fel som ska uppbringas. Sedan fångar man felet och agerar därefter. I Python kallas det *raise*



Extend Exception {#extend-exception}
-------------------------------

Vi kan skapa egna exceptions genom att ärva från basklassen `Exception` och tvinga fram dem vid behov. Det kan hända att vi vill kunna tvinga fram fel som i vanliga fall inte är ett fel. Först skapar vi en egendefinierad basklass för våra *custom exceptions*:

```python
class Error(Exception):
   """User defined class for custom exceptions"""
   pass
```
Vi ser att den ärver från klassen Exception och därmed möjligheten att skicka med ett meddelande som kan skrivas ut när felet kastats.


Förutsättning {#pre}
-------------------------------
<!--
Du har läst delen om GET och POST i guiden "[Php på 20 steg](kunskap/kom-i-gang-med-php-pa-20-steg#globals)" eller vet vad det innebär.  
Du har läst artikeln om "[Flask och Jinja2](kunskap/flask-och-jinja2)".  
Du har läst artikeln om "[SQLAlchemy](kunskap/sqlalchemy)".   -->







Avslutningsvis {#avslutning}
------------------------------

Det var det hela. Smidigt och strukturerat. Prova gärna att lägga till fler funktioner i tabellen, tex sortering eller visa max antal och paginering.

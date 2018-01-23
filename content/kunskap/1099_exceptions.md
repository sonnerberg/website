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



raise Exception {#raise-exception}
-------------------------------

När man pratar om felhantering stöter man på termer som att *kasta ett exception* (throw exception) och *fånga ett exception* (catch exception). När man kastar ett exception så talar man om att det har blivit ett fel och definierar vilket fel som ska uppbringas. Sedan fångar man felet och agerar därefter. I Python kallas det *raise* exception, och kan med fördel användas i en try/except. Det är då i `try:` man kastar ett exception och fångar det i `except:`.

För att själv tvinga fram det använder vi `raise`:

```
>>> raise Exception("Something happened!")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
Exception: Something happened!
```

Vi ser ovan att man kan skicka med ett meddelande till Exception som skrivs ut. I följande stycke tar vi reda på hur man kan skapa egna exceptions och använda dem i ett sammanhang.


Extend Exception {#extend-exception}
-------------------------------

Vi kan som sagt skapa egna exceptions. Det gör vi genom att ärva från basklassen `Exception` och tvinga fram dem vid behov. Det kan hända att vi vill kunna tvinga fram fel som i vanliga fall inte är ett fel.

Ponera att vi ska skapa ett spel, där man ska gissa på ett nummer och får för varje gång reda på om vi gissat för lågt eller för högt.

Först skapar vi en egendefinierad basklass för våra *custom exceptions*, eller *extended exceptions*. Ett vanligt sätt är att samla dem i en fil, exceptions.py eller errors.py.

```python
class Error(Exception):
   """User defined class for custom exceptions"""
   pass
```

Det är inget krav att vi skapar en egen basklass utifrån Exception. Det är dock en god standard så vi nöjer oss med det. Vi ser att den ärver från klassen Exception och därmed möjligheten att skicka med ett meddelande som kan skrivas ut när felet kastats.

Vi vill ha exceptions för när man gissat för högt och för lågt, så vi fyller på vår klass-fil med två klasser till:

```python
class ValueTooLowError(Error):
   """Raised when the input value is too low"""
   pass

class ValueTooHighError(Error):
   """Raised when the input value is too high"""
   pass
```

Nu har vi ett exception för varje fel som vi vill tvinga fram. Studera main.py och se hur vi kan tvinga fram våra exceptions:

```python
#!/usr/bin/env python3

"""
Main file for testing exceptions
"""
import random
from exceptions import ValueTooLowError
from exceptions import ValueTooHighError

rand_val = random.randint(1, 100)

while True:
    try:
        in_val = int(input("Ange siffra: "))

        if in_val < rand_val:
            raise ValueTooLowError
        elif in_val > rand_val:
            raise ValueTooHighError
        break
    except ValueTooLowError:
        print("För lågt, prova igen!")

    except ValueTooHighError:
        print("För högt, prova igen!")

print("Siffran {} är rätt!".format(in_val))
```

Ett alternativ är att byta `print("...")` mot att skicka med meddelandet direkt till respektive exception, `raise ValueTooHighError("För högt, prova igen!")`.



Avslutningsvis {#avslutning}
------------------------------

Nu har vi tittat på hur vi kan skapa egna exceptions, så kallade *custom exceptions* eller *extended exceptions*. Vill du läsa mer kan du göra det i [dokumentationen](https://docs.python.org/3/tutorial/errors.html)

---
author: aar
revision:
    "2020-01-16": "(B, aar) Finputsad inför VT20."
    "2018-11-18": "(A, aar) Första versionen, uppdelad av större dokument."
...
Instansmetoder
==================================

En metod är en funktion som är definierad inuti en klass. Det finns tre typer: instans-, statisk- och klassmetod. Vi har redan skapat en instansmetod i form av `__init__()`. Vi kollar lite mer på instansmetoder.



Instansmetoder {#instansmetoder}
----------------------------------

Instansmetoder identifieras på att den första parametern heter `self`, oftast. I instansmetoder använder man sig av instansattributen, om man vill ha en metod i en klass där man inte behöver använda instansattributen skapar men en statisk metod istället.



### Instansmetod 

Vi skapar en metod som returnerar en formaterad sträng med information om bilen.

[FIGURE src=/image/oopython/guide/car_instans_meth.png? class="right" caption="Klassdiagram över Car med instansmetod."]

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1
        self.car_nr = Car.car_count

    def present_car(self):
        return "The model {m} costs {p}$.".format(
            m=self.model, p=self.price
        )
```

Metoden `present_car()` har enbart `self` som argument. I metoden använder vi bara värden från `self` parametern. Vi kollar på hur vi anropar metoden.

```
volvo = Car("volvo v40", 40000)
print(volvo.present_car())
The model volvo v40 costs 40000$.
```

Notera att vi inte skickade med något argument till metoden i anropet. Detta är vad som utgör en instansmetod, Python skickar automatiskt objektet, som metoden anropades på, som första argument till metoden. I koden ovanför när vi kör `volvo.present_car()`, i `present_car(self)` metoden är `self` vårt `volvo` objekt.

Vi kan egentligen döpa om `self` till vad vi vill, det är bara ett parameternamn. Men i Python är det standard att döpa den till self. I många andra språk kallar man den `this`. Testa byt namn på `self` i metoden och kör koden igen för att se att den fortfarande fungerar.

Vi kan självklart skicka med fler argument till metoden om vi vill det, i metod definitionen lägga vi bara till fler parametrar efter self. I anropet skickar vi in argument som vanligt, men då tilldelas de till parametrarna efter `self` i parameterlistan.

```
    def present_car(self, test, test2):
        return "The model {m} costs {p}$. {t1}, {t2}".format(
            m=self.model, p=self.price, t1=test, t2=test2
        )

car = Car("volvo v40", 40000)
print(car.present_car("hej", "hej"))
The model volvo v40 costs 40000$. hej, hej
```

Ta bort test parametrarna innan ni fortsätter.

Precis som vi såg i förra delen, att vi inte kan komma åt ett instansattribut från klassen kan vi inte komma åt en instansmetod från klassen heller. Man måste anropa metoden på en objekt/instans av en klass.

```
car = Car("volvo v40", 40000)
Car.price
    Car.price
    AttributeError: class Car has no attribute 'price'
```

```
car = Car("volvo v40", 40000)
Car.present_car
    print(car.present_car("hej", "hej"))
    TypeError: unbound method present_car() must be called with Car instance as first argument (got str instance instead)
```

Om ni tycker att felmeddelandet låter konstigt kan ni fråga på föreläsningen varför felet är formulerat så.

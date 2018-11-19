---
author: aar
revision:
    "2018-11-18": "(A, aar) Första versionen, uppdelad av större dokument."
...
Metoder
==================================

En metod är en funktion som är definierad inuti en klass. Det finns tre typer: instans-, statisk- och klassmetod. Vi har redan skapat en instansmetod i form av `__init__()`. Vi kollar lite mer på instansmetoder.



Instansmetoder {#instansmetoder}
----------------------------------
Tidigare använde vi dot-notation för att komma åt attributen i ett objekt. Men vanligvis brukar man inom objektoerienterad programmering inte använda det utanför instansen. Utan då använda man sig at get- och set metoder som man har skapat för varje attribut. Vi börjar med att skapa get metoder för våra attribut.



### Get metoder 

En "get" metod för ett attribut brukar oftast enbart returnerar attributets värde. 

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1

    def get_model(self):
        return self.model

    def get_price(self):
        return self.price
```

Vi skapade två get metoder, en för varje attribut. I och med att de enbart ska returnera ett attributs värde behövs bara `self` som parameter, så vi kommer åt rätt instans värde.

Vi testar att använda metoderna.

```
>>> print(bmw.get_model())
BMW

>>> print(bmw.get_price())
100000
```



### Set metoder 

Då tittar vi på "set" och precis som ni gissar så används oftasts "set" metoder för att ändra värdet på attribut. En "set" metod brukar enbart tilldela ett argument till ett attribut.


```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1

    def get_model(self):
        return self.model

    def get_price(self):
        return self.price

    def set_model(self, model):
        self.model = model

    def set_price(self, price):
        self.price = price
```

Att skapa set metoder var inte svårare än så. Låt oss testa använda dem också.

```
>>> print(bmw.set_model("BMW X2"))
>>> print(bmw.get_model())
BMW X2

>>> print(bmw.set_price(500000))
>>> print(bmw.get_price())
500000
```



### Instansmetod

Get och set metoderna vi har skapat nu är exempel på instansmetoder. Instansmetoder identifieras på att den första parametern är `self`. I instansmetoder använder man sig av instansattributen, om man vill ha en metod i en klass där man inte behöver använda instansattributen skapar men en statisk metod istället. Vi kommer kolla på det längre fram i guiden.

Vi skapar en till instansmetod, en för att skriva ut information om bilen:

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1

    ...
    
    def present_car(self):
        print("Model: {m}, Price: {p}".format(m=self.model, p=self.price))
```

Nu kan vi använda den på följande sätt:

```python
>>> bmw.present_car()
Model: BMW X2, Price: 500000

>>> volvo.present_car()
Volvo, Price: 150000
```

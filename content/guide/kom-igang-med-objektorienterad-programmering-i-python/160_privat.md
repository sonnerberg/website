---
author: aar
revision:
    "2021-01-13": "(B, aar) Omskriven och la till stycke om property decorator."
    "2020-01-16": "(A, aar) Första versionen, separerade privata attribut från mangling för att få in i kmom01."
...
Information hiding
==================================

Information hiding är när man gömmer intern data, så att den inte kan användas på fel sätt eller utanför den egna klassen. Låt oss säga att vi har en klass som har ett attribut som innehåller någon känslig data. Då vill vi inte att det ska gå att använda den hur som helst. Vi vill kanske kontrollera hur värdet sätts, man måste göra en speciell uträkning för att få ett nytt värde, eller att värdet bara är hemligt och man ska inte komma åt det utanför instansmetoder. Vi vill kunna begränsa tillgången till attribut eller metoder utanför klassdefinitionen.

Det finns tre olika klassificeringar inom klassisk objektorientering, publik, skyddad och privat. Men Python följer inte det till hundra utan här har vi istället publik, skyddad och "manglad" [name mangling](https://docs.python.org/3.7/tutorial/classes.html#private-variables). I tabellen nedanför finns en kort sammanfattning av vad de betyder. Här kommer vi gå igenom typen skyddad och vi går igenom manglad i [information hiding del2](guide/kom-igang-med-objektorienterad-programmering-i-python/230_information_hiding_2). Än så länge har alla våra attribut och metoder varit publika.

| Implementation | Typ     | Syfte                                                                                 |
|----------------|---------|---------------------------------------------------------------------------------------|
| name           | publik  | Kan användas hur som helst, var som helst och av vem som helst.                       |
| _name          | skyddad | Använd inte om du inte vet vad du gör. Använd på egen risk (utanför klassen).         |
| __name         | manglad | Hindra subklasser från att överskugga metoder och attribut.                           |



Privata attribut och metoder {#privatAttributMetoder}
--------------------------------------------------------


Som jag skrev ovan så finns inte _privat_ på samma sätt i Python som det finns i andra språk. Inom de flesta andra programmeringsspråk, när ett attribut är privat går det inte att använda det attributet i kod som inte ligger i den egna klassen. T.ex. i vår Car klass om vi gör `price` till ett privat attribut skulle vi inte kunna skriva `volvo.price` (om vi har ett Car objekt som ligger i variabeln volvo) men i en metod i klassen skulle vi kunna använda `self.price`.

I python finns bara en överenskommelse att attribut/metoder vars namn börjar med ett `_` ska klassas som "privata". Vilket innebär att du ska bara använda attributen/metoderna om du verkligen vet vad du gör eller om du måste. Detta uppfyller mer kraven för typen skyddad, men i och med att det inte finns privat används både privat och skyddad för samma sak i Python.

`_<namn>` Används för att markera att en metod/attribut inte är en del av det publika api:et och den ska generellt sätt inte ändras eller användas utanför instansen. Det finns dock inget som stoppar någon från att göra det.

Vi kan ta priset på bilar som exempel. Priset i sig är inte hemligt men vi vill kontrollera hur det kan ändras. Vi vill att datan fortfarande ska vara tillgängligt i det publika API:et, det ska gå att läsa värdet och ändra det, men vi vill begränsa vilket pris som får sättas. T.ex. ska det inte gå att ändra värdet på en bil hur som helst efter att det är satt, man får kanske max sänka priset med en viss procent. Om attributet då är publikt finns det inget som skyddar priset från att ändras utan att det uppfyller priskravet.

Om vi har ett sälj system där säljare kan sänka priset på produkter under black friday, om vi inte använder privata attribut eller metoder kanske någon skriver liknande kod.

```python
class SellSystem():

    ...
    def set_temporary_sale(self, new_price, time, numberplate):
        self.cars[numberplate].price = new_price
        self.sale_end_date = time

```

Metoden sänker priset på en vissa bil under en vissa tid. `self.cars` är en dictionary med bilar där nummerplåtarna är nycklar till Car objekten som är värden. Här är `price` attributet publikt och vilken kod som helst kan ändra värdet och använda det. Om vi tänker oss att vi har en bil som kosta 200,000 och under black friday ska de sänka priset med 10,000 men säljaren är trött och råkar skriva in 100,000 istället, rätt stor skillnad på slutpriset. Om vi gör `price` till ett privat attribut och skapar en metod som måste användas när man ska ändra värdet kan vi lägga in en check som kollar att sänkningen aldrig är mer än 70% t.ex.

Vi uppdaterar Car så att price är privat och skapar en set och en get metod för attributet.

[FIGURE src=/image/oopython/guide/car_priv_attr.png? class="right" caption="Klassdiagram över Car med instansmetod."]

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self._price = price

        Car.car_count += 1
        self.car_nr = Car.car_count

    def get_price(self):
        return self._price

    def set_price(self, new_price):
        if float(new_price) / float(self._price) > 0.7:
            self._price = new_price
            print(f"New price is {self._price}")
        else:
            raise ValueError("New price is too low. You can max lower it with 30%")
```

Vi bytte namn på `price` till `_price` för att markera det som privat. Användningen av attributet ska kontrolleras av `get_price` och `set_price`. Get och set metoder är klassiskt inom objektorientering, vi använder dem för att kapsla in datan i ett objekt och styra dess användning. Man kan tycka att här behöver vi egentligen inte någon get method i och med att den bara returnerar värdet. Men i och med att attributet är privat ska vi ha det ändå. Bara för att förstärka att man inte ska använda attributet direkt. Vi testar använda den nya koden också.

```python
car = Car("volvo v40", 40000)
print(car._price)
40000
print(car.get_price())
40000
car.set_price(35000)
New price is 35000
car.set_price(10000)
ValueError: New price is too low. You can max lower it with 30%

print(car.present_car())
AttributeError: 'self' object has no attribute 'price'
```

Som ni ser kan vi egentligen fortfarande använda `car._price` men vi ska inte och det ger valideringsfel, `Access to a protected member _price of a client class (protected-access)`. Nu får vi fel när vi använder oss av `present_car` och även `__add__` och `__iadd__`. De metoderna använder fortfarande `price`. Vi behöver nu uppdatera de metoderna, bara för att vi i efterhand ändrade price till ett privat attribut. Det finns ett mer pythonic sätt att hantera privat/set/get metoder, vilket vi kommer kolla på längre ner.

Vi kan också göra metoder privata med `_` på samma sätt som attribut. Det görs oftast på metoder som bara används av andra metoder i en klass. T.ex. gör någon speciell uträkning men den kräver ett sammanhang som ges utav att en annan metod körs först. Så då vill vi inte att metoden ska vara tillgänglig som en publik metod. Genom att göra metoden privat visar vi för andra utvecklare att metoden inte ska användas.




Pythonic get() och set() {#pythonic}
-------------------------------------

Vi skrev om vår kod vilket gjorde att vi nu har flera metoder som inte längre fungerar. Det är jobbigt och gör att vi behöver uppater våra metoder till att använda `_price` istället för `price`. Vi kan sätta detta i ett större perspektiv. Tänk om vi jobbar i ett stor system med 100+ klasser med 10+ utvecklare som skriver koden. Hur hade vår ändring ovanför påverkat alla andra klasser? All annan kod utanför vår Car klass som använde `price` attributet slutar också att fungera. Vilket gör att med vår ändring hade vi också behöver leta upp alla andra ställen i systemet som använder `price` och uppdatera den koden till att använda vår getter och setter metoder.

Stycket ovanför beskriver hur man gör i de flesta andra OO programmeringsspråken, privata attribut får en `get_attributename` och en `set_attributename` metod. Där get returnerar värdet och set ändrar värdet. Men det ställer ju till problem om vi gör en sen tidigare attribut publik till privat för då ändrar vi på det publika API:et för klassen. Python har så klart ett mer Pythonic sätt att göra det på som dessutom inte introducerar en ändring i det publika API:et.



## property decorator {#property}

Vi lär oss en till decorator, tidigare kollade vi på `@staticmethod` som gör att en metod blir statisk. Nu ska vi lära oss `@property` decorator.

Vi har den gamla lösningen med get och set.

```python
class Car():
    ...
    def __init__(self, model, price):
        ...
        self._price = price

    ...

    def get_price(self):
        return self._price

    def set_price(self, new_price):
        if float(new_price) / float(self._price) > 0.7:
            self._price = new_price
            print(f"New price is {self._price}")
        else:
            raise ValueError("New price is too low. You can max lower it with 30%")

```

Vi börjar med att göra get method pythonic med `@decorator`.

```python
class Car():
    ...
    
    @property
    def price(self):
        print("getter method called")
        return self._price

>>> car = Car("volvo", 200000)
>>> print(car.price)
getter method called
200000
>>> print(car._price)
200000
```

Magic!

`price()` metoden anropas utan att vi skriver med `()`. Det är en av effekterna av `@property` decorator. Vi har `_price` som ett privat attribut och skyddar det samtidigt som vi har kvar det publika API:et med `price`, fast det är egentligen en metod.

Vi gör också set metoden till en decorator.

```python
class Car():
    ...

    @property
    def price(self):
        print("getter method called")
        return self._price

    @price.setter
    def price(self, new_price):
        print("setter method called")
        if float(new_price) / float(self._price) > 0.7:
            self._price = new_price
            return "New price is " + str(self._price)
```

Här använder vi en annan decorator, `@price.setter`. När vi använder `@property` på `price` metoden skapas ett property objekt och `car.price` är egentligen det objektet och inte metoden. Fast det objektet anropar vår metod när koden försöker läsa objektet som ett värde, `car.price`. `@price.setter` gör att set moden för `price` läggs till i price objektet och anropas om koden tilldelar till det objektet, `car.price = x`.

Vi kollar hur det ser ut när vi använder det i koden.

```python
>>> car = Car("volvo", 200000)
>>> car.price = 180000
setter method called
>>> print(car.price)
getter method called
180000
>>> car.price = 50000
setter method called
ValueError: New price is too low. You can max lower it with 30%
```

Python anropar olika metoder baserat på hur vi använder attributet i koden, om vi läser eller tilldelar. Nu har vi samma funktionalitet som med get och set metoden samtidigt som vår kod har kvar det publika API:et vilket gör att vår ändring från publik till privat inte förstör annan kod som använder Car objekt. Även de andra metoderna som inte fungerade förut fungerar igen.

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self._price = price

        Car.car_count += 1
        self.car_nr = Car.car_count

    @property
    def price(self):
        print("getter method called")
        return self._price

    @price.setter
    def price(self, new_price):
        print("setter method called")
        if float(new_price) / float(self._price) > 0.7:
            self._price = new_price
        else:
            raise ValueError("New price is too low. You can max lower it with 30%")

    def present_car(self):
        return "The model {m} costs {p}$.".format(
            m=self.model, p=self._price
        )

    def __add__(self, other):
        if isinstance(other, Car):
            return self.price + other.price
        if isinstance(other, int):
            return self.price + other
        raise ValueError("Car doesn't not support addition with object")

    def __iadd__(self, other):
        if isinstance(other, Car):
            self.price += other.price
            return self
        if isinstance(other, int):
            self.price += other
            return self
        raise ValueError("Car doesn't not support addition with object")

    @staticmethod
    def calculate_price_reduction(price):
        return int(price * 0.66)

    def reduce_price(self):
        self.price = self.calculate_price_reduction(self.price)
        return "Priset för {m} är nu {p}.".format(m=self.model, p=self.price)

    @classmethod
    def wheel_message(cls):
        print("A car normally have {nr} wheels".format(nr=cls.wheels))


>>> car = Car("volvo", 200000)
>>> print(car.present_car())
The model volvo costs 200000$.
>>> print(car + 1000)
getter method called
201000
>>> car += 3100
getter method called
setter method called
>>> print(car.price)
getter method called
203100
```

Om ni har svårt att hänga med i alla anrop, kopiera in koden i **Thonny eller annan debugger** och stega igenom koden! Det kommer hjälpa er att förstå koden mycket bättre än att bara titta på den och exekvera den.

För en längre och lite mer djupgående förklaring av `@property` kan ni läsa [Python @property decorator](https://www.programiz.com/python-programming/property).

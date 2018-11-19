---
author: aar
revision:
    "2018-11-19": "(A, aar) Första versionen, uppdelad av större dokument."
...
Operatoröverlagring
==================================

Operatorer inom programmering (`+, -, *, /, <, >` med flera), har ett förutbestämt syfte och vi är vana vi att vi kan använda dem fungerar på våra värden. Men när vi skapar egna klasser gömmer vi datan i objekt och då kan vi bara addera eller subtrahera två objekt och förväta oss att det ska fungera. Vidare har ofta våra objekt flera attribut med olika värden. Hur ska Python veta vilka av attributen som ska användas vid uträkningrna?

Här kommer **operatoröverlagring** in i bilden. När vi använder en operator, "+, -, /, \*", så är det en hemlig metod som anropas och exekverar, som med `__init__()`. I våra egenskapade klasser kan vi skriva över dessa metoderna och på så sätt bestämma vad som ska ske när man använder en operatorn.



Addition {#add}
----------------------------------

 Låt säga att vi vill kunna addera våra bil-objekt och få reda på det sammanlagda priset. Först testar vi rakt av:

```python
>>> bmw = Car("BMW", 100000)
>>> volov = Car("Volvo", 150000)
>>> print( bmw + volvo )
TypeError: unsupported operand type(s) for +: 'Car' and 'Car'
```

Det gick inte så bra. `+`-operatorn vill ju ha siffror och inte objekt. Metoden som anropas vid `+` operatorn heter `__add__()`, Vi lägger till en metod som överlagrar operatorn i klassen:

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1

    def present_car(self):
        print("Model: {m}, Price: {p}".format(m=self.model, p=self.price))

    @staticmethod
    def calculate_price_reduction(aPrice):
        return int(aPrice * 0.66)

    def reduce_price(self):
        self.price = self.calculate_price_reduction(self.price)
        return "Priset för {c} är nu {p}".format(c=self.model, p=self.price)

    def __add__(self, other):
        return self.price + other.get_price()
```

Vi använder `__` före och efter metoden, `__<method>__`, och lägger till parametern `other`. När vi skriver `bmw + volvo` utgår vi från objektet till vänster om `+`. Så `self` innehåller "bmw" instansen och `other` innehåller "volvo". Vi testar köra det igen med vår nya metod:

```python
>>> print( bmw + volvo )
250000

>>> print( volvo + bmw )
250000
```

Nu har vi överlagrat vår första operator. Det är ett programmerat beteende i Python att leta efter en `__add__()` metod och anropa den när man använder `+` operatorn och det finns en specifik metod för varje operator. Även för jämförelse operatorerna som `==, <, > <= >=` m.m, med de metoderna kan vi programmera hur två objekt av klassen Car avgör t.ex. vilket objekt som är störst eller minst. Vid subtraktion heter den metoden t.ex. `__sub__()` och vid `==` heter den `__eq__()`. Alla går att hitta i [Pythons dokumentation](https://docs.python.org/3/library/operator.html). 

Med operatorer som `+=` och `-=` behöver man tänka efter på ett annat sätt så vi kollar på hur det ser ut när man överlagrar `+=`. 

Additions tilldelning {#iadd}
----------------------------------

Även kallat _additions tilldelnings operatorn_, metoden som vi behöver överlagra heter `__iadd__()`. Innan vi börjar koda den ska vi tänka efter vad det är operatorn betyder och vad den ska göra. `x += y` är samma sak som att skriva `x = x + y`. Så vår metod behöver göra en vanlig addition, uppdatera det det vänstra objektet med det nya värdet och returnera self instansen. Vi får inte glömma att det är en metod som anropas vilket kommer att returnera ett värde som kommer tilldelas till variabeln till vänster. Om vi inte returnerar något kommer variabeln få `None` som värde efter man gör operationen. För vårt exempel med priset på bilar betyder det att den ska addera priset på två bilar, sätta priset på det vänstra objektet till summan och returnera instansen. 

Vi lägger till koden för det, men försök gärna själv först. Skapa en ny instansmetod som heter `__iadd__(self, other)` som uppdaterar `price` i `self` med summan av deras priser och returnerar `self`.

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1

    def present_car(self):
        print("Model: {m}, Price: {p}".format(m=self.model, p=self.price))

    @staticmethod
    def calculate_price_reduction(aPrice):
        return int(aPrice * 0.66)

    def reduce_price(self):
        self.price = self.calculate_price_reduction(self.price)
        return "Priset för {c} är nu {p}".format(c=self.model, p=self.price)

    def __add__(self, other):
        return self.price + other.get_price()

    def __iadd__(self, other):
        self.price += other.get_price()
        return self

print(bmw.get_price())
100000

print(volvo.get_price())
250000

bmw += volvo
print(bmw.get_price())
250000

print(volvo.get_price())
150000
```

`bmw += volvo` kan även visualiseras som `bmw = bmw.__iadd__(volvo)`. Med andra ord tilldelar vi `bmw` variablen samma objekt som den redan hade.

Nu så. Samma koncept gäller för övriga operatorer och kan vara behändigt vid hantering av klasser av olika slag.

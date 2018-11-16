---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Klass
==================================

Vi skapar en egen klass med statiska- och instansattribut och instansierar två objekt av klassen.



Skapa en klass {#skapa-en-klass}
------------------------------

Låt oss gå igenom hur man skapar en bil klass, "Car". För enkelhetens skull hoppar jag över [docstrings](https://en.wikipedia.org/wiki/Docstring) i artikeln. En klass skapas med:  

```python
class Car():
```



### Statiska attribut

Något som "alla" bilar har gemensamt är att de har 4 hjul, så vi skapar ett _statiskt attribut_ som innehåller hur många hjul alla bilar har. Vi lägger även till ett statiskt attribut som vi använder som en räknare för att hålla koll på hur många objekt vi har skapat av klassen. _statiska attribut_ innehåller värden som är gemensamma för alla objekt av klassen till skillnad från _instansattribut_ som är individuella för varje objekt av klassen.

```python
class Car():
    wheels = 4
    car_count = 0
```

Sådär ja, vad fint det blev. Vi går vidare till att lägga till instansattribut som ska innehålla data som vi vill ska vara personlig för varje objekt. De statiska attributen som ligger här ägs av bas-klassen Car.



### Instansattribut

Instans attribut skapar vi i _konstruktorn_; metoden som körs när en ny instans skapas. Alla bilar kommer ha 4 hjul men övriga attribut kan skilja sig mellan objekten. Konstruktormetoden heter `__init__` och den måste ha parametern `self` först i parameterlistan. "self" används för att referera till objektet som konstruktorn ska skapa. Vi fyller på med instansattribut för modell och pris. I och med att `__init__`-metoden används för att skapa nya objekt av vår klass är det ett bra ställe att öka `car_counter` med 1. Då kommer `car_counter` öka med 1 varje gång vi skapar ett nytt Car objekt:

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price

        Car.car_count += 1
```

För att vi ska kunna initiera objekten med individuella värden har vi en parameter för varje instansattribut och tilldelar de argumenten som skickas med till våra instansattribut. I början av konstruktorn kan vi se `self` som ett nytt tomt objekt, det innehåller bara en koppling till att det tillhör klassen Car. Inne i `__init__` konstruerar vi vad objektet ska innehålla och vilken data som ska finns i objektet. Raden `self.model = model` gör att objektet (self) får ett attribut som heter "model" och det attributet tilldelas ett värde som har skickats med, parametern model. Raden under gör samma sak fast med ett attribut som heter "price" istället. Sist i konstruktorn ökar vi det statiska attributet `car_count` som ligger i klass Car med 1. 

Nu har vi ett objekt/en instans av Car klassen som innehåller två attribut med specifika värden. Vi kollar hur det ser ut när vi anropar konstruktorn, skapar objektet och skriver ut dess innehåll.

```python
>>> bmw = Car("BMW", 100000)
```

Nu har vi skapat en instans av klassen Car med 4 hjul, märket BMW och med ett pris på 100.000. Förhoppningsvis la du märke till att vi aldrig anropade `__init__()` och vi skickade bara med två argument medan konstruktorn har 3 parametrar. `__init__()` är en så kallad magisk funktion, vi kommer gå igenom dem mer i nästa kmom. Kort sagt ska vi inte anropa den själva utan Python gör det automatiskt när vi anropar klassen, `Car()`. Vidare till argumenten, vi ska inte själva skicka med något argument för första parametern i konstruktorn, `self`, utan det gör Python automatiskt. Vi behöver bara skicka med värden för de resterande två parametrarna.

Vi skapar ytterligare en instans av Car klassen:

```python
>>> volvo = Car("Volvo", 150000)
```

Vi testar att skriva ut objekten:

```python
>>> print(bmw)
<__main__.Car object at 0x7f824cc7b4e0>

>>> print(volvo)
<__main__.Car object at 0x7f824cc7b4a8>

>>> print("Antal bilar: {antal}".format(antal=Car.car_count))
Antal bilar: 2
```

Det ser ju bra ut. Två instanser av "Car" som inte refererar till samma minnesplats, vilket betyder att det är två separat objekt med olika värden. Vi ser också att räknaren fungerar.



För att komma åt attributen kan vi använda så kallad dot-notation, vi tittar på hur det kan se ut.

```python
>>> print(bmw.wheels)
 4

>>> print(bmw.model)
BMW

>>> print(volvo.model)
Volvo
```
instansattribut
Vi ska dock inte använda oss av dot-notation utanför klasserna i kursen utan i nästa sektion visar vi hur man jobbar med attributen via metoder istället.

"bmw" är en instans av Car, så om vi ändrar attributet `wheels` i efterhand, så ändras den för alla objekt skapade från klassen:

```python
>>> print(Car.wheels)
4
>>> print(volvo.wheels)
4
>>> print(bmw.wheels)
4

>>> Car.wheels = 12

>>> print(Car.wheels)
12
>>> print(volvo.wheels)
12
>>> print(bmw.wheels)
12

>>> bmw.wheels = 1

>>> print(volvo.wheels)
12
>>> print(Car.wheels)
12
>>> print(bmw.wheels)
1
```

Om du var uppmärksam hängde du med på att i sista utskrifterna hade bmw inte samma värde som volvo och Car. Man kan inte tilldela värden till statiska attribut via objekt, `bmw.wheels`. Då lägger man till ett nytt instansattribut i bara det objektet med det nya värdet. Medan klassen, Car, och alla andra instanser, volvo, har kvar det statiska attributet och det värdet. Därför hade inte `bmw` samma utskrift på slutet.
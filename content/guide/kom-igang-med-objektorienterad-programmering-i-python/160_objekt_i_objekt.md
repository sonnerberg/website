---
author: aar
revision:
    "2018-11-19": "(A, aar) Första versionen, uppdelad av större dokument."
...
Objekt i objekt
==================================

Vi går ett steg längre och skapar en till klass vars objekt vi lägger i objekt av en annan klass. Vi ska gå in på det mer i senare delar av guiden men vi börjar med det lite smått här. Det är egentligen inget speciellt, vi har redan gjort det, t.ex. för instans attributet `model`. Strängar är också objekt det är bara det att vi inte skapat klassen för dem själva. Utan klassen finns redan i Python och det skapas ett nytt objekt av den klassen när vi skriver t.ex. `"Jag skapar nu ett nytt str objekt"`, sträng klassen heter `str` i Python. Så egentligen är det inget speciellt vi kollar på nu, det är bara att vi har skapat klassen själva.

Vi kollar även lite snabbt på något som heter List comprehension i slutet.



Ny klass {#ny_klass}
----------------------------------

Vi skapar en ny klass för extrautrustning i bilarna så vi kan ha koll på vad bilarna har för extra utrustning. Vi döper den till `Equipment` och ger den instansattributen `price`, `type_`, och `name`. Tanken är att vi ska skapa objekt av `Equipment` som ligger i `car` objekt. Notera att vi har variabeln `type_`, egentligen vill vi att den ska heta `type` men det finns en inbyggd funktion i Python med samma namn och den vill vi inte skriva över (då klagar valideringen). Enligt [PEP8](https://www.python.org/dev/peps/pep-0008/#descriptive-naming-styles), som vi följer när vi skriver vår kod, ska man då ha ett `_` efter variabelnamnet. 

[FIGURE src=/image/oopython/guide/eqp_class.png class="right" caption="Klassdiagram över klassen Equipment."]

```python
class Equipment():

    def __init__(self, name, type_, price):
        self.type_ = type_
        self.price = price
        self.name = name

    def get_price(self):
        return self.price

    def get_name(self):
        return self.name

    def get_type(self):
        return self.type_
```

Nu har vi grunder för en fullutrustad bil, men vi behöver koppla Equipment objekt till Car objekt. Tanken är att ett Car objekt ska kunna innehålla X antal Equipment objekt så vi lägger till ett nytt instansattribut i Car som innehåller en tom lista. Vi skapar även en ny instansmetod i Car där vi skapar och lägger till nya Equipment objekt i listan.

[FIGURE src=/image/oopython/guide/car_eqp.png class="right" caption="Klassdiagram över klassen Car med Equpment."]

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price
        self.equipment = []

        Car.car_count += 1
    
    def add_equipment(self, name, type_, price):
        temp = Equipment(name, type_, price)
        self.equipment.append(temp)

    ...
```

Så ja nu testar vi köra koden och lägger till lite utrustning i en bil.

```python
>>> volvo = Car("Volvo", 150000)
>>> volvo.add_equipment("Bluetooth", "Entertainment", 2000)
>>> volvo.add_equipment("7 inch display", "Entertainment", 10000)
>>> volvo.equipment[0].get_name()
Bluetooth

>>> volvo.equipment[0].get_price()
2000
```

Vi går vidare med att lägga till en funktion som räknar ut totalvärdet av ett Car objekt, inkludera priset för utrustningen. För att göra detta på ett snabbt och Pythonic sätt ska vi använda oss av List comprehension.



List comprehension {#comprehension}
----------------------------------

[List comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) är ett sätt att skapa listor, oftast utifrån värden i en annan lista vi gör någon operation på. I vårt exempel vill vi skapa en ny lista som bara innehåller priserna för varje Equipment objekt i `equipment` listan. Som vi sen kan addera och använda för att räkna ut totalvärdet på ett Car objekt. Jag lägger till instansmetoden `get_total_value()` i Car.

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price
        self.equipment = []

        Car.car_count += 1
    
    def get_total_value(self):
        equipment_prices = [eqp.price for eqp in self.equipment]
        return self.price + sum(equipment_prices)
    ...

>>>volvo.get_total_value()
162000
```
`[eqp.price for eqp in self.equipment]` är vår list comprehension, det består av hakparenteser och innehåller ett uttryck efterföljt av en for-loop definition, sen kan den innehålla 0 eller flera if-satser. Man kan alltså få in if-satser också men vi har inte det i vårt exempel. List comprehension returnerar alltid en lista. `eqp.price` är vårt uttryck som ska uttföras på varje element i den gamla listan och värdet som uttrycket producerar vill vi ska läggas till i den nya listan som returneras. `for eqp in self.equipment` är for-loopen, vi itererar över varje element i listan `self.equipment` och lägger i variabeln `eqp`. 

Om vi inte hade använt list comprehension hade vi gjort på följande sätt:

```python
    ...
    
    def get_total_value(self):
        equipment_prices = []
        for eqp in self.equipment:
            equipment_prices.append(eqp.price)

        return self.price + sum(equipment_prices)

    ...
```

List comprehension är ett snabbt sätt att få ner tre rader till en. Vi testar lägga till en till tycker jag. Metoden `present_car()` borde också visa vad för utrustning bilen har. Så jag lägger till en ny metod i `Equipment` klassen som returnerar en formaterad sträng och sen lägger jag till den i utskriften i metoden `present_car()` för alla instanser av Equipment.

```python
class Equipment():

    def __init__(self, name, type_, price):
        self.type_ = type_
        self.price = price
        self.name = name

        ...
        
        def get_info(self):
            return "Name: {}, Type: {}, Price: {}".format(self.name, self.type_, self.price)


class Car():
    ...
    
    def present_car(self):
        equipment_info = "\n".join([eqp.get_info() for eqp in self.equipment])
        info = "Model: {m}, Price: {p}\nEquipment:\n{e}".format(m=self.model, p=self.price, e=equipment_info) 
        print(info)

>>>volvo.present_car()
Model: Volvo, Price: 150000
Equipment:
Name: Bluetooth, Type: Entertainment, Price: 2000
Name: 7 inch display, Type: Entertainment, Price: 10000
```

I detta exemplet anropar vi `get_info()` på varje element i `self.equipment`, detta läggs i en lista som vi gör om till en sträng med `"\n".join()`.



All kod {#all_kod}
----------------------------------

Jag visar upp hela koden vi har producerat här.

[FIGURE src=/image/oopython/guide/eqp_complete.png class="right" caption="Klassdiagram över klassen Equipment."]

```python
class Equipment():

    def __init__(self, name, type_, price):
        self.type_ = type_
        self.price = price
        self.name = name

    def get_price(self):
        return self.price

    def get_name(self):
        return self.name

    def get_type(self):
        return self.type_

    def get_info(self):
        return "Name: {}, Type: {}, Price: {}".format(self.name, self.type_, self.price)

```

```python
class Car():
    wheels = 4
    car_count = 0

    def __init__(self, model, price):
        self.model = model
        self.price = price
        self.equipment = []

        Car.car_count += 1

    def present_car(self):
        equipment_info = "\n".join([eqp.get_info() for eqp in self.equipment])
        info = "Model: {m}, Price: {p}\nEquipment:\n{e}".format(m=self.model, p=self.price, e=equipment_info) 
        print(info)

    @staticmethod
    def calculate_price_reduction(aPrice):
        return int(aPrice * 0.66)

    def reduce_price(self):
        self.price = self.calculate_price_reduction(self.price)
        return "Priset för {c} är nu {p}".format(c=self.model, p=self.price)

    def add_equipment(self, name, type_, price):
        temp = Equipment(name, type_, price)
        self.equipment.append(temp)

    def __add__(self, other):
        return self.price + other.get_price()

    def __iadd__(self, other):
        self.price += other.get_price()
        return self
```

[FIGURE src=/image/oopython/guide/car_complete.png caption="Klassdiagram över klassen Car."]


Testa koden, lek runt med den så du förstår vad som sker och hur man kommer åt attribut och anropar metoder.

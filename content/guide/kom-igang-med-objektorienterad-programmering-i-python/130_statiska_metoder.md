---
author: aar
revision:
    "2020-01-16": "(B, aar) Finputsad inför VT20."
    "2018-11-18": "(A, aar) Första versionen, uppdelad av större dokument."
...
Statiska metoder
==================================

I förra delen lärde vi oss att Python alltid skickar med den egna instansen som argument till metoder i en klass (som vi döper till _self_ i parameterlistan). Detta är för att när man jobbar objektorienterat behöver man oftast använda instansen som en metod anropas på. Men ibland vill man ha metoder som inte använder en instans av en klass i en metod. Detta är oftast "hjälp" funktioner som man vill ha kopplade till en klass.

Om vi bara skapar en vanlig instansmetod fast vi använder bara inte `self` parametern i metoden skulle det fungera men då kommer valideringen klaga med felet `Method could be a function (no-self-use)`. Här kommer _statiska metoder_ in i bilden. Det är en metod som ligger i en klass där Python inte automatisk skickar med instansen som första argumentet. Till statiska metoder skickas argument till metoden likadant som det fungerar för vanliga funktioner. 



Lägg till en statisk metod i klassen {#statiskmetod}
----------------------------------

Man brukar säga att en bil förlorar 1/3 av sitt värde när man lämnar bilfirman med bilen. Så vi skapar en statisk metod som tar bort 1/3 av ett pris, samt en instansmetod som använder den statiska metoden:

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

    @staticmethod
    def calculate_price_reduction(aPrice):
        return int(aPrice * 0.66)

    def reduce_price(self):
        self.price = self.calculate_price_reduction(self.price)
        return "Priset för {m} är nu {p}.".format(m=self.model, p=self.price)
```

[FIGURE src=/image/oopython/guide/car_statik_meth.png caption="Klassdiagram över Car med statisk metod."]

Du kan troligen gissa vilken av det två nya metoderna som är den statiska. För att skapa en statisk metod behöver man skriva `@staticmethod` på raden ovanför metod definitionen. `@staticmethod` kallas för en **decorator**, det är något som dynamiskt ändrar funktionaliteten på en funktion. I detta fallet gör den så att Python inte skickar med den egna instansen som det första argumentet till metoden. Alltså så att vi inte behöver ha med parametern `self` i parameterlistan. 
Det kan tyckas konstigt att vi sen även skapat en instansmetod som bara anropar den statiska. Men att vi gör så ger oss en slags abstraktion, vi kan använda den statiska metoden utan att vi behöver ha ett Car objekt för att dra av 1/3 av en summa. Men oftast kommer vi vilja använda metoden i samband med ett Car objekt. Därför skapar vi även instansmetoden för att spara några rader kod och göra den mer DRY. 

Vi använder funktionerna.

```python
>>> print( Car.calculate_price_reduction(200000) )
132000

>>> bmw = Car("BMW", 100000)

>>> print( bmw.reduce_price() )
Priset för BMW är nu 66000

>>> print( bmw.calculate_price_reduction(200000) )
132000
```

Som du ser kan vi även använda den statiska metoden direkt från klassen. Vi behöver inte ha skapat något objekt av klassen för att använda metoden.

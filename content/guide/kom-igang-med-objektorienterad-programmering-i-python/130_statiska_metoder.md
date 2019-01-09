---
author: aar
revision:
    "2018-11-18": "(A, aar) Första versionen, uppdelad av större dokument."
...
Statiska metoder
==================================


En metod i ett klassobjekt använder oftast parametern _self_ och tillhör därför varje instans. Vill man ha en mer generell metod som inte behöver vara enskilt beroende utav instanserna kan man använda _statiska metoder_. Det är metoder som man vill ha kopplade till klassen men de använder sig inte av instansen.



Lägg till en statisk metod i klassen {#statiskmetod}
----------------------------------

 Man brukar säga att en bil förlorar 1/3 av sitt värde när man lämnar bilfirman med bilen. Så vi skapar en statisk metod som tar bort 1/3 av ett argument, samt en instansmetod som använder den statiska metoden:

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
```

[FIGURE src=/image/oopython/guide/car_statik_meth.png caption="Klassdiagram över Car med statisk metod."]

Du kan troligen gissa vilken av det två nya metoderna som är den statiska. För att skapa en statisk metod behöver man skriva `@staticmethod` på raden ovanför metod definitionen. `@staticmethod` kallas för en **decorator**, det är något som dynamiskt ändrar funktionaliteten på en funktion. I detta fallet gör den så att Python inte skickar med den egna instansen som det första argumentet till metoden. Alltså så att vi inte behöver ha med parametern `self` i parameterlistan. 
Det kan tyckas konstigt att vi sen även skapat en instansmetod som bara anropar den statiska. Men att vi gör så ger oss en slags abrstraktion, vi kan använda den statiska metoden utan att vi behvöver ha ett Car objekt för att dra av 1/3 av en summa men oftast kommer vi vilja använda metoden i samband med ett Car objekt. Därför skapar vi även instansmetoden för att spara några rader kod och göra den mer DRY. 

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

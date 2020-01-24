---
author: aar
revision:
    "2020-01-24": "(B, aar) Tog bort del om private som nu är i eget dokument."
    "2018-11-27": "(A, aar) Första versionen, uppdelad av större dokument."
...
Information hiding del 2
==================================

Information hiding är när man gömmer intern data, så att den inte kan användas på fel sätt eller utanför den egna klassen. Låt oss säga att vi har en klass som har ett attribut som innehåller någon känslig data. Då vill vi inte att det ska gå att använda den hur som helst. Vi vill kanske kontrollera hur värdet sätts, man måste göra en speciell uträkning för att få ett nytt värde, eller att värdet bara är hemligt och man ska inte komma åt det utanför instansmetoder. Vi vill kunna begränsa tillgången till attribut eller metoder utanför klassdefinitionen.

I första delen gick vi igenom skyddad eller private, i denna delen ska vi kolla på "manglad" eller [name mangling](https://docs.python.org/3.7/tutorial/classes.html#private-variables). I tabellen nedanför finns en kort sammanfattning av vad de betyder. Efter den går vi igenom de olika mer noggrant. 

| Implementation | Typ     | Syfte                                                                                 |
|----------------|---------|---------------------------------------------------------------------------------------|
| name           | publik  | Kan användas hur som helst, var som helst och av vem som helst.                       |
| _name          | skyddad | Använd inte om du inte vet vad du gör. Använd på egen risk                            |
| __name         | manglad | Hindra subklasser från att överskugga metoder och attribut.                           |



Name mangling {#nameMangling}
------------------------------

Vi utgår från koden i första delen

[FIGURE src=/image/oopython/guide/vid_mov_priv_attr.png class="right" caption="Klassdiagram över Video och Movie med privat attribut."]

```python
class Video():

    def __init__(self, title, length, revenue):
        self.title = title
        self.length = length
        self._revenue = revenue
        
    ...
    
    def get_revenue(self): 
        return self._revenue

class Movie(Video):

    def __init__(self, title, length, revenue, director, rating):
        super().__init__(title, length, revenue)

        self.director = director
        self.rating = rating

    ...
>>> charlie = Video("Charlie bit my finger", 1, 10000)
>>> dogs = Movie("Isle of Dogs", 101, 64241499, "Wes Anderson", 8.0)

>>> charlie.get_revenue()
10000
>>> charlie._revenue
10000

>>> dogs.get_revenue()
64241499
>>> dogs.revenue
64241499
```

Name mangling är då till för att förhindra en subklass från att använda/skriva över en metod/attribut i basklassen. Dock är det vanligt att utvecklare använder `__` för att göra attribut "privata", men det ska man inte.
En metod med `__` i början kan "bara" användas i instansen den skapas i, med `self.__<namn>`. Detta är en egenskap privata attribut/metoder har i många andra programmeringsspråk, men inte i python, och därför är det lätt hänt att `__` används istället för `_`.

Jag tänker att man drar 30% av skatten på inkomster för alla typer av videos. Vi lägger till en publik metod för att öka inkomsten och en med name mangling för dra 30% på de nya intäkterna. I och med att vi inte kan komma åt metoden med name mangling utanför instansen behöver vi en publik metod som anropas den andra.

```python
class Video():

    ...

    def __draw_tax(self, revenue):
        self._revenue += revenue * 0.7
        print("New revenue is: {}".format(self._revenue))

    def add_revenue(self, money):
        self.__draw_tax(money)



>>> charlie.__draw_tax(10000)
AttributeError: 'Video' object has no attribute '__draw_tax'

>>> charlie.add_revenue(10000)
New revenue is: 17000
```

Som ni ser kan vi komma åt `__draw_tax()` genom metoden `add_revenue()` i instansen med `self.__draw_tax()`.  
Vi testar att överskugga metoden i Movie för att sänka skatten:

[FIGURE src=/image/oopython/guide/vid_mov_name_mangl.png class="right" caption="Klassdiagram över Video och Movie med name mangling."]

```python
class Video():

    ...

    def __draw_tax(self, revenue):
        self._revenue += revenue * 0.7
        print("New revenue is: {}".format(self._revenue))

    def add_revenue(self, money):
        self.__draw_tax(money)

class Movie(Video):

    ...

    def __draw_tax(self, revenue):
        self._revenue += revenue * 0.9
        print("Lowered taxes and new revenue is: ".format(self._revenue))

>>> dogs.add_revenue(1500000)
New revenue is: 65291499
```

Utskriften visar att subklassen använder`__draw_tax()` metoden från basklassen även om det finns en metod med samma namn i subklassen. Jämför det med hur `print_info()` och `to_string()` fungerar.

```python
class Video():
    ...

    def to_string(self):
        return  "{title} is {length} minute(s) long".format(
                title=self.title,
                length=self.length,
        )

    def print_info(self):
        print(self.to_string())

    def __draw_tax(self, revenue):
        self._revenue += revenue * 0.7
        print("New revenue is: {}".format(self._revenue))

    def add_revenue(self, money):
        self.__draw_tax(money)

class Movie(Video):

    ...

    def to_string(self):
        return  "{base_msg}, has the director {dir} and a rating of {rating}".format(
            base_msg=super().to_string(),
            dir=self.director,
            rating=self.rating
        )

    def __draw_tax(self, revenue):
        self._revenue += revenue * 0.9
        print("Lowered taxes and new revenue is: ".format(self._revenue))


>>> charlie.print_info()
Charlie bit my finger is 1 minute(s) long
>>> dogs.print_info()
Isle of Dogs is 101 minute(s) long, has the director Wes Anderson and a rating of 8.0
>>> charlie.add_revenue()
New revenue is: 17000.0
>>> dogs.add_revenue(1500000)
New revenue is: 65291499
```

För `to_string()` används den överskuggade metoden i subklassen medan för `__draw_tax()` används inte den "överskuggade" metoden i subklassen utan där används metoden från basklassen. Detta är för att vi inte har använt name mangling på `to_string()` och då kan vi faktiskt överskugga metoden från basklassen.

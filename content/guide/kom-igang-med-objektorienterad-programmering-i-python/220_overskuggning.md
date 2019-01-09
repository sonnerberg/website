---
author: aar
revision:
    "2018-11-26": "(A, aar) Första versionen, uppdelad av större dokument."
...
Överskuggning av metoder
==================================

Överskuggning är att skriva över en metod från en basklass i en subklass för att anpassa funktionaliteten för subklassen. I vårt fall, skapa en metod som heter `print_info` i Movie som tar med `director` och `rating`.



Överskugga `print_info()` {#overskugga}
--------------------------------------------------

Vi kopierar `print_info()` från Video, klistar in den i Movie klassen och lägger till director och rating i utskriften.

```python
class Video():

    def __init__(self, title, length):
        self.title = title
        self.length = length

    def print_info(self):
        print("{title} is {length} minute(s) long".format(
                title=self.title,
                length=self.length,
        ))

class Movie(Video):

    def __init__(self, title, length, director, rating):
        super().__init__(title, length)

        self.director = director
        self.rating = rating

    def print_info(self):
        print("{title} is {length} minute(s) long, has the director {dir} and a rating of {rating}".format(
                title=self.title,
                length=self.length,
                dir=self.director,
                rating=self.rating
        ))

>>> charlie = Video("Charlie bit my finger", 1)
>>> dogs = Movie("Isle of Dogs", 101, "Wes Anderson", 8.0)

>>> charlie.print_info()
Charlie bit my finger is 1 minutes long
>>> dogs.print_info()
Isle of Dogs is 101 minute(s) long, has the director Wes Anderson and a rating of 8.0
```

Som vi ser, när `charlie.print_info()` anropas körs metoden `print_info()` i Video klassen och när `dogs.print_info()` anropas körs `print_info()` i Movie klassen. Detta är effekten av att överskugga en metod i en subklass.

Men nu har vi lite kod som är samma på två ställen. Det hade varit snyggare om vi inte behöver ha med `title` och `lenght` i `print_info` i subklassen utan istället återanvända metoden från basklassen. Det kan vi såklart göra. Vi kan använda `super()` för att komma åt basklassens metoder, så det vi kan göra är att anropa `print_info()` i Video från `print_info()` i Movie. 

```python
class Movie(Video):

    ....

    def print_info(self):
        super().print_info()
        print(", has the director {dir} and a rating of {rating}".format(
                dir=self.director,
                rating=self.rating
        ))

>>> charlie.print_info()
Charlie bit my finger is 1 minutes long
>>> dogs.print_info()
Isle of Dogs is 101 minute(s) long
, has the director Wes Anderson and a rating of 8.0
```

Utskriften blev inte så snygg för Movie instansen, det är för att vi gör en print i båda utan att formatera det på ett snyggt sätt. Vi snyggar till det genom att flytta skapandet av strängen till en egen metod, en klassisk `to_string()` metod.

[FIGURE src=/image/oopython/guide/vid_mov_overl_meth.png class="right" caption="Klassdiagram över Video och Movie med överskuggning."]

```python
class Video():

    ...

    def to_string(self):
        return "{title} is {length} minute(s) long".format(
                title=self.title,
                length=self.length,
        )

    def print_info(self):
        print(self.to_string())
    
class Movie(Video):

    ...

    def to_string(self):
        return "{base_msg}, has the director {dir} and a rating of {rating}".format(
            base_msg=super().to_string(),
            dir=self.director,
            rating=self.rating
        )

    def print_info(self):
        print(self.to_string())

>>> charlie.print_info()
Charlie bit my finger is 1 minutes long
>>> dogs.print_info()
Isle of Dogs is 101 minute(s) long, has the director Wes Anderson and a rating of 8.0
```

Vi har lagt till metoden `to_string()` i båda klasserna. I subklassen Movie använder vi `super().to_string()` för att anropa `to_string()` i basklassen och på så sätt få strängen med title och length.

Nu har vi två metoder som ser exakt likadana ut, `print_info()`. Den anropar bara `to_string()` och skriver ut strängen som returneras. Vi kan faktiskt ta bort metoden i subklassen, Movie, så vi bara har den i Video. Om vi gör det, när man anropar `dogs.print_info()` anropas metoden som ligger i basklassen och i metoden när `self.to_string()` anropas är `self` ett Movie objekt och har därför en reference till `to_string()` i Movie och inte i Video när det anropas. 

Vi tar en snabb kik på hur hela koden för båda klasserna ser ut och att utskrifterna fungerar som de ska.
```python
class Video():

    def __init__(self, title, length):
        self.title = title
        self.length = length

    def to_string(self):
        return  "{title} is {length} minute(s) long".format(
                title=self.title,
                length=self.length,
        )

    def print_info(self):
        print(self.to_string())
    
class Movie(Video):

    def __init__(self, title, length, director, rating):
        super().__init__(title, length)

        self.director = director
        self.rating = rating

    def to_string(self):
        return  "{base_msg}, has the director {dir} and a rating of {rating}".format(
            base_msg=super().to_string(),
            dir=self.director,
            rating=self.rating
        )

>>> charlie = Video("Charlie bit my finger", 1)
>>> dogs = Movie("Isle of Dogs", 101, "Wes Anderson", 8.0)

>>> charlie.print_info()
Charlie bit my finger is 1 minute(s) long
>>> dogs.print_info()
Isle of Dogs is 101 minute(s) long, has the director Wes Anderson and a rating of 8.0
```



Abstract Method {#abstract_method}
--------------------------------------------------

Ibland vill man tvinga en subklass att överskugga en metod från basklassen. Det kan vara för att man vill påminna någon att metoden behöver implementeras, en så kallad TO-DO, eller kan metoden vara en så kallad *abstract method*. En abstrakt metod är en metod som är deklarerad men innehåler inte någon implementation. Den är tillför att skapa en struktur eller mall som subklassen behöver uppfylla.

Vi kan skapa en abstrakt metod med `_NotImplementedError_`. För att testa detta lägger vi till en metod i Video klassen, där vi lyfter ett `_NotImplementedError_`, och överskuggar inte metoden i Movie:


```python
class Video():

    ...

    def mustOverride(self):
        raise NotImplementedError("Subclasses must implement this!")


>>> charlie.mustOverride()
NotImplementedError: Subclasses must implement this!

>>> dogs.mustOverride()
NotImplementedError: Subclasses must implement this!
```

Precis som vi förväntade oss får vi `runtimeException` både från charlie och dogs. För att fixa detta behöver vi överskugga `mustOverride()` i Movie.
Nackdelen med "NotImplementedError" är att vi inte kan lägga någon funktionalitet i `mustOverride()` metoden i Video. Den kommer alltid bara slänga `NotImplementedError`. Men det är också tanken, `NotImplementedError` ska bara användas när metoden inte ska implementeras i basklassen.

```python
class Movie(Video):
    ...
    def mustOverride(self):
        print("Abstract method is overridden")

>>> charlie.mustOverride()
NotImplementedError: Subclasses must implement this!

>>> dogs.mustOverride()
Abstract method is overridden
```

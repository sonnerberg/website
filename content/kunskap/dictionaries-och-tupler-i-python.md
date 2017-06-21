---
author: efo
category: python
revision:
  "2017-06-21": (A, efo) Första utgåvan inför kursen python H17.
...
Dictionaries och tupler i Python
==================================

[FIGURE src=image/python/dictionary.jpg?w=c5 class="right"]

Vi har tidigare bekantat oss med listor som ett sätt att spara data som har ett samband. Vi har sätt att varje element i listan får ett numerisk index och att vi kan hämta ut data med hjälp av detta index. Vi har även sett att det går att stega sig igenom listan med en `for`-loop. Ibland vill man inte använda sig av ett numerisk index, men däremot en nyckel som pekar ut ett värde.



<!--more-->



Kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/dictionary) och här på [dbwebb](repo/python/example/dictionary).



Nycklar och värden {#nyckel}
--------------------------------------

I övningen [Kom igång med datatypen lista i Python](kunskap/kom-igang-med-datatypen-lista-i-python) skapade vi listor för att representera en shoppinglista. Vi ska i denna övning flytta fokus från den som handlar till butikens lager och titta på hur vi med hjälp av en `dictionary`, även kallat `dict`, kan representera lagret. Dictionaries finns i många olika programmeringsspråk och kallas ofta associativa arrayer eller hashmaps.

Vår råa data ser ut på följande sätt:

```bash
20 st. köttfärs
80 st. grädde
33 st. krossade tomater
42 st. gul lök
```

Vi har alltså en vara men även ett antal av den specifika varan. Vi vill alltså koppla ihop varan (vår nyckel) med antalet av den varan (vårt värde). Låt oss titta på hur vi gör detta med en `dictionary`.

```python
warehouse = {
    "köttfärs" : 20,
    "grädde" : 80,
    "krossade tomater": 33,
    "gul lök" : 42
}

print(warehouse["krossade tomater"])

# skriver ut: 33
```

Vi definerar en `dictionary` med hjälp av `{}` sen anges nyckeln ett kolon och sen värdet. Mellan varje nyckel-värde par har vi ett komma för att separera paren. Efter att vi har definerat `warehouse` hämtar vi ut lagersaldot för krossade tomater. Detta göras genom att använda `[]` med nyckeln och vi får då tillbaka värdet.

Varje måndag får vår lilla butik leverans av nya varor och då måste lagersaldot uppdateras och nya nyckel-värde par måste läggas i.

```python
warehouse["krossade tomater"] = 58

warehouse["röd lök"] = 7

print(warehouse)

# skriver ut: {'grädde': 80, 'köttfärs': 20, 'krossade tomater': 58, 'röd lök': 7, 'gul lök': 42}
```

Vi ser ovan att både uppdatering av befintliga nyckel-värde par och skapande av nya görs med samma kommando. Finns nyckeln uppdateras värdet annars läggs det till ett nyckel-värde par. Precis som med listor har vi möjligheten att stega oss igenom en `dictionary`. Vi använder funktionen `items()` för att hämta ut nyckel och värde samtidigt.

```python
for key, value in warehouse.items():
    print(key, value)

# skriver ut:
# krossade tomater 58
# köttfärs 20
# gul lök 42
# röd lök 7
# grädde 80
```



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna övning skapat ett oerhört simpelt lager där vi kan hålla koll på vad som finns i vår lilla butik.

---
author: efo
category: python
revision:
  "2018-06-27": (B, efo) Uppdaterad med sortering baserad på value.
  "2017-06-21": (A, efo) Första utgåvan inför kursen python H17.
...
Dictionaries och tupler i Python
==================================

[FIGURE src=image/python/dictionary.jpg?w=c5 class="right"]

Vi har tidigare bekantat oss med listor som ett sätt att spara data som har ett samband. Vi har sett att varje element i listan får ett numerisk index och att vi kan hämta ut data med hjälp av detta index. Vi har även sett att det går att stega sig igenom listan med till exempel en `for`-loop. Ibland vill man inte använda sig av ett numerisk index, men däremot en nyckel som pekar ut ett värde och i denna övning ska vi titta på hur vi kan göra detta med hjälp av dictionaries.



<!--more-->



Kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/dictionary) och här på [dbwebb](repo/python/example/dictionary).



Nycklar och värden {#nyckel}
--------------------------------------

I övningen [Kom igång med datatypen lista i Python](kunskap/kom-igang-med-datatypen-lista-i-python) skapade vi listor för att representera en shoppinglista. Vi ska i denna övning flytta fokus från den som handlar till butikens lager och titta på hur vi med hjälp av en dictionary, även kallat `dict`, kan representera lagret. Dictionaries finns i många olika programmeringsspråk och kallas även associativa arrayer eller hashmaps.

Vår råa data ser ut på följande sätt:

```bash
20 st. köttfärs
80 st. grädde
33 st. krossade tomater
42 st. gul lök
```

Vi har alltså en vara men även ett antal av den specifika varan. Vi vill alltså koppla ihop varan (vår nyckel) med antalet av den varan (vårt värde). Låt oss titta på hur vi gör detta med en dictionary.

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

Vi definerar en dictionary med hjälp av `{}` sen anges nyckeln, ett kolon och sen värdet. Mellan varje nyckel-värde par har vi ett komma för att separera paren. Efter att vi har definerat `warehouse` hämtar vi ut lagersaldot för krossade tomater. Detta görs genom att använda `[]` med nyckeln och vi får då tillbaka värdet.

Varje måndag får vår lilla butik leverans av nya varor och då måste lagersaldot uppdateras och nya nyckel-värde par måste läggas i.

```python
warehouse["krossade tomater"] = 58

warehouse["röd lök"] = 7

print(warehouse)

# skriver ut: {'grädde': 80, 'köttfärs': 20, 'krossade tomater': 58, 'röd lök': 7, 'gul lök': 42}
```

Vi ser ovan att både uppdatering av befintliga nyckel-värde par och skapande av nya görs med samma kommando. Finns nyckeln uppdateras värdet annars läggs det till ett nytt nyckel-värde par. Precis som med listor har vi möjligheten att stega oss igenom en dictionary. Vi använder funktionen `items()` för att hämta ut nyckel och värde samtidigt.

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

Vi noterar att nyckel-värde paren skrivs ut i en konstig ordning, inte alls som vi skrev in paren ovan. Detta är för att datastrukturen dictionary är osorterat och vi kan aldrig räkna med ordningen i en dictionary.

[INFO]
Från och med python 3.6 är dictionaries ["insertion ordered"](https://docs.python.org/3.6/whatsnew/3.6.html#new-dict-implementation). Det betyder att nyckel-paren är sparade i ordningen de läggs in i dictionaryn. Som när man gör append() på en lista för att lägga till nya värden.

Om någon är intresserad av hur det är implementerat kan ni läsa en [överskådlig förkling](https://stackoverflow.com/a/39980744).
[/INFO]



### Sortering av dictionary {#sort}

Om vi vill ha ut värdena sorterat använder vi oss av funktionen `keys()` som returnerar alla nycklar. Vi kan sedan sortera nycklerna med samma sorteringsfunktioner som vi använde för listor. I exemplet nedan använder vi nyckeln för att hämta ut värdet från `warehouse`.



#### Sortering på key {#sort-key}

```python
for key in sorted(warehouse.keys()):
    print(key, warehouse[key])

# skriver ut:
# grädde 80
# gul lök 42
# krossade tomater 58
# köttfärs 20
# röd lök 7
```

`warehouse.keys()` funktionen returnerar `['köttfärs', 'grädde', 'krossade tomater', 'gul lök']`. Som vi sorterar med `sorted()` och loopar igenom, då kan vi använda nycklarna i loopen för att plocka ut värdena. Vilket ger oss dictionariens innehåll sorterat på nycklarnas värde i bokstavsordning.

Om vi istället vill sortera på antal varor, value, för att se vilka varor vi har flest av kräver det lite mer. Vi kan använda funktionen [itemgetter](https://docs.python.org/3/library/operator.html#operator.itemgetter) från den inbyggda modulen [operator](https://docs.python.org/3/library/operator.html#module-operator).



#### Sortering på value {#sort-value}

`itemgetter`  funktionen behöver värdena istället för nycklarna från dictionarien. För det kan vi använda funktionen `.items()` på vår dictionary.

<!-- ### förklara hur sorteringen funkar!  så de kan använda den på dictionaries och tupler... kolla hur jag löst emission.-->
<!-- ```python
print(warehouse.items())
f = itemgetter(0)
print(f([('köttfärs', 20), ('grädde', 80), ('krossade tomater', 33), ('gul lök', 42)]))

f2 = itemgetter(1)
print(f2([('köttfärs', 20), ('grädde', 80), ('krossade tomater', 33), ('gul lök', 42)]))

for x in warehouse.items():
    print(f(x), end=" ")
    print(f2(x))

print(sorted(warehouse.items(), key=itemgetter(1)))

print(sorted(warehouse.items(), key=itemgetter(1), reverse=True))

for key, value in sorted(warehouse.items(), key=itemgetter(1), reverse=True):
    print(key, value)
``` -->
```python
from operator import itemgetter

for key, value in sorted(warehouse.items(), key=itemgetter(1), reverse=True):
    print(key, value)

# skriver ut:
# grädde 80
# krossade tomater 58
# gul lök 42
# köttfärs 20
# röd lök 7
```

Vi ser ovan att vi inte importerar hela operator modulen enbart itemgetter delen. Vi använder `itemgetter` för att hämta ut värdet istället för nyckeln. Hade vi angett `key=itemgetter(0)` hade vi fått nyckeln istället. Vi använder `reverse=True` för att sortera i fallande ordning. `reverse=False` sorterar i stigande ordning.



<!-- #### Visa .values() också? -->

### Dictionaries i dictionaries

<!-- LÄgg till här? kolla hur jag använder dicts i dicts i uppgiften. -->

På ett riktigt lager räcker det inte bara med antal varor som är kvar, vi vill även ha en möjlighet att ange priset. Med dictionaries, precis som med listor, har vi möjligheten att skapa dictionaries i dictionaries, så kallade nestlade dictionaries. Detta gör att vi kan ha både antalet och ett pris för varje vara. Vi kan nu skriva ut en sorterad lista med pris på följande sätt.

```python
warehouse_deluxe = {
    "köttfärs" : { "stock" : 20, "price" : 50 },
    "grädde" : { "stock" : 80, "price" : 20 },
    "krossade tomater": { "stock" : 33, "price" : 10 },
    "gul lök" : { "stock" : 42, "price" : 5 }
}

for key in sorted(warehouse_deluxe.keys()):
    print(key, warehouse_deluxe[key]["price"])

# skriver ut:
# grädde 20
# gul lök 5
# krossade tomater 10
# köttfärs 50
```

För de som är intresserade finns ett litet exempel i Pythons [dokumentation för dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries).



Tupler {#tuples}
--------------------------------------
Ibland vill man ha en sekvens av data som inte ska eller kan ändras. I Python använder man tupler (tuples på engelska) för att åstadkomma detta. Tupler är en sekvens av data som kan vara av olika typer och vi skapar en tupel med hjälp av `()`. Tupler kan inte ändras men vi kan hämta ut data med hjälp av index för datat med samma notation (`[index]`) som för en lista. I vårt lager vill vi att varje vara ska ha en streckkod och ett internt lager nummer, dessa ska aldrig ändras så vi väljer att använda en tupel för denna data. I exemplet nedan har vi definerat en nyckel `ids` i varje element i `warehouse_deluxe` och som värde för nyckeln har vi en tupel. Vi lägger igen till "röd lök" i vårt lager och vi avslutar exemplet med att skriva ut en formatterad sträng med alla varor i lagret.

```python
warehouse_deluxe = {
    "köttfärs" : { "stock" : 20, "price" : 50, "ids" : (1234, "K14") },
    "grädde" : { "stock" : 80, "price" : 20, "ids" : (3141, "L12") },
    "krossade tomater": { "stock" : 33, "price" : 10, "ids" : (4224, "E13") },
    "gul lök" : { "stock" : 42, "price" : 5, "ids" : (2742, "D02") }
}

warehouse_deluxe["röd lök"] = {}
warehouse_deluxe["röd lök"]["stock"] = 7
warehouse_deluxe["röd lök"]["price"] = 9
warehouse_deluxe["röd lök"]["ids"] = (6314, "D04")

for key in sorted(warehouse_deluxe.keys()):
    print("{product} costs {price} and we have {stock} in stock. It has barcode {barcode} and stock id {stock_id}.".format(
        product=key,
        price=warehouse_deluxe[key]["price"],
        stock=warehouse_deluxe[key]["stock"],
        barcode=warehouse_deluxe[key]["ids"][0],
        stock_id=warehouse_deluxe[key]["ids"][1]
    ))

# skriver ut:
# grädde costs 20 and we have 80 in stock. It has barcode 3141 and stock id L12.
# gul lök costs 5 and we have 42 in stock. It has barcode 2742 and stock id D02.
# krossade tomater costs 10 and we have 33 in stock. It has barcode 4224 and stock id E13.
# köttfärs costs 50 and we have 20 in stock. It has barcode 1234 and stock id K14.
# röd lök costs 9 and we have 7 in stock. It has barcode 6314 and stock id D04.
```

För de som är intresserade finns ett litet exempel i Pythons [dokumentation för tupler](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences).



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna övning skapat ett oerhört simpelt lager där vi kan hålla koll på vad som finns i vår lilla butik med hjälp av en dictionary. Till slut använde vi även tupler för data som vi inte vill ändra. Dictionaries och liknande datastrukturer i andra programmeringsspråk är oerhört användbara för att spara data där vi har en nyckel vi vill koppla till et värde.

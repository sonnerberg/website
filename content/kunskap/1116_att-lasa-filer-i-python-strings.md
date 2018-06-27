---
author: efo, aar
category: python
revision:
  "2017-06-21": (B, aar) Utökad inför python-v2.
  "2017-06-14": (A, efo) Första utgåvan inför kursen python H17.
...
Att läsa filer i Python
==================================
Fram tills nu har vi bara jobbat med data som ligger i RAM-minnet, vilket betyder att när vi stänger ner programmet försvinner all data vi har skapat i programmet. Ett sätt att kunna spara den data så att den finns tillgänglig när vi startar upp programmet igen senare är att spara datan till en fil. Att kunna jobba med filer gör att vi kan spara data permanent och även inspektera den när programmet är avstängt.

Vi ska i denna övning läsa data från filer, lägga till data och ta bort data från filer.



<!--more-->



Kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/file/string) och här på [dbwebb](repo/python/example/file/string). Ni kan ignorera "list-to-file.py" och kolla i "string-to-file.py" istället, det är den vi kommer jobba efter. Där finns även filen vi läsar data från, "items.txt".


Introduktion {#intro}
--------------------------------------
Vi gör ett simpelt program för att skapa en inköpslista. Vi har redan tre saker i filen "items.txt" som behöver inhandlas, i vårt program ska vi kunna lägga till, ta bort och visa upp innehållet i filen.

I programmet ska vi kunna göra val för om vi vill läsa vad filen innehåller, lägga till en sak i filen, skriva över innehållet i filen och att ta bort en sak från filen. Vi börjar med en klassisk while-loop med meny och input.

```python
def menu():
    print(
        """
1. Show file content
2. Add item, append
3. Replace content
4. Remove an item
        """
        )
    return int(input("Choice: "))

def choice(inp):
    if inp == 1:
        pass
    elif inp == 2:
        pass
    elif inp == 3:
        pass
    elif inp == 4:
        pass
    else:
        exit()

if __name__ == "__main__":
    while(True):
        choice(menu())
```
Vi har en funktion för skriva ut valen som finns och en för kolla vilket val som är gjort. if-satsen i "choice()" är förbered för det fyra valen som ska gå att göras, senare ersätter vi `pass` med funktionsanrop. Vi går vidare till val 1, att läsa vad som finns i en fil.

Läsa från fil {#lasa}
--------------------------------------
Börjar med att öppna filen `items.txt` och kolla på innehållet. Den innehåller tre saker, "cookie", "cake" och "tea", en sak på varje rad. Innehållet i filen är egentligen en sträng, `"cookie\ncake\ntea"`, där din texteditor tolkar "\n" som en ny rad. Vi kommer återkomma till detta senare i övningen.

Vidare till koden, vi börjar med val 1, att läsa filens innehåll. När man jobbar med filer behöver man öppna dem, det görs med funktionen `open("filnamn")` där man skickar sökvägen till filen som argument. Funktionen returnerar ett fil objekt som blir kopplingen till filen. Efter man är jobbat färdig med filen behöver man stänga kopplingen. Vi kommer använda oss av nyckelordet `with` för att stänga kopplingen automatisk så vi inte behöver komma ihåg att göra det manuellt.
Vi kolla på hur koden kan se ut för att läsa en fil.

```python
filename = "items.txt" # global variable for holding filename
def readfile():
    # with - as for reading a file automatically closes it after reading is done
    with open(filename) as filehandle:
        content = filehandle.read()
    return content
    
...
    if inp == 1:
        print(readfile())
...
```
Jag hårdkodar vad filen heter som en global variable i början. I funktionen "readfile()" använder vi "with" för att skapa ett block, vi lägger koden som använder filen inom det blocket. `open(filename) as filehandle` är i princip samma sak som att skriva `filehandle = open(filename)`, med andra ord kommer vi åt kopplingen till filen via variabeln `filehandler`. I blocket skriver vi koden för att jobba med filen och det är inte mycket som krävs för att läsa en fil. `filehandler.read()` läser filens innehåll och returnerar det som en sträng. När all kod som ligger inom blocket har exekverat stängs kopplingen automatiskt. Om vi inte hade använt "with" hade vi behövt lägg till en rad ovanför `return content` där vi stänger kopplingen. I if-satsen för de olika valen uppdaterar vi val 1 till att anropa `readfile()` och skriva ut vad den returnerar. 

Testa kör programmet, jag visar vilket val jag gör med `$x` i exemplet nedanför.

```bash
python3 string-to-file.py
$1
cookie
cake
tea
```
Så här kan det se ut när man läser en fil i Python, vi går vidare till att skriva data till filen så vi kan lägga till nya saker.



Skriva till fil {#skriva}
--------------------------------------





Vi har nu en lista som innehäller tre element som vi har läst in från filen `items.txt`. Notera `\n` i sista elementet, `\n` är en radbrytning och egentligen inget vi vill ha med i listan. Så vi kan använda funktionen `strip()` för att ta bort såkallat whitespace (mellanrum, radbrytning osv.) från änderna av strängen.

```python
# the name of the file
filename = "items.txt"

# with - as for reading a file automatically closes it after reading is done
with open(filename) as filehandle:
    line = filehandle.readline().strip()

# split the line into a list on the comma ","
items_as_list = line.split(",")
# print what the list looks like
print(items_as_list)
```

Vi får nu utskriften `['cookie', 'cake', 'tea']` som vi hade förväntat från första början.

Dock ger inläsning från fil än så länge inte mer än vad vi hade fått om vi bara hade skapat listan för hand. Vi ska nu titta på hur vi kan lägga till flera element i listan och hur vi skriver listan till fil.



Skriva till fil {#skriva}
--------------------------------------
Vi vill lägga till ett element i slutet av listan och vet sen tidigare att då använder vi `list` funktionen `append()`. Då vi inte vill skriva listan direkt till fil gör vi om den med motsatsen till `split()` som heter `join()`. Precis som `split()` är `join()` en strängfunktion så vi anger först strängen som vi vill använda som 'lim' och sen anger vi listan som vi vill sätta ihop till en sträng. Precis som när vi läste från fil använder vi `with` när vi vill skriva till en fil. Dock måste vi öppna filen med skrivrättigheter och det gör vi genom att använda flaggan `w`.

```python
# add item to the list
items_as_list.append("cup")
# print what the list looks like after change
print(items_as_list)

# join the list into a string with a comma ","" between every item
list_as_str = ",".join(items_as_list)
# show what the string looks like after join
print(list_as_str)

# write the line to the file
with open(filename, "w") as filehandle:
    filehandle.write(list_as_str)
```



Avslutningsvis {#avslutning}
--------------------------------------
Vi har nu sett hur vi kan läsa raderna från en fil via en sträng till en lista, hur vi lägger till element i listan och hur vi skriver den ändrade listan till fil. Filhantering är ett viktigt verktyg för att spara undan data som kan återanvändas vid nästa exekvering av programmet och vi har i denna övning fått en introduktion till hur man gör detta i Python.

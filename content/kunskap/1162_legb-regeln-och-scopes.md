---
category: python
author:
    - mbn
revision:
  "2020-08-13": (A, mbn) Skapad inför V3 HT20.
...
LEGB regeln och scopes i Python
==================================

Vi har i tidigare övningar och uppgifter introducerats till variabler, funktioner, `if`-satser och loopar. Vi ska i denna övning gå djupare in på hur funktioner och variabler kan påverka varandra.

<!--more-->

Vi rekommenderar att du kodar med i denna övning så du själv får känna på hur det är att skriva Python kod.


Introduktion {#introduktion}
--------------------------------------

I ett programmeringsspråk innebär “scope” den synlighet och levnadstid som variabler och parametrar har. Python följer det så kallade LEGB -regeln som är namngett efter de första bokstäverna från dess egna scopes (Local, Enclosing, Global och Built-in).

Regeln fungerar som en slags prioritering för namnuppsökning och bestämmer ordningen Python letar upp variabler. Om man till exempel refererar till ett visst namn kommer Python att titta upp det namnet i följd i det lokala, inneslutande, globala och inbyggda scopen. Om namnet existerar får man den första matchningen, annars kommer det att uppstå felmeddelanden.


Det globala scopet {#det-globala-scopet}
--------------------------------------
När man deklarerar en variabel utanför en funktion kommer det att bli en global variabel. Detta betyder att man kan nå den från vart man än befinner sig i programmet.

Låt oss titta på hur en global variabel kan skapas i Python.

```python
x = "global"

def foo():
    print("x inside:", x)

foo()
print("x outside:", x)
# skriver ut:
# x inside: global
# x outside: global
```

I koden ovan skapade vi `x` som är en global variabel och funktionen `foo()` för att skriva ut den. Men vad skulle hända om man vill ändra värdet på `x` i funktionen?

```python
x = "global"

def foo():
    x = x * 2
    print(x)

foo()
# skriver ut:
# UnboundLocalError: local variable 'x' referenced before assignment
```

Detta ger oss ett felmeddelande eftersom Python kommer att behandla `x` som en lokal variabel. Vi lämnar detta problem tills vidare och återkommer lite senare.


Det lokala scopet {#det-lokala-scopet}
--------------------------------------
Det lokala (eller funktions) scopet skapas vid [`lambda`](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions) och funktions -anrop. Tänk dig att varje `def`-uttryck har sin egna lilla bubbla. När den förstörs kommer alla namn och värden försvinna.   
Så här fungerar det:

```python
def foo():
    y = "local"

foo()
print(y)
# skriver ut:
# NameError: name 'y' is not defined
```
```python
def foo():
    y = "local"
    print(y)

foo()
# skriver ut:
# local
```

Vi ser att det globala scopet inte kan få tillgång till `y` och den kan endast komma åt inuti i `foo()`.


Om vi återgår till felmeddelandet från exempel 2 kan vi se hur båda scopen krockar. I det första exemplet kände vår funktion igen `x` från det globala scopet men i det andra försökte vi definiera ett lokalt `x`, vilket betyder att vi inte längre hade tillgång till den globala variabeln innan vi multiplicerade den.

Normalt sätt är det en "bad practice" att ändra värden på globala variabler inuti i lokala scopes, men om man behöver göra det så finns nyckelordet `global`. Detta låter oss att använda och skriva över globala variabler i andra scopes.   
Låt oss ta en titt på hur det kan se ut:

```python
x = "global "
y = "global"

def foo():
    global x
    y = "local"
    x = x * 2
    print("x inside:", x)
    print("y inside:", y)

foo()
print("x outside:", x)
print("y outside:",  y)
# skriver ut:
# x inside: global global 
# y inside: local
# x outside: global global
# y outside: global
```

Det inbyggda scopet {#det-inbyggda-scopet}
--------------------------------------
Det inbyggda scopet fungerar lite annorlunda och innehåller alla specialreserverade nyckelord. Man kan kalla på dessa var man än befinner sig i program. Inga definitioner behövs före användning.

Nyckelord är helt enkelt speciella reserverade ord. De lagras för specifika ändamål och kan **inte** skrivas över eller användas för något annat syfte i programmet. En lista på alla nyckelord kan hittas i [Pythons dokumentation](https://docs.python.org/3/reference/lexical_analysis.html#keywords).


Det inkapslade scopet {#det-inkapslade-scopet}
--------------------------------------
Det inkapslade (eller icke-lokala) scopet kan vara lite förvirrande till en början och inträffar när man jobbar med nestade funktioner. En nestad funktion är en funktion som är definierad inuti i en annan och används främst till closures. Closures är inget ni behöver kunna men om man är nyfiken kan du hitta mer information på [denna länk](). 


En nestad funktion kan se ut såhär:

```python
def outer():
    x = "local"

    def inner():
        nonlocal x
        x = "nonlocal"
        print("inner:", x)

    inner()
    print("outer:", x)

outer()
# skriver ut:
# inner: nonlocal
# outer: nonlocal
```

I detta fallet är `inner()` vårat inkapslade scope medans `outer()` fortfarande ligger i det lokala. På samma sätt som de globala variabelnamn kan de lokala namnen nås från dess inre funktioner, men inte tilldelas eller uppdateras.


Om du vill ändra dessa måste du använda nyckelordet `nonlocal`. Med detta kan du precis som med `global`, definiera en lista med namn som kommer att behandlas som icke-lokala. 





Avslutningsvis {#avslutning}
--------------------------------------
Scope är något som förekommer i de flesta programmeringsspråk men kan ha olika typer och regler. Men nu vet du hur Python hanterar sina variabler, vad LEGB-regeln är och hur du ska använda de globala och icke-lokala nyckelorden. Du kan enkelt manipulera variabler i nestade funktioner utan problem.

Alla kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/scope) och här på [dbwebb](https://dbwebb.se/repo/python/example/scope). Funktions- och variabelnamnen har ändrats i kodexemplen då funktioner i samma modul måste ha unika namn.

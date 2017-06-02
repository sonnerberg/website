---
author: efo
category: python
revision:
  "2017-05-31": (A, efo) Första utgåvan inför kursen python H17.
...
Funktioner, parametrar och returvärden
==================================
Vi har i tidigare övningar och uppgifter introducerats till variabler, matematiska operationer, `if`-satser och loopar. Vi ska i denna övning bekanta oss med ett sätt att dela in kod, som gör det möjligt att återanvända delar av program. Vi ser hur vi skapar funktioner, hur vi kan skicka med data till funktioner och hur funktionerna kan skicka tillbaka resultat.



<!--more-->



Funktioner {#funktioner}
--------------------------------------
Funktioner används för att dela upp och kategorisera delar av vår kod som gör det möjligt att återanvända koden på flera ställen i våra program. Funktioner finns i nästan alla programmeringsspråk och är en av viktigaste verktygen vi har som programmerare. Vi kommer i denna övning utgå ifrån kod utan funktioner och långsamt men säkert delar vi upp koden i återanvändbara delar. I exemplen nedan utgår vi från ett verkligt problem och bygger vår kod utifrån det samtidigt som vi delar upp och återanvänder vår kod genom att introducera funktioner.

> Två kollegor ska äta lunch tillsammans och har båda med lunchlådor. Dansken Emil har med Rød Pølse och Svensken Andreas har med köttbullar med mos. Emil värmar sin mat i microvågsugnen på 800 W i 2,5 minut och Andreas värmar sin mat i 3,5 minut också han på 800W. Hur mycket energi går åt till att värma varje maträtt? Vad kostar det att värma maten med ett kWh pris på 78.04 öre per kWh?

Vilken data får vi i uppgiften?

Emil värmar i 2,5 minut på 800W.
Andreas värmar i 3,5 minut på 800W.
kWh pris för el på 78,04 öre per kWh.

Vi kan även formeln för att beräkna energi åtgången i kWh om vi kan tiden och effekten: energi = effekt gångar  tiden i timmar delat med 1000.

Låt oss se hur vi översättar detta till python kod.

```python
emil_time = 2.5 / 60
andreas_time = 3.5 / 60

emil_energy = 800 * emil_time / 1000
andreas_energy = 800 * andreas_time / 1000

print("Emil använder " + str(emil_energy) + " kWh")
print("Andreas använder " + str(andreas_energy) + " kWh")

prize_per_kwh = 78.04

emil_cost = emil_energy * prize_per_kwh / 100
andreas_cost = andreas_energy * prize_per_kwh / 100

print("Emils lunch kostar " + str(emil_cost) + " kr")
print("Andreas lunch kostar " + str(andreas_cost) + " kr")

# skriver ut:
# Emil använder 0.033333333333333326 kWh
# Andreas använder 0.04666666666666666 kWh
# Emils lunch kostar 0.02601333333333333 kr
# Andreas lunch kostar 0.03641866666666667 kr
```

Vi noterar att beräkningarna på raderna 4 och 5 samt 12 och 13 är lika förutom att raderna använder olika variabler. Vi ser här en möjlighet att skapa delar av koden som är återanvändbara med hjälp av funktioner. Hur ser då en funktion ut i python.

```python
def calculate_energy():
    """
    Calculates the energy consumption i kWh
    """
    emil_energy = 800 * emil_time / 1000
    print("Emil använder " + str(emil_energy) + " kWh")
```

På första raden använder `def` för att tala om för python att här vill vi definera ett namn som vi kan återanvända. Efter `def` skriver vi funktionens namn, som vi använder när vi vill köra koden inuti i funktionen. Efter namnet anger vi `()` för att markera att detta är en funktionen. Raden avslutas som till exempel en `if`-sats eller en `for`-loop med `:`. Efter att vi har definerat vår funktion lägger vi till en 'docstring' som dokumenterar vad funktionen gör.



Parametrar {#parametrar}
--------------------------------------
Ovanstående exempel på funktion beräknar bara energi åtgången för Emils tillagning. Så än så länge har vi ingen vinst av att skapa funktionen, men med hjälp av parametrar till funktionen kan vi använda samma kod för både Emil och Andreas. Parametrar är värden som vi skickar in till en funktion. Värdena blir automatisk till variabler, som existerar enbart inuti i funktionens kod. I kodexemplet nedan är `time_in_microwave` och `name` parametrar till funktionen. Dessa blir variabler inne i funktionen och bara där.

```python
def calculate_energy(time_in_microwave, name):
    """
    Calculates the energy consumption i kWh
    And prints the consumption together with the name
    """
    energy = 800 * time_in_microwave / 1000
    print(name + " använder " + str(energy) + " kWh")

emil_time = 2.5 / 60
calculate_energy(emil_time, "Emil")

andreas_time = 3.5 / 60
calculate_energy(andreas_time, "Andreas")

# skriver ut:
# Emil använder 0.033333333333333326 kWh
# Andreas använder 0.04666666666666666 kWh
```

Vi har nu kapslat in vår kod för att beräkna energiåtgången. Denna koden kan återanvändas för nya personer som ska värma mat så låt oss titta på ett sånt exempel.

> Emil och Andreas kollegor Mikael och Kenneth köper mat i restaurangen. Men hissen upp till matsalen är långsam så deras mat hinnar kalna innan de är uppe. Båda värmar maten, men bara på 600W i 30 sek.

Vi måste nu skriva om funktionen lite grann då vi förutom tiden och namnet även vill kunna ta emot effekten som maten ska värmas med. Vi definerar alltså en ny parameter `effect`. I och med att vi oftast vill värma vår mat på 800W kan vi lägga till ett fördefinerat värde, som parametern får om man inte anger ett annat värde när man använder funktionen. Det fördefinerade värde defineras med ett lika med tecken efter parametern. Vi kan nu använda funktionen med antingen två eller tre paramatrar. Om vi använder med två parametrar får variabeln effect värdet 800.

```python
def calculate_energy(time_in_microwave, name, effect=800):
    """
    Calculates the energy consumption i kWh
    And prints the consumption together with the name
    """
    energy = effect * time_in_microwave / 1000
    print(name + " använder " + str(energy) + " kWh")

emil_time = 2.5 / 60
calculate_energy(emil_time, "Emil")

andreas_time = 3.5 / 60
calculate_energy(andreas_time, "Andreas")

kenneth_and_mikael_time = 0.5 / 60
calculate_energy(kenneth_and_mikael_time, "Mikael", 600)
calculate_energy(kenneth_and_mikael_time, "Kenneth", 600)

# skriver ut:
# Emil använder 0.033333333333333326 kWh
# Andreas använder 0.04666666666666666 kWh
# Mikael använder 0.005 kWh
# Kenneth använder 0.005 kWh
```



Returvärden {#returvarden}
--------------------------------------
I vårt ursprungliga exempel använde vi den beräknade energi åtgången till att beräkna kostnaden för att värma maten. Det enda vi gör i vår funktion är att skriva ut ett meddelande och vårt beräknade värde finns enbart inne i funktionen. För att resten av vårt program ska kunna ta del av det beräknade värdet måste vi skicka tillbaka det till programmet eller som det heter programmeringsspråk returnera. Vi använder oss av konstruktionen `return` för att skicka tillbaka värdet. Notera att vi har tagit bort parametern `name` då den inte längre behövs för utskriften.

```python
def calculate_energy(time_in_microwave, effect=800):
    """
    Calculates the energy consumption i kWh
    Resturns the consumption
    """
    energy = effect * time_in_microwave / 1000
    return energy

emil_time = 2.5 / 60
emil_energy = calculate_energy(emil_time)
```

Vår variabel `emil_energy` innehåller nu värdet från variabeln `energy` inne i funktionen. Vi kan nu definera ytterligare en funktion som beräknar kostnaden av elen utifrån en energiåtgång för att vårt program ska fungera som tidigare.

```python
def calculate_energy(time_in_microwave, effect=800):
    """
    Calculates the energy consumption i kWh
    Returns the consumption
    """
    energy = effect * time_in_microwave / 1000
    return energy

def calculate_cost(energy, prize_per_kwh=78.04):
    """
    Calculates the cost for a given energy consumption
    Returns the cost in kr
    """
    cost = energy * prize_per_kwh / 100

emil_time = 2.5 / 60
emil_energy = calculate_energy(emil_time)
emil_cost = calculate_cost(emil_energy)

print("Emil använder " + str(emil_energy) + " kWh och detta kostar " + str(emil_cost) + " kr")
# skriver ut:
# Emil använder 0.033333333333333326 kWh och detta kostar 0.02601333333333333 kr
```

Vi har nu två funktioner som kan återanvändas. Vi skickar in parametrar både med och utan fördefinerat värde och returnerar värden från våra funktioner.



Formattering för bättre utskrifter {#format}
--------------------------------------



Avslutningsvis {#avslutning}
--------------------------------------
Funktioner är en av de viktigaste byggstenarna i programmering.

Alla kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/functions) och här på [dbwebb](https://dbwebb.se/repo/python/example/functions). Funktionsnamnen har ändrats i kodexemplen då funktioner i samma modul måste ha unika namn.

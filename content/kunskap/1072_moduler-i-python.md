---
author: efo
category: python
revision:
  "2017-06-02": (A, efo) Första utgåvan inför kursen python H17.
...
Moduler i Python
==================================

[FIGURE src=image/python/lego.jpg?w=c5 class="right"]

Funktioner i Python gjorde att vi kan återanvända kod och att vi hade möjlighet för att sätta namn koden som vi vill använda. Ibland vill vi dela upp koden ännu mer för att enkelt kunna återanvända flera funktioner i flera olika program. Vi ska i denna övning titta på hur vi kan skapa en modul och hur vi importerar modulen i en annan Python-fil.



<!--more-->



Vi fortsätter på exemplet från övningen [Funktioner, argument och returvärden](kunskap/funktioner-argument-och-returvarden) så har du inte gjort den övningen rekommenderar vi att du gör den först.



Moduler {#moduler}
--------------------------------------
I slutet av övningen [Funktioner, argument och returvärden](kunskap/funktioner-argument-och-returvarden) ser våra funktioner ut på följande sätt.

```python
# energy_calculation.py
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
    return cost
```

Dessa två funktioner hänger ihop och har ett sammanhang och som de strukturerade programmerare vi är tänker vi att dessa kan vi ju använda en annan gång. Detta görs lättast i Python genom att skapa en modul. Vi skapar en ny fil `energy_calculation.py` där vi lägger ovanstående två funktioner.

I en annan ny fil `main.py` skriver vi själva programmet. Vi har alltså nu våra funktioner i en fil och själva programmet i ett annat. För att vi kan använda våra funktioner från filen `energy_calculation.py` måste vi importera den filen in i `main.py`. Detta gör vi genom att använda `import`. Notera att vi skriver `import energy_calculation` och inte att vi importerar själva filen, så ingen filändelse. Vi har nu tillgång till alla funktioner vi har definerat i `energy_calculation.py`. Vi kommer åt funktionerna genom att skriva modulens namn följd av en punkt (.) och sen funktionens namn.

```python
# main.py

import energy_calculation

emil_energy = energy_calculation.calculate_energy(emil_time)
```



Avslutningsvis {#avslutning}
--------------------------------------
Vi har nu kort introducerat moduler i Python. Moduler är ett sätt att kategorisera och dela upp kod för återanvändning och ett bra arbetssätt när mängden av kod växer eller att du vill använda samma kod i olika projekt. För de som vill veta mer om moduler i Python beskrivs moduler i [Python Tutorial Chapter 6 Modules](https://docs.python.org/3/tutorial/modules.html).

Alla kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/functions) och här på [dbwebb](https://dbwebb.se/repo/python/example/functions). Kodexemplet innehåller hela exemplet från tidigare övningar, men uppdelat i modulen `energy_calculation.py` och huvudprogrammet finns i `main.py`.

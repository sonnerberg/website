---
author: efo
category: python
revision:
  "2017-06-02": (A, efo) Första utgåvan inför kursen python H17.
...
Moduler i python
==================================
Funktioner i python gjorde att vi kan återanvända kod och att vi hade möjlighet för att sätta namn koden som vi vill använda. Ibland vill vi dela upp koden ännu mer för att enkelt kunna återanvända flera funktioner i flera olika program. Vi ska i denna övning titta på hu vi kan skapa en modul och hur vi importerar modulen i en annan python fil.



<!--more-->



Vi fortsätter på exemplet från övningen [Funktioner, parametrar och returvärden](kunskap/funktioner-parametrar-och-returvarden) så har du inte gjort den övningen rekommenderas vi att du gör den först.



Moduler {#moduler}
--------------------------------------
I slutet av övningen [Funktioner, parametrar och returvärden](kunskap/funktioner-parametrar-och-returvarden) ser våra funktioner ut på följade sätt.

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
    return cost
```

Dessa två funktioner hänger ihop och har ett sammanhang och som de strukturerade programmerare vi är tänker vi att dessa kan vi ju använda en annan gång. Detta görs lättaste i python genom att skapa en modul. Vi skapar alltså en ny fil `energy_calculation.py` där vi lägger ovanstående två funktioner.




Avslutningsvis {#avslutning}
--------------------------------------


Alla kodexempel från denna övningen finns i kursrepot för [python-kursen](https://github.com/dbwebb-se/python/tree/master/example/functions) och här på [dbwebb](https://dbwebb.se/repo/python/example/functions).

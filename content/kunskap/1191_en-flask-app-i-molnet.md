---
author: efo
revision:
    "2021-12-07": (A, efo) Skapad inför VT2022.
...
En Flask App i molnet
==================================

I denna övningen använder vi Flask för att skapa ett eget API som svarar med JSON data. I slutet av övningen driftsätter vi appen i Azure's cloud.


<!--more-->



Förkunskaper {#prereqs}
--------------------------------------

Du har installerat [labbmiljön](../kurser/moln/labbmiljo) för kursen och läst igenom artikeln [Introduktion till molnet](kunskap/introduktion-till-molnet).



Flask {#flask}
--------------------------------------

[Flask](https://flask.palletsprojects.com/en/2.0.x/) beskrivs som ett "micro-framework". Vi vill använda Flask för att skapa ett Application Programming Interface (API). Ett API är ett sätt för olika applikationer att kommunicera med varandra. Det API som vi ska skapa ska svara på olika url'er som vi kallar `endpoints`. Vi vill att vårt API ska svara med JSON.

När vi anropar en server från en webbläsare till exempel om vi skriver `https://dbwebb.se` görs ett GET-anrop. Så när vi skriver ett API definierar vi de olika endpoints för olika url'er där vi vill att vår server/API ska svara med olika data i JSON-formatet.

Låt oss titta på hur det kan se ut. I din katalog som du skapade och använde i kmom01 skapa en ny underkatalog `lager_api`. Vi kommer återanvända denna underkatalogen i inlämningsuppgiften senare i kmomet.

Om du vill titta på ett fullständigt exempel finns ett i [moln/flask_starter](https://github.com/dbwebb-se/moln/tree/main/flask_starter).



Virtual Environment {#venv}
--------------------------------------

För att vi ska kunna installera externa paket som `Flask` och `requests` behöver vi berätta för Python att vi vill ha en virtual environment där vi kan spara dessa moduler.

Följa instruktionerna för ditt operativsystem i Flask's guide för [Virtual environments](https://flask.palletsprojects.com/en/2.0.x/installation/#virtual-environments). Du behöver inte skapa en ny katalog om du har gjort det ovan. Om du använder WSL terminalen eller Cygwin terminalen kan du använda instruktionerna för macOS/Linux. Vi ser även till att aktivera vår virtual environment.

Som ett sista steg i installationen installerar vi Flask med hjälp av Pythons pakethanterare `pip`.

```python
pip install Flask
```

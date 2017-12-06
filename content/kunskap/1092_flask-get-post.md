---
author: lew
revision:
    "2017-12-01": (A, lew) First version for v2.
category:
    - oopython
...
Flask, POST och GET
===================================

[FIGURE src=/image/oopython/kmom02/topimage-art1.png?w=c5 class="right"]

Vi ska titta närmare på hur man kan jobba med POST och GET i Flask. Målet är att vi ska med hjälp av formulär, tabeller och klasser med arv, presentera innehåll i vår Flask-applikation.  

<!--more-->  

Intro {#intro}
-------------------------------
När vi hämtar en webbsida används HTTP-metoden GET. Det man skickar hamnar då synligt i adressfältet, tex: `http://localhost:5000?id=2&car=volvo`.

Vill vi däremot inte att datan, eller informationen vi skickar, ska synas, så kan vi använda metoden POST. POST kan bland annat inte bokmärkas, cachas eller sparas i historiken till skillnad från GET-metoden. POST-data skickas i headern, så den är ej synlig i URL:en.  

[Läs mer om POST och GET](http://www.w3schools.com/tags/ref_httpmethods.asp).

Vi ska som sagt gå igenom båda två och se hur de kan användas tillsammans med Python och Flask. Vill du hänga med och koda själv redan nu kan du skapa filerna som används i artikeln:

[FIGURE src=/image/oopython/kmom02/tree_flask2.png]



Förutsättning {#pre}
-------------------------------

Du har läst delen om GET och POST i guiden "[Php på 20 steg](kunskap/kom-i-gang-med-php-pa-20-steg#globals)" eller vet vad det innebär.  
Du har läst artikeln om "[Flask med Jinja2](kunskap/flask-med-jinja2)".  
Du har läst artikeln om "[Klassrelationer](kunskap/klass-relationer)".  



Struktur {#struktur}
-------------------------------

Innan vi kommer igång med koden kan det vara bra att tänka igenom vad det är man vill åstadkomma. Det minskar risken att hamna snett och behöva kasta kod och göra om. Målet är en sida som kan lägga till fordon i ett "garage", som i sin tur visas upp i en tabell. Tabellen ska uppdateras automatiskt och vi blandar inte in någon databas, utan det vi lämnar koden med några fordon hårdkodade. Till detta skapar vi en basklass, `Vehicle` och subklasser i form av `Car`, `Motorcycle` och `Trailer`. Vi ska hantera GET och POST i routen och agera korrekt beroende hur vi skickar en request till routen. När vi klickar på länken i navbaren görs ett GET-request och när vi postar formuläret kan vi använda POST. Vi kan med fördel i detta fallet använda samma route, kallad "garage" i artikeln.

En vattentät plan är på plats så vi börjar kika på koden.

Klasserna {#klasserna}
-------------------------------

Nu tar vi en titt på hur klasserna ser ut.



###Basklassen Vehicle {#basklass-vehicle}

```python
#!/usr/bin/env python3

"""
Class file for Vehicle
"""

class Vehicle():
    """
    Base class
    """
    def __init__(self, brand, model, color):
        """
        init method
        """
        self.brand = brand
        self.model = model
        self.color = color

    def get_brand(self):
        return self.brand

    def get_model(self):
        return self.model

    def get_color(self):
        return self.color
```



###Subklassen Car {#subklass-car}

```python
#!/usr/bin/env python3
"""
Class file for Car
"""

from vehicle import Vehicle

class Car(Vehicle):
    """
    Class for Car
    """
    vehicle_type = "Car"

    def __init__(self, brand, model, color):
        super(Car, self).__init__(brand, model, color)

    def get_type(self):
        """
        returns the type
        """
        return self.vehicle_type
```
Här skickar vi vidare initieringsvariablerna till super-klassen, basklassen, Vehicle. Metoderna i basklassen kommer gälla för subklasserna med, fast för den egna instansen.

Nu kan vi skapa en instans av klassen Car som ärver från klassen Vehicle: `volvo = Car("Volvo", "XC90", "Blå")`. Den informationen vill vi ha från formuläret. Du bör nu kunna se hur klasserna för Motorcycle och Trailer ska se ut. Det löser du.



Formulär och tabell {#formular-och-tabell}
-------------------------------

###Garage.html {#garage.html}

Börja med att lägga till ett menyval i navbaren för `garage.html`, samt en route som returnerar rätt sida. Vi ska utnyttja Jinja2's funktionalitet för att hantera mallar och skapa mallar, *templates*, för tabellen och formuläret. Som du såg i början av artikeln så har vi mapparna templates/forms och templates/tables. Kika sedan på garage.html:

```html
{% include 'header.html' %}

<div class="container">
    <div class="page-header">
        <h1>Hantera garaget</h1>
    </div>
    <div class="row">
        <div class="col-md-3 col-md-offset-1">
            <h3>Lägg till</h3>
            {% include 'forms/add_vehicle.html' %}
        </div>
        <div class="col-md-3 col-md-offset-1">
            <h3>Garage</h3>
            {% include 'tables/show_vehicles.html' %}
        </div>
    </div>
</div>

{% include 'footer.html' %}
```
När vi kallar på `{% include ... %}` letar Jinja2 automatiskt i mappen templates/. Vi kan på detta sättet separera koden och inkludera formulär, tabeller och övrig html-kod. För att få en snygg layout använder vi Bootstrap's färdiga klasser. Klassen `row` gör sitt bästa för att innehållet ska hamna på en rad. Klassen `col-md-3` tar upp 3 kolumner av 12. Klassen `col-md-offset-1` puttar elementet 1 kolumn till åt höger. Forumläret och tabellen kommer hamna brevid varandra på samma rad, och vara lika breda.



###Mallen för formuläret {#mall-formular}

Mallen för formuläret, templates/forms/add_vehicle.html, ser ut på följande sätt:

```html
<form role="form" method="POST" action="{{ url_for('garage') }}">
    <div class="form-group">
        <label for="type">Type: </label>
        <select class="form-control" name="type" id="type">
            <option value="car">Car</option>
            <option value="motorcycle">Motorcycle</option>
            <option value="trailer">Trailer</option>
        </select>
    </div>
    <div class="form-group">
        <label for="brand">Tillverkare: </label>
        <input type="text" name="brand" class="form-control" />
    </div>
    <div class="form-group">
        <label for="model">Modell: </label>
        <input type="text" name="model" class="form-control" />
    </div>
    <div class="form-group">
        <label for="color">Färg: </label>
        <input type="text" name="color" class="form-control" />
    </div>
    <button type="submit" class="btn btn-default">Lägg till</button>
</form>
```

Vi sätter metoden till POST och action till den sökvägen vi vill skicka formuläret när vi gör submit. Attributet `name` är även här namnet vi når formulärets data med när vi tar hand om det.



###app.py {#app-py}

Nu återstår bara att hantera det inskickade formuläret. Det kan vi göra i routen för garage.html:

```python
@app.route("/garage", methods=["POST", "GET"])
def garage():
    """ Garage route """

    if request.method == "POST":
        if request.form["type"] == "car":
            vehicle = Car(request.form["brand"], request.form["model"], request.form["color"])
            garage_list.add_vehicle(vehicle)
        if request.form["type"] == "motorcycle":
            vehicle = Motorcycle(request.form["brand"], request.form["model"], request.form["color"])
            garage_list.add_vehicle(vehicle)

        # omitted code in explanation purpose

    return render_template("garage.html", garage=garage_list)
```

Här talar vi om att det är helt i sin ordning att ta sig hit via både POST och GET. Med modulen `request` kan vi se hur användaren har tagit sig in i routen med `request.method`. Om requesten är GET behöver vi inte göra något, då ska bara sidan renderas. Om det däremot är POST betyder det att det är formuläret som skickats och det behöver vi ta hand om. Tidigare nämndes att det är formulärets attribut `name` som används och det når vi via request.form["attribut"]. Sedan skapar vi en instans av den klassen och lägger i listan `garage`. Listan är skapad ovanför alla routes med några hårdkodade instanser. Sist så skickar vi med listan till garage.html och låter tabellen ta hand om den för utskrift.



###Mallen för tabell {#mallen-for-tabell}

Vi hoppar in i templates/ igen och mappen tables/.

```html
<table class="table">
    <thead>
        <tr>
            <th>Typ</th>
            <th>Tillverkare</th>
            <th>Modell</th>
            <th>Färg</th>
        </tr>
    </thead>
<tbody>
    {% for vehicle in garage.show_vehicles() %}
    <tr>
        <td>{{ vehicle.get_type() }}</td>
        <td>{{ vehicle.get_brand() }}</td>
        <td>{{ vehicle.get_model() }}</td>
        <td>{{ vehicle.get_color() }}</td>
    </tr>
    {% endfor %}
</tbody>
</table>
```

Här skapar vi tabellen och i `<tbody>` där magin händer, använder vi en for-loop som går igenom den inskickade listan och dess respektive metoder.





Avslutningsvis {#avslutning}
------------------------------

Det var det hela. Smidigt och strukturerat. Prova gärna att lägga till fler funktioner i tabellen, tex sortering eller visa max antal och paginering.

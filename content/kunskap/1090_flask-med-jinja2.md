---
author: lew
revision:
    "2017-11-10": (A, lew) Updated version for VT18.
category:
    - oopython
...
Flask med Jinja2
===================================

[FIGURE src=/image/oopython/kmom03/kmom03_top_jinja.png?w=c8 class="right"]

[Flask](http://flask.pocoo.org/) är ett microramverk för Python, som gör det möjligt att skapa webbapplikationer. Det är litet men kraftfullt. Vi ska gå igenom hur man installerar det och kommer igång med en enkel sida.

[Jinja2](http://jinja.pocoo.org/) är en så kallad "template engine" för Python som renderar template-filer åt oss.

<!--more-->



Förutsättning {#pre}
-------------------------------

Du kan grunderna i Python och du vet vad variabler, typer, objekt och funktioner innebär.  
Du är medveten om strukturen och uppbyggnaden av en webbsida.
<!-- Du har gjort övningen "[Kom igång med Flask](kunskap/kom-igang-med-flask)".   -->
<!-- Du har gjort övningen "[Kom igång med objekt](kunskap/kom-igang-med-objekt)". -->



Installation {#installation}
------------------------------

Både Flask och Jinja2 kan installeras med pakethanteraren `pip`. Har du inte pip installerat, kika på [instruktionerna för pip](kunskap/python-pakethantering-med-pip#installera). Kör du Windows, starta en terminal som administratör och skippa `sudo`.

Sparka igång en terminal och installera Flask:

```bash
$ sudo pip3 install Flask
```

Paketet Jinja2 ingår i Flask. Skulle det inte finnas installerat så installerar du det på följande vis:

```python
$ sudo pip3 install Jinja2
```

Allt klart? Bra, nu är det bara att köra igång.



Frontcontroller {#frontcontroller}
------------------------------

Vi skapar en fil som vi döper till `app.py`. Det är frontcontrollern till applikationen, dvs den fil som hanterar alla inkommande routes och servar webbläsaren med korrekt fil.

Öppna en terminal och leta dig fram till mappen `kmom01/my_app`.

```bash
$ touch app.py
```

Öppna filen i en editor, förslagsvis Atom, och kopiera in följande kod:

```python
#!/usr/bin/env python3
"""
My first Flask app
"""
# Importera relevanta moduler
from flask import Flask

app = Flask(__name__)

@app.route("/")
def main():
    """ Main route """
    return "Välkommen!"

if __name__ == "__main__":
    app.run()
```

Med hjälp av `@app.route()` kan vi hantera inkommande routes och serva önskat innehåll, i det här fallet strängen "Välkommen!".

Routen / är roten, start eller index om man så vill. En route kan ses som en trafikpolis som dirigerar om trafiken. Om vi har en route `@app.route('/telefon')` kan vi nå den via `http://example.com/telefon`. Funktionen som definieras under behöver inte ha samma namn som routen. Det underlättar dock då Flask bland annat använder funktionsnamnet för att hänvisa till dess sökväg. Flask kan använda till exempel `url_for('main')`, och hade i detta fallet hänvisat till routen `/` (roten). Men mer om det senare, nu går vi vidare.

Starta applikationen med:

```bash
$ python3 app.py
```

Om allt är ok ser du: ` * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)`  

Peka sedan webbläsaren på `localhost:5000`, alternativt `127.0.0.1:5000` så ser du resultatet.

[FIGURE src=/image/oopython/kmom01/flaskstart.png?w=w2 caption="Applikationen snurrar på localhost:5000."]



Applikation {#applikation}
------------------------------

###Bootstrap {#bootstrap}

Vi ska använda [Bootstrap](http://getbootstrap.com/) i applikationen. Det underlättar en snygg design och responsivitet.  

[Temat som används](https://getbootstrap.com/docs/3.3/examples/starter-template/).  

Du får självklart använda ett annat tema om du vill. De flesta teman har bara en annan .css-fil och kan skilja sig lite i klassnamn och struktur. Inga större skillnader.

Nu kör vi.

Först stänger vi ner servern (ctrl-c) och skapar vi filerna som behövs.

Använd terminalen och ställ dig i "my_app":
```bash
$ mkdir templates static
$ mkdir static/styles
$ touch templates/index.html
$ touch templates/header.html
$ touch templates/footer.html
$ touch static/styles/style.css
```

[FIGURE src=/image/oopython/kmom01/tree1.png caption="Filstruktur."]

Flask använder en viss mappstruktur när den letar efter filerna. Till exempel:  

* .html-filer och dynamiska filer som ska servas ska ligga i mappen /templates
* bilder och annat statiskt material ska ligga i /static
* egna stylesheets (css) ska ligga i /static/styles  

Som du såg ovan så skapade vi `header.html` och `footer.html`. Vi ska använda Jinja2 för att separera koden så vi använder en header och en footer som inkluderas på alla sidor. På så vis behöver vi bara ändra koden på ett ställe vid eventuell uppdatering och vi återanvänder koden. [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) är bra.

Allt har sin plats. Struktur. Det finns såklart andra resurser att tillgå som i sin tur har "egna" platser i applikationen men för stunden räcker det med det här.



###header.html {#header}

För Bootstrap's filer använder vi oss av [CDN](https://en.wikipedia.org/wiki/Content_delivery_network). Det krävs att man har åtkomst till internet, då Bootstraps filer laddas in via `http`. Det blir färre filer lokalt. Smidigt!  

Öppna header.html i editorn och kopiera in följande kod:

```html
<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <title>Applikation i Flask</title>

    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" rel="stylesheet">

    <!-- Private stylesheet, loads last -->
    <link rel="stylesheet" href="{{ url_for('static',filename='styles/style.css') }}">
</head>

<body role="document">
    <nav class="navbar navbar-inverse navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false"   aria-controls="navbar">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a class="navbar-brand" href="{{ url_for('main') }}">Min första Flask app</a>säkerxhetsrisk
            </div>
            <div id="navbar" class="navbar-collapse collapse">
                <ul class="nav navbar-nav">
                    <li class="active"><a href="{{ url_for('main') }}">Hem</a></li>
                </ul>
            </div>
        </div>
    </nav>
```

Det här är den "övre" delen av en klassisk Bootstrap-mall. Vi laddar även in en egen stylesheet efter Bootstraps. Det är med den vi kan "personifiera" stylen då vi inte har Bootstraps filer lokalt.  



Flask använder `url_for()` för sökvägen ska bli korrekt. I koden ovan ser vi bland annat:

```html
<link rel="stylesheet" href="{{ url_for('static',filename='styles/style.css') }}">
```

Stylesheets och bilder ska ligga i mappen static/. Med argumentet `filename=` kan vi skicka med ett filnamn, eller resten av sökvägen om det är uppdelat i mappar i static/. Om man har en bild till exempel me.png i mappen static/images/ når man den med:

```html
<img src="{{ url_for('static',filename='images/me.png') }}">
```

Vi har även länken i navbaren:

```html
<a href="{{ url_for('main') }}">
```

Här hämtas sökvägen till routen `main`. Jämför det med `<a href="index.html">` i detta fallet.



###footer.html {#footer}

Här behöver vi stänga alla öppna taggar och ladda in det sista. Bootstrap använder ett externt bibliotek, JQuery, så vi behöver även ladda in det via CDN. Ta nu följande kod och lägg i footer.html:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
</body>
</html>
```



###index.html {#index}

Vi hoppar över till index.html och använder Jinja2 för att inkludera header.html och footer.html.

```html
{% include 'header.html' %}

<div class="container" role="main">
    <div class="page-header">
        <h1>Stiligt! En fungerande applikation.</h1>
        <h3>Nu inkluderas headern och footern med hjälp av Jinja2</h3>
    </div>
</div>

{% include 'footer.html' %}
```



###style.css {#style}

Vi har som sagt vår egna stylesheet att tillgå. [Bootstrap's dokumentation](https://getbootstrap.com/docs/3.3/components/#navbar-component-alignment) talar om för oss att *"The fixed navbar will overlay your other content, unless you add padding to the top of the \<body\>"* och *"The fixed navbar will overlay your other content, unless you add padding to the bottom of the \<body\>"*.

Vi lägger till det i vår egna stylesheet style.css:

```css
body {
  padding-top: 70px;
  padding-bottom: 30px;
}
```



###app.py {#app}

Vi måste ju ändra så vi servar en html-fil istället för en sträng. För att kunna rendera html filer behöver vi importera metoden "render_template" och använda den.

```python
from flask import Flask, render_template
```

Bra, nu kan vi använda den i vår route:

```python
@app.route("/")
def main():
    """ Main route """
    return render_template("index.html")
```

Underbart! Testa nu att kicka igång servern med `python3 app.py` och öppna `localhost:5000` i din webbläsare.  

[FIGURE src=/image/oopython/kmom01/app1.png?w=w2 caption="En fungerande applikation."]

För att se responsiviteten kan du prova att förminska fönstret så kommer menyn ändras när fönstret blir tillräckligt litet.



Utöka applikationen {#utoka}
-------------------------------

Det är ju lite tråkigt att bara ha en sida. Vi tittar på hur man utökar med en sida till.

Vi kommer behöva skapa en ny sida i /templates-mappen lägga till en route i `app.py` samt uppdatera header.html med ett nytt menyval. Inte krångligare än så.



###Lägg till en sida {#lagg-till-en-sida}

Vi lägger till en sida, `about.html`. Vi utgår ifrån att den nya filen har samma struktur som `index.html` så vi kopierar bara den.

```bash
# Ställ dig i me_app/
$ cp templates/index.html templates/about.html
```



###Lägg till ett menyval {#lagg-till-ett-menyval}

Om vi kikar i header.html så ser vi raden:

```html
<li class="active"><a href="{{ url_for('main') }}">Hem</a></li>
```

Här behöver vi lägga till ett nytt \<li\> element för den nya sidan:

```html
<li class="active"><a href="{{ url_for('main') }}">Hem</a></li>
<li><a href="{{ url_for('about') }}">Om</a></li>
```

Innan vi går vidare till routen kan vi ordna så att det aktiva menyvalet får klassen .active.

```html
<ul class="nav navbar-nav">
    <li {%- if request.path == "/" %} class="active" {% endif %}><a href="{{ url_for('main') }}">Hem</a></li>
    <li {%- if request.path == "/about" %} class="active" {% endif %}><a href="{{ url_for('about') }}">Om</a></li>
</ul>
```

Vi använder Jinja2 och modulen "request" som importeras i app.py. En if-sats kollar pathen och lägger till klassen `active` om den matchar. Studera koden ovan så du är med på vad som händer.



###Lägg till en route {#lagg-till-en-route}

Vi öppnar filen `app.py` igen och tittar på routen. Lägg till följande kod under den första routen:

```python
@app.route("/about")
def about():
    """ About route """
    return render_template("about.html")
```



Skicka med parametrar {#skicka-med-parametrar}
------------------------------

För att göra vår app lite mer användbar kan vi skicka med parametrar vid routingen i app.py. Det gör att vi kan använda ren python-kod och sedan presentera det i html-koden.  

Vi kikar på hur det går till i app.py. Innan `@app.route()` lägger vi till några variabler:  

```python
my_name = "Kenneth Lewenhagen"
my_course = "OOPython"
```

Låt säga att vi vill skicka med variablerna till `about.html`. Om du kommer ihåg [strängformatering](https://www.youtube.com/watch?v=BkMm0lX-Ytc&list=PLKtP9l5q3ce93pTlN_dnDpsTwGLCXJEpd&index=18) från förra Pythonkursen kan du nog lista ut hur det fungerar.  

I app.py:

```python
@app.route("/about")
def about():
    return render_template("about.html", name=my_name, course=my_course)
```

Nu fattas det bara att använda variablerna i about.html. Vi lägger till placeholders med hjälp av `{{ }}`.

```html
<p>Jag heter {{ name }} och det här är kursen {{ course }}.</p>
```

about.html tar emot de skickade variablerna och placerar ut dem.

Om vi nu drar igång servern och pekar webbläsaren på `localhost:5000/about`:

[FIGURE src=/image/oopython/kmom01/jinja2_result.png?w=w2 caption="Utskrift via variabler."]


Flask i debug-läge {#debug}
------------------------------

Det finns ett [debug-läge](http://flask.pocoo.org/docs/0.12/quickstart/#debug-mode) inbyggt i Flask som automatiskt startar om Python servern när du ändrar din Python kod. Det funkar inte när du ändrat i någon template kod, ex. html filerna, utan bara när du ändrat på din Python kod. Nedanför kan du se hur man startar Flask i debug-läge. Obs! Tanken är att man bara kör med debug-läge i utvecklingsfasen då att ha det aktiverat är en säkerhetsrisk.

```python
if __name__ == "__main__":
    app.run(debug=True)
```

Avslutningsvis {#avslutning}
------------------------------

Kika igenom dokumentationen för [Flask](http://flask.pocoo.org/) och [Jinja2](http://jinja.pocoo.org/docs/2.10/). Fundera lite på vad mer man kan göra med Flask och Jinja2. Det är oerhört kraftfullt och öppnar upp många möjligheter med Python-kod på webbsidan.

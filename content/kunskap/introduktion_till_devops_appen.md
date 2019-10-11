---
author: aar
category: devops
revision:
  "2019-06-24": (A, aar) Första utgåvan inför kursen devops.
...
Introduktion till Devops appen
==================================

[FIGURE src=image/devops/bild-på-startsidan?w=c10 class="right"]

Introduktion till projektet vi ska jobba med i hela kursen. Vi ska titta på lite kod, strukturen och de olika verktygen som används för appen.
<!--more-->

Vi behöver ett projekt/en app att jobba med när vi ska lära oss devops. Jag har redan skapat en blog som du ska använda och jobba vidare med i kursen. Bloggen baseras på [The Flask mega tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). I den tutorialen visar Miguel hur man skapar en blog i Flask från grunden till att driftsätta den.



## Appen {#appen}

Koden för appen är redan klar och finns i repot [devops](https://github.com/dbwebb-se/microblog), börja med att forka och klona repot. Här följer några videos som du kan kolla på för att få en uppfattning av hur bloggen fungerar och koden ser ut. Använd även [The Flask mega tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world) för att förstå koden.

[YOUTUBE src="PUigbi1lGQU" caption="110 Introduktion till app strukturen och repot."]

[YOUTUBE src="cHWrwQQlEjY" caption="111 Genomgång av appens kod."]

[YOUTUBE src="kB5UvNxuHxo" caption="112 Genomgång av koden för testerna."]



## Länkar {#lankar}

[Flask och Jinja2](kunskap/flask-och-jinja2) och dess förkunskaper kan du använda för att lite snabbt få kolla på Flask.

[SQLAlchemy and You](http://lucumr.pocoo.org/2011/7/19/sqlachemy-and-you/) introducerar SQLAlchemy och visar upp grundliga exempel.

[FLask SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) dokumentation för SQLAlchemy paketet vi använder.

[Pytest](https://docs.pytest.org/en/latest/) använder vi för testning.

[Understanding the Python Mock Object Library](https://realpython.com/python-mock-library/) här förklaras hur `mock` och `patch` fungerar.

[Flask WTF](https://flask-wtf.readthedocs.io/en/stable/) använder vi för att skapa formulär integrerat med Flask.

[Flask-Migrate](https://flask-migrate.readthedocs.io/en/latest/) migrerar SQLAlchemy kod till databaser.

[FLask-Login](https://flask-login.readthedocs.io/en/latest/) användare hantering med session.

[Flask-Moment](https://github.com/miguelgrinberg/Flask-Moment) formaterar datum och tid i Jinja2 templates med moment.js.

[Flask-Bootstrap](https://pythonhosted.org/Flask-Bootstrap/) addon för bootstrap i Jinja2 och WTF.

[python-dotenv](https://saurabh-kumar.com/python-dotenv/) Gör om key-value par till miljövariabler.



Avslutningsvis {#avslutning}
--------------------------------------

Det är många olika saker att ta in i denna artikeln, ni har fått känna på hur det är att jobba med driftsättning av en applikation ni inte skapat själva och sett olika delar som kan ingå. Under kursens gång ska vi jobba oss ifrån att göra saker manuellt till att det antingen sker automatisk eller i alla fall finns i ett skript.

Artikeln baseras mycket på [The Flask mega tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xvii-deployment-on-linux).

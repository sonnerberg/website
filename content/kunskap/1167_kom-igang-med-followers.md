---
author: moc
category:
    - devops
    - flask
    - python
    - sql
revision:
    "2020-09-29": (A, moc) Skapad inför HT2020.
...
Intro {#intro}
==================================

I denna artikeln ska vi jobba igenom [kapitel 8](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-viii-followers) i Miguel's guide, så att vi kan följa andra användare och se inlägg från de personer som användare följer på sin feed.


Vi kommer främst att jobba med `SQLAlchemy ORM` i python ramverket `flask` och `pylint` för att skriva enhetstester till de nya uppdateringarna.

<!-- more -->

Förutsättningar {#prereq}
===========================
Du har läst och kollat igenom [introduktion till devops appen](kunskap/introduktion_till_devops_appen) och fått igång applikationen.


Steg 1. Databas {#step1-databas}
---------------------------------
Just nu består databasen två tabeller, `User` som håller koll på alla användare och `Post` som hanterar inläggen. Det vi skall göra nu är att lägga till en associeringstabell _eller kopplingstabell_ och jag väljer att döper den till `followers`. Här vill vi länka användarens `user_id` till det användar id't personen vill följa har.

Vi börjar med att skapa den nya modellen i filen `app/models.py` och lägger vår kod ovanför klassen `User`.

```python
followers = db.Table('followers',
    db.Column('follower_id', db.Integer, db.ForeignKey('user.id')),
    db.Column('followed_id', db.Integer, db.ForeignKey('user.id'))
)
# ..
```

Anledningen varför vi inte gjorde denna tabell till en klass liknande de andra, kär att detta endast är en kopplingstabell, den skall skall alltså inte hålla någon annan information eller funktionalitet än två stycken `foreign keys`.


Nu behöver vi bara berätta `User` -modellen att skapa en relation till `followers`. Detta kan göras med hjälp av `db.relationship()`:

```python
class User(UserMixin, db.Model):
    # ...
    followed = db.relationship(
        'User', secondary=followers,
        primaryjoin=(followers.c.follower_id == id),
        secondaryjoin=(followers.c.followed_id == id),
        backref=db.backref('followers', lazy='dynamic'), lazy='dynamic')
```

Den första parametern `'User'` är strängnamnet på den främmande tabellens klassnamn och eftersom vi skapar en relation från en användare till en annan refererar vi denna till sig själv.   
Nästa argument `secondary` sätts till kopplingstabellens variabelnamn så att den vet vart datan skall sparas. Medans `primaryjoin` och `secondaryjoin` berättar hur kopplingen mellan User modellen kopplas till followers och lika så followers till User.

Den sista parametern `backref` definierar hur vi skall hämta datan när `User.followed` kallas. 


Ändringarna som vi precis gjorde i databasen måste nu läggas till i våran databasmigration:

```bash
╰─ (venv) $ flask db migrate -m "followers"
INFO  [alembic.runtime.migration] Context impl SQLiteImpl.
INFO  [alembic.runtime.migration] Will assume non-transactional DDL.
INFO  [alembic.autogenerate.compare] Detected added table 'followers'
  Generating /home/moc/git/kurser/microblog/migrations/versions/ab124256c621_followers.py ... done

╰─ (venv) $ flask db upgrade
INFO  [alembic.runtime.migration] Context impl SQLiteImpl.
INFO  [alembic.runtime.migration] Will assume non-transactional DDL.
INFO  [alembic.runtime.migration] Running upgrade 37f06a334dbf -> ab124256c621, followers
```

Och nu så skall vår nya databas version vara genererad och satt som den aktiva versionen.


Steg 2. Lägga till och ta bort "follows" {#step2-add-remove-followers}
--------------------------------------------------------------------------
Vi använder oss utav [`SQLAlchemy`](https://www.sqlalchemy.org/) som vårat *active directory*. Denna modul gör det enkelt att hantera relationer mellan tabeller då den agerar som att det vore listor. Exempelvis, om `user1` vill börja följa en ny användare (`user2`), kan man bara använda `list.append()` för att lägga till den nya användaren:

```python
user1.followed.append(user2)
```


En "unfollow" kan då hanteras på ett liknande sätt:

```python
user1.followed.remove(user2)
```

Som vi ser är det ganska enkelt att följa och ta bort användare från sin lista, men eftersom det är viktigt att kunna återanvända kod, kommer vi att lägga till tre nya metoder som skall hantera detta i vår `User` modell. Detta kommer även att underlätta enhetstestningen som vi skall göra lite senare:

```python
class User(UserMixin, db.Model):
    #...
    def follow(self, user):
        if not self.is_following(user):
            self.followed.append(user)

    def unfollow(self, user):
        if self.is_following(user):
            self.followed.remove(user)

    def is_following(self, user):
        return self.followed.filter(
            followers.c.followed_id == user.id).count() > 0
```

`follow()` och `unfollow()` använder samma kod som vi gick igenom tidigare, skillnaden är att vi lägger till en extra koll `is_following()` för att undvika dubbletter om relationen redan existerar. Samma logik kan appliceras när man skall göra en "unfollow".


Steg 3. Hämta inlägg från använade man följer {#step3-collect-posts}
----------------------------------------------------------------------
Nu är vi nästan helt klara, det vi vill lägga till är är att appen även skall skriva alla inlägg från användare man följer. Till detta behöver vi lägga till en ny databas query i User modellen. Detta gör vi genom att skapa en ny metod `followed_posts`.


```python
class User(UserMixin, db.Model):
    #...
    def followed_posts(self):
        return Post.query.join(
            followers, (followers.c.followed_id == Post.user_id)).filter(
                followers.c.try == self.id).order_by(
                    Post.timestamp.desc())
```
Queryn fungerar fast den hämtar inte ens egna inlägg. Det ensklast sättet skulle vara att användarna följde sig själva men det är en ful-lösning och kommer inte att hålla i längden. Så istället gör vi en till query som hämtar ut sina egna inlägg och returnerar en `union` på dessa.

```python
def followed_posts(self):
        followed = Post.query.join(
            followers, (followers.c.followed_id == Post.user_id)).filter(
                followers.c.follower_id == self.id)
        own = Post.query.filter_by(user_id=self.id)
        return followed.union(own).order_by(Post.timestamp.desc())
```


Steg 4. Lägg till enhetstester {#step4-unittests}
--------------------------------------------------

Även om vi inte har gjort några större ändringar i koden vill vi se så försäkra oss om att allting fungerar, både nu och i framtiden. Vi använder oss utan modulen `pytest` för att skriva våra tester som i senare kursmoment, skall köras automatiskt när vi pushar upp vår kod.

```python
# pylint: disable=redefined-outer-name
from datetime import datetime, timedelta
from unittest import mock
import pytest
from app.models import User, Post
from app import db

...

def test_follow(test_app): # pylint: disable=unused-argument
    """
    Test that follow appends new Users to followed.
    Test that unfollow removes the User from followed.
    """
    user1 = User(username='john', email='john@example.com')
    user2 = User(username='susan', email='susan@example.com')
    db.session.add(user1)
    db.session.add(user2)
    db.session.commit()
    assert user1.followed.all() == []

    user1.follow(user2)
    db.session.commit()

    assert user1.is_following(user2) is True
    assert user1.followed.count() == 1
    assert user1.followed.first().username == "susan"
    assert user2.followers.count() == 1
    assert user2.followers.first().username == "john"

    user1.unfollow(user2)
    db.session.commit()
    assert user1.is_following(user2) is not True
    assert user1.followed.count() == 0
    assert user1.followers.count() == 0

def test_follow_posts(test_app): # pylint: disable=unused-argument
    """
    Test that all personal and posts from followed users are shown.
    """
    # create four users
    user1 = User(username='john', email='john@example.com')
    user2 = User(username='susan', email='susan@example.com')
    user3 = User(username='mary', email='mary@example.com')
    user4 = User(username='david', email='david@example.com')
    db.session.add_all([user1, user2, user3, user4])

    # create four posts
    now = datetime.utcnow()
    post1 = Post(body="post from john", author=user1,
                 timestamp=now + timedelta(seconds=1))
    post2 = Post(body="post from susan", author=user2,
                 timestamp=now + timedelta(seconds=4))
    post3 = Post(body="post from mary", author=user3,
                 timestamp=now + timedelta(seconds=3))
    post4 = Post(body="post from david", author=user4,
                 timestamp=now + timedelta(seconds=2))
    db.session.add_all([post1, post2, post3, post4])
    db.session.commit()

    # setup the followers
    user1.follow(user2)  # john follows susan
    user1.follow(user4)  # john follows david
    user2.follow(user3)  # susan follows mary
    user3.follow(user4)  # mary follows david
    db.session.commit()

    # check the followed posts of each user
    follow1 = user1.followed_posts().all()
    follow2 = user2.followed_posts().all()
    follow3 = user3.followed_posts().all()
    follow4 = user4.followed_posts().all()
    assert follow1 == [post2, post4, post1]
    assert follow2 == [post2, post3]
    assert follow3 == [post3, post4]
    assert follow4 == [post4]
```

Utöver att vi skapar nya användare, kollar så att de kan göra follows/unfollows ser vi också till att testa om inläggen renderas på det sätt vi tänkte oss när de användaren följer lägger till nya poster.

Vi kan nu köra `make test-unit` för att kontrollera om våra nya tester går igenom:

```bash
╰─ (venv) $ make test-unit
find . -name '*.pyc' -exec rm -f {} +
find . -name '*.pyo' -exec rm -f {} +
find . -name '__pycache__' -exec rm -fr {} +
find . -name '.pytest_cache' -exec rm -fr {} +
rm -f .coverage
rm -rf tests/coverage_html
find . -name '*~' -exec rm -f {} +
find . -name '*.log*' -exec rm -fr {} +
---> Running all tests in tests/unit
==================================================== test session starts ====================================================
platform darwin -- Python 3.7.3, pytest-6.1.1, py-1.9.0, pluggy-0.13.1
rootdir: /home/moc/git/kurser/microblog/tests/unit, configfile: ../../pytest.ini
collected 12 items

tests/unit/auth/forms/test_registration_form.py ....                                                                  [ 33%]
tests/unit/main/forms/test_edit_profile_form.py ..                                                                    [ 50%]
tests/unit/models/test_post.py .                                                                                      [ 58%]
tests/unit/models/test_user.py .....                                                                                  [100%]

==================================================== 12 passed in 0.69s =====================================================
/Library/Developer/CommandLineTools/usr/bin/make clean-py
find . -name '*.pyc' -exec rm -f {} +
find . -name '*.pyo' -exec rm -f {} +
find . -name '__pycache__' -exec rm -fr {} +
find . -name '.pytest_cache' -exec rm -fr {} +
```


Steg 5. Integrera följare med applikationen {#step5-integrate}
---------------------------------------------------------------
Funktionaliteten för backendedn existerar och går igenom testerna, det som nu behövs göras är att lägga till två nya GET routes i `app/main/routes.py` som hanterar följandet:


```python
"""
Contains routes for main purpose of app
app/main/routes.py
"""
from datetime import datetime
from flask import render_template, flash, redirect, url_for, request, current_app
from flask_login import current_user, login_required
from app import db
from app.main.forms import EditProfileForm, PostForm
from app.models import User, Post
from app.main import bp


# ...
@bp.route('/follow/<username>')
@login_required
def follow(username):
    """
    Follow a User
    """
    user_ = User.query.filter_by(username=username).first()
    if user_ is None:
        flash('User {} not found.'.format(username))
        return redirect(url_for('index'))
    if user_ == current_user:
        flash('You cannot follow yourself!')
        return redirect(url_for('user', username=username))
    current_user.follow(user_)
    db.session.commit()
    flash('You are following {}!'.format(username))
    return redirect(url_for('main.user', username=username))

@bp.route('/unfollow/<username>')
@login_required
def unfollow(username):
    """
    Unfollow a User
    """
    user_ = User.query.filter_by(username=username).first()
    if user is None:
        flash('User {} not found.'.format(username))
        return redirect(url_for('index'))
    if user_ == current_user:
        flash('You cannot unfollow yourself!')
        return redirect(url_for('user', username=username))
    current_user.unfollow(user_)
    db.session.commit()
    flash('You are not following {}.'.format(username))
    return redirect(url_for('main.user', username=username))
```

Flask och SQLAlchemy hanterar det mesta, `current_user` är den inloggade användaren och `username` användarnamnet vi skickar med i urlen.

Båda routerna har samma logik, först kollar vi om användaren existerar i vår databas och sedan kollar vi så att vi inte försöker lägga till eller ta bort oss själva.

Går dessa kontroller igenom committar vi ändringen i databasen, sätter en bekräftelse att ändringen har skett och redirectar oss till `/user/<username>`. Det sista som återstår är nu att visa upp en länk som användaren kan klicka på för att antingen editera sin profil, följa eller avfölja användaren man kollar på.


```html
<!-- app/templates/user.html -->
{% extends "base.html" %}

{% block app_content %}
    <table>
        <tr valign="top">
            <td><img src="{{ user.avatar(128) }}"></td>
            <td>
                <h1>User: {{ user.username }}</h1>
                {% if user.about_me %}<p>{{ user.about_me }}</p>{% endif %}
                {% if user.last_seen %}<p>Last seen on: {{ user.last_seen }}</p>{% endif %}
                <p>{{ user.followers.count() }} followers, {{ user.followed.count() }} following.</p>
                {% if user == current_user %}
                <p><a href="{{ url_for('main.edit_profile') }}">Edit your profile</a></p>
                {% elif not current_user.is_following(user) %}
                <p><a href="{{ url_for('main.follow', username=user.username) }}">Follow</a></p>
                {% else %}
                <p><a href="{{ url_for('main.unfollow', username=user.username) }}">Unfollow</a></p>
                {% endif %}
            </td>
        </tr>
    </table>
    <hr>
    {% for post in posts %}
        {% include '_post.html' %}
    {% endfor %}
{% endblock %}
```

Nu är allt klart, prova att starta applikationen och kolla så att allt fungerar. Det finns dock inget sätt att lista alla användare just nu, så för att se kunna se en användare behöver du gå in på deras url. E.g `http://localhost:5000/user/sven`.


Sammanfattningsvis {#sammanfattningsvis}
---------------------------------------------------------------
I devops är vi med och utvecklar, testar, automatiserar och driftsätter projekt som vi jobbar med.
Även om vi bara har gjort lite av de två första kommer ni snart att få smak på hur hela processen kan gå till.

Ni behöver inte kunna allt som står i artikeln upp och ner men iallafall ha lite koll på hur appen fungerar. Så kolla gärna igenom [introduktionen till devops appen](kunskap/introduktion_till_devops_appen) en gång till om något är oklart.

Hojta till i Discord om ni kör fast eller har andra funderingar. Annars är det bara att och kör på, lycka till!
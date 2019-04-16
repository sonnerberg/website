---
author: lew
revision:
    "2019-04-12": "(A, lew) Första versionen."
...
Python
=======================

Vi går igenom hur vi kan installera Flask och jobba med en server i Python.

Även här behöver vi lite struktur innan vi kör igång:

```
$ touch app.py Dockerfile requirements.txt
```

### requirements.txt {#requirements}

Vi kan använda filen *requirements.txt* för att specificera vad vi vill installera i kontainern. Nu är det bara Flask så den blir väldigt liten:

```
Flask

```


### app.py {#app}

Vi skapar enklast möjliga Flask-applikation. Servern har en route som returnerar "Hello from Flask!":

```
#!/usr/bin/env python3

from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello from Flask!'

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```



### Dockerfile {#dockerfile}

Det vi inte sett innan är **ENTRYPOINT**. Det fungerar likt `CMD`, förutom att om vi lägger till kommandon när vi kör `$ docker run ...` kommer inte ENTRYPOINT att ignoreras. Vi använder även pip3 för att installera det som behövs. Vi hade säker kunna hitta någon passande image med både Python och Flask installerat, men var är det roliga i det?

```
FROM debian:stretch-slim

RUN apt-get update && \
    apt-get install -y python3-pip python3-dev build-essential
COPY . /app

WORKDIR /app

RUN pip3 install -r requirements.txt

ENTRYPOINT ["python3"]

CMD ["app.py"]
```



### Bygga och köra {#build-n-run}

Nu har vi allt på plats för att bygga vår image...

`$ docker build -t python-flask-test:v1 .`

...och köra den:

`$ docker run --rm -p 5000:5000 python-flask-test:v1`

Nu kan vi peka webbläsaren mot `localhost:5000`.

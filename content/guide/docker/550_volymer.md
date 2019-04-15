---
author: lew
revision:
    "2019-04-12": "(A, lew) Första versionen."
...
Volymer
=======================

Istället för att kopiera in datan och bygga om imagen varje gång vi ändrar något kan vi använda volymer. En lokal mapp kan då mappas mot en virtuell mapp inuti kontainern. Vi kikar på hur det ser ut med en enkel sida.


### Utgångsläge {#utgangslage}

Utgångsläget är att vi har en mapp med filerna som ska servas, `example-site/`. I den har vi en index-fil. Mappen `example-site/` ska mappas mot `/var/www/html/` i servern.



### Dockerfile {#dockefile}

Dockerfilen kan se ut "som vanligt". Vi sköter volymen när vi kör kontainern.

Dockerfile:

```
FROM debian:buster-slim

RUN apt-get update && \
    apt-get -y apache2

CMD apachectl -D FOREGROUND
```

Vi bygger imagen...
```
$ docker build -t username/imagename:tag .
```

... och kör den med:
```
$ docker run -p 8083:80 -v $(pwd)/example-site/:/var/www/html/ username/imagename:tag
```

`$(pwd)` returnerar sökvägen till den mappen vi står i. Använder du Windows (cmd) kan du istället använda `%cd%` för att få fram sökvägen. Vi pekar sedan mappen `example-site/` mot den interna `/var/www/html/`. 

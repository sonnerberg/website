---
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Kopiera in filer
=======================

Vi kan kopiera in egna filer och mappar till en Docker container. Om vi har ett program vi vill kunna köra i containern behöver de kunna nås inifrån containern. Ett sätt är att använda `COPY` kommandot i Dockerfile.

```
FROM debian:buster-slim

WORKDIR scripts

COPY scripts/ /scripts/

RUN chmod +x /scripts/*.bash
```

**WORKDIR** beskriver *arbetsmappen* för kommande kommandon i Dockerfile. Om mappen inte finns så skapas den. Om vi ger relativa sökvägar till WORKDIR kommer de relatera till föregående WORKDIR's mapp.  
**COPY** kopierar in den lokala mappen *scripts* in i imagen och kallar den *scripts* även där. Notera det begynnande `/` i målet.  
**RUN** används för att köra kommandon i byggskedet av imagen. Här gör vi filerna exekverbara.

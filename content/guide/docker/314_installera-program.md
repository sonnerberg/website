---
author: lew
revision:
    "2022-04-13": "(B, lew) Uppdatering inför HT22."
    "2019-04-11": "(A, lew) Första versionen."
...
Installera program
=======================

Vi vet att vi kan exekvera kommandon via instruktionen `RUN`. Vi använder det för att köra ytterligare kommandon i containern. Låt säga att vi vill installera *nano*, *cowsay* och *fortune*.

```
FROM ubuntu:22.04

RUN apt update && \
    apt -y install nano \
    cowsay \
    fortune

WORKDIR scripts

COPY scripts/ /scripts/

RUN chmod +x /scripts/*.bash
```

För att kunna installera fler program behöver vi först uppdatera pakethanterarens listor. Sedan är det bara att installera.

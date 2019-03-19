---
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Vad är Docker?
=======================

Information om Docker hittar du på [docker.com](https://www.docker.com). Låt oss hålla det enkelt och jämföra Docker med virtualiseringsmiljön VirtualBox. Vi kan använda det för att köra andra operativsystem på vår egen dator, eller operativsystem paketerade tillsammans med programvaror. Docker kallar en sådan samling av operativsystem och programvara för en _image_ som körs i en _kontainer_. Vi kan till exempel starta upp en kontainer som bygger på en image med Linux, Apache, PHP och MySQL, och vi kan använda det utan att behöva installera dessa programvaror på vår egen dator.

Några fördelar med kontainrar är att de numera är relativt små och lättviktiga, speciellt med tanke på att vi inte har så stora problem med lite diskutrymme längre. En kontainer har även samma beteende, oberoende på vilken övrig miljö vi använder.  

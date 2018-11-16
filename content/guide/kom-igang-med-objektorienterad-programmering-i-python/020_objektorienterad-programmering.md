---
author: aar
revision:
    "2018-11-16": "(A, aar) Första versionen, kopierade från php guiden och ändrat."
...
Objektorienterad programmering
==================================

Objektorienterad programmering är *en* av många programmeringsparadigmer. Ett programmeringsspråk sorteras vanligen in i en programmeringsparadigm för att beskriva hur man kan koda i det. Många språk stödjer flera programmeringsparadigmer, man kan alltså välja hur man skriver sin kod, enligt en eller flera paradigmer. Ett vanligt sätt att lära sig programmera är "[procedural programmering](https://en.wikipedia.org/wiki/Procedural_programming)". Det är det sättet du har använt dig av i tidigare kurser. Men nu handlar det alltså om den [objektorienterade programmeringsparadigmen](https://en.wikipedia.org/wiki/Object-oriented_programming).



Objekt {#objekt}
----------------------------------

I objektorientering finns objekt. Ett objekt har instansattribut (properties) och metoder (funktioner kopplade till ett objekt). Instansattribut används för att lagra ett *state* av ett objekt, ett visst läge som definieras av värdet på dess instansattribut. När man vill ändra ett läge för objektet, eller bara använda objektet för att utföra en uppgift, då använder man dess metoder. Metoderna är en förteckning över vad objektet kan göra. Vi kan kalla det objektets API.

Ett objekt har all sin förmåga samlad i metoder och attribut. Allt som objektet behöver lagra finns i dess instansattribut och allt man kan göra med objektet exponeras via dess metoder. Exakt hur objektet verkställer saker och ting är objektets ansvar. Man kan säga att objektet *kapslar in* detaljerna för implementation och erbjuder endast ett publikt API (gränssnitt) i form av metoderna. Själva implementationen av metoderna är en sak för objektet själv. 



Klass {#klass}
----------------------------------

Ett objekt skapas utifrån en klass. En klass är en mall utifrån vilken man kan skapa nya objekt. När man skapat ett objekt kallas det en instans av klassen. Att skapa ett objekt kan kallas att [instansiera](http://en.wikipedia.org/wiki/Instance_(computer_science)) klassen till ett objekt, eller att instansiera ett objekt av klassen.



Manualen {#manualen}
----------------------------------

Vår bästa vän är som vanligt manualen som har beskrivningar över [objekt och klasser](https://docs.python.org/3/tutorial/classes.html).

> *Referensmanualen är din bästa vän.*

Låt oss skriva en klass.

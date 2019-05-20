---
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Vad är Docker?
=======================

Låt oss hålla det enkelt och jämföra Docker med virtualiseringsmiljön VirtualBox. Vi kan använda det för att köra andra operativsystem på vår egen dator, eller operativsystem paketerade tillsammans med programvaror. Docker kallar en sådan samling av operativsystem och programvara för en _image_ som körs i en _kontainer_. Vi kan till exempel starta upp en kontainer som bygger på en image med Linux, Apache, PHP och MySQL, och vi kan använda det utan att behöva installera dessa programvaror på vår egen dator.

Några andra fördelar med kontainrar är att de numera är relativt små och lättviktiga, speciellt med tanke på att vi inte har så stora problem med lite diskutrymme längre. En kontainer har även samma beteende, oberoende på vilken övrig miljö vi använder. En kontainer innehåller även allt som mjukvaran behöver för att fungera som utvecklaren planerat.

Vi kan titta på några grundskillnader mellan VM's (VirtualBox) och Kontainrar (Docker):

| VM's                                                	| Kontainrar                                  	|
|-----------------------------------------------------	|---------------------------------------------	|
| Fullständig isolering av applikationer från Host OS 	| Kan dela resurser mellan applikation och OS 	|
| Varje VM har eget OS                                	| Varje kontainer kan dela OS resurser        	|
| Startar på några minuter                            	| Startar på några sekunder                   	|
| Kräver mycket resurser                              	| Kräver mindre resurser                      	|
| Svårt att hitta färdigkonfigurerade VM's            	| Finns gott om färdiga kontainrar            	|
| Tar ofta mycket plats                               	| Tar ofta mindre plats                       	|
| Kan enkelt flytta en VM till en annan Host          	| En kontainer förstörs och startas på nytt   	|
| Tar lång tid att skapa                              	| Går snabbt att skapa                        	|

Mer information om Docker hittar du på [docker.com](https://www.docker.com).

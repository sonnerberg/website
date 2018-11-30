---
author: efo
revision:
    "2018-10-11": "(A, efo) Första versionen."
...
Detaljer
=======================

Vi tar nedan en titt på några av detaljerna i ramverket som kan göra en stor skillnad för helheten.



### Breadcrumbs

En detalj som ofta glöms bort är de små länkar som underlättar navigation i ett träd av sidor på en webbplats. Vi har i nedanstående exempel utgått från de breadcrumbs som finns här på sidan. Att lägga dessa på en rad med '/' eller annan avdelare i mellan ger ett lugnt och trevligt utseende, som bidrar till helheten. Vi använder pseudo-selektorerna `::after`, `:last-child` och `:hover` för att få till alla delar av breadcrumbs.

[CODEPEN src=PxXQPY user="dbwebb" tab="result" caption="Breadcrumbs"]

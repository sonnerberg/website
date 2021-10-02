---
author: mos
category:
    - kurs webtec
revision:
    "2021-06-15": "(A, mos) Första utgåvan."
...
Bygg en databasdriven webbplats med PHP med SQL
===================================

Du skall bygga en databasdriven webbplats och använda CRUD (Create, Read, Update, Delete) för att jobba mot databasen.

<!--more-->

[WARNING]

**Arbete pågår**

Artikeln visar grovt veckans uppgift men detaljer skall uppdateras.

[/WARNING]



Förkunskaper {#forkunskaper}
-----------------------

Du har grundläggande kunskap om databasen SQLite och SQL.

Du har grundläggande kunskap om PHP PDO.

Du vet vad begreppet CRUD innebär i sammanhanget.

Du kan bygga webbsidor med PHP och begreppet sidkontroller och vyer.

Du kan HTML formulär med GET och POST samt du vet vad "self submitting form" och en processingsida med redirect innebär.



<!--
Genomgång {#genom}
------------------------

Här är en video som "pratar" dig igenom uppgiftens upplägg och visar hur du kommer igång.

[YOUTUBE src="gKzwQTG9eCI" width=700 caption="Kurs mvc kmom03 tisdagsgenomgång, del 3/3 uppgiften (Zoom med Mikael)."]
-->



Introduktion och förberedelse {#intro}
-----------------------

I denna uppgiften skall du spara alla filerna i katalogen `me/pdoweb`.

Använd din ToDo databas som grund för uppgiften. Spara databasfilen i `me/pdoweb/db/todo.sqlite`.

Du har sedan tidigare utvecklat en webbplats i `me/session`. Du kan utgå från den och dess innehåll för att nu tillföra sidkontroller som kopplas till databasen.

Det finns också en tom kodbas som du kan utgå ifrån.

Det är bara de databasrelaterade sidkontrollerna som är viktiga i uppgiften. Du kan själv välja om din webbplats innehåller fler sidkontroller, till exempel genom att låta dina sidkontrollers från uppgiften `me/session` vara kvar. Eller så låter du uppgiften enbart innehålla databasrelaterade sidkontrollers.



Kopiera {#kopiera}
-----------------------

Du kan välja om du vill utgå från en tom kodbas eller om du vill kopiera din kodbas från `me/session`

Så här börjar du med en tom kodbas.

```text
# Gå till roten av ditt kursrepo
cp -ri example/php/pagecontroller-setup/* me/pdoweb/
cd me/pdoweb
```

Så här börjar du genom att kopiera din kodbas från `me/session`.

```text
# Gå till roten av ditt kursrepo
cp -ri me/session/* me/pdoweb/
cd me/pdoweb
```



Installera med composer {#composer}
-----------------------

Börja med att uppdatera din installation med composer.

```text
composer update
```



Krav {#krav}
-----------------------

Utför följande krav.

De krav som är markerade med [OPTIONELL] är valbara och du väljer själv om du vill utföra dem.


1. Sidkontroller "Status" som visar om du har extension för PDO och SQLite installerad i PHP och Apache.

1. Sidkontroller "Connect" som visar att du kan koppla upp dig mot databasen. Koden som kopplar dig mot databasen skall sparas i en funktion.

1. Sidkontroller "Select" som visar att du kan koppla upp dig mot din databas och ställa en SELECT fråga och visa upp resultsetet, på något vis.

1. Sidkontroller "Search" som låter dig söka i databasen, via ett GET formulär.

1. Sidkontroller "Show" som låter dig visa flera rader i en tabell genom att söka efter något.

1. Sidkontroller "Single" som låter dig visa en rad genom att skicka in ett id i querysträngen. Du kan visa värdena i ett formulär där alla fälten är readonly.

1. Uppdatera sidkontrollern "Show" och länka samman den med "Single". Du skall i "Show" kunna klicka på radens id och komma till sidan som heter "Single" som visar en rad med samma id.

1. Sidkontroller "Insert" som låter dig stoppa in en ny rad i databasen. När raden är tillagd skall det göras en redirect till "Single" och visa den nya raden.

1. [OPTIONELL] Sidkontroller "Update" som låter dig uppdatera en rad i databasen. Man kan först leta reda på den raden man vill uppdatera i "Show", sedan kan man klicka på en länk i den raden som heter "Edit". Man kommer då till ett (post) formulär där man kan redigera innehållet i raden och sedan spara det (via en processingsida).

1. [OPTIONELL] Sidkontroller "Delete" som låter dig radera en rad i databasen. Man kan först leta reda på den raden man vill uppdatera i "Show", sedan kan man klicka på en länk i den raden som heter "Delete". Man kommer då till ett (post) formulär där man får en fråga om man verkligen vill radera raden, klickar man "Yes" raderas raden (via en processingsida).

1. Besvara följande frågor i din redovisningstext.

    * Berätta hur det gick att lösa uppgiften, var något extra svårt, lurigt, krångligt eller flöt det på smidigt?
    * Är det något som du är extra nöjd med i ditt resultat från uppgiften?



Publicera {#publicera}
-----------------------

Avsluta uppgiften så här.

1. Validera och publicera ditt resultat på studentservern `dbwebb publish pdoweb`.

1. Testa ditt resultat så att det passera de automatiska testerna med `dbwebb test pdoweb`.

1. När du är klar kan du publicera resultatet med `dbwebb publish pdoweb`.

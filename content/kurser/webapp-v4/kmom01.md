---
author:
  - efo
revision:
  "2022-01-17": (A, efo) Första utgåvan för kursen.
...
kmom01: Vår första React Native app
==================================

Vi ska i detta kursmomentet ta en titt på hur vi utvecklar appar med hjälp av ramverken React Native och Expo. Vi tar en titt på båda ramverken och hur vi utvecklar med hjälp av TypeScript i React Native. Dessutom introduceras Lager-API:t som är med oss i kmom01-kmom06 och hur vi hämtar data från det API:t.



<!--more-->



Vi har i tidigare kurser sett hur vi man kan skapa applikationer i webbläsaren där vi aldrig laddar om sidan. Vi ska fortsätta på det spåret och bygga vidare på detta med webbens inbyggda teknologier för till exempel hämtning av data från ett API.

Som ett första steg skapar vi en me-app anpassat främst för mobilen, men som även fungerar klockrent på en större enhet. På en av sidorna i vår me-app hämtar vi data från Github för att visa upp våra repon. Det är även här vi skriver redovisningstexten så vi ska titta på hur vi gör mycket text lättläst på små och stora enheter.

Som en sista del av kursmomentet ska vi börja med en löpande uppgift där vi i detta kursmoment skapar början till en lagerhanteringsapp. Nedan finns en liten video som visar hur det kan se ut när man är klar med Lager appen del 1.

[YOUTUBE src=xp8blJ060XM width=630 caption="Lager appen del 1."]



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 1 studietimme)*

Det finns en [längre beskrivning om kursens labbmiljö](./../installera-labbmiljo). Läs den om du är osäker på vad som skall göras, eller om detta är din första dbwebb-kurs.

[Installera labbmiljön](kurser/webapp-v4/labbmiljo) för kursen.

Uppdatera [dbwebb-cli](dbwebb-cli) samt klona och initiera kursrepot.

```text
# Gå till din katalog för dbwebb-kurser
dbwebb selfupdate
dbwebb clone webapp
cd webapp
dbwebb init
```



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 6-10 studietimmar)*



### Artiklar {#artiklar}

Läs följande artiklar för att få bakgrunden till övningarna.





### Video  {#video}

1. Det finns en [videoserie](https://www.youtube.com/playlist?list=PLKtP9l5q3ce-1cVPTFJ_Zw9b7N2Y4_ANI) kopplat till kursen, titta på videos som börjar på 0 och 1.



### Lästips {#lastips}

1. Läs översiktligt denna samling av "best-practices" för typografi på webben [Typography Handbook](http://typographyhandbook.com). Spara den i dina bokmärken som en framtida referens.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 6-10 studietimmar)*



### Övningar {#ovningar}

Gör följande övningar för att träna inför uppgifterna.

1. Läs igenom artikeln "[Typografi i mobila enheter](kunskap/typografi-i-mobila-enheter)". Spara koden i `me/kmom01/typography`.

1. Gör övningen "[En Single Page Application](kunskap/en-single-page-application-me-app)". Spara resultatet i `me/redovisa`.





### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Lager appen del 1](uppgift/lager-appen-del-1)". Spara din kod i `me/kmom01/lager1-v2`.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Är du sedan tidigare bekant med utveckling av mobila appar?
* Vad tycker du om utvecklingsmiljön med React Native och Expo jämfört med utvecklingsmiljön i tidigare dbwebb-kurser?
* Vilket är den viktigaste lärdomen du gjort om typografi för mobila enheter?
* Du har i kursmomentet hämtat data från två stycken API. Hur kändes detta?

TIL är en akronym för “Today I Learned” vilket leksamt anspelar på att det finns alltid nya saker att lära sig, varje dag. Man brukar lyfta upp saker man lärt sig och där man kanske hajade till lite extra över dess nyttighet eller enkelhet, eller så var det bara en ny lärdom för dagen som man vill notera.

* Vilken är din TIL för detta kmom?

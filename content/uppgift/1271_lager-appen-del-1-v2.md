---
author: efo
category: javascript
revision:
  "2022-02-16": (A, efo) Första utgåvan i samband med kursen webapp v4.
...
Lager appen del 1
==================================

[FIGURE src=image/webapp/warehouse.jpg?w=c5 class="right"]

I denna uppgift skapar du grunden för en lager-app, du använder dina kunskaper från övningar och kurslitteratur för att skapa en mobil-app. Du hämtar JSON data från ett befintligt REST API och i denna första del ligger fokus på en enkel listning av produkter.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------
Du har jobbat igenom guiden "[Kom igång med Git och GitHub](guide/git)" och övningarna "[En app i Expo och React Native](kunskap/en-app-i-expo-och-react-native)" och "[Typografi i mobila enheter](kunskap/typografi-i-mobila-enheter)".



Introduktion {#intro}
-----------------------
Du har blivit kontaktat av företaget Infinity Warehouses då ryktet går på stan att du har koll på mobila applikationer. Infinity Warehouses vill ta steget in i 2000-talet och automatisera deras gamla omoderna lagerhanteringssystem. Infinity Warehouses har tidigare anställd en backend programmerare, men när hen hörde orden design, användbarhet och tillgänglighet sprang hen skrikande bort. Backend programmeraren hade dock hunnit skapa ett REST API innan hen försvann ner i serverrummet. [Dokumentationen för API:t](https://lager.emilfolino.se/v2) hjälper dig en bit på vägen.

Skapa först en API-nyckel som du använder för att hämta just din data. Du kan sedan välja om du vill skapa nya produkter eller kopiera de befintliga produkterna. Du kommer i kommande kursmoment fortsätta arbetet med din lager-app, så rekommendationen är att skapa dina egna produkter då du kan vinkla din app mot dina intressen.

Ett bra verktyg för att testa sig fram med API:er är Postman. Du kan även skapa egna produkter eller ändra de som du kopierade med Postman.

I följande videos visar Emil hur du skapar en API-nyckel. I Postman fortsätter vi sedan med att kopiera den befintliga uppsättning produkter och uppdatera produkterna så de blir lite mer intressanta. Vi skapar även helt nya produkter.

[YOUTUBE src=Ad7R_iHXR7k width=630 caption="API nyckel"]

[YOUTUBE src=464oRgVq4ns width=630 caption="Kopiera produkter"]

[YOUTUBE src=AFMaZJk_jmo width=630 caption="Ändra produkt"]

[YOUTUBE src=nwcFboQY_lk width=630 caption="Skapa produkt"]



Krav {#krav}
-----------------------

1. Skapa en applikation anpassad för mobilen i Expo och React Native.

1. Appen ska innehålla en lagerförteckningslista där produkterna listas med namn och hur många som finns.

1. Commit:a dina ändringar och lägg till en ny tagg (v1.0.*).

1. Push:a repot till GitHub, inklusive taggarna.



Extrauppgift {#extra}
-----------------------
Det finns inga extrauppgifter.

---
author:
    - nik
revision:
    "2020-10-12": (A, nik) Nysläpp för design-v3
...
Kmom02: SASS och typografi
====================================

[WARNING]
***Utveckling pågår***

Detta kmom är under uppdatering, påbörja inte förrän denna gula rutan är borttagen.

[/WARNING]

Vi har nu en bas av en webbplats. Vi vet hur vi lägger till innehåll i webbplatsen och vi kan styla den. Låt oss då gå vidare och skapa en bättre bas för vårt tema. Temat, eller vår style, skapar vi med hjälp utav SASS, en preprocessor till CSS. Vi lär oss grunderna i SASS och hur vi bygger CSS-filer från SASS-konstruktioner.

Vi försöker bygga en modulär struktur av SASS-filer som vi delar in i SASS-moduler. Det skapar en grund som blir enklare att återanvända i andra 
sammanhang men även enklare att jobba med. Vi testar att överföra vårt tema ifrån kmom01 till SASS. Därefter bygger vi vidare på vårt tema och samtidigt fördelar vi koden i olika SASS-moduler.

<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>


Labbmiljön  {#labbmiljo}
---------------------------------

*(ca: 2-4 studietimmar)*

Installera följande.

1. Installera labbmiljön för Node.js och npm via "[Installera nodejs och npm](labbmiljo/node-och-npm)".



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*



### Kurslitteratur  {#kurslitteratur}

Läs följande:

1. Läs i boken "[The Principles of Beautiful Web Design](kunskap/boken-the-principles-of-beautiful-web-design)". Det ger dig en bakgrund i tankar och hur man gör layout och komponerar ihop designen i en webbsida.

    * Kap 1: Layout and Composition
    * Kap 4: Typography



### Design med HTML5 och CSS3  {#guide}

1. Läs igenom följande sektion i guiden "[Design med HTML5 och CSS3](guide/design-med-html5-och-css3)".
    * [Typografi](guide/design-med-html5-och-css3/typografi)
    * [Responsivitet](guide/design-med-html5-och-css3/responsivitet) (repetition)

I sektionen [Typografi](guide/design-med-html5-och-css3/grid-och-typografi) tittar vi främst på hur typografi kan skapa lättläst och anpassad typografi på en webbplats.

### SASS {#sass}

För att komma igång så kan du läsa igenom följande artiklar:

1. Läs översiktligt Kalles artikel om CSS preprocessors, "[CSS Preprocessors are cool](http://dbwebb.se/article/Kalle_CSS_LESS_SASS.pdf)". Artikeln ger en introduktion till CSS preprocessorer och behandlar skillnader och likheter mellan LESS och SASS som är två olika preprocessorer till CSS.

1. I kursen använder vi SASS så bekanta dig med [SASS](https://sass-lang.com/guide) och se vad du kan göra. SASS är uppbyggd som ett programmeringsspråk, så kika runt bland de manualer som finns men fokusera på "SASS Basics" för att lära dig hur du skriver SASS konstruktioner.

### SASS moduler {#sassmodul}

Följande moduler kommer du att använda när du bygger ditt tema i den kommande uppgiften.

1. Kika på hur du kan nollställa style med [Normalize.css](http://necolas.github.com/normalize.css/) samt läs snabbt om hur [Normalize fungerar](http://nicolasgallagher.com/about-normalize-css/) och vem som använder det.

1. Titta snabbt och översiktligt på [Font Awesome](https://fontawesome.com/) och se vilka ikoner man kan skapa med dess hjälp. Leta reda på webbsidan som visar hur man installerar Font Awesome och se om du kan hitta hur man installerar det som en LESS-modul med hjälp av pakethanteraren npm. Vi kommer att göra detta senare i uppgiften.

### Fonter och ikoner {#fonter}

Det finns mängder med sidor där man kan hitta ikoner och fonter gratis, nedan listas några av alternativen:

* [Google Fonts](https://fonts.google.com/)
* [DaFont](https://fontawesome.com/)
* [Font Awesome](https://fontawesome.com/)
* [Icons8](https://icons8.com/)

Många av de ikoner och emojis man ser idag bestäms av [Unicode Consortium](https://en.wikipedia.org/wiki/Unicode_Consortium) som består av nio medlemmar, där bland Microsoft, Apple och Google. Det gör att en många ikoner/emojis finns tillgängliga oavsett vilken enhet man surfar via, utan att behöva ladda ner några ytterligare filer. Värt att notera är dock att ikonerna skiljer sig mellan olika enheter. Du kan se vilka som är tillgängliga här:

* [Unicode Icons](https://unicode-table.com/en/)

### Om responsivitet {#responsivitet}

Läs följande om responsivitet.

1. Läs artikeln "[Responsive Web Design Basics](https://developers.google.com/web/fundamentals/design-and-ux/responsive/)" som ger dig en introduktion i tekniker kring ämnet.


Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*

### Testa på {#testa}

Det finns ett färdigt exempel i `example/sass-example` som innehåller de nödvändiga filerna för att testa på SASS. För att jobba med dem, ställ dig i roten av kursrepot och kör:

```bash
rsync -rd example/sass-example/ me/kmom02/sass/
```

Hoppa in i mappen och testa lägg till din egna regel till exemplet. För att göra om din SASS (.scss) till CSS så kan du köra `npm run style` förutsatt att du har node/npm installerat och hämtat hem de nödvändiga modulerna med hjälp av `npm install`.

### Övningar {#ovningar}

Följande övningar bör genomföras:

1. Arbeta igenom artikeln [Kom igång med SASS och npm](kunskap/kom-igang-med-sass-och-npm) som hjälper dig att sätta upp SASS i din portfoliosida.

1. Arbeta igenom artikeln [Ikoner och fonter](kunskap/design-ikoner-och-fonter) som går igenom hur man kan ladda in ikoner och fonter.


### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Lös uppgiften ["Utveckla din portfolio sida med en om-sida och ett SASS-tema"](uppgift/utveckla-din-portfolio-kmom02).

1. Försäkra dig om att du har gjort `dbwebb publish me` och taggat din inlämning med version 2.0.0 (eller högre) samt pushat repot inklusive taggarna till GitHub.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Vad tycker du om SASS än så länge?
* Är du bekant med Node, npm eller npm scripts (t.ex. `npm run lint`) sedan tidigare? Vad anser du om det?
* Hur kändes det att kompilera SASS till CSS, var det något du reflekterade över?
* Kommentera ditt tema, hur kan man beskriva dess design och hade du några planer på "design" när du byggde ditt tema?
* Valde du att dela upp din kod? Vilka uppdelningar valde du att göra?
* Vilken är din TIL för detta kmom?

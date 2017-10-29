---
author:
    - mos
category:
    - labbmiljo
    - kursen ramverk2
    - test
revision:
    "2017-10-23": (A, mos) Första versionen.
...
Kom igång med en testmiljö i JavaScript
==================================

[FIGURE src=image/snapht17/docker-logo.png?w=c5 class="right"]

Tanken är att vi förbereder oss för ett större utvecklingsprojekt i JavaScript och vi vill säkerställa att vi har en utvecklingsmiljö där vi kan testa vår programvara.

Vilken typ av tester vill vi göra och vilka verktyg kan hjälpa oss med detta? Låt oss gå igenom läget i JavaScript och använda några testrelaterade verktyg för att sätta en grund.

<!--more-->

[WARNING]
** Arbete pågår **
<[/WARNING]
<!--stop-->



Förkunskaper {#forkunskaper}
--------------------------------------------------------------------

Du har en labbmiljö motsvarande kursen ramverk2 och du kan grunderna i enhetstestning.



Testning {#testning}
--------------------------------------------------------------------

Låt oss först ta lite om olika typer av testning.



### Enhetstestning {#unit}

På engelska blir det _unit testing_ ([Wikipedia om Unit Testing](https://en.wikipedia.org/wiki/Unit_testing)) och det handlar om att testa varje enhet av kod för sig själv. Det är _white box testing_ ([Wikipedia om White box testing](https://en.wikipedia.org/wiki/White-box_testing)) eftersom vi har full insyn i koden vi testar. Vi kan se källkoden och vi kan se att våra testfall verkligen exekverar alla delar av koden. Förutsatt att vi använder oss av kodtäckning, code coverage ([Wikipedia om Code Coverage](https://en.wikipedia.org/wiki/Code_coverage)). Att se kodtäckningen är viktigt i enhetstesterna, annars gör vi det onödigt svårt för oss. Kodtäckning är också ett sätt att visa för utomstående hur mycket av kodbasen som är testad via enhetstester. Att nå 100% i kodtäckning är bra, men man nöjer sig ofta med 70%. Hur myckt kodtäckning man kan få är också beroende av hur testbar koden är. Är koden inte skriven för att vara testbar så kan man ge sig på att det är svårt att skriva testfall i enhetstester och uppnå hög kodtäckning.

Varje testfall i enhetstestet innebär att man anropar en eller flera metoder/funktioner i sitt testobjekt. Testobjektet är den kodmodul man testar. Därefter så verifierar man att ett visst utfall är uppfyllt. Man har alltså vissa förväntningar på vad som skall hända när koden körs och det skall man verifiera efter att koden körts. Vi kallar detta _assertions_ ([Wikipedia om Assertion](https://en.wikipedia.org/wiki/Assertion_(software_development))) som är villkor som skall vara uppfyllda.

> "If there is no assertion, it isn't a test."

När man tänker på test och utveckling av kod i samklang så tenderar man att skriva kod som också är testbar och enkel att testa. Det blir till en erfarenhet som sitter i ryggraden om att koden jag skriver måste gå att testa i enhetstester. Bäst att skriva den testbar med ett tydligt publikt API och resten skyddat. Här funderar jag på vad som kan injectas in i modulen och troligen tänker jag igenom vad som kan mockas och inte ([Wikipedia om Mock object](https://en.wikipedia.org/wiki/Mock_object)), redan när jag utvecklar och skriver koden. När jag ser att jag skriver kod som är svår att testa så kan jag alltid välja att göra refactoring för att koden skall vara enklare att testa.

Det är alltså olika att skriva helt ny kod som man vill skall vara testbar, jämfört med att införa enhetstester för kod som inte nödvändigtvis är speciellt testbar i sitt ursprungsläge.

Varje testfall skall kunna köras isolerat från alla andra testfall. Man behöver alltså tänka på att varje test man skriver skall kunna köras oberoende av de andra testerna och oberoende av testernas inbördes ordning. Dte burkar finnas stöd för att sätta upp en miljö för varje testfall och/eller suite av testfall. En bonus när man lyckas med detta är att alla tester kan köras parallellt. Det är en fördel när alla tester börjar ta längre tid, att köra tester parallellt snabbar upp och effektiviserar utvecklingsitden.



### Testdriven utveckling {#tdd}

TDD är förkortningen av testdriven utveckling ([Wikipedia om Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development)) som är en utvecklingsprocess som säger att man börjar skriva ett eller flera testfall och därefter skriver man koden för att lösa testfallen.

Vi kan förklara utvecklingsmodellen med följande steg.

1. Skriv ett tetfall.
2. Exekvera testsuiten och se testfallet misslyckas.
3. Skriv koden.
4. Kör testerna (alla passerar).
5. Refactor, skriv om, organisera om, kodbasen efterhand som den växer.
6. Repetera.

TDD säger alltså att vi pratar i termer om testfall och utvecklingen, koden vi skriver, drivs fram av de testfall vi lägger till.

Som en bonus blir all vår kod testbar och troligen skriven för att vara testbar.

TDD får oss att skriva koden som löser testfallen, möjligen får det oss att fokusera på det som är viktigt i koden.



### Behaviour driven utveckling {#bdd}

BDD är en vidareutveckling av TDD och står för Beteende-driven utveckling ([Wikipedia om Behavior-driven development](https://en.wikipedia.org/wiki/Behavior-driven_development))
BDD. Det som är intressant i BDD, ur aspekten testning, är att man diskuterar systemet i features som skrivs ned i ett textdokument. Dessa features dokumenteras på ett sätt så att både programmerare och systemets slutanvändare och ledning kan förstå dem. Det blir ett material där olika roller kan diskutera hur systemet skall fungera. Man får ett egen språk att samtala om systemet.

Dessa features, berättelser om hur systemet skall fungera, kan sedan automatgenerera testfall som kan köras av programmeraren. Dessa kan sedan styra utvecklingen och koden som skrivs för att lösa feature för feature.

Så här kan en feature vara skriven, exemplet är taget från [`mosbth/cimage`](https://github.com/mosbth/cimage/tree/resize/features).

```text
Feature: src
    Display an image by selecting its source.

    Scenario: Source is not a valid image name
        Given Set src "NO_IMAGE"
        When Get headers for image
        Then Returns status code "404"

    Scenario: Get only source image
        Given Set src "test_100x100.png"
        When Get image
        Then Returns status code "200"
        And Compares to image "test_100x100.png"
```

I fallet ovan används programvaran Behat för att parsa featuren och generera testbar kod och för att exekvera alla testfall. Den som jobbar med testsuiten behöver skriva en del kod bakom för att hanteringen kring `Given`, `When`, `Then` och `And` skall fungera, se det som att det är metoder som utförs bakom texten.

BDD kan vara en bra utvecklingmetodik som driven utvecklingen via testbar kod och erbjuder ett språk som både programmerare och icke-programmerare kan prata.



### Funktionstester {#functiontest}

Låt oss benämna funktionstester ([Wikipedia om Functional testing](https://en.wikipedia.org/wiki/Functional_testing)) som testar en feature, en systemfunktion. Ta ett exempel att "registrera en ny användare". Ett sådant test innebär att man utför de steg som krävs för att registrera en användare. Det kan vara genom att använda ett grafiskt användargränssnitt (GUI), eller genom ett CLI-interface (Commandline interface) eller via ett API i koden eller ett publikt API via REST.

Funktionstester är i allmänhet _black-box tester_ ([Wikipedia om Black-box testing](https://en.wikipedia.org/wiki/Black-box_testing)) där man inte nödvändigtvis behöver ha koll på den underliggande koden. Man vill testa en systemfunktion och man bryr sig inte om vilka underliggande moduler som används.

Det kan finnas ett gränsområde där enhetstester övergår i funktionstester, gränsen går troligen någonstans där man slutar mocka och istället använder systemets riktiga moduler för att utföra en systemfunktion, men eller utan ett gränssnitt (GUI/CLI/API).

I webbsammanhang vill man ofta utföra funktionstester i formen av en webbläsare, man vill simulera en webbläsare för att utföra hela åtgärden "registrera en ny användare". I sådana fall finns det programvara som hjälper testaren att simulera knapptryck och analysera webbsidan som kommer tillbaka som svar. Programvaran benämns ofta _headless browser_ ([Wikipedia om Headless browser](https://en.wikipedia.org/wiki/Headless_browser)) och det kan vara ett viktigt verktyg i testning.

Det är alltmer vanligt att en webbtjänst både erbjuder ett (REST) API och ett traditionellt webb-GUI. Det kan göra webbtjänsten enklare att testa då ett (REST) API ger en tydlig bild av vad man kan göra med systemet. Ett traditionellt webb-GUI är inte nödvändigtvis lika tydligt om man man kan göra och vilket resultat man får tillbaka.



### Övriga tester {#ovriga}

Det finns många fler typer av tester som man kan vilja genomföra och kategorisera som egna typer av tester. Låt oss nämna några.

Integrationstester ([Wikipedia om Integration testing](https://en.wikipedia.org/wiki/Integration_testing)) fokuserar på att testa att flera moduler kan samverka på ett tänkt sätt. Man ser det som ett steg i en CI pipeline (Continuous integration) att alla moduler, eller en delmängd av dem, behöver integreras i någon steg och då kan man verifiera med en testsuite att integrationen gick bra. Likt alla testfaser behöve man bestämma kiteria för vad som skall testas, hur och vad som bestämmer att testerna går bra.

I systemtestfasen ([Wikipedia om System testing](https://en.wikipedia.org/wiki/System_testing)) utförs en serie av tester mot systemet som helhet. Alla moduler är på plats och systemet snurrar i en miljö som är relevant och motsvarar systemets riktiga driftsmiljö. Man kan utföra säkerhetstester, usabilitytester, prestandatester och stresstester eller tester av dokumentationen. Man tänker på systemet som helhet och testar de aspekter som är viktiga och relevanta. I systemtestet kan man verifiera systemets icke-funktionella krav via icke-funktionella tester ([Wikipedia om Non-functional testing](https://en.wikipedia.org/wiki/Non-functional_testing)).

Ett annat test som kan vara av vikt är acceptanstester ([Wikipedia om Acceptance testing](https://en.wikipedia.org/wiki/Acceptance_testing)). Det är tester som utförs inför, tillsammans med, eller av kunden, när de tar emot leveransen. Där är ett viktigt dokument där du och kunden gemensamt tagit fram som en del av beställningen och där testerna som beskrivs syftar till att testa att kunden verkligen fått det de beställde. Ur beställarens synpunkt kan acceptanstestet vara nästan lika viktigt som kravspecen då ett avklarat acceptanstest innebär att fakturan kan skickas och kunden har accepterat att systemet möter de kriteria som var viktigt.



Testverktyg för JavaScript {#toolsjs}
--------------------------------------------------------------------

Som i de flesta programmeringsspråk så erbjuder ekomiljön kring JavaScript ett större utbud av verktyg som kan användas för att bygga upp en testmiljö.

Om vi börjar "underifrån" med enhetstester så är de mer kända verktygen [Mocha](https://mochajs.org/) och [Jasmine](https://jasmine.github.io/) med en tydlig uppstickare av [Jest](http://facebook.github.io/jest/).

Det är inte en enkel sak att välja testverktyg, men om man börjar välja något så kan man ta det vidare därifrån.

På min kravlista finns att kodtäckning skall fungera för mina enhetstester. I JavaScript-världen finns främst [Istanbul](https://istanbul.js.org/) och [Blanket.js](http://blanketjs.org/) som ger oss denna möjlighet. Testverktyget jag väljer behöver alltså ha en känd koppling mot något av dessa verktyg.

När jag går från enhetstester till funktionstester så kan behovet av en headless browser komma upp. Här finns [Selenium](http://www.seleniumhq.org/) som en av de mer kända. Men alternativen är flera.

När jag väl bestämt mig för verktygen behövs en testrunner som kör mina tester och en hantering av testrapporten så den kan visas upp för programmerare och kanske även extern personal.

Allt som allt, någonstans här är namnen på de testverktyg som vanligtvis används inom JavaScript och jag tänker välja bland dessa.



Kodmoduler att testa {#kodmoduler}
--------------------------------------------------------------------

Innan jag väljer verktyg så behöver jag en kodbas som jag vill testa. För denna övnings skull så bygger jag en kortlek och ett [kortspel Black Jack](https://sv.wikipedia.org/wiki/Black_Jack). Det bör fungera för att visa hur testerna kan fungera med den testmiljö jag nu skall välja.

_Du hittar mitt exempelprogram i kursrepot för ramverk2 under `example/black-jack`. Där finns det körbart i form av ett CLI-program, ett RESTful API och ett webb-GUI. Se dess README-fil för att se hur du startar upp respektive klient och hur du kör testsuiten._

Låt oss då titta på de olika tester som körs på systemet och vilka verktyg jag valde.



Enhetstestning i JavaScript {#unitjs}
--------------------------------------------------------------------

Det första testverktyget jag valde är för enhetstester. De verktygen jag valde mellan var främst [Mocha](https://mochajs.org/), [Yasmine](https://jasmine.github.io/) och [Jest](http://facebook.github.io/jest/). Mitt val föll på Mocha och jag gjorde ett testprogram i `example/test/unittest-mocha` för att se hur det fungerade.

```text
example/test/unittest-mocha$ tree .
.          
├── package.json     
├── src             
│   └── card        
│       └── card.js 
└── test           
    └── card 
        ├── card.js   
        └── cardParameterized.js
```

Min källkod finns i `src/card` och mina enhetstester ligger i `test/card`. De båda filerna under test-katalogen innehåller samma tester, men testfallen är olika implementerade. Börja att kika i filen `card.js` då den är tydligast i hur testfallen kan skrivas. När du tycker att det blir alltför mycket kod i testfallen så tittar du istället i `cardParameterized.js` för att se hur man kan skriva mindre kod för samma testfall.

Koden som testas är en klass `Card` som skall fungera som ett kort i en vanlig kortlek.

Innan vi kan köra testerna så behöver vi installera Mocha. Det går att installera med `npm install mocha` eller bara `npm install` eftersom filen `package.json` redan innehåller en referens till Mocha. När installationen är klar kan du köra testfallen med `npm test` eftersom `package.json` redan är konfigurerad för att köra Mocha med enhetstesterna.

```text
npm install
npm test
```

Resultatet du ser är körningen av samtliga enhetstester. Men hur väl lyckas vi med kodtäckningen?



Kodtäckning vid enhetstestning {#covjs}
--------------------------------------------------------------------

När man kör enhetstester är man i princip beroende av ett verktyg som kan visa kodtäckningen för testfallen. Här väljer jag verktygen [Istanbul](https://istanbul.js.org/). I katalogen `example/test/unittest-mocha-istanbul` har jag utökat mitt exempel med att använda Istanbul tillsammans med Mocha.

För att kunna köra testerna med kodtäckning behöver du först installera kommandoradsklienten [`nyc`](https://github.com/istanbuljs/nyc) via `npm install nyc` eller bara `npm install`. Sedan kan du köra testerna igen, nu med kodtäckning inkluderat.

```text
npm install
npm test
```

I filen `package.json` körs nu kommandot `nyc --reporter=html --reporter=text mocha 'test/**/*.js'` där `nyc` sköter kodtäckningen för alla testfall som `mocha` exekverar. Vi får en rapport i ren text och i katalogen `cover` genereras en HTML-rapport.

[FIGURE src=image/snapht17/mocha-nyc-codecoverage.png?w=w2 caption="Kodtäckningen är på 100% i vårt exempel."]

Med en HTML-rapport är det enkelt att klicka sig fram och se vilka delar av koden som täcks av testfallen. Kodtäckning är ett viktigt verktyg när man gör enhetstester.



Docker mot olika Node versioner {#docker}
--------------------------------------------------------------------

Ibland vill man välja vilken version av Node man använder för sina enhetstester. Det kan vara bra att kunna köra testerna mot godtycklig version av Node, eventuellt kombinerad med specifika versioner av andra programvaror. Här kan Docker hjälpa oss.

I katalogen `example/test/unittest-docker` har jag förberett ett exempel som köra samma testfall men man kan välja att köra dem mot en Docker kontainer som kör en specifik installation av Node.

Du kan köra testerna mot en specifik kontainer på något av följande sätt.

```text
docker-compose run node_alpine npm test
npm run docker-alpine
```

Du kan sedan köra testerna mot en äldre version av Node på följande sätt.

```text
# Node version 7
docker-compose run node_7_alpine npm test
npm run docker-7

# Node version 6
docker-compose run node_6_alpine npm test
npm run docker-6
```

Nu har du alltså möjligheten att köra tester med samma kodbas mot flera versioner av Node. Det är kraftfullt och kan spara dig tid när du utvecklar och måste ha koll på att koden fungerar på olika versioner.

Det är filen `docker-compose.yml` som styr vilka kontainrar som startas upp. I `package-json` ligger de kommandon som körs och npm erbjuder en kortare väg att starta upp testerna.

Filen `docker-compose.yml` hänvisar till de Docker-filer som ligger i katalogen `docker/`. Det är instruktioner till hur respektive image skall byggas upp och vad den skall innehålla. Alla images utgår från [node](https://store.docker.com/images/node). Kommandot `docker-compose` bygger upp respektive image första gången den används. Om du gör ändringar i en image-fil kan det kräva att du bygger om den, till exempel via `docker-compose build node_7_alpine`.



### Dubbelkolla vilken version som körs {#nodeversion}

Om du vill dubbelkolla vilken version av Node som körs i en kontainer, bara för att vara säker, så kan du starta upp en interaktiv session och kolla versionerna.

```text
$ docker-compose run node_alpine node
> process.version       
'v8.8.1'                
> process.versions      
{ http_parser: '2.7.0', 
  node: '8.8.1',        
  v8: '6.1.534.42',     
  uv: '1.15.0',         
  zlib: '1.2.11',       
  ares: '1.10.1-DEV',   
  modules: '57',        
  nghttp2: '1.25.0',    
  openssl: '1.0.2l',    
  icu: '59.1',          
  unicode: '9.0',       
  cldr: '31.0.1',       
  tz: '2017b' }         
```



Valideringsverktyg {#validering}
--------------------------------------------------------------------

Vi är ju inne på tester, men låt oss ta ett litet sidospår och säkerställa att vi även har validering av koden vi skriver, vi vill ha validering av kodstil och en linter. Det finns ett förberett exempel under `example/test/validate`.

Eftersom vi utgår från kodstilen som definieras i [`javascript-style-guide`](https://www.npmjs.com/package/javascript-style-guide) så hämtar vi hem den och använder dess konfigurationsfiler.

```text
npm install javascript-style-guide --save-dev
cp node_modules/javascript-style-guide/{.eslintrc.json,.jscsrc} .
```

Vi behöver installera respektive validator.

```text
npm install jscs eslint --save-dev
```

Nu kan vi köra dem och eftersom de redan finns definierade i `package.json` så kör vi dem via npm.

```text
npm run jscs
npm run eslint
```

Om du hellre vill jobba med kommandot make och en Makefile så finns det i exempelkatalogen. Förutsatt att du har installerat även mocha och nyc (`npm install`) kan du köra samtliga tester via `make test`. Makefilen är föreberedd för att köra både validering och enhetstester.

```text
make test
```

När makefilen kör enhetstester så genereras kodtäckningen till katalogen `build/`. Det är för att undvika att skräpa ned i katalogen och samla bygg-relaterade filer i en katalog som är enkel att ta bort vid behov. Du kan se detaljer för hur `nyc` konfigureras i dess konfigfil `.nycrc`.



Continuous integration {#cichain}
--------------------------------------------------------------------

Nu när vi har en makefil på plats kan vi fortsätta och sätta igång en CI-kedja för att automatisera våra tester.

Det som sammanhåller alla tester är nu sekvensen `make install check test` som installerar det som behövs via `package.json` och sen kör testerna.

```text
make install   # Installerar allt som finns i package.json
make check     # Kollar och visar versioner på installerade verktyg
make test      # Exekvera validatorer och testfall
```

Då bygger vi en CI kedja. Som demo objekt använder jag GitHub repot [janaxs/blackjack](https://github.com/janaxs/blackjack). Kika där så ser du allt integrerat och badges som visar status.



### Byggverktyg Travis och CircleCI {#buildtools}

Först tar vi ett byggsystem, eller två. Jag väljer [Travis](https://travis-ci.org/) och [CircleCI](https://circleci.com/). Syftet med byggsystemet är att checka ut din kod och köra dina tester varje gång du checkar in en ny version av din kod.

Jag lägger till mitt repo till Travis och CircleCI.

I katalogen `example/test/ci` ligger en konfigurationsfil `.travis.yml` och en `.circleci/config.yml` som är exempel på konfigurationsfiler för Travis respektive CircleCI (v2). Om du kikar i filerna ser du referenser till `make install` och `make test`.



### Kodtäckning med Coveralls och Codecov {#codecov}

Byggsystemen kör testerna och kan sedan rapportera kodtäckningen till två system som är specialiserade på kodtäckning. I detta fallet använder jag [Coveralls](https://codecov.io/gh/janaxs/blackjack) och [Codecov](https://codecov.io/).

Jag lägger till mitt repo till Coveralls och Codecov.

Sedan behöver jag skicka en rapport från byggsystemets senaste tester. Det gör jag med `package.json` på följande sätt.

```json
"scripts": {
  "report-coveralls": "nyc report --reporter=text-lcov | coveralls",
  "report-codecov": "nyc report --reporter=lcov > coverage.lcov && codecov"
},
``` 

Det som behövs för att detta skall fungera är att paketen `coveralls` och `codecov` installeras. Det är specifika paket som bara är till för att rapportera kodtäckningen.

```text
npm install coveralls codecov --save-dev
```

Vid nästa bygge kommer ny kodtäckningen skickas upp till respektive system, förutsatt att kommandona körs. Jag har valt att köra dem från Travis så du kan se hur de körs i konfigurationsfilen `.travis.yml`.

```text
after_success:
    - npm run report-coveralls
    - npm run report-codecov
```



### Kodkvalitet med Codeclimate och Codacy {#codequal}

Till slut integrerar jag även med två verktyg som har fokus på kodkvalitet. Det är [Codeclimate](https://codeclimate.com/) och [Codacy](https://www.codacy.com/app/mosbth/blackjack/dashboard).

Jag lägger till mitt repo till Codeclimate och Codacy.

De båda verktygen har olika sätt att visualisera hur de upplever min kodkvalitet. Verktygen kan också visa kodtäckning om jag väljer att bifoga en sådan rapport.

Delvis kan alltså dessa båda verktyg ersätta de två verktyg vi såg som enbart hade fokus på kodtäckning. Vilka verktyg man i slutändan använder får bli en sak att utvärdera.

I detta läget behöver jag inte göra mer, de båda verktygen checkar automatiskt ut min kod när den uppdateras.



### CI kedja klar {#ciklar}

Då var vår CI kedja klar med två alternativ för byggsystem, kodtäckning och kodkvalitet. 



Funktionstestning i JavaScript {#funktionjs}
--------------------------------------------------------------------





Avslutningvis {#avslutning}
--------------------------------------------------------------------

Vi har gått igenom de första stegen i hur man kommer igång med Docker via kommandot `docker` och `docker-compose`. Vi har också sett hur images och kontainrar fungerar och hur de kan användas för att göra en flexibel test- och utvecklingsmiljö kopplad till ditt repo.

Avslutningsvis såg vi hur man kan göra egna images.

Det finns en [forumtråd kopplad till denna artikeln](t/6956). Där kan du ställa frågor eller bidra med tips och trix.

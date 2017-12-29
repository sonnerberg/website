---
author: mos
category:
    - nodejs
    - javascript
    - mysql
    - kursen dbjs
    - kursen databas
revision:
    "2017-12-29": (A, mos) Uppdaterad version av tidigare artikel.
...
MySQL och Node.js (v2)
==================================

[FIGURE src=/image/snapvt17/npm-mysql.png?w=c5 class="right"]

Vi skall se hur vi kan koppla oss med JavaScript och Node.js mot en MySQL databas med hjälp av paket vi installerar med npm.

Vi använder en befintlig databas och kopplar upp oss mot den med ett par enkla JavaScript-filer och gör en rapport via SELECT och en sökfunktion där vi filterar resultatet.

Vi använder async/await för att hantera den asynkrona beteendet och vi gör en enkel inmatning från tangentbordet.

<!--more-->

När vi är klara har vi byggt ett litet skript som söker i databasen via JavaScript och Node.js.

[FIGURE src=/image/snapvt18/nodejs-mysql-search.png?w=w3 caption="Med JavaScript och Node.js bygger du ett skript som kopplar sig till din databas."]



Tidigare versioner av artikeln {#early}
--------------------------------------

Denna version av artikeln är en uppdaterad variant av "[MySQL och Node.js](kunskap/mysql-och-nodejs)" och bygger på att användaren redan har tillgång till en befintlig databas och bygger på async/await konstruktionen från ES2017 (ES8).



Förutsättning {#pre}
--------------------------------------

Du har redan koll på databasen MySQL och du kan grunderna i Node.js och JavaScript på serversidan.

Du har installerat npm och du har Node.js version 8 eller senare.

Exempelprogram finns i ditt kursrepo (dbjs, databas) under `example/nodejs/mysql`.

Du är bekant med guiden "[Kom igång med SQL i MySQL](guide/kom-igang-med-sql-i-mysql)" och har tillgång till datasen "skolan" som är fylld med visst innehåll.



API mot MySQL {#api}
--------------------------------------

Vi behöver ett API som låter oss prata med databasen via JavaScript och Node.js. Vi väljer [paketet mysql](https://www.npmjs.com/package/mysql) som är ett av de mer använda.

Jag vill använda programmeringsstilen med async/await för att hantera asynkrona anrop. För det syftet väljer jag [paketet promise-mysql](https://www.npmjs.com/package/promise-mysql) som är en wrapper kring paketet mysql.

Jag går till kursrepot och installerar modulerna med npm. Jag installerar i rooten av kursrepot så kan alla exempelprogram i kursrepot använda samma installation.

```bash
# Ställ dig i rooten av ditt kursrepo.
$ npm install mysql promise-mysql
```

Klart. Då testar vi om installationen gick bra.



Koppla mot MySQL {#connect}
---------------------------------------

Jag gör ett kort exempelprogram för att verifiera att min installation fungerar. Tanken är att göra en koppling mot databasen, utföra en SELECT och sedan avsluta. Det ger mig ett test på att installationen har gått bra.

Jag sparar koden i en fil `connect.js`.

```javascript
/**
 * To verify that mysql is installed and is working.
 * Create a connection to the database and execute
 * a query without actually using the database.
 */
(async function() {
    const mysql = require("promise-mysql");
    const db    = await mysql.createConnection({
        "host":     "localhost",
        "user":     "user",
        "password": "pass",
        "database": "skolan"
    });
    let sql;
    let res;

    sql = "SELECT 1+1 AS Sum";
    res = await db.query(sql);

    console.info(res);

    db.end();
})();
```

Jag lägger hela programmet i en funktion, ett eget mainprogram som körs direkt. Jag använder async/await för att hantera att vissa av anropen är ansynkrona och jag vill förenkla och behöver ett (traditionellt) synkront flöde där varje funktion är klar innan nästa utförs.

Så här ser det ut när jag testkör programmet.

```text
$ node connect.js
[ RowDataPacket { Sum: 2 } ]
```

Svaret jag förväntade mig är `Sum: 2` och det får jag inuti en datastruktur. En bra start och paketen jag installerat fungerar enligt plan.



Skapa en config.json {#config}
---------------------------------------------

Om vi tittar på exempelprogrammet ovan så krävs ett antal rader för att göra uppkopplingen till databasen. Dessa kommer jag behöva i alla mina filer som skall koppla sig mot databasen. Det vore trevligt om alla filer kunde dela en gemensam konfigurationsfil.

Jag skapar en JSON-fil med de detaljer som behövs för att koppla sig mot databasen och döper den till `config.json`.

```json
{
    "host":     "localhost",
    "user":     "user",
    "password": "pass",
    "database": "skolan"
}
```

Jag tar en kopia av `connect.js` och sparar som `connect_config.js` och uppdaterar enligt följande.

```javascript
(async function() {
    const mysql  = require("promise-mysql");
    const config = require("./config.json");
    const db     = await mysql.createConnection(config);

    // rest of code
})();
```

Nu använder jag konstruktionen `require` för att läsa in konfigurationsfilen till ett objekt `config` som jag sedan använder för att skapa databasens uppkoppling.

Det blev några färre kodrader vilket oftast blir enklare att hantera och leder till mer lättläst kod. Den stora fördelen är att jag nu kan dela konfigurationen mellan flera filer.



Rapport från databasen {#query}
---------------------------------------------

Jag tänker skapa en rapport som visar innehållet i en tabell. I databasen jag använder finns tabellen `larare` och jag tänker skriva ut en lista med alla lärare och vilken avdelning de jobbar på.

Om du är osäker på vad tabellen innehåller så går du till guiden och "[Skapa rapporter från tabellen](guide/kom-igang-med-sql-i-mysql/skapa-rapporter-fran-tabellen)".



### SELECT fråga {#select}

Jag tar en kopia av `connect_config.js` och sparar som `teachers.js` och uppdaterar enligt följande.

```javascript
/**
 * Show teachers and their departments.
 */
(async function() {
    const mysql  = require("promise-mysql");
    const config = require("./config.json");
    const db     = await mysql.createConnection(config);
    let sql;
    let res;

    sql = `
        SELECT
            akronym,
            fornamn,
            efternamn,
            avdelning
        FROM larare
        ORDER BY akronym;
    `;
    res = await db.query(sql);

    console.info(res);

    db.end();
})();
```

Jag väljer att skriva SQL-satsen på flera rader, som en [template sträng](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) med backticks, jag tycker det blir tydligare på det viset.

När jag kör skriptet kommer resultsetet skrivas ut, det är en array och varje matchande rad (lärare) är ett objekt. Det ser ut så här.

```text
$ node teachers.js
[ RowDataPacket {
    akronym: 'ala',
    fornamn: 'Alastor',
    efternamn: 'Moody',
    avdelning: 'DIPT' },
  RowDataPacket {
    akronym: 'dum',
    fornamn: 'Albus',
    efternamn: 'Dumbledore',
    avdelning: 'ADM' },

... resten av raderna
```

Datatypen `RowDataPacket` är en egenskapad datatyp som ligger i npm modulen mysql.



### Skriv ut som JSON {#json}

I sammanhanget JavaScript är formatet JSON ofta använt för att hantera data. Vi kan konvertera resultsetet till en JSON struktur ([`JSON.stringify()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)) och skriva ut den med följande kodrader.

```javascript
// Output resultset as JSON
let data;

data = JSON.stringify(res, null, 4);
console.info(data);
```

När vi kör programmet får vi nu istället en utskrift i form av formatterad JSON data som ser ut så här.

```text
[
    {
        "akronym": "ala",
        "fornamn": "Alastor",
        "efternamn": "Moody",
        "avdelning": "DIPT"
    },
    {
        "akronym": "dum",
        "fornamn": "Albus",
        "efternamn": "Dumbledore",
        "avdelning": "ADM"
    }
}
```

Det är ofta enkelt att konvertera mellan JavaScripts datastrukturer och JSON-formatet.



### Skriv ut som formatterad text {#pad}

Jag kan få en mer kontrollerad utskrift om jag loopar genom resultsetet och skriver ut informationen i formen av en tabell. Jag kan använda funktionenerna [`String.padStart()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) och [`String.padEnd()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd) för att formattera min utskrift och jag kan använda konstruktionen [`for..of`](https://developer.mozilla.org/sv-SE/docs/Web/JavaScript/Reference/Statements/for...of) för att loopa genom resultsetet.

Principen är så här.

```javascript
// Loop through each row the resultset
for (const row of res) {
    console.info(row);
}
```

Vi vill formattera utskriften som en tabell och då kan det se ut så här med lite strängformattering.

```javascript
// Output as formatted text in table
let str;

str  = "+-----------+---------------------+-----------+----------+\n";
str += "| Akronym   | Namn                | Avdelning |   Lön    |\n";
str += "|-----------|---------------------|-----------|----------|\n";
for (const row of res) {
    str += "| ";
    str += row.akronym.padEnd(10);
    str += "| ";
    str += (row.fornamn + " " + row.efternamn).padEnd(20);
    str += "| ";
    str += row.avdelning.padEnd(10);
    str += "| ";
    str += row.lon.toString().padStart(8);
    str += " |\n";
}
str += "+-----------+---------------------+-----------+----------+\n";
console.info(str);
```

När vi kör programmet får vi nu en väl formatterad tabell som innehåller informationen från databasen.

```text
$ node teachers.js
+-----------+---------------------+-----------+----------+
| Akronym   | Namn                | Avdelning |   Lön    |
|-----------|---------------------|-----------|----------|
| ala       | Alastor Moody       | DIPT      |    27594 |
| dum       | Albus Dumbledore    | ADM       |    85000 |
| fil       | Argus Filch         | ADM       |    27594 |
| gyl       | Gyllenroy Lockman   | DIPT      |    27594 |
| hag       | Hagrid Rubeus       | ADM       |    30000 |
| hoc       | Madam Hooch         | DIDD      |    37580 |
| min       | Minerva McGonagall  | DIDD      |    49880 |
| sna       | Severus Snape       | DIPT      |    40880 |
+-----------+---------------------+-----------+----------+
```

Nu känns det som vi har kontroll över hur vi kan ställa frågor mot databasen och skriva ut resultatet på olika sätt.



Söka i databasen {#search}
---------------------------------------------

Säg att vi vill reducera antalet rader i tabellen och bara skriva ut de som matchar en söksträng, hur kan man göra det?

Jag tar en kopia av `teachers.js` och skapar `search.js`. Men eftersom koden växer så väljer jag att dela ut koden i funktioner så att min main-funktion blir så liten som möjligt.

Jag flyttar koden som skriver ut resultsetet i tabellformat till en egen funktion och jag flyttar själva SQL-frågan till en funktion. I main-funktionen tänker jag hantera tangentbordsinmatningen.

Efter att ha flyttat runt koden till funktioner så ser min main-funktion ut så här.

```javascript
/**
 * Main function.
 * @async
 * @returns void
 */
(async function() {
    const mysql  = require("promise-mysql");
    const config = require("./config.json");
    const db     = await mysql.createConnection(config);
    let str;
    let search;

    str = await searchTeachers(db, search);
    console.info(str);

    db.end();
})();
```

Allt som tidigare gjordes i main-funktionen är nu inuti funktionen `searchTeachers()` som returnerar resultatet i form av en sträng med tabellen som går att skriva ut.



### Läsa in från tangentbord {#read}

Vi kan använda [Node.js modulen readline](https://nodejs.org/api/readline.html) för att läsa in söksträngen via tangentbordet.

I vår main-funktion gör vi require på modulen och initierar den.

```javascript
// Read from commandline
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});
```

Sedan ställer vi en fråga och när användaren skriver in svaret så anropas vår callback där vi anropar databasen och skriver ut svaret.

```javascript
// Ask question and handle answer in async arrow function callback.
rl.question("What to search for? ", async (search) => {
    let str;

    str = await searchTeachers(db, search);
    console.info(str);

    rl.close();
    db.end();
});
```

Likt referensmanualen använder vi en [arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) för att definiera callbacken som tar ett argument `search` som är det som matas in från tangentbordet. Eftersom vi vill använda `await` inuti callbacken så måste den defineras som `async`.

Vi behöver stänga databasen och `rl` inuti callbacken, efter att allt är klart och utskrivet.



### Argument till SELECT {#argsel}

Nu har vi en söksträng att söka efter, då skall vi konstruera SELECT-frågan med hjälp av argumentet `search`. Här tar vi hjälp av modulen mysql och möjligheten att lägga till `?` som ersättare för ett argument i frågan. Fördelen är att argumenten _escapas_ för att undvika skadliga injektioner i din SQL-kod.

Vår nuvarande SELECT ser ut så här i sitt sammanhang, ännu utan att ta hänsyn till argumentet `search`.

```javascript
/**
 * Output resultset as formatted table with details on a teacher.
 *
 * @async
 * @param {connection} db     Database connection.
 * @param {string}     search String to search for.
 *
 * @returns {string} Formatted table to print out.
 */
async function searchTeachers(db, search) {
    let sql;
    let res;
    let str;

    console.info(`Searching for: ${search}`);

    sql = `
        SELECT
            akronym,
            fornamn,
            efternamn,
            avdelning,
            lon
        FROM larare
        ORDER BY akronym;
    `;
    res = await db.query(sql);
    str = teacherAsTable(res);
    return str;
}
```

Vi skriver om SELECT-satsen så att den tar hänsyn till vår söksträng.

```javascript
let like = `%${search}%`;

sql = `
    SELECT
        akronym,
        fornamn,
        efternamn,
        avdelning,
        lon
    FROM larare
    WHERE
        akronym LIKE ?
        OR fornamn LIKE ?
        OR efternamn LIKE ?
        OR avdelning LIKE ?
        OR lon = ?
    ORDER BY akronym;
`;
res = await db.query(sql, [like, like, like, like, search]);
```

Vi har alltså en SQL-fråga där `?` kommer att ersättas av sin motsvarighet i arrayen som bifogas till `query()`. Detta är ett bra sätt att bygga upp sin SQL-fråga tillsammans med innehåll från andra variabler.



### Testa search.js {#testsearch}

Vi kan nu testa skriptet, det kan se ut så här när man söker ut de lärare som jobbar på en viss avdelning.

```text
$ node search.js
What to search for? DIDD
Searching for: DIDD
+-----------+---------------------+-----------+----------+
| Akronym   | Namn                | Avdelning |   Lön    |
|-----------|---------------------|-----------|----------|
| hoc       | Madam Hooch         | DIDD      |    37580 |
| min       | Minerva McGonagall  | DIDD      |    49880 |
+-----------+---------------------+-----------+----------+
```

Kör programmet igen om du vill söka efter något annat.

Du har skapat en enkel rapporthantering/sökning från din databas.



Asynkron programmering i Node.js {#async}
--------------------------------------

En sak som skiljer JavaScript i Node.js, från andra traditionella programmeringsspråk, är dess asynkrona och icke blockande natur. Du har sett ett par exempel på dessa i artikeln då vi använder async/await för att serialisera de metoder som stödjer Promise.

Vi såg även ett exempel på en callback-hantering i `rl.question()` där en metod anropas när frågan besvarats.

En viktig ingrediens för att bemästra JavaScript i Node.js är att förstå de olika delarna i dess asynkrona hantering. Tidiga versioner av JavaScript, pre ES2015 (ES6) löser hanteringen med callbacks. När ES2015 (ES6) kom så introducerades Promise och när ES2017 (ES8) kom så fick vi möjligheten att använda async/await.

När man tittar på moduler till JavaScript och Node.js så får man vara vaksam på dokumentationen och se vilka möjligheter som erbjuds då de kan ha valt olika strategier för att hantera asynkrona bitar.

I artikeln försöker jag undvika att gå in på detaljer om detta, om du är nybörjare på JavaScript i Node.js så kan det vara bra att vara medveten om denna frågeställning som delvis kan upplevas frustrerande när man försöker bemästra området.

För den som vill fördjupa sig i ämnet så rekommenderas de böcker som [Axel Rauschmayer skrivit om olika versioner av JavaScript](http://exploringjs.com/).



Dokumentation {#docs}
--------------------------------------

Som du märker i artikeln så är kärnan i JavaScript dokumenterad på MDNs webbplats, när det gäller moduler specifika för Node.js så finns referensmanualen på deras webbplats och när det gäller paket vi installerar med npm så är vi hänvisade till dess README och bakomliggande GitHub repo.

Det gäller att skaffa sig kontroll över vilken referensdokumentation som är den "rätta". Refmanualen är alltid din bästa vän.



Avslutningsvis {#avslutning}
--------------------------------------

Du har nu fått en genomgång i hur MySQL kan fungera tillsammans med Node.js och du har fått en grundstruktur i hur du kan organisera ditt program.

Grundstrukturen kan du förhoppningsvis bygga vidare på, även med begränsade kunskaper i javaScript och Node.js.

Denna artikel har en [egen forumtråd](t/6270) som du kan ställa frågor i, eller ge tips.

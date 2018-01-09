---
author: mos
category:
    - nodejs
    - javascript
    - express
    - kursen dbjs
    - kursen databas
revision:
    "2018-01-09": (A, mos) Första utgåvan.
...
CRUD med Express, MySQL och lagrade procedurer
==================================

[FIGURE src=image/snapvt18/bank-header-footer.png?w=c5&a=0,30,20,0&cf class="right"]

Vi skall jobba igenom begreppet CRUD, Create, Read, Update, Delete, via ett webbgränssnitt baserat på Express och kopplat mot databasen MySQL.

Vi skall använda oss av lagrade procedurer i databasen för att skapa ett API mot databasen som alla frågor från klienterna går via. Det ger oss ett exempel på hur vi kan kapsla in SQL-koden och förenkla för klienterna.

<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har jobbat igenom artikeln "[Koppla appservern Express till databasen MySQL](kunskap/koppla-appservern-express-till-databasen-mysql)" och har tillgång til kod du kan utgå ifrån.

Du har jobbat igenom artikelserien som visar hur du programmerar i en databas via "[Lagrade procedurer i databas](kunskap/lagrade-procedurer-i-databas)", "[Triggers i databas](kunskap/triggers-i-databas)" och "[Egendefinierade funktioner i databas](kunskap/egen-definierade-funktioner-i-databas)". Du har tillgång till den databas som används i artikelserien.

De exempelprogram som används i artikeln finns i ditt kursrepo (dbjs, databas) under `example/express-crud` (det färdiga exemplet) och `example/express-mysql` (koden jag startar med).



Utgå från tidigare exempel {#utga}
--------------------------------------

Du kan kopiera exempelkoden i `example/express-mysql` och utgå från den. Jag använder den för att bygga vidare och lägga dit kod som gör att vi kan koppla oss till databasen.

När du kopierat koden behöver du installera modulerna med `npm install`.

Pröva sedan att starta servern och använda webbläsaren för att koppla dig till servern.

Vi har främst routen `bank/index` och routen `bank/balance` att utgå ifrån.



R i CRUD, Read {#read}
---------------------------------------

Den första delen handlar om att läsa information från databasen och presentera den. Det har vi egentligen redan gjort i routen `bank/balance` som gör en `SELECT *` från tabellen.

Men jag vill använda konceptet _programmera i databasen_ och tänker därför skriva om SELECT-satsen till en lagrad procedur.

Låt vara att jag inte vinner något speciellt på det, mer än själva övningen att se hur jag från klienten anropar en lagrad procedur i sin enklaste form.

Först skapar jag min lagrade procedur som visar balansen för alla konton. Du kan se all SQL-kod i filen `example/express-crud/sql/bank/ddl_procedure.sql`.

```sql
--
-- Create procedure for select * from account
--
DROP PROCEDURE IF EXISTS showBalance;
DELIMITER //
CREATE PROCEDURE showBalance()
BEGIN
    SELECT * FROM account;
END
//
DELIMITER ;
```

Jag kan anropa den via MySQL terminalklienten.

```sql
mysql> CALL showBalance();
+------+------+---------+
| id   | name | balance |
+------+------+---------+
| 1111 | Adam |   10.00 |
| 2222 | Eva  |    7.00 |
+------+------+---------+
2 rows in set (0.00 sec)

Query OK, 0 rows affected (0.00 sec)
```

Nu går jag in i min route och uppdaterar koden så att den lagrade proceduren används. 

Tidigare såg min kod ut så här.

```javascript
/**
 * Show all entries in the account table.
 *
 * @async
 * @returns {RowDataPacket} Resultset from the query.
 */
async function showBalance() {
    return findAllInTable("account");
}
```

Nu envisas jag med att uppdatera den till följande, så att den lagrade proceduren används istället.

```javascript
/**
 * Show all entries in the account table.
 *
 * @async
 * @returns {RowDataPacket} Resultset from the query.
 */
async function showBalance() {
    let sql = `CALL showBalance();`;
    let res;

    res = await db.query(sql);
    console.info(`SQL: ${sql} got ${res.length} rows.`);

    return res[0];
}
```

Det resultset som returneras från en lagrad procedur skiljer sig aningen från tidigare. En lagrad procedur kan nämlingen returnera flera svar, flera resultset. I detta fallet är det bara ett `res[0]` och det är det jag vill skicka vidare till vyn.

Sådär, nu är min kod uppdaterad och fungerar som tänkt tillsammans med en lagrad procedur.

I min vy uppdaterade jag med följande kod som ger mig möjligheter att debugga och se vad ett resultset innehåller.

```html
<pre><%= JSON.stringify(res, null, 4) %></pre>
```

Det ger en JSON representation av datat jag jobbar på. Det kan se ut så här.

[FIGURE src=image/snapvt18/bank2-balance-json.png caption="Utskrift av ett resultset i en formatterad JSON."]

Vill jag inte se utskriften kan jag kommentera bort den, men konstruktionen är bra vid behov.



C i CRUD, Create {#create}
---------------------------------------

Låt oss skapa möjligheten att lägga till en ny kontohavare med konto och kontobehållning (peng på kontot).



### Vy med HTML formulär {#cform}

Jag börjar med att göra ett HTML formulär där användaren kan mata in detaljer om det nya kontot. Routen får bli `bank/create` och vyn `views/bank/create.ejs`.

Att placera ut och styla formulär är en historia för sig. Men jag försöker med enkla medel att lägga ut ett enklare formulär. Lite CSS behövs för att ordna layouten. Men vi fokuserar på HTML-koden för formuläret, den ser ut så här.

```html
<form class="label-left" method="post">
    <fieldset>
        <legend>Create account</legend>

        <label for="id">Id</label>
        <input id="id" type="text" name="id">

        <label for="name">Name</label>
        <input id="name" type="text" name="name">

        <label for="balance">Balance</label>
        <input id="balance" type="number" name="balance">

        <input type="submit" name="doit" value="Create">
    </fieldset>
</form>
```

Om vi renderar den som en del av vyn så kan sidan se ut så här.

[FIGURE src=image/snapvt18/bank2-create-account.png caption="Ett formulär där jag kan mata in detaljer för ett nytt konto."]

Nu kan jag fylla i informationen och klicka på knappen. Men vi behöver en route som hanterar det postade formulärets data.



### Route för att hantera POST {#cpost}

Formuläret postas till servern via HTTP-metoden POST. Då gör vi en route `bank/create` som endast svarar på POST. Man kan ha samma namn på routen men olika HTTP-metoder.

Routen lägger vi tillsammans med övriga bank-routes i `route/bank.js`.

Låt oss först titta på ett utkast till routern, där vi använder post istället för get.

```javascript
router.post("/create", async (req, res) => {
    // Extract the data from the posted form
    // Send data to a stored procedure
    res.redirect("/bank/balance");
});
```

Routen ovan fungerar som den är. Om vi klickar på submit-knappen i formuläret så hamnar vi i denna routen och det enda som händer är att vi redirectas till routen `/bank/balance`.

Det vi nu måste göra är att extrahera datat som kommer i det postade formuläret. Till det använder vi en npm modul [body-parser](https://www.npmjs.com/package/body-parser) vars uppgift är att extrahera den kodade informationen i HTTP-requesten.

Vi installerar modulen.

```text
npm install body-parser --save
```

Vi aktiverar modulen enbart i den fil vi använder den, i samma fil vår post-route ligger.

```javascript
const bodyParser = require("body-parser");
const urlencodedParser = bodyParser.urlencoded({ extended: false });
```

Det vi har i `urlencodedParser` är en middleware som kan läggas till i vår route, så här.

```javascript
router.post("/create", urlencodedParser, async (req, res) => {
    // Extract the data from the posted form
    console.log(JSON.stringify(req.body, null, 4));
    // Send data to a stored procedure
    res.redirect("/bank/balance");
});
```

Vi har nu det postade formuläret i requesten i `req.body`. Vi kan debugga inkommande genom att skriva ut dess innehåll. Det blir enklare och tydligare att läsa innehållet om man formaterar det som JSON-data.

Postar vi ett tomt formulär ser utskriften ut så här.

```json
{
    "id": "",
    "name": "",
    "balance": "",
    "doit": "Create"
}
```

Bra, det ser ut som våra element i formuläret.

Då går vi över till SQL-biten.



### Lagrad procedur för insert {#cinsert}

Jag gör en lagrad procedur för att sköta själva insert-satsen. De kan se ut så här.

```sql
--
-- Create procedure for insert into account
--
DROP PROCEDURE IF EXISTS createAccount;
DELIMITER //
CREATE PROCEDURE createAccount(
	aId CHAR(4),
    aName VARCHAR(8),
    aBalance DECIMAL(4, 2)
)
BEGIN
    INSERT INTO account VALUES (aId, aName, aBalance);
END
//
DELIMITER ;
```

Det är viktigt att datatyperna matchar de som tabellen har.

Jag kan pröva att använda den lagrade proceduren.

```sql
mysql> CALL createAccount("1337", "Mega", 37.0);
Query OK, 1 row affected (0.22 sec)
```

Det blir inget resultset som svar. Men när inget går fel så antar vi alltid att det gick bra, iallfall i sammanhanget databaser.

Nu kan vi använda den lagrade proceduren i Express.



### Lagrad procedur för insert {#cinsert}

Först skapar jag en funktion i databasmodulen `src/bank.js`. Jag döper den till `createAccount`. Så här kan den se ut.

```javascript
/**
 * Create a new account.
 *
 * @async
 * @param {string} id      A id of the account.
 * @param {string} name    The name of the account holder.
 * @param {string} balance Initial amount in the account.
 *
 * @returns {RowDataPacket} Resultset from the query.
 */
async function createAccount(id, name, balance) {
    let sql = `CALL createAccount(?, ?, ?);`;
    let res;

    res = await db.query(sql, [id, name, balance]);
    console.log(res);
    console.info(`SQL: ${sql} got ${res.length} rows.`);
}
``` 

Jag anropar funktionen från min route och skickar med argumenten som kommer från det postade formuläret.

```javascript
router.post("/create", urlencodedParser, async (req, res) => {
    // console.log(JSON.stringify(req.body, null, 4));
    await bank.createAccount(req.body.id, req.body.name, req.body.balance);
    res.redirect("/bank/balance");
});
```

Nu kan vi testa. Första matar vi in detaljerna i formuläret.

[FIGURE src=image/snapvt18/bank2-create-account-post.png caption="Vi fyller i formuläret med detaljer om kontot."]

När vi klickar på submit-knappen postas formulärdatat till vår post-route som skapar en ny kontohavare och gör en redirect när det är klart. När det postade formuläret hanteras i routen skrivs detaljer och logginformation ut i terminalen. Det kan vi använda för att debugga.

Så här ser sidan ut vi kommer till.

[FIGURE src=image/snapvt18/bank2-account-created.png caption="Det nya kontot är skapat och finns nu med i sammanställningen över kontohavare."]

Det var C:et i CRUD, Create för att skapa nya rader i databasen.



Visa detaljer om enbart ett konto {#visaett}
---------------------------------------

Hur kan vi visa detaljer om ett specifikt konto på en egen sida? Ja, det finns naturligtvis varianter, men säg att vi kunde skapa en dynamisk route som tar en parameter så routen blev `bank/account/:id` där `:id` representerar kontots id.

Då kunde vi hämta detaljerna för just det kontot och visa upp det i en vy.

Routen kan se ut så här.

```javascript
router.get("/account/:id", async (req, res) => {
    let id = req.params.id;
    let data = {
        title: `Account ${id} ${sitename}`,
        account: id
    };

    data.res = await bank.showAccount(id);

    res.render("bank/account-view", data);
});
```

Det som är nytt här är hur routen specificeras och hur `:id` kan hämtas i routen via `req.params.id`. Det är som att skicka en parameter via routen. Resten i routen är saker du känner till, en funktion `bank.showAccount()` som anropar en lagrad procedur som hämtar detaljer om just ett konto. Vyn kan ha liknande struktur som den som visar balansen, det är samma typ av information som skall visas upp.

Resultatet av en sådan route skulle kunna visas upp så här.

[FIGURE src=image/snapvt18/bank2-view-account.png caption="En dynamisk route som tar ett argument och kan visa upp detaljer om specifikt konto."]

Tänk nu, om vi uppdaterar vyn som visar balansen, och för varje konto som visas i tabellen så länkar vi dess id till denna nya routen. Då får vi en översikt med länkar till detaljer om varje konto. Det låter som en bra idé. 



U som i Uppdatera detaljer om ett konto {#uppdatera}
---------------------------------------

U:et i CRUD handlar om att uppdatera befintlig data. Säg att vi vill uppdatera detaljer om ett specifikt konto.

Nu kan vi länka till varje konto, låt oss då skapa ytterligare en länk som leder oss till ett formulär där vi kan uppdatera detaljer om ett konto.

Jag tycker det vore trevligt med lite ikoner för detta och väljer att använda [FontAwesome](http://fontawesome.io/) för det syftet.

När jag ändå håller på med ikoner så lägger jag till en ikon för att radera också. Så här blev det.

[FIGURE src=image/snapvt18/bank2-account-actions.png caption="Nu förberedd med ikoner för att göra edit och delete."]

För edit-ikonen länkar jag till routen `/bank/edit/:id`. I routen hämtar jag detaljer om kontot för det specifika kontot och visar upp det i en vy som ser ut ungefär som formuläret för att skapa konto. Det är ju ungefär samma upplägg för ett edit-formulär.

 


R som i Radera ett konto {#radera}
---------------------------------------

D:et i CRUD handlar om att göra delete på rader. Säg att vi vill radera ett konto.

För delete-ikonen länkar jag till routen `/bank/delete/:id`.




Flytta pengar mellan konton {#move}
---------------------------------------

Gör som uppgift.




Avslutningsvis {#avslutning}
--------------------------------------

Detta var en introduktion för att komma igång Express och MySQL. Vi byggde vidare på en kodstruktur vi fick i föregående artiklar och lade till kod för att koppla upp oss mot databasen och vi såg hur resultsetet kunde presenteras i vyerna.

Du har nu grunderna för att skriva din egen webb/applikationsserver som kopplar sig mot en databas och presenterar innehåll i rapporter.

Denna artikel har en [egen forumtråd](t/7218) som du kan ställa frågor i, eller ge tips.

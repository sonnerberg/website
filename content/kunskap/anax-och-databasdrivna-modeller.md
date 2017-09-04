---
author:
    - mos
category:
    - anax
    - php
    - kursen ramverk1
revision:
    "2017-08-15": "(A, mos) Första utgåvan."
...
Anax och databasdrivna modeller
==================================

[FIGURE src=image/snapht17/anax-route-config.png?w=c5&cf&a=10,50,40,0 class="right"]

Vi bygger vidare på ett exempel med formulärhantering i Anax och integrerar med en extern modul för databashantering.



<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har läst artikeln "[Anax och formulärhantering](kunskap/anax-och-formularhantering)". Denna artikel om databashantering tar vid där formulärartikeln slutade.



Glöm inte `.htaccess` {#htaccess}
--------------------------------------

Glöm inte att redigera din `.htaccess` när du publicerar till studentservern.



Bygg vidare på formulärexemplet {#initanax}
--------------------------------------

Vi jobbar vidare i samma katalog `anax4` där vi gjorde formulärexemplet. Du bör alltså ha tre routes som fungerar, nämligen `user`, `user/login` och `user/create`.

Tanken är att vi skall implementera så att vi kan skapa en användare och logga in som en användare. Vi vill visa på ett flöde som omfattar delar av formulär och CRUD mot en databas.

Testa även att öppna din webbläsare mot `htdocs` för att kontrollera att index-sidan för webbplatsen fungerar tillsammans med routen `htdocs/debug/info`.

Om du av någon anledning vill starta på nytt och utgå från koden som fanns i formulärartikeln så kan du scaffolda fram den. Se det som ett alternativ.

```bash
# Ställ dig i kursrepot me/kmom04 
anax create anax4f ramverk1-form
cd anax4f
```

Om du väljer att skapa nytt behöver du kontrollera att de olika routerna fungerar som tänkt.

Oavsett vad så bör vi nu ha en liknande kodbas att utgå ifrån. Jag jobbar vidare i min katalog `anax4`.



Installera modul för databas {#instdb}
--------------------------------------

Vi skall installera en Anax modul som hjälper oss med databashanteringen.

```bash
# Gå till anax4
composer require anax/database
```



En tabell för användare {#tabell}
--------------------------------------

Jag skapar en enkel tabell för användare. Databasmodulen innehåller ett exempel som hjälper mig skapa tabellen, ett exempel för SQLite och ett för MySQL. Jag tar och använder båda för skoj skull.

Jag börjar med att hämta SQL-koden från modulen och lägger i min egen katalog `sql/`.

```bash
rsync -av vendor/anax/database/sql/ sql/
```

Nu finns exempelfiler för att skapa databastabeller i katalogen `sql/`.



###MySQL tabell för User {#mysqlcreate}

Create database & user

mysql < sql/ddl/user_mysql.sql
mysql -uanax -panax



###SQLite tabell för User {#sqlitecreate}

$ sqlite3 data/db.sqlite < sql/ddl/user_sqlite.sql
$ chmod 777 data
$ chmod 666 data/db.sqlite
$ sqlite3 data/db.sqlite



Formulär för att skapa användare {#createuserform}
--------------------------------------

Då skall vi använda databasen genom att skapa en användare som vi lägger i databasen.

Jag har ju sedan tidigare exempel en modell-klass som heter `Anax\User\HTMLForm\CreateUser`, men den är scaffoldad och är inte perfekt i sin ursprungsform. Jag uppdaterar den och skapar ett formulär som ser ut så här.

```php
$this->form->create(
    [
        "id" => __CLASS__,
        "legend" => "Create user",
    ],
    [
        "acronym" => [
            "type"        => "text",
        ],
                
        "password" => [
            "type"        => "password",
        ],

        "password-again" => [
            "type"        => "password",
            "validation" => [
                "match" => "password"
            ],
        ],

        "submit" => [
            "type" => "submit",
            "value" => "Create user",
            "callback" => [$this, "callbackSubmit"]
        ],
    ]
);
```

Jag uppdaterar metoden `callbackSubmit()` och för att visa hur det ser ut så plockar jag ut formulärets innehåll och lägger i variabler som jag skriver ut, bara för att visa hur man kan testa sitt forumlär.

Så här ser metoden ut, bortsett från delen med databasen.

```php
/**
 * Callback for submit-button which should return true if it could
 * carry out its work and false if something failed.
 *
 * @return boolean true if okey, false if something went wrong.
 */
public function callbackSubmit()
{
    // Get values from the submitted form
    $acronym       = $this->form->value("acronym");
    $password      = $this->form->value("password");
    $passwordAgain = $this->form->value("password-again");

    // Check password matches
    if ($password !== $passwordAgain ) {
        $this->form->rememberValues();
        $this->form->addOutput("Password did not match.");
        return false;
    }

    // Save to database

    $this->form->addOutput("User was created.");
    return true;
}
```

Om jag provkör via `user/create` så kan det se ut så här.

[FIGURE src=image/snapht17/user-create-4.png caption="Förbereder mig att skapa en ny användare."]

Det gick "bra" att skapa användaren.

[FIGURE src=image/snapht17/user-create-3.png caption="Användaren skapades."]

Det ser ju ut som det kan fungera. Då skall vi bara skriva till databasen också.



Databasen som tjänst i ramverket {#dbservice}
--------------------------------------

Vi börjar med att lägga till databasen som en tjänst i ramverket. Det gör vi i `config/di.php` tillsammans med ramverkets övriga tjänster.

Koden för att lägga till tjänsten ser ut så här.

```php
"db" => [
    "shared" => true,
    "callback" => function () {
        $obj = new \Anax\Database\DatabaseQueryBuilder();
        $obj->configure("database.php");
        return $obj;
    }
],
```

Databasklassen läser in sin konfiguration från `config/database.php` och via den filen kan vi bestämma om databasen är MySQL eller SQLite. Det finns en exempelfil du kan utgå ifrån som ligger i modulen. Du hittar den i `vendor/anax/database/config/database.php`.

Jag börjar med att sätta upp databasen som en SQLite-databas och placerar databasfilen bland övriga konfigurationersfiler i `data/db.sqlite`.

Så här blir konfigurationsfilen i det fallet.

```php
<?php
/**
 * Config file for Database.
 *
 * Example for MySQL.
 *  "dsn" => "mysql:host=localhost;dbname=test;",
 *  "username" => "test",
 *  "password" => "test",
 *  "driver_options"  => [\PDO::MYSQL_ATTR_INIT_COMMAND => "SET NAMES 'UTF8'"],
 *
 * Example for SQLite.
 *  "dsn" => "sqlite:memory::",
 */
return [
    "dsn"             => "sqlite:" . ANAX_INSTALL_PATH . "/data/db.sqlite",
    "username"        => null,
    "password"        => null,
    "driver_options"  => null,
    "fetch_mode"      => \PDO::FETCH_OBJ,
    "table_prefix"    => null,
    "session_key"     => "Anax\Database",

    // True to be very verbose during development
    "verbose"         => null,

    // True to be verbose on connection failed
    "debug_connect"   => false,
];
```

För att det skall fungera behöver vi skapa katalogen `data` och göra den skrivbar för alla.

```bash
# Gå till roten av anax4
mkdir data
chmod 777 data
```

Om du vill att ditt Git-repo skall innehålla katalogen data, men ingen av dess filer, så kan du skapa filen `data/.gitignore` med följande innehåll.

```text
# Ignore everything in this directory
*
# Except this file
!.gitignore
```

Det är en teknik för att checka in en tom katalog och låta bli att checka in någon av de filer som senare hamnar i katalogen.

Nu har vi alltså en tjänst i ramverket för databasen och vilken databas det är styrs av konfigurationsfilen. Då kan vi börja använda databasen i formuläret.



Spara till databas i formulärmodellen {#savetodb}
--------------------------------------

Då har vi en ramverkstjänst för databasen. Låt oss använda den för att spara användaren i formulärklassen. Den uppdaterade `callbackSubmit()` kan se ut så här.

```php
/**
 * Callback for submit-button which should return true if it could
 * carry out its work and false if something failed.
 *
 * @return boolean true if okey, false if something went wrong.
 */
public function callbackSubmit()
{
    // Get values from the submitted form
    $acronym       = $this->form->value("acronym");
    $password      = $this->form->value("password");
    $passwordAgain = $this->form->value("password-again");

    // Check password matches
    if ($password !== $passwordAgain ) {
        $this->form->rememberValues();
        $this->form->addOutput("Password did not match.");
        return false;
    }

    // Save to database
    $db = $this->di->get("db");
    $password = password_hash($password, PASSWORD_DEFAULT);
    $db->connect()
       ->insert("User", ["acronym", "password"])
       ->execute([$acronym, $password]);

    $this->form->addOutput("User was created.");
    return true;
}
```

Den koden som skapar användaren i databasen blir alltså denna.

```php
// Save to database
$db = $this->di->get("db");
$password = password_hash($password, PASSWORD_DEFAULT);
$db->connect()
   ->insert("User", ["acronym", "password"])
   ->execute([$acronym, $password]);
```

Som du ser skriver vi inte någon SQL-kod utan använder en inbyggd _Query-builder_ som bygger upp SQL-koden bakom fasaden via metoder. Det finns inget som hindrar att du istället väljer att skriva SQL-koden som du är van vid, men jag tänkte använda Query-buildern i mitt exempel.



Logga in mot databasen {#loginthroughdb}
--------------------------------------

Då tar jag och uppdaterar koden för inloggningen och lägger till databaskod i min formulärklass `Anax\User\HTMLForm\UserLoginForm`. Jag skall kontrollera att användare och lösenord matchar.

Koden i callbackSubmit() 

```php
/**
 * Callback for submit-button which should return true if it could
 * carry out its work and false if something failed.
 *
 * @return boolean true if okey, false if something went wrong.
 */
public function callbackSubmit()
{
    // Get values from the submitted form
    $acronym       = $this->form->value("user");
    $password      = $this->form->value("password");

    // Try to login
    $db = $this->di->get("db");
    $db->connect();
    $user = $db->select("password")
               ->from("User")
               ->where("acronym = ?")
               ->executeFetch([$acronym]);

   if (!password_verify($password, $user->password)) {
       $this->form->rememberValues();
       $this->form->addOutput("User or password did not match.");
       return false;
   }

    $this->form->addOutput("User logged in.");
    return true;
}
```

Om du studerar koden ovan ser du hur informationen plockas ut formuläret, en fråga ställs till databasen för att hämta den användaren som försöker logga in. Därefter kontrolleras lösenordet om det matchar och baserat på det tillåter man att användaren blir inloggade eller ej.

Kodexemplet sparar inte undan i sessionen om inloggningen gick bra eller ej, det behöver det göra för att det skall bli en riktigt inloggning, men för tillfället nöjer vi oss med att fokusera på databasbiten.



En databasdriven modell {#dbdrivenmodel}
--------------------------------------

Låt oss fokusera på databaskoden vi nu sett. Det vore en tanke att flytta den koden och kapsla in i en klass `User` som ligger i modellagret och har ansvar för alla detaljer om en användare, inklusive vetskapen om hur användarens detaljer kan lagras i databasen.

Vi kan kalla det en modellklass som använder sig av databasen, eller en databasdriven modellklass.



###Active Record designmönster {#ardesignmonster}

För att implementera en databasdriven modellklass väljer jag en variant av designmönstret _Active Record_.

När man skriver databaskod enligt Active Record kan det se ut så här.

```php
$book = new Book();
$book->find("id", 7);
$book->price += 10;
$book->save();
```

Koden ovan laddar en bok från en databastabell, ökar priset med 10 och sparar boken till databasen. Active record ger ett enkelt sätt att låta ett objekt spara sig i databasen. Det ger ett interface och en kodstruktur som blir enhetlig för alla klasser som väljer att jobba enligt designmönstret.



###CreateUserForm och active record {#arcreateuserform}

Hur skulle detta kunna se ut i formulärklassen `CreateUserForm`? Vi tittar på en uppdatering av metoden `callbackSubmit()`. Du kan se dels den tidigare och nu bortkommenterade koden samt den nya koden som jobbar mot klassen `User` som nu använder sig av active record.

```php
/**
 * Callback for submit-button which should return true if it could
 * carry out its work and false if something failed.
 *
 * @return boolean true if okey, false if something went wrong.
 */
public function callbackSubmit()
{
    // Get values from the submitted form
    $acronym       = $this->form->value("acronym");
    $password      = $this->form->value("password");
    $passwordAgain = $this->form->value("password-again");

    // Check password matches
    if ($password !== $passwordAgain ) {
        $this->form->rememberValues();
        $this->form->addOutput("Password did not match.");
        return false;
    }

    // Save to database
    // $db = $this->di->get("db");
    // $password = password_hash($password, PASSWORD_DEFAULT);
    // $db->connect()
    //    ->insert("User", ["acronym", "password"])
    //    ->execute([$acronym, $password]);
    $user = new User($this->di->get("db"));
    $user->acronym = $acronym;
    $user->setPassword($password);
    $user->save();

    $this->form->addOutput("User was created.");
    return true;
}
```

Det är följande rader som nu skapar användaren.

```php
$user = new User($this->di->get("db"));
$user->acronym = $acronym;
$user->setPassword($password);
$user->save();
```

Kanske blir det inte mycket färre rader men vi får en inkapsling och klassen `User` har själv full koll på hur den lagras i databasen.



###LoginUserForm och active record {#arloginform}

Hur ser då formuläret för login ut `UserLoginForm` med motsvarande ändring? Låt oss titta.

```php
/**
 * Callback for submit-button which should return true if it could
 * carry out its work and false if something failed.
 *
 * @return boolean true if okey, false if something went wrong.
 */
public function callbackSubmit()
{
    // Get values from the submitted form
    $acronym       = $this->form->value("user");
    $password      = $this->form->value("password");

    // Try to login
    // $db = $this->di->get("db");
    // $db->connect();
    // $user = $db->select("password")
    //            ->from("User")
    //            ->where("acronym = ?")
    //            ->executeFetch([$acronym]);
    // 
    // if (!password_verify($password, $user->password)) {
    //    $this->form->rememberValues();
    //    $this->form->addOutput("User or password did not match.");
    //    return false;
    // }

    $user = new User($this->di->get("db"));
    $res = $user->verifyPassword($acronym, $password);
    
    if (!$res) {
       $this->form->rememberValues();
       $this->form->addOutput("User or password did not match.");
       return false;
    }

    $this->form->addOutput("User " . $user->acronym . " logged in.");
    return true;
}
```

Här är det nu två rader kod som stämmer av om akronymen och lösenordet passar. Om det passar så är objektet `$user` fyllt med detaljer från databasen och kan användas som publika medlemmar i objektet.

Så här med `$user->acronym`.

```php
$this->form->addOutput("User " . $user->acronym . " logged in.");
```



###Klassen User och active record {#arusermodel}

Jag får säga att det är en trevlig tanke att kapsla in koden i `User` och göra den klassen ansvarig för relevanta delar, inklusive hanteringen mot databasen. Låt oss titta på klassen `User` och dess olika delar.

Vi börjar med inledningen av klassen.

```php
<?php

namespace Anax\User;

use \Anax\Database\ActiveRecordModel;

/**
 * A database driven model.
 */
class User extends ActiveRecordModel
{
```

Vi ser att klassen ärver från `ActiveRecordModel` som finns i modulen `anax/database`, vi gissar oss till det eftersom namespacet är `\Anax\Database\ActiveRecordModel`.

Sedan följer en referens till databastabellen och de kolumner som finns i tabellen som nu matchas av publika properties i klassen.

```php
/**
 * @var string TABLE_NAME name of the database table.
 */
protected $tableName = "User";

/**
 * Columns in the table.
 * 
 * @var integer $id primary key auto incremented.
 */
public $id;
public $acronym;
public $password;
public $created;
public $updated;
public $deleted;
public $active;
```

I denna implementationen av active record är det viktigt att klassens medlemmar matchar direkt mot databastabellens kolumner. Det är en restriktion som krävs.

Vi fortsätter att titta i klassen och ser en metod för att skapa lösenordet när användaren skapas.

```php
/**
 * Set the password.
 *
 * @param string $password the password to use.
 *
 * @return void
 */
public function setPassword($password)
{
    $this->password = password_hash($password, PASSWORD_DEFAULT);
}
```

Detta gjordes tidigare i formulärklassen men nu är det `User` som är ansvarig gör hur lösenordet skapas.

Det känns rätt om vi fortsätter med nästa metod som verifierar akronym och lösenord när användaren försöker logga in.

```php
/**
 * Verify the acronym and the password, if successful the object contains
 * all details from the database row.
 *
 * @param string $acronym  acronym to check.
 * @param string $password the password to use.
 *
 * @return boolean true if acronym and password matches, else false.
 */
public function verifyPassword($acronym, $password)
{
    $this->find("acronym", $acronym);
    return password_verify($password, $this->password);
}
```

Vi känner igen delar av koden som tidigare låg i formulärklassen för login.

Nu är det slut, detta var hela klassen `User`. Det innebär att en hel del kod och metoder ärvs ned från klassen `ActiveRecordModel`. Där finns bland annat metoderna för `find()` och `save()`.



###Vinsten med active record {#arvinst}

Låt oss ställa frågan om och vad vi kan vinna med ytterligare ett lager framför databasen, det lager som active record tillför.

Vinsten kan vara att dölja databaskoden och jobba enbart mot metoder likt `find()` och `save()`. Implementationen döljs i klassen `ActiveRecordModel` och m vi hade kikat i den hade vi sett tydligt hur den jobbar mot databasen.

En annan vinst är att det blir en tydlig struktur för att jobba mot modellklasser som vill spara sig i databasen.En del av den repetetiva databaskoden ligger nu återanvändbar i `ActiveRecordModel` och varje ny klass som vill jobba mot databasen behöver bara utöka den.

Kanske kan vi också se att vi abstraherar bort databasen ytterligare ett steg och gör oss mer oberoende av vilken databas vi använder. Vi kan nu skriva modellklasser utan att tänka på om det är MySQL eller SQLite. De eventuella inkompabiliteter som finns mellan databaser har vi nu lager som kan hantera. Det lagret är egentligen konstruktionen av _QueryBuilder_ som databasmodulen erbjuder. När vi använder den så låter vi metoder skapa SQL-koden, vi skapar inte själva SQL-koden och klassen kan då ta hänsyn till de skillnader som finns mellan olika databaser. Detta är något som abstraktionslagret PDO inte tar hänsyn till.

Kanske är detta ett bra sätt att skriva PHP-kod som är mer oberoende av databasen. Men det kan också bli svårare att utnyttja specifika delar i databasen såsom lagrade procedurer och funktioner. Kanske, inte nödvändigtvis dock. Egentligen så är det nog så att vi kan fortfarande skriva specifik databaskod om vi vill, det går bra med lagrade procedurer och funktioner bakom variationer av ett active record mönster. Iallafall om du frågar mig.

Nåväl, åter till saken. Det kan finnas flera delar av en struktur som erbjuds av active record. Låt oss titta på ett större exempel för att se hur koden kan se ut.



CRUD av böcker med active record {#arcrud}
--------------------------------------

För att visa hur det kan se ut i ett större sammanhang så valde jag att skapa ett exempel med en samling av böcker. I exemplet kan du skapa böcker, editera dem, radera dem och visa dem. Det blir CRUD och formulär samt en databasdriven modell som använder sig av active record.



###Scaffolda exemplet bok {#scaffbook}









Avslutningsvis {#avslutning}
--------------------------------------

Vi har återigen gjort en övning i refaktoring av ramverkets kod för att studera olika alternativ till strukturer. Nu var det routern som fick en genomgång och förändring i hur konfigurationen sker.

Denna artikel har en [egen forumtråd](t/6619) som du kan ställa frågor i, eller bidra med tips och trix.

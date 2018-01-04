---
author: mos
category:
    - javascript
    - nodejs
    - kursen databas
    - kursen dbjs
    - kursen linux
revision:
    "2018-01-04": (A, mos) Uppdaterad version 2.
...
Gör en kommandoradsklient i Node.js (v2)
==================================

[FIGURE src=/image/snapht15/thinking-of-number.png?w=c5&a=0,70,75,0 class="right"]

Vi skall skapa ett terminalprogram, ett _command line interface_ (CLI), med JavaScript i Node.js. I terminalprogrammet läser vi in instruktioner från användaren via tangentbordet och i en kommandoloop låter vi programmet utföra olika funktioner utifrån vad användaren ber om.

Tanken är att ge dig grunden till ett terminalprogram med en hyffsat god kodstruktur, som du kan bygga vidare på och integrera i din specifika miljö för dina egna applikationer.

Ett terminalprogram kan vara en användbar klient, både vid utveckling och när du levererar produkter till kunder.

<!--more-->



Förutsättning {#forutsattning}
--------------------------------------

Du har Node.js installerat och kan grunderna i hur man programmerar JavaScript med Node.js.

Ditt kursrepo innehåller exempelprogrammet (linux, databas, dbjs) under `example/nodejs/cli`.



Upplägg {#spec}
--------------------------------------

Vi skall skriva ett terminalprogram med JavaScript i Node.js. Vi kommer använda en modul i Node.js som heter [`Readline`](https://nodejs.org/dist/latest/docs/api/readline.html) för att göra ett menysystem och en kommandoloop som väntar på instruktioner från användaren och tangentbordet.

Vi skall göra en variant av gissningsleken "Gissa vilket nummer jag tänker på" för att exemplifiera hur programstrukturen kan byggas upp. Spelet går ut på att någon tänker på ett tal, datorn i detta fallet, och man får ett antal gissningar på sig att gissa rätt tal. Den som tänker på talet ger ledtråden om det rätta talet är högre eller lägre än gissningen.

Vi behöver följande.

1. En main-funktion som startar upp programmet och initierar kommandoloopen.
1. En kommandoloop som läser in gissningar och fortsätter tills användaren gissat rätt eller gissningarna tar slut eller avslutar med `exit`.
1. En modul som löser spelets logik.

För att få en god kodstruktur så delar vi upp programmet i moduler som sparas i varsin fil och knyts samman i main-funktionen.

Rent användarmässigt kan det se ut så här när vi är klara.

[ASCIINEMA src=155539 caption="Vilken tal tänker jag på?"]

Låt då se hur vi bygger upp spelet, del för del.



Main-funktionen {#main}
--------------------------------------

Exempelkoden för denna sektionen ligger i ditt kursrepo under `example/nodejs/cli/parts/1`.

Vi startar med en main-funktion i filen `index.js` som även innehåller en enklare variant av vårt spel.

```javascript
/**
 * Guess my number, a sample CLI client.
 */
"use strict";

/**
 * Main function.
 * @returns void
 */
(function() {
    // Read from commandline
    const readline = require('readline');
    const rl = readline.createInterface({
        input: process.stdin,
        output: process.stdout
    });

    // Ask question and handle answer in arrow function callback.
    rl.question("Guess my number: ", (guess) => {
        let thinking;
        let message;

        thinking = Math.round(Math.random() * 100 + 1);
        guess = Number.parseInt(guess);
        message = `I'm thinking of number ${thinking}.\n`
            + `Youre guess is ${guess}.\n`
            + `You guessed right? `
            + (thinking === guess);
        console.info(message);

        rl.close();
    });
})();
```

Vi ser vår main-funktion som importerar och förbereder modulen readline. Via metoden [`rl.question()`](https://nodejs.org/dist/latest/docs/api/readline.html#readline_rl_question_query_callback) läses gissningen in och spellogiken gissar ett tal och jämför med din gissning. Men du får bara en chans.

Så här ser det ut när du kör programmet.

[ASCIINEMA src=155360 caption="En första variant av spelet för att gissa nummer, än så länge med endast en gissning."]

Vi har en god start.



En modul för spellogiken {#modul}
--------------------------------------

Exempelkoden för denna sektionen ligger i ditt kursrepo under `example/nodejs/cli/parts/2`.

Jag lyfter ut spellogiken till en egen modul `game.js`. Jag behöver minst två metoder i modulen som jag väljer att bygga som en klass. Den ena metoden initierar spelet och slumpar fram numret. Den andra metoden kontrollerar om en gissning är rätt.

Grovt sett ser min modul ut så här.

```javascript
/**
 * A module for game Guess the number I'm thinking of.
 */
"use strict";

class Game {
    /**
     * @constructor
     */
    constructor() {
        this.thinking = -1;
    }

    /**
     * Init the game and guess the number.
     *
     * @returns void
     */
    init() {
        this.thinking = Math.round(Math.random() * 100 + 1);
    }

    /**
     * Check if the guess is correct or not.
     *
     * @param {integer} guess The number being guessed.
     *
     * @returns {boolean} True if guess matches thinking, else false.
     */
    check(guess) {
        return guess === this.thinking;
    }
}

module.exports = Game;
```

Det blev en konstruktor som sätter medlemsvariabeln som kommer ihåg talet som tänks på. Det blev metoden `init()` som slumpar fram ett nytt värde och `check()` för att kontrollera om gissningen är rätt.

Egentligen vore det nog bra om jag kunde tjuvkika på vilket nuvarande tal som gäller via `cheat()` och kanske en metod `compare()` som returnerar om det verkliga talet är högre eller lägre än min gissning. Men jag utelämnar de metoderna för tillfället, du kan säkert klura ut hur de skulle byggas upp. Du hittar koden i kursrepot om du vill tjuvkika.

Modulen implementeras som en klass och klassen exporteras i sista raden i filen.

```javascript
module.exports = Game;
```

Det är export-delen som gör att modulen nu kan importeras i main-funktionen.

Jag uppdaterar min main-funktion så att den använder modulen, följande är de ändringar som främst görs.

```javascript
(function() {
    // ... readline setup
    const Game = require("./game.js");
    let game = new Game();

    game.init();

    rl.question("Guess my number: ", (guess) => {
        let message;
        let thinking = game.cheat();

        guess = Number.parseInt(guess);
        message = `I'm thinking of number ${thinking}.\n`
            + `Youre guess is ${guess}.\n`
            + `You guessed right? `
            + game.check(guess);
        console.info(message);

        rl.close();
    });
})();
```

För säkerhetsskull testkör jag spelet, men det bör fungera på samma sätt som tidigare.

[ASCIINEMA src=155366 caption="Gissningen blev rätt, uppenbarligen går det gissa rätt även med en gissning."]

Min tanke är att separera själva spelet från klienten som hanterar inmatningen och gissningen. Tanken är att spelet går att använda andra sammanhang och i andra klienter. Därför väljer jag att separera koden i två delar och undviker att lägga själva inmatningen i modulen `Game`.



En kommandoloop {#kommando}
--------------------------------------

Exempelkoden för denna sektionen ligger i ditt kursrepo under `example/nodejs/cli/parts/3`.

Låt oss nu utveckla main-funktionen för att läsa in gissningar tills det blir rätt, eller tills gissningarna tar slut, eller tills användaren avslutar genom att skriva in `exit`.

Vi väljer att använda metoden `rl.prompt()` för att hantera inmatningen. Vi använder den i en form av oändlig loop som avslutas när `exit` skrivs in. Egentligen är det en form av rekursiva anrop som sker, men effekten blir en "oändlig loop".

Låt oss se hur det ser ut när vi kör det uppdaterade exempelprogrammet.

[ASCIINEMA src=155509 caption="Nu sker inmatningen i en oändlig loop som avslutas när användaren skriver `exit`."]

Låt oss kika på koden. Först tar vi den delen som hanterar gissningen, den är nu flyttad till en egen funktion så att main-funktionen kan vara så liten som möjligt.

```javascript
/**
 * Guess the number and check if its correct.
 *
 * @param {Game}   game  The current game being played.
 * @param {number} guess The number being guessed.
 *
 * @returns {void}
 */
function makeGuess(game, guess) {
    let message;
    let thinking = game.cheat();

    guess = Number.parseInt(guess);
    message = `I'm thinking of number ${thinking}.\n`
        + `Youre guess is ${guess}.\n`
        + `You guessed right? `
        + game.check(guess);
    console.info(message);
}
```

Det är i stort sett samma funktionalitet som tidigare, skillnaden är att den är flyttad till en funktion.

Jag gjorde även en funktion för att avsluta programmet. Det visade sig att samma kod användes i flera sammanhang, vilket gör det passande att lägga i en egen funktion. Vi försöker skriva DRY kod.

```javascript
/**
 * Close down program and exit with a status code.
 *
 * @param {number} code Exit with this value, defaults to 0.
 *
 * @returns {void}
 */
function exitProgram(code) {
    code = code || 0;

    console.info("Exiting");
    process.exit(code);
}
```

Via `process.exit()` kan vi avsluta programmet och alla dess delar och vi ger möjligheten till eventuella tjänster att stänga ned sig.

Då har vi main-funktionen kvar att skåda. Där kan vi nu se en begynnande kommandoloop, implementerad med readline, eventhantering och `prompt()`.

```javascript
/**
 * Main function.
 * @returns void
 */
(function() {
    const readline = require("readline");
    const rl = readline.createInterface({
        input: process.stdin,
        output: process.stdout
    });

    const Game = require("./game.js");
    let game = new Game();

    game.init();

    rl.setPrompt("Guess my number: ");
    rl.prompt();

    rl.on("close", exitProgram);
    rl.on("line", (line) => {
        line = line.trim();
        switch (line) {
            case "quit":
            case "exit":
                exitProgram();
                break;
            default:
                makeGuess(game, line);
        }
        rl.prompt();
    });
})();
```

Överst så initierar vi modulen readline och modulen Game som tidigare. Det som skiljer är att vi nu använder `rl.setPrompt()` för att sätta vår egen prompt och sedan anropas `rl.prompt()` för att ge kontrollen till tangentbordet och låta användaren skriva in ett kommando.

Vi anger två callbacks för eventen `close` och `line`. Den första, `close`, är när användaren trycker `ctrl-d` vilket leder till att det blir samma sak som att skriva `exit`. Att trycka `ctrl-d` är ett vanligt sätt att avsluta inmatningen i ett terminalprogram.

Den andra, `line`, anropas varje gång en rad matas in via tangentbordet, en radinmatning avslutas med `Enter` av användaren. Det inmatade värdet sparas i variabeln `line` och via switch-satsen kan vi ta olika beslut baserat på dess innehåll.

När `line` innehåller strängen `exit` eller `quit` så avslutas programmet. I alla andra fall så anropas funktionen `makeGuess()` som genomför själva gissningen.



Summering {#summering}
--------------------------------------

Vi har nu en grund till ett terminalprogram som kan utföra olika saker beroende på vad användaren matar in. Vi har strukturerat vissa delar av koden i funktioner och andra i moduler. Här väljer vi det som vi tycker passar bäst för tillfället. När koden växer så kanske vi måste göra andra beslut och bygga kom kodstrukturen.

Hur kan vi bygga ut programmet med en meny som visas om man skriver `help` eller `menu`?

Kan vi lägga till ett menyval som heter `cheat` och skriver ut nuvarande siffra i spelet?

Kan vi lägga till ett menyval som heter `init` som startar om spelet och gissar talet på nytt?

Vad sägs om att lägga till ett max antal gissningar? Man måste gissa rätt siffra, men man får bara ett begränsat antal gissningar.

Hur skulle du gjort dessa utökningar av programmet? Troligen går det bra att bara bygga vidare på samma struktur du har. Känner du att det blir för mycket kod i `index.js` så har du alltid möjligheten att bryta ut delar av koden till en egen modul/fil.

Jag gjorde min egna lilla uppdatering till spelet som du ser ut så här när man spelar.

[ASCIINEMA src=155539 caption="Spelet är nu klart och strukturen för en terminalklient likaså."]

Exempelkoden för denna sektionen ligger i ditt kursrepo under `example/nodejs/cli/parts/4`.



Avslutningsvis {#avslutning}
--------------------------------------

Detta var grunderna i hur man kan sätta ihop ett terminalprogram med JavaScript i Node.js. Du har fått en grundstruktur som du kan bygga vidare på när du vill ha ett enklare terminalprogram.

Har du [tips, förslag eller frågor](t/7193) så finns det en specifik forumtråd för denna artikel.

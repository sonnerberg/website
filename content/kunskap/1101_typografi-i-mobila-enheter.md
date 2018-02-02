---
author: efo
category: javascript
revision:
  "2018-01-09": (A, efo) Första utgåvan inför kursen webapp-v3 V18.
...
Typografi för mobila enheter
==================================

[FIGURE src=image/webapp/typography.jpg?w=c5 class="right"]

I denna artikel går vi igenom hur vi anpassar typsnitt och typografin för våra mobila enheter. Fokus kommer ligga på att skapa användbara, men framför allt tillgängliga och lättlästa gränssnitt för textintensiva hemsidor. Vi kommer ta utgångspunkt i att göra en redovisningssida och kommer formatera den för läsbarhet.



<!--more-->



En grund i HTML {#html}
--------------------------------------
Vi börjar med en enkel grund i HTML där vi laddar in vår CSS kod från filen `style.css`, vi nollställar även webbläsarens grundstil med `normalize.min.css`. Vi laddar ner `normalize.min.css` med kommandot `wget https://cdnjs.cloudflare.com/ajax/libs/normalize/7.0.0/normalize.min.css`.

```html
<!-- index.html -->

<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Redovisning</title>

    <link rel="stylesheet" href="normalize.min.css" />
    <link rel="stylesheet" href="style.css" />
</head>
<body>
    <main>
        <header>
            <h1>Redovisning</h1>
        </header>
        <article>
            <h2>kmom01</h2>

            <h4>Är du sedan tidigare bekant med utveckling av mobila appar?</h4>
            <p>Jag har tidigare utvecklad en app för App Store. Men det var i Objective-C och långt ifrån webbens tekniker som används i denna kurs. Utvecklingsmiljön i denna kurs känns som mer den jag är van vid från tidigare webb kurser och webbprogramming i allmänhet.</p>

            <h4>Vilket är den viktigaste lärdomen du gjort om typografi för mobila enheter?</h4>
            <p>Hur viktikt det är med vita utrymmen (whitespace) för att klumpa ihop besläktade element. Vita utrymmen ger dessutom ett luftigare utseende, som känns mer modernt.</p>

            <h4>Du har i kursmomentet hämtat data från två stycken API. Hur kändes detta?</h4>
            <p>Att med XMLHttpRequest och fetch hämta data från de två API fungerade bra. Dokumentationen för Githubs API var från början överväldigande, men med lite tillvänning gick det att få fram det jag sökte. Ger stora möjligheter med API:er där man frikopplad från implementeringen kan få fram snygga klienter. Blir spännande att jobba vidare med detta i kommande kursmoment.</p>
        </article>
    </main>
</body>
</html>
```

[FIGURE src=image/webapp/screenshot-typo-no-style.png?w=c7 caption="Redovisningstext med nollställd stil"]



Vitt utrymme {#whitespace}
--------------------------------------
Vi börjar med den del av designen som inte har med typsnittet att göra. Vi vill skapa en sammanhang mellan de element som är besläktade, så vi börjar med att skapa sammanhang mellan frågan och svaret. Vi minskar helt enkelt marginalen under våra frågor och öker den över frågorna. Då det finns marginal även på paragrafen som innehåller svaret minskar vi marginalen där med. Vi flytter även kursmoment rubriken närmare första frågan.

```css
h2 {
    margin-bottom: 0.6rem;
}

h4 {
    margin-bottom: 0.2rem;
    margin-top: 1.8rem;
}

h4:first-of-type {
    margin-top: 0.6rem;
}

p {
    margin-top: 0.2rem;
}
```

Nu har vi skapat en sammanhang mellan frågor och svar, men ser fortfarande ihopklumpat ut. Lått oss skapa lite yta runt om texten och öka upp radavståndet för bättre läsbarhet och se om det hjälper. En bra tumregel är att ligga mellan 1,25 och 1,5 i radavstånd för längre textstycken.

```css
main {
    padding: 0.6rem;
}

h2 {
    margin-bottom: 0.6rem;
}

h4 {
    margin-bottom: 0.2rem;
    margin-top: 1.8rem;
    line-height: 1.4;
}

h4:first-of-type {
    margin-top: 0.6rem;
}

p {
    margin-top: 0.2rem;
    line-height: 1.4;
}
```

Vi har redan fått till en bättre sammanhang mellan frågor och svar. Vi har även skapat luft runt texten genom att använda vitt utrymme runt texten. Vi jämför ursprungssidan med som det ser ut nu och ser hur stor skillnad vitt utrymme kan göra.

[FIGURE src=image/webapp/screenshot-typo-whitespace.png?w=c7 class=right caption="Redovisningstext med vitt urymme"]
[FIGURE src=image/webapp/screenshot-typo-no-style.png?w=c7 caption="Redovisningstext med nollställd stil"]



Typsnitt {#font}
--------------------------------------
Nu är det dags för det som faktiskt syns på sidan och det nog enklaste sättet att förändra känslan av en hemsida. Jag har vald ut två stycken [Google Fonts](https://fonts.google.com/). Ett serif typsnitt Merriweather för brödtexten och sans-serif typsnitt Source Sans Pro för rubriker. Båda typsnitten har stora och tydliga vita områden i bokstäver som 'o', 'e' och 'c', som ger bra läsbarhet. Merriweather har små men ändå tydliga [seriffer](https://en.wikipedia.org/wiki/Serif), som skapar linjer i texten och förankrar typsnittet.

En annan viktig del av utseendet på en hemsida är storleken på typsnittet. Detta är oerhört viktigt ur ett tillgänglighetsperspektiv då rätt hantering underlättar för de som har svårigheter med synen. Vi använder "best-practice" från [Typography Handbook](http://typographyhandbook.com/) och sätter storleken till 100% och använder oss sedan av den relativa enheterna `rem` för att sätta storleken på typsnittet för paragrafer och rubriker.

```css
html { font-size: 100% }
p { font-size: 1rem }
h1 { font-size: 2.4rem }
h2 { font-size: 2.0rem }
h4 { font-size: 1.4rem }

@media (min-width: 64em) {
  html {
    font-size: 112.5%;
  }
}
```

Vi jämför skillnaden mellan den nollställda stilen innan våra ändringar och hur den slutliga redovisningssidan ser ut på en mobil enhet. En större sammanhang mellan frågor och svar och typsnitt som är läsbara och som följer användarens inställningar för textstorlek i webbläsaren.

[FIGURE src=image/webapp/screenshot-typo-font.png?w=c7 class=right caption="Redovisningstext slutlig stil"]
[FIGURE src=image/webapp/screenshot-typo-phone-no-style.png?w=c7 caption="Redovisningstext med nollställd stil"]



Avslutningsvis {#avslutning}
--------------------------------------
Vi har i denna övning skrapat ytan för typografi i mobila enheter. Vi har en grund att stå på inför redovisningssidan, men även för andra textintensiva gränssnitt. Ni kan nu göra medvetna val med avseende på typsnitt och använda vita utrymmen till eran fördel för att samla besläktade element. Använd [Typography Handbook](http://typographyhandbook.com/) och [Butterick's Practical Typography](https://practicaltypography.com/) som uppslagsverk när ni skapar tillgängliga och användbara hemsidor, så har ni ett försprång mot 90% av alla andra webbprogrammerare.

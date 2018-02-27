---
author: mos
revision:
    "2018-02-27": "(A, mos) Första utgåvan."
...
Projekt i grupp och individuell examination
====================================

_Detta dokument gäller de som läser enligt kurskoden PA1444 inom programmen International Software Engineering (ISE) och Software Engineering (SE)._

Detta kursmoment avslutar och examinerar kursen.

Upplägget är enligt följande:

* Individuell examination
* Projekt

Totalt omfattar kursmomentet (07/10) i storleksordningen 20*4 studietimmar.



Bedömning och betygsättning {#bedomning}
--------------------------------------------------------------------

När du lämnat in projektet och den individuella delen så bedöms det tillsammans med dina tidigare redovisade kursmoment och du får ett slutbetyg på kursen.

Inlämningen betygssätts som en **projektinlämning samt individuell examination** enligt [grunderna för bedömning och betygsättning vid projekt och individuell examination](kurser/faq/bedomning-och-betygsattning-projekt-och-individuell).



Individuell examination {#index}
--------------------------------------------------------------------

Examinationstillfället sker i sal på campus vid ett bokat tillfälle.

Du får en uppgift där du skall programmera en databas med tillhörande applikation under en viss tidsbegränsning.

Du får ha tillgång till internet och all kod du skrivit under kursen. Du gör uppgiften på din egen dator.

Spara alla filer i katalogen `me/kmom10/exam` och lämna in med `dbwebb publish`.



Projekt {#projekt}
--------------------------------------------------------------------

Du kan välja att lösa projektet enskilt eller i grupp om max tre deltagare.

[Läs i projektspecen](./../projekt-internetbanken) om projektet.

Spara alla filer i katalogen `me/kmom10/proj`.

Om ni jobbar i grupp så tar alla varsin kopia av projektet och lägger i sitt eget kursrepo.



### Krav 1:  {#k1}

Lös uppgiften enligt projektspecen, exklusive räntehanteringen.

Gör minst en applikation som webbaserad och minst en som CLI-baserad.

Resterande applikationer kan lösas med enbart lagrade procedurer, men då krävs det att de är tydligt dokumenterade i ER-dokumentationen.

Databasen skall heta `internetbanken` och användaren user:pass skall ha full tillgång till databasen.

SQL-filer sparar du som vanligt i `sql/ddl.sql` och `sql/insert.sql`.

Din CLI startas via filen `cli.js`.

Din webbklient startas via filen `index.js`.

Detaljer för att koppla sig mot databasen delas av klienterna och sparas i `config/internetbanken.json`.

Alla externa beroenden installeras via `package.json`.



###Krav 2: {#k2}

ER-dokumentationen sparar du i `doc/er.pdf`.

Den som testar kommer att läsa dokumentationen för att se hur dina applikationer skall användas. Det är viktigt att du är tydlig och beskriver hur de används.

När du löst saker med lagrade procedurer behöver du ange hur de skall användas.



###Krav 3: (optionellt) {#k3}

Lös kraven som rör räntehanteringen.



###Krav 4: (optionellt) {#k4}

Gör ett av följande krav:

* Lös samtliga krav/applikationer med CLI och/eller webbklient.
* Skydda webbklienten via en inloggning där du sparar användare och lösenord i databasen och använder sessioner.

<!--
Exportera till Excelark
Login m session
Flash, felhantering med session.
-->



Redovisning {#redovisning}
--------------------------------------------------------------------

Följande skall göras individuellt, även om själva projektet utfördes i grupp.

1. På din redovisningssida, skriv följande:

    1. Skriv ett allmänt stycke om hur projektet gick att genomföra. Berätta vilka ni var i gruppen och hur ni fördelade arbetet (om du jobbade i grupp). Berätta om problem/lösningar/strul/enkelt/svårt/snabbt/lång tid, etc. Var projektet lätt eller svårt? Tog det lång tid? Vad var svårt och vad gick lätt? Var det ett bra och rimligt projekt för denna kursen?

    1. Avsluta med ett sista stycke med dina tankar om kursen och vad du anser om materialet och handledningen (ca 5-10 meningar). Ge feedback till lärarna och förslå eventuella förbättringsförslag till kommande kurstillfällen. Är du nöjd/missnöjd? Kommer du att rekommendera kursen till dina vänner/kollegor? På en skala 1-10, vilket betyg ger du kursen?

1. Ta en kopia av texten på din redovisningssida och kopiera in den på Its/redovisningen. Glöm inte länka till din me-sida och projektet. 

1. Se till att samtliga kursmoment validerar.

```bash
# Ställ dig i kursrepot
dbwebb publish me
```

---
author:
    - mos
    - aar
    - efo
revision:
    "2018-06-26": (I, efo) Ändrade till individuell examination.
    "2018-06-08": (prel, mos) Nytt dokument inför uppdatering av kursen.
    "2017-09-27": (H, aar) Uppdaterade krav 6, tog bort curses.
    "2017-06-22": (G, aar) Minskade antalet rum till 5 och la till fusk kommando.
    "2016-10-13": (F, mos) Bort med gammalt stycke om curses och tillåt väderstreck.
    "2015-08-25": (E, mos) Uppgraderade till dbwebb v2.
    "2015-02-12": (D, mos, Sylvanas) Uppdaterade krav 6 och 5 (tog bort curses).
    "2015-01-08": (C, mos) Bort blå ruta med kursutveckling pågår.
    "2014-11-19": (B, mos) Tog bort `s` från kommandot se, det var duplicerat.
    "2014-11-12": (A, mos) Första versionen till python ht14.
...
Kmom10: Individuell examination
==================================

Detta kursmoment avslutar och examinerar kursen.

[WARNING]

** Kursutveckling pågår till kurs python v2 **

Kursstart hösten 2018.

[/WARNING]



Upplägg {#upplagg}
--------------------------------------------------------------------

Den individuella examinationen genomförs den 2018-10-30. Du använder dbwebb-kommandorads verktyget för att hämta din individuella examinations uppgift och för att rätta, validera och lämna in dina lösningar.

Nedanför beskriver vi upplägget för de olika studentgrupperna:

### Campus studenter {#campus}
Examination sker i sal H429 och H430 mellan 8:00 och 13:00.

### Distansprogram och kurspakets studenter {#distans}
Examination sker på valfri plats, det går att ladda ner examination från kl 8:00 till 23:59. När du har hämtat hem examinationen har du fem timmar på dig att göra klart den och lämna in.


Inlämning på [Canvas och redovisning](#redovisning) behövs inte göras inom dessa fem timmar.



Hämta examinationstillfälle 2018-10-30 (try1) {#hamta}
----------------------------------------------------------------------

I [Om examination med dbwebb exam](kurser/python-v2/kmom10/om) finns mer information om `dbwebb exam`-verktyget.

Innan du kör kommandon nedan uppdatera `dbwebb` och kursrepot samt skapa kataloger i din me katalog med följande kommandon.

```bash
# stå i kursrepot dbwebb-kurser/python
dbwebb selfupdate # eventuellt behövs sudo eller admin rättigheter
dbwebb update
dbwebb init
```


För att skapa din individuella examination skriv in följande kommando.

```
dbwebb exam create try1
```

Materialet till din individuella examination ligger nu i din kurskatalog i `me/kmom10/try1` enligt följande.

| Fil                | Innehåll                                                              |
|--------------------|-----------------------------------------------------------------------|
| `assignments.md` | Beskrivning av examinationen och de uppgifter som skall göras, öppna och läs via en texteditor.               |
| `exam.py`        | Här skall du skriva din kod för att lösa respektive uppgift i examinationen. Du kan köra programmet genom kommandot `python3 exam.py` |

`dbwebb exam correct try1` rättar din individuella examination och visar hur många uppgifter du har klarat och dina poäng.

`dbwebb validate try1` validerar din individuella examination.

`dbwebb exam seal try1` lämnar in din individuella examination.



Bedömning och betygsättning {#bedomning}
--------------------------------------------------------------------

Det finns ett särskilt dokument som beskriver hur [bedömning och betygsättning sker](kurser/faq/bedomning-och-betygsattning-individuell).

Under hela examinationen kan du köra kommandot `dbwebb exam correct try1` för att rätta dina lösningar och se hur många poäng du har uppnått.



Redovisning {#redovisning}
--------------------------------------------------------------------

Efter din individuella examination lämna in en redovisningstext på din me-sida och via Canvas uppgiften 'Individuell examination'. I redovisningstexten skriv följande:

1. För varje uppgift du implementerade, dvs 1-5, skriver du ett textstycke om minst 5 meningar där du beskriver den tekniska implementationen.

1.  Skriv ett allmänt stycke om hur den individuella examinationen gick att genomföra. Problem/lösningar/strul/enkelt/svårt/snabbt/lång tid, etc. Var den individuella examinationen lätt eller svår? Vad var svårt och vad gick lätt? Var den individuella examinationen en bra och rimlig examination av denna kursen?

1. Avsluta med ett sista stycke med dina tankar om kursen och vad du anser om materialet och handledningen (ca 5-10 meningar). Ge feedback till lärarna och förslå eventuella förbättringsförslag till kommande kurstillfällen. Är du nöjd/missnöjd? Kommer du att rekommendera kursen till dina vänner/kollegor? På en skala 1-10, vilket betyg ger du kursen?

1. Ta en kopia av texten från din inlämning i Canvas och gör ett inlägg i kursforumet och berätta att du är klar.

1. <u><b>Distansprogram- och Kurspaket studenter</b></u> kompletterar redovisningstexten med att spela in en kort video där de visar kod och berättar om de tekniska implementationerna de gjorde i den individuella examinationen. Lägg till en länk till videon i redovisningstexten på inlämningen på Canvas.



Förberedelse {#forberedelse}
----------------------------------------------------------------------

Du har innan examinationen möjlighet att förbereda dig genom att göra en test examination. Test examinationen fungerar på liknande sätt. Du kan hämta hem den med följande kommando:

```bash
dbwebb exam create prep
```

Materialet till din individuella examination ligger nu i din kurskatalog i `me/kmom10/prep` enligt följande.

| Fil                | Innehåll                                                              |
|--------------------|-----------------------------------------------------------------------|
| `assignments.md` | Beskrivning av examinationen och de uppgifter som skall göras, öppna och läs via en texteditor.               |
| `exam.py`        | Här skall du skriva din kod för att lösa respektive uppgift i examinationen. Du kan köra programmet genom kommandot `python3 exam.py` |



`dbwebb exam correct prep` rättar din individuella examination och visar hur många uppgifter du har klarat och dina poäng.

`dbwebb validate prep` validerar din individuella examination.

`dbwebb exam seal prep` lämnar in din individuella examination.



Omexamination {#omexamination}
----------------------------------------------------------------------
Som student har du rätt till tre examinationstillfällen med andra ord om du inte klarar första har du två försök till på dig.
Följande tillfällen erbjuds efter 2018-10-30:

Omexaminationstillfälle torsdagen den 2019-01-10.

Restexaminationstillfälle måndagen den 2019-06-10.

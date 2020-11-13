---
author: nik
category:
    - kurs/design-v3
    - grid
    - flex
revision:
    "2020-11-11": (A, nik) Skapad inför ht20
...
Bygg om din rapport-sida med CSS-Grid
===================================

Du skall bygga om rapport-sidan på din portfolio sida med hjälp utav CSS-Grid.

Du börjar med att strukturera upp din samlingssida för alla rapporter och följer sedan upp med att fixa din layout på varje individuell sida.

<!--more-->

Förkunskaper {#forkunskaper}
-----------------------

Du har jobbat igenom följande tre delar i "[Design med HTML5 och CSS3](guide/design-med-html5-och-css3)"

* [CSS Grid Layout](guide/design-med-html5-och-css3/css-grid-layout)
* [Flexbox - Parent Elements](guide/design-med-html5-och-css3/flexbox)
* [Flexbox - Child Elements](guide/design-med-html5-och-css3/flexbox-del2)

Och artikeln [Skapa en specifik layout i Pico](kunskap/skapa-en-specifik-layout-i-pico) som beskriver hur du kan skapa en layout för specifika sidor.

Krav {#krav}
-----------------------

Det är ofta man som utvecklare ska bygga något ifrån Wireframes. En alumni till programmet, Matilda, var snäll att fixa fyra wireframes som ni ska försöka efterlikna i eran landningssida och report-sida.

### Landningssida

Din landningssida för report ska ha ett liknande upplägg till detta på desktop:

[FIGURE src=image/design-v3/wireframes/frame_2.png caption="Vår landningssida på desktop"]

För att uppnå detta ska du använda dig utav CSS-Grid. Sidan skall vara responsiv så om man går in på den via en mobil enhet så ska det istället se ut såhär:

[FIGURE src=image/design-v3/wireframes/frame_1.png caption="Vår landningssida på en telefon"]

### Report

Varje enskild rapportsida ska nu ha en sidebar så man enkelt kan navigera mellan kursmoment, såhär kan det t.ex se ut:

[FIGURE src=image/design-v3/wireframes/frame_3.png caption="Vår enskilda report-sida på desktop"]

För att uppnå detta ska du använda dig utav antingen CSS-Grid eller flexbox. Sidan ska även vara responsiv genom att sidebar:en döljs. Såhär kan det se ut:

[FIGURE src=image/design-v3/wireframes/frame_4.png caption="Vår enskilda report-sida på mobil"]

Extrauppgifter {#extra}
-----------------------

* Lägg på din report till länkar längst upp/ner som tar dig tillbaka till landningssidan.
* Implementera gärna flexbox eller grid på någon annan del av din sida om du får tid över.


Tips från coachen {#tips}
-----------------------

Testa gärna att göra olika layouts om du får tid över.

Lycka till och hojta till i Discord om du behöver hjälp!

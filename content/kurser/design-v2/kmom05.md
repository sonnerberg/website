---
author:
  - mos
  - efo
revision:
    "2018-10-19": (D, efo) Uppdatering med design guide.
    "2018-06-08": (prel, mos) Nytt dokument inför uppdatering av kursen.
    "2017-11-27": (C, mos) Genomgången inför ht17.
    "2016-11-28": (B, mos) La till manualen om CImage som läsresurs.
    "2016-11-15": (A, mos) Första utgåvan.
...
Kmom05: Bild
====================================

[WARNING]

**Kursutveckling pågår till kurs design v2**

Kursstart hösten 2018.

[/WARNING]


[FIGURE src="image/dbwebbisar.jpg?w=200&h=150&a=0,20,20,50&cf" class="right"]

Låt oss ägna ett kursmoment åt att testa runt med bilder och publicera dem på en webbplats.

Vi behöver vara medvetna om att bilder kan vara tunga att ladda och det vill vi hitta sätt att hantera. Hur tunga (stora) behöver bilder vara när de skall visas på en webbplats? Behöver de vara lika tunga på en desktop och på en mobil enhet?

Kan man ha olika bilder som visas på olika enheter? Det låter som en vettig idé men fungerar det i dagsläget?

<!--more-->

[FIGURE src="image/dbwebbisar.jpg?w=200&h=150&a=0,20,20,50&cf" class="left"]

Är det skillnad på foton och skärmdumpar? Ja, det är en fråga man skulle vilja ha svar på.

Om man vill beskära bilder, är det vettigt och hur gör man då? Vi har ju alltid fotoredigeringsprogram likt Gimp, men låt oss kika på alternativ som kan passa en webbprogrammerare.

Låt oss testa runt och placera och beskära dessa bilder för att visa att vi bemästrat området. Inklusive responsivitet med bilder via en LESS modul.

Innan du påbörjar kursmomentet så kan du ta en sväng ut i skogen, eller staden, ta med din kamera och fota loss lite. Så får du lite material att lägga upp på din me-sida.

[FIGURE src="image/dbwebbisar.jpg?w=200&h=150&a=0,20,20,50&cf" class="center"]

Vi har många frågeställningar om bilder, men låt se om vi kan bringa klarhet i några av dem.

[FIGURE src="image/dbwebbisar.jpg?w=700"]
[FIGURE src="image/dbwebbisar.jpg?w=500"]
[FIGURE src="image/dbwebbisar.jpg?w=300"]
[FIGURE src="image/dbwebbisar.jpg?w=100"]



<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 8-10 studietimmar)*



### Kurslitteratur  {#kurslitteratur}

Läs följande:

1. Läs i boken "[The principles of Beautiful Web Design](kunskap/boken-the-principles-of-beautiful-web-design)".

    * Kap 5 Imagery



### Design med HTML5 och CSS3  {#guide}

1. Läs igenom följande sektion i guiden "[Design med HTML5 och CSS3](guide/design-med-html5-och-css3)".
    * [Bilder](guide/design-med-html5-och-css3/bilder)

I sektionen [Bilder](guide/design-med-html5-och-css3/bilder) använder vi olika tekniker för att skapa responsiva bilder och bilder som fungerar bra på högupplösta skärmar.



### Om responsivitet {#responsivitet}

Läs följande om responsivitet.

1. Läs artikeln "[Responsive images](https://developers.google.com/web/fundamentals/design-and-ux/responsive/images)" som ger dig en insyn i ämnet bilder och responsiva webbplatser.

1. Som extra läsning kring responsiva bilder rekommenderas [AlistApart: Using Responsive Images (Now) (2015)](http://alistapart.com/article/using-responsive-images-now) som ger en ytterligare översyn av tekniker som kan användas.



### Webbplatsers laddningstid {#artikel}

Studera följande för att förbereda dig för uppgiften där du skall analysera webbplatsers laddningstid.

1. Läs översiktligt igenom artikeln "[Moz om Page Speed](https://moz.com/learn/seo/page-speed)".

1. Kika snabbt på Googles "[PageSpeed Insights Rules](https://developers.google.com/speed/docs/insights/rules)" för att snabba upp sidor.



### Lästips verktyg {#lastips}

Följande tips på verktyg är bra att ha för en webbprogrammerare. Verktygen handlar om att hantera bilder i olika form och på olika sätt.

1. [GIMP](https://www.gimp.org/) är en fri variant till bildbehandlingsprogram likt Photoshop.

1. [Inkscape](https://inkscape.org/en/) är ett fritt program för att rita och hantera bilder i vektorgrafik såsom SVG.

1. Ett bra snapshot-verktyg för skärmdumpar vill du integrera i din verktygslåda. Du vill ha ett verktyg där du enkelt kan ta en snapshot på hela eller delar av skärmen eller på en specifik applikation eller på innehållet i en webbsida. Det är smidigt om det är kopplat till ett enklare ritverktyg vilket gör det enkelt att rita på din snap. På Linux använder jag ett verktyg som heter [Shutter](http://shutter-project.org/).

1. [ImageMagick](imagemagick.org/) är ett verktyg som hjälper dig att analysera och konvertera bildfiler på kommandoraden. Verktygen går att installera på både Windows, Mac OS och Linux.

1. Gå översiktligt igenom [manualen för Cimage](https://cimage.se/) som är ett php-skript som beskär dina bilder utan behov av ett bildhanteringsverktyg. Cimage finns redan installerad i ditt ramverk. Manualen ger dig en insyn i hur du kan använda verktyget i den kommande uppgiften. Manualen ger också en översikt av olika begrepp och hantering kring bilder, bildformat, beskärning av bilder, optimering av filstorlekar och kvalitetsaspekter så se den som rent utbildningsmaterial kring bildhantering.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 8-10 studietimmar)*



### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften "[Utvärdera webbplatsers laddningstid och användbarhet](uppgift/utvardera-webbplatsers-laddningstider-och-anvandbarhet)". Du skall skriva en rapport, ensilt eller i grupp.

1. Gör uppgiften "[Bygg ut ditt Anax Flat tema med stöd för bilder](uppgift/anax-flat-tema-med-bilder)". Du skall bygga en blogg som är full av bilder och på det sättet visa upp att du behärskar bildhanteringen med Cimage, FIGURE och LESS-modulen som stylar figure-elementet.

<!--
1. I kursrepot `example/figure` finns två exempel som visar hur man kan jobba med `<figure>` och uppnå responsiva bilder. Studera och undersök exemplet och försök förstå hur det fungerar och hur det är uppbyggt. Där hittar du LESS-kod du kan låna till uppgiften.
    * [Figure and figcaption](repo/design/example/figure/figure.html)
    * [Figure and figcaption med media queries](repo/design/example/figure/figure-responsive.html)

1. Pröva att bygga en enkel blogg i Anax Flat genom att studera exempel på [hur man gör en blogg i Anax Flat](anax/gor-en-blogg) i Anax läs igenom hur du kan använda [shortcodes i Markdown](anax/shortcodes).
-->

1. Försäkra dig om att du har gjort `dbwebb publishpure redovisa` och taggat din inlämning med version 5.0.0 (eller högre) samt pushat repot inklusive taggarna till GitHub.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Berätta kort om erfarenheterna med din undersökning av webbplatsers laddningstid.
* Har du några funderingar kring Cimage och dess nytta och features?
* Lyckades du uppnå ett bra sätt och en LESS-struktur för att jobba med dina bilder i webbplatsen?
* Vad är din egen uppfattning kring bilder för webben, nedladdningstid och möjligheter med responsiva bilder samt allmänt kring bildbehandling för webben?
* Vilken är din TIL för detta kmom?






<!--
### Tekniker för att skriva för webben {#skriva}

1. Läs följande kapitel i guiden "[Skriva för webben](https://www.iis.se/lar-dig-mer/guider/hur-man-skriver-for-webben/)".

    * 6. Skriva texter för webben

-->




<!--
### Video  {#video}

Kika på följande video.

1. Moderskeppet är duktiga på foto och video, du kan hämta inspiration från deras fria youtube-kanal. Jag hittade att följande spellistor känns delvis relevanta för detta kursmoment.

    * [Guider om Foto](https://www.youtube.com/playlist?list=PL7jFK1saS1_Aexc_tx2wWClpQOShZkD2_)
    * [Inspiration för fotografer](https://www.youtube.com/playlist?list=PL7jFK1saS1_DGvKLYHOBb9HlCd_6id-vS)
    * [Bilder och upphovsrätt för designers](https://www.youtube.com/playlist?list=PL7jFK1saS1_DYHuwI_r5U7vVeY6RhZlIM)
-->

<!--
Titta på följande:

1. Till kursen finns en videoserie, "[Teknisk webbdesign och användbarhet](https://www.youtube.com/playlist?list=PLKtP9l5q3ce93K_FQtlmz2rcaR_BaKIET)", kika på de videor som börjar på 5.
-->




<!--
Installera LESS-modulen via npm https://www.npmjs.com/package/@desinax/figure.

Artikel om hjälpverktyg för bildhantering.
    * Var hittar jag fria bilder?
    * Bilder kan man köpa?

Artikel om att spara utrymme i img/-katalogen. (använd bash-skriptet för att testköra och installera några av postprocessingverktygen)

Bildlära, vad tänka på om bilder.

Fotolära, hur ta fotografier.

Image sprites.

jpeg (foton) kontra png (skärmdump)
color space
storlek på bilderna
kvalitet

-->

<!--
1. Integrera din webbplats så den drar nytta av [CImage](anax/cimage-for-bildskalning) och [snygga länkar](anax/snygga-lankar). Du behöver därefter inte ladda onödigt stora bilder i din webbplats. Använd shortcoden för FIGURE så blir din Markdown-kod snyggare och enklare att läsa.
-->

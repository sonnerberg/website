---
author: efo
category: javascript
revision:
  "2018-02-07": (A, efo) Första utgåvan inför kursen webapp v3.
...
Tabeller i mobila enheter
==================================

[FIGURE src=/image/webapp/table.png?w=c5 class="right"]

Tabeller används i stor utsträckning i affärssystem och andra administrationsgränssnitt. Ofta är dessa applikationer för desktop användare, men med tanke på i hur stor utsträckning mobila enheter används är det bra om tabeller även designas för små enheter. Det stora problemet med tabeller är ofta att det är mycket data på liten yta, som blir än mindre på en mobil enhet. Vi ska i denna övning titta på två sätt för att designa tabeller för mobila enheter.



En tabell att börja med {#tabell}
--------------------------------------
Vi börjar med nedanstående tabell och redan här i övningen ser vi problemet. Det finns inte tillräckligt mycket plats för att visa tabellen utan radbrytningar.

<table>
<thead>
<tr><th>Artikelnr.</th><th>Namn</th><th>Beskrivning</th><th>Lagersaldo</th><th>Lagerplats</th></tr>
</thead>
<tbody>
<tr><td>14-RNT</td><td>Skruv M14</td><td>Skruv M14, värmförsinkad</td><td>12</td><td>A1B4</td></tr>
<tr><td>12-RNT</td><td>Skruv M12</td><td>Skruv M12, värmförsinkad</td><td>14</td><td>A1B5</td></tr>
<tr><td>10-RNT</td><td>Skruv M10</td><td>Skruv M10, värmförsinkad</td><td>20</td><td>A1B6</td></tr>
<tr><td>08-RNT</td><td>Skruv M8</td><td>Skruv M8, värmförsinkad</td><td>2</td><td>A1B7</td></tr>
<tr><td>06-RNT</td><td>Skruv M6</td><td>Skruv M6, värmförsinkad</td><td>6</td><td>A1B8</td></tr>
<tr><td>14-TNT</td><td>Mutter M14</td><td>Mutter M14, värmförsinkad, passar 1214-RNT</td><td>13</td><td>A1C4</td></tr>
<tr><td>12-TNT</td><td>Mutter M12</td><td>Mutter M12, värmförsinkad, passar 1212-RNT</td><td>23</td><td>A1C4</td></tr>
<tr><td>10-TNT</td><td>Mutter M10</td><td>Mutter M10, värmförsinkad, passar 1210-RNT</td><td>12</td><td>A1C4</td></tr>
<tr><td>08-TNT</td><td>Mutter M8</td><td>Mutter M8, värmförsinkad, passar 1208-RNT</td><td>4</td><td>A1C4</td></tr>
<tr><td>06-TNT</td><td>Mutter M6</td><td>Mutter M6, värmförsinkad, passar 1206-RNT</td><td>1</td><td>A1C4</td></tr>
</tbody>
</table>

Om vi tittar på tabellen i mobilen ser vi ännu mindre av tabellen. Vi noterar även att det nu går att scrolla i sidled något vi vill försöka undvika på mobiler då det försvårar navigationen på sidan. Så målet för de två designs vi gör är inga radbrytningar och tabellen får inte vara bredare än skärmen på mobila enheter.

[FIGURE src=/image/webapp/screenshot-table-no-style.png?w=c7 caption="Tabellen i en mobil enhet."]



Avslutningsvis {#avslutning}
--------------------------------------

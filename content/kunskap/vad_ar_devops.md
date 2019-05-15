---
author: aar
revision:
  "2019-05-13": (A, aar) Första revisionen.
...

Vad är DevOps? För varje definition du kollar kommer du troligen få ett nytt svar. För många handlar DevOps om automation och olika verktyg men DevOps är större än så. I denna artikeln ska vi försöka gå igenom vad DevOps faktiskt innebär för dig som utvecklare och din organisation.



Vad är DevOps?
==========================

Enligt boken The DevOps Handbook är målet med DevOps är att skapa en arbetsmiljö där alla inom organisationen samarbetar, genom att skapa *cross-functional teams*, för att uppnå organisationens mål och ge värde åt kunderna. Utvecklare, produkt ägare, QA, IT och säkerhet ska jobba tillsammans för att göra det skapa ett snabbt flöde mellan planerat arbete och produktion. Flödet möjliggörs av QA, IT och säkerhets arbete för att skapa automatiserade verktyg och plattformar som utvecklarna kan använda för att snabbt och självständigt utveckla, testa och driftsätta sin kod. Samtidigt som de uppnår stability, reliability, availability och security. Allt detta är det tänkt ska göra att utvecklare öka produktivitet, möjliggöra organisatorisk lärande, skapa hög anställningsnöjdhet och gör att företaget vinner marknadsdelar.

The DevOps Handbook är skriver av fyra personer som var med och mynta DevOps och hjälpt det växa till vad det är idag. De beskriver DevOps som "a manifestation of creating a dynamic, learning organisation that continually reinforce high-trust cultural norms.". Detta uppnås genom att skapa koalitioner mellan alla inblandade i ett företag/projekt, Utvecklare, IT-operationer, produkt ägare, arkitekter och säkerhet.

Den rådande arbetssituationen hos de flesta företag beskrivs som att utvecklare och IT är motståndare och testning och säkerhet aktiviteter händer bara i slutet av projekt när det är för sent att ändra något. Dessutom tar kritiska aktiviteter kräver för mycket manuellt arbete och många överlämningar vilket leder till långa väntetider. Som i sin tur påverkar projektet negativt och leder till ett negativare värde för kunden och i slutändan organisationens mål.



Varför DevOps?
==========================

I bilden nedanför kan vi se hur mängden tid och krav som krävs för att driftsätta ny funktionalitet har minskat över de senaste fyra årtionden.

[FIGURE src=/img/devops/table.png caption="Trender inom software delivery. Källa: The DevOps Handbook"]

Branschen har gått från att företag behöver flera år och riskera att gå i konkurs när en ny funktionalitet ska introduceras till att företag kan göra det på ett par veckor. Men tack vare utvecklingen av molnet och virtuella maskiner och introduktionen av DevOps kan företag idag driftsätta ny funktionalitet fler hundra gånger om dagen. Företag kan snabbt och lätt sätta upp nya miljöer för att testa idéer och se vad som ger kunder och organisationen mest nytta. 

Dagens marknad är full av konkurrenter, det dyker upp nya startups varje dag som försöker utmana varandra med liknande tjänster. För att ha en chans att överleva denna marknaden krävs det av företag att de är snabba på att få ut och experimentera med ny funktionalitet. Företag som inte klarar av det löper stor risk att snabbt förlora marknadsvärde åt de snabba konkurrenterna.






Bygg upp om gemensama mål och hur företag fungerar nu och sen hur vi kan ösa det med devops?

# Myter {myter}

Boken The DevOps handbook skingrar ett antal myter kring DevOps.

- DevOps är bara för Start-up företag.

- DevOps ersätter Agile. Man kan se Agile en möjliggörare för DevOps och att DevOps är en logisk fortsättning på det agila arbetssättet i att uppnå högkvalitativ kod i små teams.

- DevOps är inkompatibel med säkerhet. Traditionellt sätt läggs ett stort fokus på säkerhet i slutet av ett projekt innan det skickas till slutkunden. Inom DevOps finns inte den slutperioden på samma sätt, istället ska säkerhetsaspekter vara inkorporerade i utvecklings cykeln. Precis som utveckling ska säkerhet jobbas med iterativt.

- DevOps eliminerar IT-operationer. Syftet med DevOps är inte att ersätta Ops, men det kan ändra hur man jobbar med Ops. Istället för att eliminera Ops så ska det få IT att samarbeta med utvecklarna och jobba på plattformen på liknande sätt som utvecklare jobbar på en produkt. Då plattformen är Ops produkt, som utvecklarna ska använda för att testa och driftsätta sina projekt på.

- DevOps är bara Infrastructure as Code och automatisering. Även om automatisering är en stor del av DevOps kräver det också en kulturell norm och arkitektur där delade mål kan uppnås från start till slut. Christopher Little skrev "DevOps isnät about automation, just as astronomy isn't about telescopes".



Patrick Debois mynta termen DevOps när han anordnade DevOpsDays första gången.

blue-green deployment
---
author: aar
revision:
    "2021-06-01": (A, aar) Första versionen.
...
Hur ber man om hjälp med kod i chatten?
==================================

Det händer ofta att koden vi skriver inte fungerar och vi kan inte komma på varför själva. Då är det bra att det finns ett community där vi kan be om hjälp, där kommer våra chatter in i bilden där lärare och andra studenter kan hjälpa oss. Här ska vi lära oss hur vi kan utforma vår fråga så att vi får svar så snabbt som möjligt.

<!--more-->

Jag rekommenderar att först läsa [Lärarstöd och handledning](kurser/faq/lararstod-och-handledning), där lär ni hur ni kan tänka om att ställa frågor. Här lär vi oss hur vi ställer dem.



# Sammanfattning

Innan ni ställer frågan är det bra om ni kan avgränsa var felet uppstår. Ta reda på i vilken fil, sen vilken funktion i filen och det bästa är om ni kan säga exakt vilken rad i filen felet finns på. Det är också bra om ni kan återskapa felet, vad gör ni som ger felet? Kortfattat vill vi veta, hur ser koden ut, vad händer, vad vill du ska hända och vad gör du när felet uppstår.

När ni faktiskt ber om hjälp formulera en fråga istället för att skriva "Hej min kod funkar inte". Då vet vi inte hur vi ska hjälpa dig och måste be dig skicka med de sakerna som det står om här. För tips om hur ni formulerar frågan, kollan in när [Mikael pratar med sin gummi anka](https://dbwebb.se/kurser/faq/lararstod-och-handledning#anka).

Oroa dig inte om att verka dum eller dålig. De lättaste felen är ofta svårast att hitta. Till säkert 30% av frågorna vi får är svaret "ni saknar en avslutande parentes". Det händer alla programmerare och är inte något man behöver skämmas för. 



# Vilken information bör en frågan innehålla?

Inkludera er kod, men ta inte med **all** fungerande kod. Majoriteten av koden är oftast inte intressant för frågan. Försök avgränsa mängden kod ni visar till bara det som är relevant till felet. Oftast borde det inte vara mycket mer än 5 rader. Det är också en bra övning för er om ni kan avgränsa felet till specifika rader. 

Inkluder resultatet/utskriften av ditt program när det går fel. Det går oftast att utläsa från utskriften vad som gått fel och då underlättar det om det redan är med i frågan. Vi kan också förklara hur ni ska tolka resultatet för att förstå vad som gick fel.

Inkludera radnummer i koden. Det är lättare att prata om kod om vi kan säga "på rad 38...", istället för "på raden som börjar börjar med if something_is_true".

Inkludera uppgiften ni försöker lösa. Vi har många uppgifter i kursen och vi kommer inte alltid ihåg exakt vad som ska göras (speciellt i labbuppgifterna). Det underlättar om vi kan läsa er kod i samband med vad den ska uppnå.



### Exempel

I frågan försöker jag vara tydlig med vad jag gör och vad jag vill ha hjälp med. Jag skickar också med bilden nedanför så att de kan se min kod, felet och exakt vad som är uppgiften.

> Jag försöker lösa uppgift 1.2 i lab1 men mitt program kraschar när jag kör det. Jag försöker addera 100 med variabeln från uppgift 1.1 men programmet kraschar när jag kör det och jag förstår inte felmeddelandet jag får i terminalen, kan någon hjälpa mig förstå felmeddelandet?


[FIGURE src=image/hjalp.png caption="Exempel på screenshot med ett fel."]

Notera att jag också har strökigt under det viktiga i terminalen för attt jag hade gjort irrelevanta saker tidigare i terminalen som den som hjälper mig inte behöver titta på.

På den frågan hade svarit kunnat se ut på följande sätt.

> Felet säger att du inte kan addera ett heltal med en sträng. I uppgiften står det att du ska använda heltalet 100. Men på rad 78 tilldelar du 100 som en sträng.



# Hjälpmedel

Här har vi tips på olika verktyg som är bra när man jobbar med kod och vill dela med sig eller fråga om hjälp.
Inkludera en screenshot. Det är ett lätt sätt för oss att se samma sak som ni ser. På Windows 10 kan ni använda `windows-shift-s` för att klippa ut en del av skärmen.
Ibland är det bra att se all kod

- Formatera text som kod i chatten. Discord stödjer [Markdown](https://guides.github.com/features/mastering-markdown/), med det kan vi styla texten på olika sätt. Vi kan t.ex. använda **\`\`\`** för att omsluta delar i en text för att det ska formateras som kod. 

    Exempel, överst i bilden ser vi koden som vanlig text. I nedre halvan har jag omslötit koden med **\`\`\`** före och efter. Ni kan göra det mitt i en text så är det bara det innanför som blir formaterat som kod.
    
[FIGURE src=image/formatering.png caption="Exempel formaterad text i discord."]

Använd det när ni delar kod i chatten och inte använder er av screenshots.

- [codeshare](https://codeshare.io/), ett verktyg för att dela och sammarbeta med kod. Är bra om man behöver visa en större mängd kod när man om hjälp.
- [gist](https://gist.github.com/), påminner om codeshare fast är mer statiskt. Detta är med för att visa upp kod.
- Valfritt program för att ta screenshots. 
    - Windows har bra inbyggt med `windowsknapp+shift+s`. 
    - På Mac kan ni använda `Shift+Command+4`.
    - För linux funkar `PrtSc` knappen bra.
- Använd paint liknande program för att rita på bilden.

Här kan ni se när Kenneth använder både Codeshare och gist för att fråga om hjälp. Notera att han ställer frågan i vår gamla Gitter chat. Den används inte längre utan nu är det Discord som gäller.

[YOUTUBE src=lrVtvqlhWjY caption="Kenneth visar hur man delar med sig av kod med codeshare och github.]

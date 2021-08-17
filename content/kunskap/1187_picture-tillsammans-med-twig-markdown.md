---
author: nik
category:
    - bilder
revision:
    "2021-08-17": (A, nik) Uppdaterad med version 2 efter feedback.
...
Picture-elementet tillsammans med Twig och Markdown {#intro}
=====================================

Vi har nu gått igenom hur man jobbar med cimage samt hur man kan ladda in rätt bilder med hjälp utav `<picture>` och `srcset`. Låt oss kombinera den kunskapen och kolla på hur man kan länka mobilanpassade bilder både i Markdown och Twig

<!--more-->

Förutsättningar {#forutsattningar}
-------------------------------------

Du har arbetat igenom följande artiklar:

* "[Cimage, hur fungerar det?](kunskap/cimage-hur-fungerar-det)"
* "[Hur kan vi göra bilder och video responsivt](kunskap/hur-kan-vi-gora-det-responsivt)"

Twig {#twig}
-------------------------------------

I Twig kan vi skriva vanlig HTML, så där är det relativt simpelt att länka våra bilder. Jag utgår ifrån en bild, `sheep.jpg` som har sökvägen `portfolio/assets/img/sheep.jpg`. Jag väljer att wrap:a min bild med en länk till originalet, så om man vill se bilden i sin rätta storlek är det bara trycka på den. I exemplet så nöjer jag mig med två storlekar, en för små enheter och en för stora enheter.

```html
<a href="{{ base_url }}/image/sheep.jpg" target="_blank">
    <picture>
        <source media="(min-width: 668px)" srcset="{{ base_url }}/image/sheep.jpg">
        <img src="{{ base_url }}/image/sheep.jpg&w=667" alt="A sheep">
    </picture>
</a>
```

Vi kombinerar helt enkelt `{{ base_url}}` som pekar på rooten av Pico-ramverket (i vårt fall `me/portfolio`). Sen lägger vi till sökvägen `/image` som i vår `.htaccess` pekar oss till cimage. Därefter säger vi vilken bild vi vill använda, `sheep.jpg` och de parametrar vi vill skicka med till cimage, t.ex. `&w=667`.

Markdown {#markdown}
-------------------------------------

I Markdown ser det snarlikt ut, bara att vi behöver uppdatera vår `{{ base_url }}` till `%base_url%` så länken fungerar som det ska, ungefär såhär:

```html
<a href="%base_url%/image/sheep.jpg" target="_blank">
    <picture>
        <source media="(min-width: 668px)" srcset="%base_url%/image/sheep.jpg">
        <img src="%base_url%/image/sheep.jpg&w=667" alt="A sheep">
    </picture>
</a>
```

Avsluningsvis  {#avslutningsvis}
-------------------------------------

Nu bör ni kunna utnyttja cimage och `<picture>` oavsett var ni väljer att arbeta med era bilder. Om det är några frågor eller om något är oklart, tveka inte att hojta till i Discord så kollar vi på det. Annars lycka till och kör på!

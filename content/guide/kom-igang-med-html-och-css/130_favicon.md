---
author: lew
revision:
    "2018-06-13": "(A, lew) Första versionen."
...
Favicon {#favicon}
=======================

En webbplats kan ha en *favicon*, en liten bild som visas tillsammans med webbplatsen uppe i webbläsarens flik.

Det är något vi kan lägga till i sidas `<head>`-del med följande konstruktion.

```html
    <link rel='shortcut icon' href='img/favicon.png'/>
</head>
```

Sedan laddar du om och kan se ikonen, *faviconen*, i webbläsarens flik.

[FIGURE src=/image/htmlphp/guide/murphy/show-favicon.png?w=w2 caption="En favicon!."]

Formatet för en favicon är från början filformatet ICO, men de flesta webbläsare klarar även vanliga PNG-bilder. Ett tips är att inte ladda in en för stor bild, då den ändå kommer förminskas. Ett bra mått är 32x32px.

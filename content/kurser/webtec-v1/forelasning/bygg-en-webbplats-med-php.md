---
author: mos
revision:
    "2021-09-17": "(A, mos) Första utgåva inför kursstart HT2021."
...
Bygg en webbplats med PHP
====================

Visa hur du kommer igång med uppgiften 'Bygg en webbplats med PHP' samt förklara bakomliggande begrepp kring den kodbas vi jobbar med.

Genomgången sker i en tisdags zoom.

Genomgången/föreläsningen är i fem delar.

Föreläsningarna bygger på koden som finns i exempelrepot under [`example/php/pagecontroller/step*`](https://github.com/dbwebb-se/webtec/tree/main/example/php/pagecontroller). Exempelkoden är uppdelad i step1 - step9 och varje step har en förklarande text i README.md.

Första delen ger bakgrunden till hur PHP används i webbplatser via exempelkoden step1 (och step2).

Del 1 är 46 minuter lång.

[YOUTUBE src="2R_bIZBae0g" width=700 caption="Kom igång och lös uppgiften 'Bygg en webbplats med PHP', del I/V (Tisdags-Zoom, vecka 2, 10-11)"]

Andra delen hanterar step2 (sammanfattning) och step3, step4 och step5 som ger en grundstruktur och konceptet om vyer.

Del 2 är 48 minuter lång.

[YOUTUBE src="V6wVglmO2iA" width=700 caption="Kom igång och lös uppgiften 'Bygg en webbplats med PHP', del II/V (Tisdags-Zoom, vecka 2, 11-12)"]

Tredje delen inleds med step7 som hanterar content i separata filer och fortsätter sedan med step8 som hanterar HTML formulär med GET och POST.

Del 3 är 42 minuter lång.

[YOUTUBE src="rl1L8vaNYEs" width=700 caption="Kom igång och lös uppgiften 'Bygg en webbplats med PHP', del III/V (Tisdags-Zoom, vecka 2, 13-14)"]

Fjärde delen hanterar step9 med cookies och sessioner samt processingsidor.

Del 4 är 22 minuter lång.

[YOUTUBE src="a_0UWHfU_AM" width=700 caption="Kom igång och lös uppgiften 'Bygg en webbplats med PHP', del IV/V (Tisdags-Zoom, vecka 2, 14-14:30)"]

Femte delen hanterar uppgiften och hur man kommer igång med den.

Del 5 är 40 minuter lång.

[YOUTUBE src="Z-8xl1KcmHI" width=700 caption="Kom igång och lös uppgiften 'Bygg en webbplats med PHP', del II/V (Tisdags-Zoom, vecka 2, 11-12)"]



Resurser
------------------------

Som underlag till föreläsningen används bland annat exempelprogramm som finns i kursrepot.

1. `example/php/pagecontroller-exercise` som är grunden för uppgiften.
1. `example/php/pagecontroller` som visar steg för steg hur man bygger upp kodstrukturen.

Pakethantering

* [Composer](https://getcomposer.org/) och [Packagist](https://packagist.org/)

Koncept och strukturer

* Sidkontroller
    * Design pattern for [Page Controller](https://martinfowler.com/eaaCatalog/pageController.html) by Martin Fowler
* Vyer
    * [Understanding MVC Views in PHP](https://stackoverflow.com/a/16596704/341137)

Design princip

* [Separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)
* [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
* [KISS principle](https://en.wikipedia.org/wiki/KISS_principle)

Webbteknologier

* HTML formulär
    * [MDN on form](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
* [GET](https://www.php.net/manual/en/reserved.variables.get.php)
* [POST](https://www.php.net/manual/en/reserved.variables.post.php)
* [SESSION](https://www.php.net/manual/en/reserved.variables.session.php)
* [COOKIE](https://www.php.net/manual/en/reserved.variables.cookies.php)

Validatorer

* [phpcs](https://github.com/squizlabs/PHP_CodeSniffer/wiki)
* [phpmd](https://phpmd.org/)
* [phpstan](https://phpstan.org/)
    * [PHPStan: Find Bugs In Your Code Without Writing Tests!](https://phpstan.org/blog/find-bugs-in-your-code-without-writing-tests)
* [psalm](https://psalm.dev/)

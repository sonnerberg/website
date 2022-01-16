---
author: mos
revision:
    "2021-12-21": "(E, mos) Bort med referens till forum och ändra från MySQL till MariaDB och workbench i egen artikel samt flytta Windows terminaler till egna artiklar."
    "2019-01-09": "(C, mos) Lade till Docker."
    "2019-01-08": "(B, mos) Delade in artikeln i delar, beroende på operativsystem."
    "2018-03-20": "(A, mos) Uppdelad från ett större dokument."
...
MariaDB Server och MySQL Workbench
==================================

Du vill installera databasen MariaDB tillsammans med desktopklienten MySQL Workbench och terminalklienten.



Installation {#installation}
----------------------------------

1. Välj rätt artikel beroende på vilket operativsystem du använder.

* [Installera MariaDB Server på Windows 10](kunskap/installera-mariadb-server-pa-windows-10)
* [Installera MariaDB Server på macOS](kunskap/installera-mariadb-server-pa-macos)
* [Installera MariaDB Server på Linux](kunskap/installera-mariadb-server-pa-linux)

Om du jobbar på Windows så vill du troligen även jobba igenom den av följande artiklar som hanterar den terminalen du vill jobba i. Det kan förenkla och spara dig tid i kursen.

* [MariaDB klient och Windows med cmd terminalen](coachen/mariadb-och-windows-cmd-terminal)
* [MariaDB klient och Windows med cygwin terminalen](coachen/mariadb-och-windows-cygwin-terminal)
* [MariaDB klient och Windows med WSL2 bash terminal](coachen/mariadb-och-windows-wsl2-bash-terminal)

2\. Du kan nu gå vidare och [installera MySQL WorkBench](kunskap/installera-mysql-workbench).

3\. Ett tips till dig som vill slippa skriva användare, lösenord och eventuellt hostnamnet är att skapa din egen konfigurationsfil `.my.cnf`, i artikeln "[MariaDB klienten och filen .my.cnf](coachen/mariadb-klient-och-my-cnf)" får du se hur man gör det.



Använd MySQL/MariaDB via Docker {#docker}
----------------------------------

För den som är väl bekant med Docker kan det vara ett kompletterande möjlighet att köra databasservern som en docker kontainer. Du kan se hur man sätter upp grunderna i artikeln "[Kör MySQL Server och MySQL WorkBench via Docker](kunskap/kor-mysql-server-och-mysql-workbench-via-docker)".

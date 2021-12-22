---
author: mos
revision:
    "2021-12-20": "(C, mos) Omskriven inför v2 och MariaDB."
    "2019-01-24": "(B, mos) Bort med överflödigt ;."
    "2019-01-21": "(A, mos) Första versionen."
...
Skapa en root användare
==================================

Vi skall skapa en ny användare i databasen, en användare som har samma behörighet som root användaren.

Spara SQL-koden du gör i en fil och döp den till `create-user-dbadm.sql`.



Skapa en ny användare {#createuser}
--------------------------------------

Dokumentationen för att skapa en ny användare finns i [CREATE USER](https://mariadb.com/kb/en/create-user/).

Öppna terminalklienten och skriv följande SQL-kod för att skapa en användare.

```text
CREATE USER 'dbadm'@'localhost'
IDENTIFIED BY 'P@ssw0rd!'
;
```

Ge användaren fullständiga rättigheter på alla databaser `*.*`, det blir i princip samma rättigheter som en root-användare som har tillgång till allt.

```text
GRANT ALL PRIVILEGES
ON *.* TO 'dbadm'@'localhost'
WITH GRANT OPTION
;
```

Kommandot [`GRANT` finns beskrivet i manualen](https://mariadb.com/kb/en/grant/).

Bra, då har vi en användare som har fulla rättigheter i databasservern.



Använd den nya användaren {#useuser}
--------------------------------------

Nu kan vi använda den nya användaren. Pröva att göra det i terminalklienten. Logga in i terminalklienten med din nyskapade användare.

```text
mariadb -u dbadm
```

Det kan se ut så här när du kollar vilken användare du är inloggad med.

```text
MariaDB [(none)]> SELECT USER();
+-----------------+
| USER()          |
+-----------------+
| dbadm@localhost |
+-----------------+
```



Ta bort en användare {#dropuser}
--------------------------------------

Om du behöver ta bort användaren och skapa den igen så kan du droppa (ta bort) den så här.

Kommandot [`DROP USER` finns beskrivet i manualen](https://mariadb.com/kb/en/drop-user/).

```text
MariaDB [(none)]> DROP USER IF EXISTS 'dbadm'@'localhost';
Query OK, 0 rows affected (0.000 sec)
```



Status på en användare {#statususer}
--------------------------------------

Innan du går vidare kan du kontrollera att din nya användare `dbadm` har rätt rättigheter. Det bör se ut så här när du tittar på rättigheterna för användaren dbadm.

```text
MariaDB [(none)]> SELECT
    ->     User,
    ->     Host,
    ->     Grant_priv,
    ->     Super_priv,
    ->     Trigger_priv,
    ->     plugin
    -> FROM mysql.user
    -> WHERE
    ->     User IN ('dbadm')
    -> ORDER BY User
    -> ;
+-------+-----------+------------+------------+--------------+--------+  
| User  | Host      | Grant_priv | Super_priv | Trigger_priv | plugin |  
+-------+-----------+------------+------------+--------------+--------+  
| dbadm | localhost | Y          | Y          | Y            |        |  
+-------+-----------+------------+------------+--------------+--------+  
```

Du kan se hur det ser ut hos dig genom att köra följande SQL-kod i din terminal.

```text
SELECT
    User,
    Host,
    Grant_priv,
    Super_priv,
    Trigger_priv,
    plugin
FROM mysql.user
WHERE
    User IN ('dbadm')
ORDER BY User
;
```

Nu har du konfigurerat upp en första användare i din databasserver, det är ett bra första steg.



Kontrollera ditt skript {#skript}
--------------------------------------

Dubbelkolla att du har skrivit in alla SQL-kommandon i ditt skript. Detta är viktigt om du senare behöver återställa din databas.



Problem och facit? {#problem}
--------------------------------------

Om du får problem så finns det ett par skript som du kan köra för att skapa rätt användare.

```text
# Stå i rooten av ditt kursrepo
mariadb < example/sql/v2/check-users.sql
```

Du kan även studera skriptet `example/sql/v2/create-user-dbadm.sql`.

Du kan titta i de skripten och använda informationen för att skapa ditt egna skript.

---
author: mos
revision:
    "2018-01-02": "(A, mos) Första versionen, uppdelad av större dokument."
...
Skapa fler tabeller
==================================

En skola har kurser som ges vid olika kurstillfällen. På varje kurstillfälle finns det en lärare som är kursansvarig.

Låt oss skapa tabellerna för kurs och kurstillfalle.

Spara den SQL-kod du skriver i filen `ddl_more_tables.sql`.



Tabell för kurs {#kurs}
----------------------------------

Låt oss börja med att skapa tabellen för kurs.

| Kolumn    | Datatyp                      |
|-----------|------------------------------|
| kod       | CHAR(6) PRIMARY KEY NOT NULL |
| namn      | VARCHAR(40)                  |
| poang     | FLOAT                        |

Skriv SQL-koden för att skapa tabellen.



Tabell för kurstillfalle {#kurstillfalle}
----------------------------------

Vi fortsätter att skapa tabellen kurstillfalle.

| Kolumn                      | Datatyp                                 |
|-----------------------------|-----------------------------------------|
| id                          | INT AUTO_INCREMENT PRIMARY KEY NOT NULL |
| kurskod                     | CHAR(6) NOT NULL                        |
| kursansvarig                | CHAR(3) NOT NULL                        |
| lasperiod                   | INT NOT NULL                            |

Skapa ovanstående tabeller med SQL. Leta i refmanualen om något är oklart, till exempel så vill du kanske slå upp `AUTO_INCREMENT` som ger en automatgenererad nyckel.



Främmande nycklar {#frammande}
----------------------------------

En främmande nyckel är ett sätt att länka samman tabellerna. I vårt fall är kursansvarig en främmande nyckel i tabellen kurstillfälle som kan länka ett kurstillfälle till detaljerna om den kursansvarige läraren.

På samma sätt är kurskod i kurstillfälle en främmande nyckel som länkar kurstillfället till en specifik kurs.

Det är bra att ange främmande nycklar i tabellerna. Det förtydligar att det finns en *constraint*, en begränsning eller integritet, i din databas.

Den SQL-kod som behövs kan se ut ungefär så här:

```sql
--
-- Create table: kurstillfalle
--
DROP TABLE IF EXISTS kurstillfalle;
CREATE TABLE kurstillfalle
(
    -- All columns and their definitions

    PRIMARY KEY (id),
    FOREIGN KEY (kurskod) REFERENCES kurs(kod),
    FOREIGN KEY (kursansvarig) REFERENCES larare(akronym)
);
```

Uppdatera hur du skapar tabellen så att du anger främmande nycklar som en constraint, ett integritetsvillkor.



Testa villkoret för foreign key {#testfk}
----------------------------------

För att testa hur databasen hanterar integritetsvillkoret så skapar du de båda tabellerna. Sedan försöker du droppa tabellen kurs.

Du får troligen ett sådant här meddelande.

> "Error Code: 1217. Cannot delete or update a parent row: a foreign key constraint fails"

Det säger att du inte kan droppa tabellen kurs eftersom tabellen kurstillfalle är beroende av den via ett foreign key constraint.

Om du vill droppa samtliga tabeller så behöver du göra det i rätt ordning. Ofta är det bra att lägga dessa DROP i inledningen av den fil som skapar/droppar tabellerna.

Så här droppar du tabellerna i rätt ordning.

```sql
-- Drop tables in order to avoid FK constraint
DROP TABLE IF EXISTS kurstillfalle;
DROP TABLE IF EXISTS kurs;
```

Uppdatera så att din fil kan köra alla SQL-kommandon i sekvens.



Storage engines {#storage}
----------------------------------

I MySQL finns det olika lagringssätt för tabeller, så kallade "storage engines". De säger hur tabellerna lagras och styr vilka algoritmer som gäller för sökning i tabellerna. De vanligaste är MyISAM och InnoDB.

MyISAM tar inte hänsyn till den integritetskoll som 'FOREIGN KEY' antyder. Det gör dock InnoDB.

Man anger vilket lagringssätt som skall användas när man skapar tabellen, om man inte anger det så används det som är standard för databasen eller för installationen av databasmotorn. Vilken lagringsmotor som är standard kan skilja mellan installation så det är alltid bäst att ange den för att vara säker. Läs kort om [MySQL och Storage Engines](http://dev.mysql.com/doc/refman/5.7/en/storage-engines.html).

```sql
--
-- Ange vilket sätt som tabellerna skall lagras på
--
CREATE TABLE t1 (i INT) ENGINE MYISAM;
CREATE TABLE t2 (i INT) ENGINE INNODB;
```

Vi använder INNODB som är den senaste versionen av storage engines och normalt är den standard vid nyinstallationer.

Uppdatera din fil så att du explicit anger INNODB som storage engine.



Specificera teckenkodning {#ddlcharset}
----------------------------------

Uppdatera hur du skapar tabellerna och ange explicit charset till `utf8` och collation till `utf8_swedish_ci` för hela tabellerna.

Du kan ange charset och collation i slutet av dina CREATE statement.

```sql
--
-- Ange teckenkodning för en tabell
--
CREATE TABLE t1 (i INT) CHARSET utf8 COLLATE utf8_swedish_ci;
CREATE TABLE t2 (
    i INT
)
ENGINE INNODB
CHARSET utf8
COLLATE utf8_swedish_ci
;
```

Lägg även denna konstruktion överst i filen.

```sql
SET NAMES 'utf8';
```



Foreign key mellan tabeller {#fklink}
----------------------------------

Om du nu kör alla kommandona i din fil så får du troligen ett fel som säger att du inte kan skapa en foreign key från tabellen kurstillfälle till tabellen lärare.

Felmeddelandet kan se ut så här när du försöker göra CREATE TABLE kurstillfalle.

> "Error Code: 1215. Cannot add foreign key constraint"

Anledningen är att tabellen larare inte är skapad på samma sätt, mer specifikt så innehåller tabellen inte en definition på charset och collation som stämmer överens med den som finns i kurstillfälle. Av den anledningen går det inte länka tabellerna med ett foreign key constraint.

För att lösa detta så uppdaterar vi tabellen lärare och sätter samma charset och collation på den.

```sql
--
-- Update table larare to use same charset and collation.
--
ALTER TABLE larare CONVERT TO CHARSET utf8 COLLATE utf8_swedish_ci;
```

Nu går det åter att skapa ett foreign key constraint mellan tabellerna.



Visa SQL-koden för CREATE TABLE {#showcreate}
----------------------------------

Du kan visa hur en tabell är skapad med kommandot SHOW CREATE TABLE. Det ger dig detaljer för tabellen.

Så här ser det nu ut.

```sql
mysql> SHOW CREATE TABLE kurs \G;
*************************** 1. row ***************************
       Table: kurs
Create Table: CREATE TABLE `kurs` (
  `kod` char(6) COLLATE utf8_swedish_ci NOT NULL,
  `namn` varchar(40) COLLATE utf8_swedish_ci DEFAULT NULL,
  `poang` float DEFAULT NULL,
  PRIMARY KEY (`kod`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_swedish_ci
1 row in set (0.00 sec)
```

Jag använder `\G` för att låta MySQL skriva ut resultatet rad för rad, istället för den vanliga med kolumn för kolumn.

```sql
mysql> SHOW CREATE TABLE kurstillfalle \G;
*************************** 1. row ***************************
       Table: kurstillfalle
Create Table: CREATE TABLE `kurstillfalle` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `kurskod` char(6) COLLATE utf8_swedish_ci NOT NULL,
  `kursansvarig` char(3) COLLATE utf8_swedish_ci NOT NULL,
  `lasperiod` int(11) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `kurskod` (`kurskod`),
  KEY `kursansvarig` (`kursansvarig`),
  CONSTRAINT `kurstillfalle_ibfk_1` FOREIGN KEY (`kurskod`) REFERENCES `kurs` (`kod`),
  CONSTRAINT `kurstillfalle_ibfk_2` FOREIGN KEY (`kursansvarig`) REFERENCES `larare` (`akronym`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_swedish_ci
1 row in set (0.00 sec)
```

Kommandot SHOW TABLE är bra när man inspekterar en databas, när man vill se hur tabellerna är uppbyggda.



Kontrollera setup.bash {#setupkontr}
----------------------------------

Låt oss nu kontrollera att det går att återskapa databasen med bash-skriptet.

Det är dock troligt att du råkar på följande fel i filen `ddl.sql`.

> "ERROR 1217 (23000) at line 10: Cannot delete or update a parent row: a foreign key constraint fails"

Det handlar om i vilken ordning som tabellerna droppas. Du löser det genom att droppa alla tabeller överst i `ddl.sql`.



Kontrollera filen {#filen}
----------------------------------

Innan du är helt klar så kontrollerar du att du kan köra samtliga SQL-satser, i en och samma sekvens, i filen du jobbar i.

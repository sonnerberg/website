---
author: mos
category:
    - databas
    - mysql
revision:
    "2021-12-21": "(A, mos) Flyttat till eget dokument."
...
MariaDB klienten och filen .my.cnf
==================================

Vi sätter upp en miljö där vi använder konfigurationsfilen `.my.cnf` för att förenkla och slippa skriva långa kommandon när vi startar terminalklienten för databasen MariaDB.

<!--more-->



Förberedelse {#prep}
--------------------------------------

Du har installerat databasen MariaDB och du kan koppla upp dig mot den med en terminalklient.

Du kan hantera terminalen och navigera i din hemmakatalog.



Läs på om .my.cnf {#mycnf}
--------------------------------------

Du kan läsa om hur det fungerar i artikeln "[Configuring MariaDB with Option Files](https://mariadb.com/kb/en/configuring-mariadb-with-option-files/)".



Ett exempel på filen .my.cnf {#exempel}
--------------------------------------

Med tanke på hur vi installerar databasen MariaDB i kursen databas så kan följande exempel fungera som en mall för filen `.my.cnf`.

```text
# Template config file for databas-v2

[client]
user=dbadm
password=P@ssw0rd

# host for cygwin
#host=127.0.0.1

# host for WSL2 bash, change <hostname> to its real value
#host=<hostname>.local

#port=3306
#protocol=tcp

# To allow for using LOAD DATA INFILE
loose-local-infile = 1
```

Du behöver eventuellt anpassa filen till ditt system. Du kan också ha en sådan här fil i varje terminal du använder.



Spara filen .my.cnf {#spara}
--------------------------------------

Normalt sett kan du placera file `.my.cnf` i din hemmakatalog i den terminal du använder.

I alla bash-terminal (Linux, macOS, Cygwin, WSL2 bash) innebär det att du skall placera filen i `$HOME/.my.cnf`.

I windows cmd terminal kan du placera filen som `C:\my.ini`.

Du kan kontrollera att du lagt filen på rätt plats så här.

```text
# For all bash terminals
ls -l $HOME/.my.cnf
cat $HOME/.my.cnf
```

Du bör också sätta rättigheterna på filen till 600 vilket innebär att bara du kan läsa filen.

```text
chmod 600 $HOME/.my.cnf
```

Om du får felmeddelande som påpekar att konfigurationsfilens rättigheter är alltför vidlyftiga, så löser du det genom att ändra filens rättigheter.

Felmeddelandet kan säga följande.

> "mysql: [Warning] World-writable config file '/home/mos/.my.cnf' is ignored."



Testa om konfigurationsfilen används {#test}
--------------------------------------

Du kan alltid kontrollera var din terminalklient letar efter konfigurationsfilern genom att skriva följande kommando.

```text
mariadb --help --verbose
```

I inledningen av texten som skrivs ut kan du läsa något i stil med följande.

```text
Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf ~/.my.cnf

The following groups are read:
mysql client client-server client-mariadb
```

Det är detaljer om hur klienten läser konfigurationsfilerna, i vilken ordning och vilka grupper som läses.

Du kan också testa och se exakt vilka detaljer från konfigurationsfilen som används.

Det kan till exempel se ut så här med en konfigurationsfil som enbart anger user och password.

```text
$ mariadb --print-defaults
mariadb would have been started with the following arguments:
--user=dbadm --password=P@ssw0rd!
```


Avslutningsvis {#avslut}
--------------------------------------

Nu skall det fungera. Denna konfigurationsfilen är bra att ha och jobbar man mycket med terminalprogrammen så kan det underlätta att spara viss konfigurationsinformation i filen.

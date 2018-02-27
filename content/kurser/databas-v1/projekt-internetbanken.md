---
author: mos
revision:
    "2018-02-27": "(B, mos) Uppdaterad inför vt18."
    "2017-02-23": "(A, mos) Kopierad från GoogleDocs och översatt till svenska samt aningen modifierad."
...
Projekt: Internetbanken
==================================

Du är en senior konsult på företaget "HögProfilKonsultMedSlips". Du har tilldelats en uppgift att utveckla en Internetbank till den svenska kunden, "BankBluffOBåg AB".

Du har resultatet från en förstudie som en kollega har förberett, det ger dig basen till en ER modell.

Du har kraven på systemet och de klienter du skall implementera.

Din uppgift är nu att implementera, leverera och dokumentera Internetbanken (IB).

Lycka till!

<!--
excel, csv för input och sätta upp tabellerna.
csv output till excel för att visa resultat (admin-delen)
backup av databasen?

Visa hur projektet testas?

Visa senaste transaktioner (bra testa).
-->



Pre study {#studie}
--------------------------------------------------------------------

This is the pre study made on IB.



### Account and account holders {#account}

The IB shall provide bank accounts for customers (account holders). An account holder can have several accounts. Each account can be shared between two or more account holders.

The bank cashier creates new accounts and new account holders. An account can be shared between account holder(s). The cashier can enable for several account holders to share one account.

Information on an account holder is name, birth date, street and city of residence. A userid is created for each account holder. This is to be used for access verification. A 4-digit pincode shall also be created for each userid.

Information related to an account is the balance and the account number.



### Account holder access {#holder}

The account holder can access their accounts by a web interface. They shall be able to list their accounts with the balance. It shall be visible if the account is shared with another account holder.

The account holder can move money between their own accounts. Each time they move money they need to pay 3% of the moved amount to your own special and secret account. You wish to get money for a house in a sunny foreign country.



### Swishing the money {#swish}

The account holders can use their accounts through a mobile application where they can swish money to another account. Swishing is done by, using the swish application, inserting the userid and a 4-digit pincode followed by the account number, the amount to swish and the receiving account number. The pincode is private for each account holder.

Each time a swish is done, a fee of 2% of the swished amount should be taken and stored in your special and secret account. See this as your insurance for days to come; perhaps a nice lodge in sunny Spain can come out of this.



### Calculating interest {#calculate}

The calculation of interest is done on a daily basis. It is performed manually by executing a stored procedure that calculates the interest for each account. The procedure takes the following arguments; interestRate, dateOfCalculation. The interest is calculated by `interestRate * accountBalance / 365`.

The result shall be stored in a separate table with the values of the calculated interest, date for calculation, and account number.

The yearly accumulated interest for a specific account can be calculated by summing all entries, for the specific account.



### Logging {#log}

A log entry shall be written to a log table each time the balance is updated for an account. The entry should consist of the account number, current balance, amount changed and time.



### Secret account {#secret}

The secret account is an ordinary account. The fees stored in the secret account is taken from the existing money, you can not produce more money than the bank has.





Requirements on Applications {#reqs}
--------------------------------------------------------------------

You shall develop supprto for the following end user applications:

* Cashier administration
* Swish application
* Account holder
* Management reports



### Cashier administration {#cashier}

The following tasks shall be supported:

* Add an account holder.
* Add a new account and connect it to an account holder.
* Connect an additional account holder to an existing account.
* Show all account holders with their accounts and balance.
* Show all accounts together with the the accumulated interest for each account.

Implement the application as a CLI program or a web interface.



### Swish application {#swish}

The following task shall be supported:

* Swish money by inserting userid, pincode, sending account, receiving account and amount.

Implement the application as a CLI program or a web interface.



### Account holder {#webint}

The following tasks/reports shall be supported:

* Show all accounts for an account holder.
* Make it visible if the account is shared with other account holders (show their names).
* Move money between their own accounts.
* Show the accumulated interest for each account.

Implement the application as a CLI program or a web interface.



### Management reports {#reportsint}

The following reports should be supported:

* Show the sum of the balance of all accounts, including the secret account.
* Present all entries in the log table.
* Show the content of your own special account where all transaction fees goes. (This one is for the nice lodge in sunny Spain).

Implement the application as a CLI program or a web interface or as plain stored procedures.



### Additional reports {#morereports}

The following tasks shall be supported using SQL stored procedures.

* Perform the calculation of interests for a specific day on all accounts.
* Show the accumulated interest for all accounts on a specific day.
* Show the accumulated interest for all accounts on a specific year.

Implement the application as a CLI program or a web interface or as plain stored procedures.



### Other {#other}

Try to build a good structure of your database and provide a good API for the database reports through procedures, functions, triggers and views.

Ensure that your reports/tasks works in the database before you try to integrate them with the various GUIs.



Requirements on presenting the project {#redovisning}
--------------------------------------------------------------------



### The database {#db}

The database must contain at least the following data:

* At least 7 account holders and at least 15 accounts.
* At least 3 account holders shall share 3 or more accounts.
* The accounts should contain some money.
* You should have made calculation of interest for at least 2 different dates.



### The documentation {#docs}

The documentation should be proper, nice-looking and complete.

Document the database in line with the intentions of "[Kokbok för databasmodellering](kunskap/kokbok-for-databasmodellering)".

Document your applications.

* Describe the intention of each application.
* Shortly describe how to work with the application.
* Some screenshot could enhance the documentation.

Make it look nice.

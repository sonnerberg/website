---
author: lew
revision:
    "": "(A, lew) Första versionen."
...
Logiska operatorer
=======================

Innan vi går vidare och tittar på hur vi jobbar med de så kallade logiska operatorerna har vi olika sätt att hantera dem. Nu för tiden behöver vi inte vara lika bakåtkompatibla som tidigare. I alla fall inte i den här kursen.

### Det "gamla" sättet {#gamla}

Med enkel hakparantes (single square bracket, [ ]) använder vi samma metoder som återfinns i det inbyggda kommandot *test*. Man kan säga att de är synonymer. Tips: `$ man test`.

```bash
#!/usr/bin/env bash
#
# An example script with the old, backwards compatible way

val1=5
val2=3

if [ "$val1" -gt "$val2" ]
then
    echo "$val1 is bigger than $val2"
fi
```

### Det "nya" sättet {#nya}

Från och med Bash v2.02 fungerar det uppdaterade sättet, dubbla hakparanteser (double square bracket, [[ ]]). En skillnad är att den nya versionen är ett nyckelord, istället för ett program (test). Det har inte samma grundkrav på hur det ska bete sig. Till exempel är kravet inte lika hårt att man bör lägga variablerna inom citationstecken: `"$variable"`.

```bash
#!/usr/bin/env bash
#
# An example script with the new, updated way

val1=5
val2=3

if [[ $val1 -gt $val2 ]]
then
    echo "$val1 is bigger than $val2"
fi
```

Vi kör vidare på det nya sättet använder enbart `[[ ... ]]`.

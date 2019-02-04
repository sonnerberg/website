---
author: lew
revision:
    "": "(A, lew) Första versionen."
...
Variabler
=======================

Varabler i Bash kan innehålla vilket värde som helst, det är ett så kallat *otypat* språk. Vi tilldelar med `=` utan mellanslag mellan referensen och värdet. När vi vill använda variabeln använder vi ett dollartecken framför:



### En start {#en-start}

```bash
#!/usr/bin/env bash
#
# An example script for the linux course

my_number=42
my_name="Deep Thought"

echo "My name is $my_name and the answer is: $my_number"
```

Det är "god sed" att kapsla in variablerna i dubbla citationstecken, `"`. Anledningen blir mer tydlig när vi kommer till for-loopar men vad som händer är att innehållet presenteras som en sträng, och riskerar inte att bli uppdelat, som man kanske vill att faktiska kommandon ska vara. Det möjliggör också att vi kan använda enkla citationstecken inuti de dubbla. För att demonstrera kikar vi på följande exempel:

```bash
#!/usr/bin/env bash
#
# An example script for the linux course

some_text="This contains some    spaces"

echo $some_text     # This contains some spaces
echo "$some_text"   # This contains some    spaces
```



### Konstanter {#konstanter}

Konstanter skrivs med versaler:

```bash
#!/usr/bin/env bash
#
# An example script for the linux course

MY_NUMBER=42
my_name="Deep Thought"

echo "My name is $my_name and the answer is: $MY_NUMBER"
```

I läget ovan kan vi ändra på konstanten, utan att något går sönder. För att undvika det kan vi skapa en variabel med inbyggda nyckelord `declare -r` eller `readonly`. Då förhindrar vi att de kan ändras på:

```bash
#!/usr/bin/env bash
#
# An example script for the linux course

declare -r MY_NUMBER=42
# Alternativt
readonly MY_NAME="Deep Thought"

MY_NUMBER=5 # Ger felmeddelandet "MY_NUMBER: readonly variable"

echo "My name is $MY_NAME and the answer is: $MY_NUMBER"
```

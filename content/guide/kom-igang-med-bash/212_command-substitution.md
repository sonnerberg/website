---
author: lew
revision:
    "": "(A, lew) Första versionen."
...
Command substitution
=======================

Innan vi går vidare går vi igenom något som kallas *command substitution*. I vissa fall vill man använda resultatet av ett exekverat kommando. Det går att göra på olika sätt och det sker via ett *subshell*. Vi kikar på det rekommenderade sättet.



```bash
#!/usr/bin/env bash
#
# An example script for the linux course

path="$(pwd)" # Sparar resultatet av kommandot "pwd" i en variabel (command substitution)
result=$(ls -al "$path") # Här används $path (command substitution)

echo "$result" # Skicka vidare resultatet där det kan användas
```

Resultatet av kommandot `ls -al pwd` kommer hamna i variabeln `result`. Kommandot `pwd` ger den nuvarande mappens sökväg. Vi har alltså använt *command substitution*. Bra då har vi koll på det.

Man kan även stöta på användandet av back-ticks `` `command` ``. Resultatet blir detsamma, men det kan lätt bli problem om man hamnar i en situation där man vill nesta kommandon (köra kommandon i kommandon).

En annan sak att notera är kommandon som tex `$(cat file.txt)` kan användas på ett snabbare sätt med `$(< file.txt)`

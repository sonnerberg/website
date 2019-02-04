---
sectionHeader: true
linkable: true
...
Aritmetik
=======================

```bash
#!/usr/bin/env bash
#
# An example script for the linux course

value1=5
value2=10
value3=$value1+$value2

echo "$value3" # Prints 5+10

value1=5
value2=10
let value3=$value1+$value2

echo "$value3" # Prints 15

value1=5
value2=10
value3=$(( value1 - value2 ))

echo "$value3" # Prints -5
```

<!-- let -->
<!-- (()) -->
**
+=
++
--
<
>

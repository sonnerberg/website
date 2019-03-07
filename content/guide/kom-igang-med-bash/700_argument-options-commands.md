---
sectionHeader: true
linkable: true
...

Argument, options och commands
=======================

Vad är egentligen *arguments*, *options* och *commands*? Vi försöker få rätt på vad som är vad. Till vår hjälp tar vi ett script vi känner till, dbwebb-cli.

Om vi tittar på hjälp-delen av dbwebb: `$ dbwebb -h` så kan vi nästan överst hitta:

`> Usage: dbwebb [options] <command> [arguments]`



<!-- $#	Stores the number of command-line arguments that were passed to the shell program.
$?	Stores the exit value of the last command that was executed.
$0	Stores the first word of the entered command (the name of the shell program).
$*	Stores all the arguments that were entered on the command line ($1 $2 ...).
"$@"	Stores all the arguments that were entered on the command line, individually quoted ("$1" "$2" ...). -->

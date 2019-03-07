---
sectionHeader: true
linkable: true
...

Wordsplitting och $IFS
=======================

Internal Field Separator (space, tab, newline)

word="some:thing another word"

loop

IFS_BACKUP=$IFS
IFS=":"

loop again

IFS=$IFS_BACKUP

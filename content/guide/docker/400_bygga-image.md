---
sectionHeader: true
linkable: true
author: lew
revision:
    "2019-03-14": "(A, lew) Första versionen."
...
Dockerfile
=======================

TBD

Glöm ej - Prune dangling images:
`docker rmi $(docker images -f "dangling=true" -q)`

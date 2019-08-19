---
author:
    - efo
    - lew
category: webbprogrammering
revision:
    "2019-08-19": (A, lew) Uppdatering inför HT19.
...
Create a web page on Apache Virtual Host
==================================

Fix a site with an Apache Virtual Host. You get to configure a Named Apache Virtual Host and make a small web page that will be hosted by your own web server.

<!--more-->



Prerequisites {#forkunskaper}
-----------------------

Du har jobbat igenom guiden "[Install web pages with Apache Name-based Virtual Hosts](kunskap/install-web-pages-with-apache-virtual-hosts)".



Introduction {#intro}
-----------------------

The files you create and use in this task should be saved in your course repo in the directory `me/kmom01/vhost`. They are used to report the task.

Create a file, `log.txt`, and place it in the directory above.



Requirements {#krav}
-----------------------

1. Create an Apache Virtual Host `me.linux.se`. Save a copy of the config file `me.linux.se.conf` in your course repo. Make sure you can access the site with your browser on your local development computer.

1. Open a terminal, use `lynx` to open your newly created website. Enter the command you use in the log (`log.txt`).

1. Take a screenshot of the terminal that shows when using `lynx` to access the site. Save it as `dump.png`. Save the image in .png format and use lower case letters in the file name.

1. Publish your answers as follows.

```bash
# Ställ dig i kurskatalogen
dbwebb publish kmom01
```

Correct any errors that pop up and publish again. When it looks green you are done.

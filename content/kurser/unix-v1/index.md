---
title: unix-v1
author:
    - efo
    - lew
revision:
    "2019-08-16": (A, efo, lew) Första revisionen inför kursstart HT2019.
...
UNIX
==================================

**UNIX and Linux, an overview and introduction** aka _unix_ introduces students to the command prompt, basic tools and commands, their areas of application, and ways to combine them into larger workflows.

<!--more-->



Lab environment requirements {#labb}
------------------------

In the course, you install a Linux operating system on your own machine with the virtualization system VirtualBox. You need a computer with at least 8GB of internal memory for it to work well. With less internal memory, it takes longer to complete the exercises and it can feel sluggish.

You can also perform the installation on another computer, an older laptop for example. Or you can use virtual servers that you install on your own.

In short, you should install a linux server and you need a good enough environment for it to work without any worries.



Prerequisites {#prerequisites}
------------------------

> General requirements for university studies.



Content {#content}
------------------------

The key components of the course are:

* comparison between dialogue based on the
command line interface and graphical user interface
(GUI) with predefined menu selections

* use of pipelines as a method for incremental
development based on problem specifications and
partial solutions for advanced testing

* operating systems based on files: introduction to
hierarchical filing systems, the taxonomy problem
and its solution through hard and soft links,
streams, authorisation and ownership

* text as a general format for semi-structured data:
creation, extraction, processing and output of
multi-level delimiters (e.g. fields and posts).
Operations of filtering and limiting, and how they
can be constructed from standard commands such
as head, tail, awk, grep and sed (POSIX standard)

* methods to combine different tools: string
escaping, embedded commands and expansions, regular expressions, pipelines and redirection



Aims and learning outcomes {#outcomes}
------------------------

#### Knowledge and understanding

On completion of the course, the students shall be
able to:

* demonstrate an understanding of the functionality
of the POSIX core tools

#### Competence and skills

On completion of the course, the students shall be
able to:

* break down problems into smaller parts with
well-defined inputs and outputs
* analyse the usefulness of tools in different
problem-solving phases
* create suitable test data for both partial and
holistic solutions, and identify test cases
* integrate partial solutions into holistic solutions to
solve problems.



Assignment prerequisites {#aprerequisites}
------------------------

Complete all steps of the [VirtualBox guide](guide/virtualbox_en).

All assignments and the following installation guide should be completed inside the installed virtual environment.

Install the lab environment by completing the steps in the [`dbwebb` installation guide](kurser/unix-v1/installera-labbmiljo).



Assignments {#assignments}
------------------------

The course is divided into several assignments.

### Assignment 1: Virtual Hosts {#kmom01}

Det första kursmomentet går ut på att installera Debian/Linux och logga in på maskinen som en server, via SSH.

För att lyckas med det så behöver du bekanta dig med grunderna i terminalen och lära dig ett par av de viktigaste kommandona som utförs i terminalen.

[Instructions](kurser/unix-v1/kmom01).



### Assignment 2: Bash {#kmom02}

Nu har vi en Linux-server. Låt oss installera ett par webbplatser på den. Det låter som en vettig syssla för en webbprogrammerare.

Ett bra sätt att installera många webbplatser på en och samma maskin är Apache Virtual Hosts och det är något vi skall bekanta oss med.

Samtidigt behöver vi bekanta oss med fler Unix-kommandon så vi känner oss hemma i terminalen, SSH och att jobba med Linux som en server.

[Instructions](kurser/unix-v1/kmom02).



### Assignment 3: Regular expressions {#kmom03}

Mycket handlar om att förenkla vardagen som programmerare genom att automatisera de processer och rutiner man utför. En hel del av det vi gör kan automatiseras via skript, till exempel bash-skript med kommandon. Men för att göra det behöver vi ha koll på hur man skapar skript och hur man programmerar i bash.

[Instructions](kurser/unix-v1/kmom03).



### Assignment 4: Mazerunner {#kmom04}

Nu har vi en Linux-server, en webbserver och vi kan grunderna i att bygga skript i bash. Låt oss nu kika på en annan sak, hur man bygger egna servrar i Linux med Node.js.

Så, vi behöver starta med att installera Node.js på servern och komma igång med hur Node.js fungerar. Vi kör på med några övningar och sedan ser vi hur man byggger upp en enkel webbserver, eller webbtjänst, med Node.js. Vi närmar oss ett gränsland där webbservern blir till en webbtjänst. Det blir tydligt i hur vi använder Node.js för att skapa kod som både hanterar webbservern som sådan och lägger till tjänster som utförs av javaScript-funktioner.

[Instructions](kurser/unix-v1/kmom04).



Literature {#litteratur}
----------------------------

* **[The Linux Command Line](kunskap/boken-the-linux-command-line)** -- William Shotts
    An easy-to-read and pleasant book with an open license that makes the book available freely on the book's website. The book gives a good introduction to the Linux beginner, system commands and the terminal.



Ladok {#ladok}
------------------------

According to the syllabus, there are a number of ladok moments and they are linked to the course parts as follows.

| Assignments     | Ladok credits in course plan        |
|-----------------|-------------------------------------|
| Assignment 1    | Written assignment 1 - 1.5 hp - A-F |
| Assignment 2    | Written assignment 2 - 2.0 hp - A-F |
| Assignment 3    | Written assignment 3 - 2.0 hp - A-F |
| Assignment 4    | Written assignment 4 - 2.0 hp - A-F |



Course evaluation and course development {#kursutvardering}
-----------------------------------------------------

At the end of the course you receive a link to the course evaluation in Canvas. The course evaluations are important for course development so please take 3-5 minutes to complete the course evaluation.



Course plan {#kursplan}
-----------------------------------------------------

The syllabus is the formal document of the course that has been established by the university. When the course is evaluated, it is done against the syllabus. In the syllabus you can read about the course's classification, purpose, content, goals, general abilities, learning and teaching, assessment and examination, literature, etc.

[Course plan for DV1466](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1466)

[Course plan for DV1563](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1563)

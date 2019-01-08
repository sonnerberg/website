---
views:
    flash:
        region: flash
        template: default/image
        data:
            src: "image/snapvt19/windows-cowsay.png?c=800,200,0,0&w=1100&sharpen"
author:
    - mos
category: 
    - labbmiljo
    - windows
    - bash
revision:
    "2019-01-08": "(A, mos) Uppdaterad installationsprocess för 1803."
...
Installera Bash i Windows 10 (v 1803)
==================================

[FIGURE src=image/snapvt19/windows-cowsay.png?w=c5&a=0,70,60,0 class="right"]

Så här gör du för att installera Bash i Windows 10 samt installera det som behövs för att komma igång med kurserna.

Installationsprocessen förutsätter att du har ett uppdaterat system av Windows 10 64bitar system med version 1803.

<!--more-->



Förutsättning {#pre}
-------------------------------

Du har minst en 64-bitars version (x64) av Windows 10.

Dubbelkolla att ditt versionsnummer startar på minst 1803 och att du har en Windows build 16215, eller senare, genom att trycka `Windows key + R` och köra programmet `winver`. 

[FIGURE src=image/snapvt19/win10-winver.png caption="Version 1803 eller högre behöver vara installerad."]

Installationsstegen nedan bygger på information från artikeln "[Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)".



Installera Bash {#install}
-------------------------------

Bash finns med i din Windows installation men du behöver sätta på det på följande sätt.



### Sätt på "Windows Subsystem for Linux" {#wsl}

Starta PowerShell som administratör och kör följande kommando för att aktivera "Windows Subsystem for Linux (WSL)".

Sök efter PowerShell och starta som administratör genom att högerklicka med musen.

[FIGURE src=image/snapvt19/search-windows-power-shell.png caption="Starta PowerShell som administratör."]

Kör följande kommando i PowerShell för att aktivera WSL. Kopiera och pasta in i PowerShell med högerklick på musen.

```text
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

[FIGURE src=image/snapvt19/power-shell-enable-linux.png?w=w3 caption="Kör kommandot i PowerShell, som administratör."]

Starta om Windows när du ombeds göra det.



### Installera Debian GNU/Linux från Windows Store {#winstore}

Öppna Windows Store, till exempel genom att köra kommandot `ms-windows-store:` via `Windows key + R`.

[FIGURE src=image/snapvt19/run-ms-windows-store.png caption="Starta Windows Store för att installera Linux."]

Sök efter "Debian GNU/Linux" och välj att "Hämta/Installera".

[FIGURE src=image/snapvt19/windows-store-debian.png caption="Installera Debian GNU/Linux via Windows Store."]

Vi väljer att installera Debian för kurserna. Det finns dock flera andra installationer av Linux som du kan göra, till exempel Ubuntu.



### Starta Debian GNU/Linux första gången {#startbash}

Du kan starta Debian via Windows Store, eller genom att köra kommandot `debian` via sökfältet eller via `Windows key + R`.

Första gången ombeds du att skapa en användare med lösenord, gör det.

Därefter är Debian installerat och klart. Du har nu en Linux-terminal, en bash terminal, i din Windows.

[FIGURE src=image/snapvt19/windows-10-debian.png?w=w3 caption="Nu är Debian för Windows installerat och klart."]



Pakethantering {#paket}
------------------------------

För att installera program så använder du en pakethanterare som heter `apt-get`. Med den kan du installera paket, tjänster och programvaror i din terminal.

De grundläggande paket som du behöver för kurserna finns redan installerade.

För att testa pakethanteraren kan du installera paketet `cowsay` som är ett litet skoj-paket.

Vi börjar med att uppdatera installationen med senaste informationen om de paket som finns.

```text
sudo apt-get update
```

Nu kan vi installera paketet `cowsay`.

```text
sudo apt-get install cowsay
```

Nu kan vi köra programmet.

```text
cowsay "Hej alla webbprogrammerare!"
```

[FIGURE src=image/snapvt19/windows-cowsay.png?w=w3 caption="Nu är du redo för Linux med en bash-terminal på Windows."]

Vill du vet mer om programmet så öppnar du dess manualsida. Manualsidor är källan till kunskap i en linux terminal.

```text
man cowsay
```

Om programmet `man` inte finns installerat så installerar du det.

```text
sudo apt-get install main
```

Man kan söka efter de programpaket som går att installera.

```text
sudo apt-cache search cowsay
```

Det var grunderna i pakethantering och installation av paket i Linux och terminalen.



Bra att ha {#braattha}
------------------------------

Följande tips kan göra din bekantskap lite trevligare med Linux och bash-terminalen för Windows.



### Sudo utan lösenord {#sudo}

För att slippa skriva lösenord varje gång du skriver kommandot `sudo` så kan du lägga en fil i katalogen `/etc/sudoers.d/` och döpa filen till ditt användarnamn. Filen skall innehålla en rad likt denna (där min användare är "mos").

```text
mos ALL=NOPASSWD: ALL
```

Följande kommandorad skapar en sådan fil för din användare.

```bash
sudo bash -c "echo '$USER ALL=NOPASSWD: ALL' > /etc/sudoers.d/$USER && cat /etc/sudoers.d/$USER"
```

Här är en forumtråd som hanterar [sudo utan lösenord](t/4327).



### Kopiera och pasta i terminal {#copypaste}

När du är i terminalen kan du markera ett textstycke med musen och högerklicka. Sedan kan du göra paste genom att högerklicka igen. Detta fungerar även om du vill göra paste till ett fönster utanför Bash, alternativt så trycker du `ctrl-v` för att pasta till ett annat fönster.

Vill du kopiera från ett annat fönster till terminalen så markerar du texten och lägger den i copy-bufferten (via `ctrl-c` eller högerklickmenyn) och du gör paste i terminalen via högerklick.



### Var finns Windows hemma-katalog? {#winhome}

Du kör Linux i ett eget system där du har speciella Linux-användare och ett filsystem för Linux. Din installation fungerar som ett eget system, ett subsystem inuti Windows. Därav namnet "Windows Subsystem for Linux (WSL)".

Du kan komma åt ditt vanliga filsystem, din "vanliga" `C:` och på det sättet dela filer mellan Linux och Windows. Du hittar dina Windows-kataloger under `/mnt`.

Du kan använda kommandot `ls` för att lista de kataloger som ligger under katalogen `/mnt`. I mitt fall ligger där katalogen `c` som innehåller alla filerna på min `C:`.

```text
$ ls -l /mnt
total 0
drwxrwxrwx 1 mos mos 512 Jan  8 02:27 c
```

Sökvägen till min hemmakatalog i Windows blir då `/mnt/c/Users/mos/` där min Windowsanvändare heter "mos".

För att göra det enkelt att nå filerna i din Windows hemma-katalog så kan du skapa en symbolisk länk i din hemmakatalog.

```text
$ cd && ln -s /mnt/c/Users/mos/ winhome
$ ls -l
total 0
lrwxrwxrwx 1 mos mos 17 Jan  8 03:53 winhome -> /mnt/c/Users/mos/
```

Nu kan jag enkelt nå mina filer som ligger hos min Windows-användare.

Det rekommenderas att du sparar dina egna filer under din Windows-användare. Det gör det enklast att nå dem både via WSL och via vanliga Windows-applikationer.



### Vilken version av Linux {#version}

Du kan kontrollera vilken version av Bash du har med kommandot `lsb_release`. Installera kommandot om det inte finns.

Tecknet `$` är en del av prompten och ingår inte i kommandot du skall skriva in.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 9.6 (stretch)
Release:        9.6
Codename:       stretch
```



### Uppdatera din installation {#update}

Du uppdaterar och uppgraderar din installation med pakethanteraren genom att köra följande kommando.

```text
sudo apt update && sudo apt upgrade
```



Avslutningsvis {#avslutning}
------------------------------

Det finns en [forumtråd](t/8161) där du kan ställa frågor, eller ge tips och trix, om denna artikel. Kika där om du får problem. Tråden ligger i subforumet [Windows för Webbprogrammerare](forum/viewforum.php?f=55).

Vill du ställa specifika frågor om Unix/Linux, bash eller terminalen så passar subforumet [Unix och Linux](forum/viewforum.php?f=49)

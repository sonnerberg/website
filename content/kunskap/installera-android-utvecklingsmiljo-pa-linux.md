---
author: efo
category:
    - webbprogrammering
    - webapp
revision:
  "2018-02-20": (A, efo) Första utgåvan inför kursen webapp-v3.
...
Installera Android utvecklingsmiljö på Linux
==================================

[FIGURE src=/image/webapp/android-robot.png?w=c5 class="right"]

Denna guide visar dig hur du installerar de nödvändiga komponenterna av Android SDK för att kunna köra en Android emulator.

Jag kommer att installera endast det nödvändigaste för att få tillgång till emulatorn. Software Development Kit (SDK) kan ta mycket plats på din hårddisk, om du bara installerar de absolut nödvändiga paketen tar det upp mot 6-7 GiB.



<!--more-->



Installera Java {#java}
--------------------------------------
Du kan behöva Java JDK, på linux installeras detta lättast genom att använda `apt-get`. Följande kommandon installerar Java JDK 8 på en debian eller ubuntu maskin.

```bash
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main"
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
$ javac -version
```

De ska nu se ungefär följande output: `javac 1.8.0_161`. Det viktiga är att det står 1.8 först.

<!-- För att vi ska kunna bygga apparna behövs även byggsystemet gradle. Vi installerar detta genom att ladda ner en zip fil och packa ut den. Vi använder version 4.1 då det är den Cordova använder.

```bash
wget https://services.gradle.org/distributions/gradle-4.1-bin.zip
sudo mkdir /opt/gradle
sudo unzip -d /opt/gradle gradle-4.1-bin.zip
```

Vi lägger till gradle i PATHEN och ser att allt fungerar.

```bash
echo export PATH=$PATH:/opt/gradle/gradle-4.1/bin >> ~/.profile
source ~/.profile
gradle -v
``` -->



Installera Android Studio {#studio}
--------------------------------------
Google har under senaste året ändrat så att man måste installera Android Studio för att kunna använda sig av Android SDK och Android Emulatorn.

För att installera gå till [Android Studio](https://developer.android.com/studio/index.html) och tryck på knappen **DOWNLOAD ANDROID STUDIO**. Spara zip-filen i din hemmakatalog så den är lätt att hitta.

Kör sedan nedanstående kommando för att packa upp zip-filen till katalogen `/usr/local`.

```bash
$ sudo unzip [NAMN på zip-filen] -d /usr/local/
```



Installera en virtuell enhet {#avd}
--------------------------------------
För att vi kan köra våra appar i en virtuellt använder vi oss av Android Virtual Device manager (avdmanager).

Vi installerar med följande kommando en virtuell enhet kallad 'phone' som ska efterlikna Google Pixel. Om du hellre vill ha en annan enhet kör kommandot `./avdmanager list device` och ändra till annat id efter `--device`.

```bash
./avdmanager create avd --name phone --device 17 --package 'system-images;android-26;google_apis;x86_64'
```



Använda en fysisk enhet {#fysisk}
--------------------------------------



Lägga till i pathen {#path}
--------------------------------------
För att Cordova ska hitta Java och Android behövs det i PATHEN. Vi lägger till det med följande kommandon.

```bash
$ echo export ANDROID_HOME="$HOME/android" >> ~/.profile
$ echo export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools >> ~/.profile
$ echo $PATH
```

Du ska nu se att `tools` och `platform-tools` ligger sist i din PATH.



Kör Cordova exemplet {#cordova}
--------------------------------------
Gå till katalogen `me/kmom05/hello` där du skapade HelloWorld exemplet när du installerade Cordova. Kör följande kommandon för att lägga till Android som platform och köra det antigen på din fysiska enhet, om den är inkopplat, eller i din Virtuella Enhet.

```bash
$ cordova
```



Avslutningsvis {#avslutning}
--------------------------------------
Nu har du förhoppningsvis kommit igång med Cordova på Android i Linux miljö och har kört HelloWorld exemplet i Simulatorn och på din fysiska enhet.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7311) om denna artikeln.

Du kan även hittar mer info i [Cordovas egna Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/index.html).

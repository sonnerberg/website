---
author: efo
category:
    - webbprogrammering
    - webapp
revision:
  "2018-02-20": (A, efo) Första utgåvan inför kursen webapp-v3.
...
Installera Android utvecklingsmiljö på Windows
==================================
[FIGURE src=/image/webapp/android-robot.png?w=c5 class="right"]

Denna guide visar dig hur du installerar de nödvändiga komponenterna av Android SDK för att kunna köra en Android emulator.

Jag kommer att installera endast det nödvändigaste för att få tillgång till emulatorn. Software Development Kit (SDK) kan ta mycket plats på din hårddisk, om du bara installerar de absolut nödvändiga paketen tar det upp mot 6-7 GiB.



<!--more-->



Installera Java {#java}
--------------------------------------
Ladda ner och installera Java JDK från [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Ladda ner rätt paket beroende på processorarkitektur: Windows x64 för 64-bits arkitektur eller Windows x86 för 32-bits arkitektur. Kör `.exe` filen som laddas ner och följ instruktionerna i guiden.



Installera Android Studio {#studio}
--------------------------------------
Google har under senaste året ändrat så att man måste installera Android Studio för att kunna använda sig av Android SDK och Android Emulatorn.

För att installera gå till [Android Studio](https://developer.android.com/studio/index.html) och tryck på knappen **DOWNLOAD ANDROID STUDIO**. Kör den nerladdade `.exe` filen och följ instruktionerna öppna Android Studio när installationen är klar.

Android Studio avslutar nu installationen bekräfta de val som kommer upp. Jag har vald mörka temat Dracula, om ni undrar över de mörka färgarna i bilderna nedan. Vi kommer inte använda Android Studio för utveckling, men är tyvärr enda sättet att installera SDK och Emulatorn, samt att kunna bygga apparna. När installationen är klar får du upp nedanstående fönster. Välj Configure > SDK Manager.

[FIGURE src=/image/webapp/screenshot-android-studio.png caption="Android Studio startfönster."]

Välj i fönstret som kommer upp 'Android 8.0 API Level 26' och bocka av 'API Level 27' tryck sedan Apply för att installera rätt SDK. Godkänna License Agreement och låt Android Studio Installera SDK:n.

[FIGURE src=/image/webapp/screenshot-android-studio-sdk.png caption="Android Studio SDK Manager."]



Installera en virtuell enhet {#avd}
--------------------------------------
Starta ett nytt Android Studio project från startfönstret i Android Studio. Klicka dig igenom guiden för att skapa ett projekt. De förifyllda värden som finns fungerar bra och enda anledningen till att vi skapar ett projekt är för att få möjlighet för att skapa en virtuell enhet. Du kommer troligen få ett fel att byggverktygen för Android inte fungerar. Trycka på länken i felet och byggverktygen ska nu installeras.

[FIGURE src=/image/webapp/screenshot-android-studio-gradle.png caption="Android Studio byggverktygen."]

I nedanstående video visas hur man skapar en virtuell enhet, som vi sedan kan använda för att köra vår HelloWorld Cordova app i. Du kan under installationen få frågan om du vill installera Intel HAXM, gör detta då det snabba upp Emulatorn avsevärt.

[YOUTUBE src=KWAsnLTClzo]



Kör Cordova exemplet {#cordova}
--------------------------------------
Gå till katalogen `me/kmom05/hello` där du skapade HelloWorld exemplet när du installerade Cordova. Kör följande kommandon för att lägga till Android som platform och köra det antigen på din fysiska enhet, om den är inkopplat, eller i din Virtuella Enhet.

```bash
# Stå i me/kmom05/hello
cordova platform add android --save
cordova run android
```

Ibland kan man få problem att VT-x är disabled vilket betyder att man inte får virtualisera. Denna [forumtråd](https://dbwebb.se/forum/viewtopic.php?t=4336) kan hjälpa till att lösa problemet.



Använda en fysisk enhet {#fysisk}
--------------------------------------
Emulatorn kräver mycket processorkraft och RAM-minne och det är ofta en fördel att utveckla mot en fysisk android enhet istället. För att använda en fysisk enhet måste enheten vara i Utvecklingsläge (Developer Mode).

1. Gå till Inställningar (Settings) och scrolla ner till Om telefon (About phone) längst ner i Inställningar.

1. Välj i undermenyn Programvaruinformation (Software Information).

1. Tryck nu 7 gånger på Kompileringsnr (Build Number). Du ska efter 3 tryckningar få upp en liten ruta om att du håller på att bli utvecklare.

1. När du har tryckt 7 gånger får du upp ett nytt menyval Utvecklaralternativ (Developer options) under Inställningar.

1. Välj under Utvecklaralternativ (Developer Options) att du vill tillåta USB-felsökning (USB Debugging).

1. Koppla in din enhet till din dator och kör kommandot `cordova run android`. Din HelloWorld app ska nu köras i din enhet istället för i emulatorn.



Avslutningsvis {#avslutning}
--------------------------------------
Nu har du förhoppningsvis kommit igång med Cordova på Android i Windows miljö och har kört HelloWorld exemplet i Emulatorn och på din fysiska enhet.

Om du har frågor eller tips så finns det en särskild [tråd i forumet](t/7311) om denna artikeln.

Du kan även hittar mer info i [Cordovas egna Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html).

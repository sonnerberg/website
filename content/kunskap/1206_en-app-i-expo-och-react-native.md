---
author: efo
category: javascript
revision:
  "2022-01-18": (A, efo) Första utgåvan inför kursen webapp-v4 VT22.
...
En app i Expo och React Native
==================================

Vi ska i denna övning skapa grunden till vår Lager app som vi kommer jobba med under kursens gång. Vi kommer använda oss av ramverken Expo och React Native för att skapa en native app skriven med hjälp av JavaScript.



<!--more-->



Förutsättning {#pre}
--------------------------------------

Du har installerat labbmiljön för kursen webapp-v4.



Expo CLI {#cli}
--------------------------------------

Vi har i tidigare kurser sett hur CLI verktyg som till exempel webpack kan vara värdefulla och enkla verktyg. Vi ska i denna kursen använda oss av Expo's CLI och det första vi gör är att skapa vår app.

```shell
# stå i me/lager
$ expo init .
```

Du får nu upp möjligheten att välja mellan fyra olika mallar (templates). Vi väljer den som heter `blank (TypeScript)` så har vi allihopa samma att utgå ifrån när vi ska börja koda. Du väljer genom att använda pil ner/pil upp och sedan enter.

```shell
? Choose a template: › - Use arrow-keys. Return to submit.
    ----- Managed workflow -----
❯   blank               a minimal app as clean as an empty canvas
    blank (TypeScript)  same as blank but with TypeScript configuration
    tabs (TypeScript)   several example screens and tabs using react-navigation and TypeScript
    ----- Bare workflow -----
    minimal             bare and minimal, just the essentials to get you started
```

Nu kommer Expo installera en massa paket med hjälp av `yarn` eller `npm` beroende på vilken pakethanterare du har installerat. Det spelar inte så stor roll, men oavsett vilken som används tar det en liten stund. När Expo är klar kan vi köra igång appen med `expo start`. Nu kommer en webbplats öppnas i din standard webbläsare. Webbplatsen innehåller en meny, en QR-kod och en svart del som fungerar som log.

I meny har vi möjligheten att välja `Connection` mellan Tunnel, LAN eller Local. Som utgångspunkt bör LAN vara markerad men välj istället Tunnel.

![Choose Connection](image/webapp/v4/choose_connection.png)

Nu ska det vara möjligt att öppna appen med hjälp av QR-koden och Expo Go appen som du installerade som en del av labbmiljön. Om du har en iOS enhet använder du kamera appen för att använda QR-koden. På Android går det direkt i Expo Go appen.

Efter nerladdning av appen till telefonen ska det nu vara möjligt att se hälsningen "Open up App.tsx to start working on your app!". Så låt oss göra det. `App.tsx` är en TypeScript fil och utgångspunkten för vår app.

```javascript
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.tsx to start working on your app!</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

De två första raderna är import av först en `StatusBar` komponent från Expo. Den visas längst ner i appen och är till för att vi ska kunna se vad som händer när vi utvecklar appen. Sedan importerar vi två [Core Components](https://reactnative.dev/docs/intro-react-native-components#core-components) `View` och `Text`, samt StyleSheet för att kunna ge stil till vår app.

Alla delar av appar vi gör i React Native är uppbyggda av olika sorters Views. När vi bygger appen med hjälp av Expo och React Native görs dessa om till Views i det mobila operativsystem vi bygger för. Som exempel blir en `Text`-View till en `UITextView` på iOS och till en `TextView` på Android.



Komponenter {#komponenter}
--------------------------------------

Komponenter är ett oerhört viktigt begrepp inom JavaScript-ramverk som till exempel Angular, React och Vue. Tanken med en komponent är att det är oberoende och återanvändbara delar av vår kod. För att förstå komponenter är artikeln [React Fundamentals](https://reactnative.dev/docs/intro-react).

I kodexemplet ovan (och inklistrat nedan med) ser vi ett första exempel på en komponent `App`. `App` i sig är en funktion som vi exporterar som `default export` från filen `App.tsx`. Från funktionen returnerar vi något som ser ut som upphottat HTML. Det kallas JSX och är en utökning av JavaScript-syntaxen, så det är mer än bara ett `template` language. För att lära oss mer om bakgrunden och grunderna i JSX rekommenderar jag artikeln [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html) från Reacts dokumentation. För den som vill gå på djupet kan artikeln [JSX In Depth](https://reactjs.org/docs/jsx-in-depth.html) läsas efteråt.

```javascript
export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.tsx to start working on your app!</Text>
      <StatusBar style="auto" />
    </View>
  );
}
```

I denna komponenten returnerar vi en `View`-Core Component som i sin tur innehåller en `Text`-Core Component, samt en Expo komponent som visar status för appen. Vi kommer senare i kursen att göra egna komponenter, som vi kan använda på liknande sätt som denna `StatusBar` komponent.

Vi ändrar lite i `App.tsx` för att se hur komponenterna fungerar och hur vi kan använda oss av styling. Vi börjar med `Text` komponenten som vi ändrar till blå och gör lite större. Notera att vi inte anger en enhet efter `fontSize` som vi i vanliga fall hade gjort i CSS. Alla storlekar anges i pixlar i React Native så därför anger vi storlek utan enhet.

```javascript
<Text style={{color: '#33c', fontSize: 42}}>Lager-Appen</Text>
```

Vi fortsätter med att lägga till en bild till appen. Jag har lagt till denna [bilden](https://raw.githubusercontent.com/dbwebb-se/webapp-v4/v1.0.0/example/assets/warehouse.jpg). Vi gör det genom att först importera bilden, ungefär som vi gör när vi importerar JavaScript objekt eller funktioner. Sedan använder vi ett `Image` element för att visa upp bilden. Viktigt att sätta både höjd och bredd på bilden, annars kommer den inte synas.

```javascript
import { StatusBar } from 'expo-status-bar';
import { Image, StyleSheet, Text, View } from 'react-native';
import warehouse from './assets/warehouse.jpg';

export default function App() {
  return (
    <View style={styles.container}>
      <Text style={{color: '#33c', fontSize: 42}}>Lager-Appen</Text>
      <Image source={warehouse} style={{ width: 320, height: 240 }} />
      <StatusBar style="auto" />
    </View>
  );
}
```

Appen bör nu se ut ungefär så här:

![Centrerad](image/webapp/v4/lager-centrerad.png)

Vi vill kanske inte alltid ha våra element centrerade på telefonen så om vi ändrar till följande stylesheet flytts elementen upp till toppen av skärmen.

```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
});
```

![Notch](image/webapp/v4/lager-notch.png)

På vissa nya telefonen kommer vårt innehåll nu gå upp i den såkallade notch. Det vill vi kanske inte och därför kan vi ersätta vår root `View`-komponent med en `SafeAreaView`-komponent istället som visar upp våra element inom ett område på telefonen som är nedanför notchen.

Vår kod ser alltså nu ut på detta sättet.

```javascript
import { StatusBar } from 'expo-status-bar';
import { Image, StyleSheet, Text, View, SafeAreaView } from 'react-native';
import warehouse from './assets/warehouse.jpg';

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <Text style={{color: '#33c', fontSize: 42}}>Lager-Appen</Text>
      <Image source={warehouse} style={{ width: 320, height: 240 }} />
      <StatusBar style="auto" />
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
});
```



Vår första egna komponent {#component}
--------------------------------------

För att vår app ska bli till en Lager-app behöver vi en lagerförteckning. Vi skapar en egen komponent som klarar av att visa upp lagret. Först skapar vi en katalog `components` och sedan filen filen `components/Stock.tsx`.

Vi börjar enkelt med att skriva ut "Lagerförteckning" och tittar på hur vi kan skapa en egen komponent. I filen `Stock.tsx` börjar vi med att definiera funktionen Stock som vi exporterar som `default export` från filen.

```javascript
export default function Stock() {

}
```

Vi anger komponent-funktioners namn med stor bokstav enligt namnkonventionen då det blir lättare att överskåda i jsx-syntaxen. Vi kan nu göra en `import` i `App.tsx` och använda komponenten med hjälp av jsx enligt `<Stock/>`.

```javascript
import Stock from './components/Stock.tsx';

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <Text style={{color: '#33c', fontSize: 42}}>Lager-Appen</Text>
      <Image source={warehouse} style={{ width: 320, height: 240 }} />
      <Stock/>
      <StatusBar style="auto" />
    </SafeAreaView>
  );
}
```

Detta bör iinnte göra nån skillnad i appen, då vi inte returnerar något från komponenten. Så låt oss göra det.

```javascript
import { Text } from 'react-native';

export default function Stock() {
  return (
    <Text style={{color: '#333', fontSize: 24}}>Lagerförteckning</Text>
  );
}
```

Först importerar vi Core-komponenten `Text` som vi sedan använder för att skriva ut texten "Lagerförteckning" i storlek 24 med färgen `#333`.



Hämta data från API {#fetch}
--------------------------------------

[INFO]
Om du inte gjort övningen "[Introduktion till Lager-API:t](kunskap/introduktion-till-lager-api)" än, är det läge nu.
[/INFO]



Git {#git}
--------------------------------------

Expo skapar ett Git-repo för oss per automatik och har med en `.gitignore` som tar bort de filerna vi inte vill ha som en del av repot.

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

Komponenter är ett oerhört viktigt begrepp inom JavaScript-ramverk som till exempel Angular, React och Vue. Tanken med en komponent är att det oberoende och återanvändbara delar av vår kod. För att förstå komponenter är artikeln [React Fundamentals](https://reactnative.dev/docs/intro-react).

I kodexemplet ovan (och inklistrat nedan med) ser vi ett första exempel på en komponent `App`. `App` i sig är en funktion, sedan exporterar vi den som `default` export från filen `App.tsx`. Från funktionen returnerar vi något som ser ut som upphottat HTML. Det kallas JSX och är ett tillägg till JavaScript syntaxen, så det är mer än bara ett `template` language. För att lära sig mer om bakgrunden och grunderna i JSX rekommenderar jag artikeln [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html) från Reacts dokumentation. För den som vill gå på djupet kan artikeln [JSX In Depth](https://reactjs.org/docs/jsx-in-depth.html) läsas efteråt.

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

Vi ändrar lite

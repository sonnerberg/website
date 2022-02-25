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

På vissa nya telefonen kommer vårt innehåll nu gå upp i den såkallade notch i toppen av telefonen. Det vill vi kanske inte och därför kan vi utanför vår root `View`-komponent lägga en `SafeAreaView`-komponent, som visar upp våra element inom ett område på telefonen som är nedanför notchen.

Vår kod ser alltså nu ut på detta sättet.

```javascript
import { StatusBar } from 'expo-status-bar';
import { Image, StyleSheet, Text, View, SafeAreaView } from 'react-native';
import warehouse from './assets/warehouse.jpg';

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.base}>
        <Text style={{color: '#33c', fontSize: 42}}>Lager-Appen</Text>
        <Image source={warehouse} style={{ width: 320, height: 240 }} />
        <StatusBar style="auto" />
      </View>
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  base: {
    flex: 1,
    backgroundColor: '#fff',
    paddingLeft: 12,
    paddingRight: 12,
  }
});
```



Vår första egna komponent {#component}
--------------------------------------

För att vår app ska bli till en riktig Lager-app behöver vi en lagerförteckning. Vi skapar en egen komponent som klarar av att visa upp lagret. Först skapar vi en katalog `components` och sedan filen filen `components/Stock.tsx`.

Vi börjar enkelt med att skriva ut "Lagerförteckning" och tittar på hur vi kan skapa en egen komponent. I filen `Stock.tsx` börjar vi med att definiera funktionen Stock som vi exporterar som `default export` från filen.

```javascript
export default function Stock() {
  return null;
}
```

Vi anger komponent-funktioners namn med stor bokstav enligt namnkonventionen då det blir lättare att överskåda i jsx-syntaxen. Vi kan nu göra en `import` i `App.tsx` och använda komponenten med hjälp av jsx enligt `<Stock/>`.

```javascript
import Stock from './components/Stock.tsx';

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.base}>
        <Text style={{ color: '#33c', fontSize: 42 }}>Lager-Appen</Text>
        <Image source={warehouse} style={{ width: 320, height: 240 }} />
        <Stock />
        <StatusBar style="auto" />
      </View>
    </SafeAreaView>
  );
}
```

Detta bör inte göra nån skillnad i appen, då vi inte returnerar något från komponenten. Så låt oss göra det.

```javascript
// components/Stock.tsx
import { Text } from 'react-native';

export default function Stock() {
  return (
    <Text style={{color: '#333', fontSize: 24}}>Lagerförteckning</Text>
  );
}
```

Först importerar vi Core-komponenten `Text` som vi sedan använder för att skriva ut texten "Lagerförteckning" i storlek 24 med färgen `#333`.



State {#state}
--------------------------------------

Än så länge har vi bara skapat statiska sidor i vår applikation, vilket inte riktigt är tanken med denna kursen. För att vi ska kunna ändra data dynamiskt i vår app kommer vi introducera begreppet och konceptet State i vår applikation. State hanterar den data vi har i komponenterna och gör det samtidigt möjligt att uppdatera vyer baserat på ändringar i State.

Vi kommer använda oss av State i denna kursen genom ett ganska så nytt koncept i React kallat [Hooks](https://reactjs.org/docs/hooks-intro.html). React Hooks möjliggör att vi kan ändra State utan att behöva skapa en klass för vår komponent och vi kan alltså hålla hela vår applikation funktionsbaserad.

Låt oss titta på ett exempel i vår Stock komponent. Vi vill hålla en lista med produkter som en del av vår applikations State. För att ytterligare dela upp i återanvändbara komponenter har jag skapat komponenten `StockList`, den ligger dock kvar i filen `Stock.tsx`.

```javascript
import { useState } from 'react';
import { Text, View } from 'react-native';
import config from "../config/config.json";

function StockList() {
  const [products, setProducts] = useState([]);

  const list = products.map((product, index) => <Text key={index}>{ product.name }</Text>);

  return (
    <View>
      {list}
    </View>
  );
}

export default function Stock() {
  return (
    <View>
      <Text style={{color: '#333', fontSize: 24}}>Lagerförteckning</Text>
      <StockList/>
    </View>
  );
}
```

Vi börjar med att importera `useState` från React. För att kunna använda State behöver vi en variabel `products` för att spara data och en funktion `setProducts` för att ändra i `products`. Vi skapar dessa två genom kodraden `const [products, setProducts] = useState([]);`. Vi sätter även ett startvärde för `products` genom att skicka med en tom array som argument till `useState`.

Det nästa vi gör att skapa en "lista" med `Text` komponenter utifrån `products` arrayen. Arrayen är tom, så vi kommer inte kunna se något, men vi gör förarbetet ändå. Vi utnyttjar en av de förträffliga "higher-order functions" som finns på array prototypen i JavaScript vilket är funktionen [map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map). `map` itererar över en array och för varje element returneras ett nytt element till en ny array.

```javascript
const list = products.map((product, index) => <Text key={index}>{ product.name }</Text>);
```

`list` blir i detta fallet en array fyllt med `Text` komponenter som i sin tur består av ett `key` attibut och produktens namn. Det är en stark rekommendation från Reacts sida att alla list element har en unik key, här utnyttjar vi index för arrayen som den unika nyckel.

När vi har skapat list arrayen vill vi även rita ut den. Det gör vi genom att skapa en `View` och inuti den lägga till list-variabeln med hjälp av {}.

```javascript
  return (
    <View>
      {list}
    </View>
  );
```

Nu är vår `products` varibel än så länge tom så låt oss fylla den med data från Lager API:t.



Hämta data från API {#fetch}
--------------------------------------

[INFO]
Om du inte gjort övningen "[Introduktion till Lager-API:t](kunskap/introduktion-till-lager-api)" än, är det läge nu.
[/INFO]

Vi har i tidigare kurser sett hur vi kan hämta data med hjälp av [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). Och vi kommer använda det tillsammans med React även i denna kursen. Ett bra ställe att börja i dokumentationen för Lager-API:t är [Kodexemplen](https://lager.emilfolino.se/v2#fetch). Vi tar första exemplet där vi hämtar de produkter som är kopplat till din egna specifika API-nyckel.

```javascript
fetch("https://lager.emilfolino.se/v2/products?api_key=[YOUR_API_KEY]")
.then(function (response) {
    return response.json();
}).then(function(result) {

});
```

I exemplet ovan hämtar vi data från den URL som vi har skrivit in. Vi får tillbaka ett svar från servern och vi gör om det till JSON med hjälp av ett Promise. I första `.then()` används funktionen `response.json()` för att returnera JSON. I nästa `.then()` har vi sedan JSON data tillgängligt i `result` variabeln.



useEffect {#useeffect}
--------------------------------------

I React vill vi säkerställa att vi bara hämtar data när vi vill eller att det behövs. Därför ska vi titta på ytterligare en [React Hook `useEffect`](https://reactjs.org/docs/hooks-effect.html), som låter oss utföra såkallade "side effects" i funktionsbaserade komponenter.

`useEffect` anropas av React till exempel när vi går in i en komponent, när vi lämnar komponenten eller State ändras. Vi ska i denna övningen använda `useEffect` för att ladda data när vi laddar komponenten, men kommer längre fram i kursen titta på de andra användningsområden.

Vi börjar med att importera Hooken genom att ändra vår `useState` import till `import { useState, useEffect } from 'react';`. Vi kan nu lägga till följande i vår `StockList` komponent.

```javascript
function StockList() {
  const [products, setProducts] = useState([]);

  useEffect(() => {
    fetch(`${config.base_url}/products?api_key=${config.api_key}`)
      .then(response => response.json())
      .then(result => setProducts(result.data));
  }, []);

  const list = products.map((product, index) => <Text key={index}>{ product.name } - { product.stock }</Text>);

  return (
    <View>
      {list}
    </View>
  );
}
```

Låt oss bryta ner den nya koden som vi la till i komponenten. Längst ut har vi:

```javascript
  useEffect(() => {

  }, []);
```

Vi ser att `useEffect` hooken tar en funktion som första argument och i detta fallet en tom array som andra argument. Den tomma arrayen säkerställer att vi bara anropar funktionen en gång när vi ritar ut komponenten. Hade vi haft med den tomma arrayen hade vår funktionen som vi skickar med som argument till `useEffect` anropats varje gång komponenten uppdaterats. Längre fram i kursen kommer vi lägga variabler i den tomma arrayen och funktionen anrops då varje gång dessa variabler ändras.

Den inre delen av `useEffect` känner vi igen sen ovan. Den stora skillnaden är att vi använder oss av "arrow-functions" för att skriva koden med färre tecken och att vi använder oss av `setProducts` funktionen som vi definierade tidigare med hjälp av `useState`.

```javascript
    fetch(`${config.base_url}/products?api_key=${config.api_key}`)
      .then(response => response.json())
      .then(result => setProducts(result.data));
```

Jag har bytt ut URL'n från det tidigare kodexemplet mot användandet av en konfig fil `config` genom "template literals". `config` är en JSON fil som jag har lagt i katalogen config. Jag importerar den med `import config from "../config/config.json";` och filen innehåller:

```json
{
    "api_key": "[YOUR_API_KEY]",
    "base_url": "https://lager.emilfolino.se/v2"
}
```

Vi bör nu kunna ladda om appen och se att en lista på produkter laddas.



Git {#git}
--------------------------------------

Expo skapar ett Git-repo för oss per automatik och har med en `.gitignore` som tar bort de filerna vi inte vill ha som en del av repot. Vi utnyttjar därför repot som redan skapats.

Vi kan börja med `git status` för att se vilka ändringar som gjorts i repot. Vi kan sedan lägga till ändringar med hjälp av `git add`. Denna första gången kan vi lägga till alla ändringar som gjorts med hjälp av `git add .` om vi står i roten av repot. Vi kan senare i projektet göra det individuellt för varje fil. Vi gör sen en `git commit` för att versionshantera filerna och förbereda för att skicka de till vårt "remote repository" på GitHub. För att lägga till ett meddelande direkt på kommandoraden använder vi oss av `git commit -m "Finished exercises for kmom01"`.

Nu är det dags att skapa ett GitHub "remote repository" enligt [Skapa GitHub repo](https://dbwebb.se/guide/git/skapa-github-repo). Jag hade rekommenderat "lager" som namn för repot på GitHub. Efter att du har skapat ett tomt repo på GitHub kopplar du ihop ditt lokala repo med det på GitHub enligt [Koppla lokalt till remote](https://dbwebb.se/guide/git/koppla-git-github).



expo publish {#publish}
--------------------------------------

För att göra det möjligt att dela med oss av appar på ett enkelt sätt för rättning kommer vi använda Expo's plattform Go. I terminalen i din lager katalog skriver du in `expo publish` och du får nu upp följande val:

```shell
An Expo user account is required to proceed.
? How would you like to authenticate? › - Use arrow-keys. Return to submit.
❯   Make a new Expo account
    Log in with an existing Expo account
    Cancel
```

Välj "Make a new Expo Account" och följ stegen för att skapa ett nytt konto. När du har skapat kontot börjar Expo att bygga appen och skicka den till Expo's webbplats. Efter ett tag ska du få en länk i terminalen och du kan gå till den länken. Där syns en QR-kod och en länk. Kopiera länken och skapa filen `expo.txt` i roten på ditt repo, klistra in länken i den filen och inget annat innehåll. Se till att göra ytterligare en `commit` i ditt repo och en `push` till ditt GitHub repo så `expo.txt` laddas upp där.

---
author: efo
category: javascript
revision:
  "2022-03-07": (A, efo) Första utgåvan inför kursen webapp-v4 VT22.
...
Routing och navigation i React
==================================

Vi ska i denna övning titta på ett sätt att skapa flera olika vyer så vår app kan göra mer än att vara en lagerförteckning.



<!--more-->



Navigation {#navigation}
--------------------------------------

React byggdes från början för att vara ett vy-bibliotek och kan i många sammanhang användas för att bara visa en vy. Vi vill dock ha en del olika vyer i vår applikation så vi väljer att använda [Expos rekommendation](https://docs.expo.dev/guides/routing-and-navigation/) för att hantera navigation.

Vi börjar därför med att installera ett antal olika paket för att hantera detta.

```shell
# stå i me/lager
$ npm install @react-navigation/native
```

För att det ska fungera tillsammans med Expo behöver vi dessutom sätta upp lite konfiguration med hjälp av nedanstående paket.

```shell
# stå i me/lager
$ expo install react-native-screens react-native-safe-area-context
```



Tab navigation {#tabs}
--------------------------------------

Vi vill i vår app använda oss av tab-navigation, dvs att navigationen hamnar längst ner på skärmen och består av små ikoner för de olika vyer. Det är fördelaktigt att på en mobil enhet ha navigationen längst ner då det är lätt och ergonomiskt att nå för användaren.

Vi behöver ett sista paket för att kunna skapa vår tab-navigation så vi installerar det och sen är det dags att titta på lite kod.

```shell
$ npm install @react-navigation/bottom-tabs
```

Vi börjar med att titta på hur strukturen för en tab-navigation ser ut och sen kommer vi anpassa vår applikation från kmom01. I kodexemplet nedan ser vi ett exempel på tab-navigation med två olika sidor, som är kopplat till var sin komponent.

```javascript
<NavigationContainer>
  <Tab.Navigator>
    <Tab.Screen name="Home" component={Home} />
    <Tab.Screen name="Settings" component={Settings} />
  </Tab.Navigator>
</NavigationContainer>
```

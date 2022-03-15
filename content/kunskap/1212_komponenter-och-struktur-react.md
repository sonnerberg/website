---
author: efo
category: javascript
revision:
  "2022-03-07": (A, efo) Första utgåvan inför kursen webapp-v4 VT22.
...
Komponenter och struktur i React
==================================

Vi ska i denna övning titta på hur vi kan använda komponenter för att bygga ut vår applikation. I slutet av övningen tittar vi på strukturen för vår app och specifikt hur vi kan förbättra kommunikationen med Lager-API:t.

Vi tar även en titt på TypeScript och hur vi kan använde det för att skapa en typad app.



<!--more-->



Förkunskaper {#prereqs}
--------------------------------------

Du har gjort uppgiften "[Lager appen del 1](uppgift/lager-appen-del-1-v2)" och övningen "[Routing och navigation i React](kunskap/routing-och-navigation-i-react)".



List-Details {#listdetails}
--------------------------------------

I många sammanhang vill vi kunna gå från en lista med till exempel ordrar till den enskilda ordern och eventuellt tillbaka igen. För att vi ska kunna göra detta i React Native vi behöver en `StackNavigator`. Vi lägger den i vår `Pick`-komponent, som blir som nedanstående.

```javascript
import { createNativeStackNavigator } from '@react-navigation/native-stack';

import OrderList from './OrderList.tsx';
import PickList from './PickList.tsx';

const Stack = createNativeStackNavigator();

export default function Pick() {
    return (
        <Stack.Navigator initialRouteName="List">
            <Stack.Screen name="List" component={OrderList} />
            <Stack.Screen name="Details" component={PickList} />
        </Stack.Navigator>
    );
}
```

Precis som när vi skapade vår Tab-navigation skapar vi i ovanstående kodexempel en `StackNavigator` som har två olika komponenter en `OrderList` och en `PickList`. Låt oss ta en titt på `OrderList`-komponenten först.



List-vyn {#list}
--------------------------------------





Avslutningsvis {#theend}
--------------------------------------

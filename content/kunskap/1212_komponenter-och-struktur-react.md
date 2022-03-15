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

I vår `OrderList`-vy vill vi skriva ut alla ordrar och sedan ha möjligheten för att gå till en plocklista för specifika ordrar, som vi sedan vill kunna packa.

Vi vill börja med att rita ut en rubrik och sedan en lista med alla ordrar som har den specifika statusen "Ny". Vi behöver alltså hämta alla ordrar från lagret och filtrera ut de med rätt status. Från kmom01 vet vi hur vi hämtar och sparar en lista med data som en del av `state` i vår app. Så vi utnyttjar den kunskapen för att göra likadant med ordrar.

```javascript
import { useState, useEffect } from 'react';
import { View, Text, Button } from "react-native";

export default function OrderList({ navigation }) {
    const [allOrders, setAllOrders] = useState([]);

    useEffect(() => {
        fetch(`${config.base_url}/orders?api_key=${config.api_key}`)
          .then(response => response.json())
          .then(result => setAllOrders(result.data));
    }, []);

    const listOfOrders = allOrders
        .filter(order => order.status === "Ny")
        .map((order, index) => {
            return <Button
                title={order.name}
                key={index}
                onPress={() => {
                    navigation.navigate('Details', {
                        order: order
                    });
                }}
            />
        });

    return (
        <View>
            <Text>Ordrar redo att plockas</Text>
            {listOfOrders}
        </View>
    );
}
```

Återigen importerar vi `useState` och `useEffect`. Vi hämtar alla ordrar från Lager-API:t och sparar de som en del av `state` i `allOrders` arrayen. Sedan använder vi ytterligare en av `Array.prototype` funktionerna `filter`. `filter` itererar över alla element i en array och returneras `true` från funktionen läggs elementet i den resulterande array annars läggs den inte till. Vi filtrerar på `order.status` i detta fallet och vill bara ha med de som har status "Ny". Sedan gör vi på samma sätt som tidigare att vi använder `map` för att iterera över alla order med status "Ny". För varje order ritar vi ut en knapp `Button`-komponent.

```javascript
return <Button
    title={order.name}
    key={index}
    onPress={() => {
        navigation.navigate('Details', {
            order: order
        });
    }}
/>
```

Här ser vi att vi skapar en knapp samt ger den ett värde som visas upp (title) och en nyckel (key). Sen använder vi oss av `onPress`-callbacken för att navigera till vår `Details` vy som vi definierade i `StackNavigator`. `navigation` objektet har vi med sen anropet till vår `OrderList`-komponent. Vi skickar med den specifika ordern som parameter till vyn och vi kommer i kommande stycke se hur vi kan hämta in den parametern.



Detalj-vyn {#details}
--------------------------------------

I plocklista-vyn vill vi visa upp information om ordern och sedan vilka produkter som ingår i ordern. Vi kan från `route` objektet som per automatik skickas med som parameter till vår komponent när komponenten är en del av en navigation. Vi ritar sedan ut 

```javascript
import { View, Text, Button } from "react-native";

export default function PickList({ route, navigation }) {
    const { order } = route.params;

    async function pick() {
        await orderModel.pickOrder(order);
        navigation.navigate("List");
    }

    const orderItemsList = order.order_items.map((item, index) => {
        return <Text
                key={index}
                >
                    {item.name} - {item.amount} - {item.location}
            </Text>;
    });

    return (
        <View style={{...Base.base}}>
            <Text>{order.name}</Text>
            <Text>{order.address}</Text>
            <Text>{order.zip} {order.city}</Text>

            <Text>Produkter:</Text>

            {orderItemsList}

            <Button title="Plocka order" onPress={pick} />
        </View>
    )
};
```



En modell i frontend {#modell}
--------------------------------------



Struktur för vår styling {#styling}
--------------------------------------



TypeScript {#typescript}
--------------------------------------


Avslutningsvis {#theend}
--------------------------------------

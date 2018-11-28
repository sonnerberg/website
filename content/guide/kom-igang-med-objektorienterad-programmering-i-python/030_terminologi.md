---
author: aar
revision:
    "2018-11-16": "(A, aar) Första versionen"
...
Objektorienterad terminologi
=======================

* **Klass**: En användardefinierad prototyp för ett objekt som definierar en uppsättning attribut som karaktäriserar alla objekt av klassen. Attributen är klassattribut och instansattribut, som nås via "dot-notation".

* **Klassattribut**: En variabel som delas mellan alla instanser av klassen. Den definieras inuti klassen men utanför klass-metoderna. Ett klassattribut kallas även _statiskt attribut.

* **Instansattribut**: En variabel som är definierad inuti en klass. Den tillhör enbart den instansen av klassen.

* **Instans**: Ett individuellt objekt av en klass.

* **Objekt**: En instans av en klass.

* **Metod**: En funktion som är definierad inuti en klass.

* **Statisk metod**: En metod i klassen som fungerar oberoende av klassen och _self_.

* **Data inkapsling**: Att bundla data med metoderna som använder datan.

* **Operatoröverlagring**: När en klass har implementerat en metod för en operator. "Operator overloading" på engelska.

* **Överskugga**: När en subklass har en metod med samma namn och antal parametrar som en metod i basklassen. "Override" på engelska. 

* **Information hiding**: Att man gömmer intern data, så att den inte kan användas på fel sätt. Hittar ingen bra översättning till svenska.

* **Data abstraktion**: Om både data inkapsling och information hiding används är det data abstraktion. Data abstraction på engelska.

### Information hiding

| Implementation | Typ     | Syfte                                                                                 |
|----------------|---------|---------------------------------------------------------------------------------------|
| name           | publik  | Kan användas hur som helst, var som helst och av vem som helst.                       |
| _name          | skyddad | Använd inte om du inte vet vad du gör. Använd på egen risk                            |
| __name         | manglad | Hindra subklasser från att överskugga metoder och attribut.                           |
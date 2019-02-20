---
author:
    - aar
revision:
    "2019-02-21": (A, aar) Första versionen.
category:
    - oopython
...
Träd Datastrukturer
===================================

[FIGURE src=/image/oopython/kmom05/datastructure_top.png?w=c5 class="right"]

Träd är en vanlig abstrakt datatyp eller datastruktur som lagrar element i en hierarkisk träd struktur, liknar ett arvsträd.

<!--more-->

Träd består av ett root element som har ett subträd av barn med en förälder nod. Det represteras som länkade noder, precis som med en länkad lista. Fast noderna har länkningar till mer än bara nästa. I denna artikeln kommer vi kolla på två binära träd, Heap och Binary Search Tree.


Förutsättning {#pre}
-------------------------------

Du kan grunderna i Python och objektorientering. Du har jobbat igenom övningen [exceptions](kunskap/exceptions) och [Datastrukturer](kunskap/datastrukturer).



Binära träd/Binary Tree {#binary}
-----------------------------
För definitionen av träd kan ni kolla in [Preliminary definition](https://en.wikipedia.org/wiki/Tree_(data_structure)#Preliminary_definition) på Wikipedia, kolla på bilderna och dess texter.

I Binära träd har varje nod max två barn noder, vilket betyder att icke-binära träd kan ha flera barn noder. Det är samma koncept, bara det att ens kod behöver ha koll på flera noder i varje nod. Tänk er en länkad lista med fler referencer.

En nod klass för ett binärt träd kan se ut på följande sätt:

```python
class Node():
    def __init__(self, key, value, parent=None):
        self.key = key
        self.value = value
        self.parent = parent
        self.left = None
        self.right = None
```



Heap {#heap}
------------------------------

Heap är ett specialiserat träd där förälder noden har ett värde som antingen är högre eller lägre än sin barn. Om föräldern alltid är högre kallas det en Max Heap och om det är mindre heter det en Min Heap.

[FIGURE src=/image/oopython/kmom05/heap1.png caption="Max heap."]

Varje cirkel representeras av en nod (Node) som har en referens till sin förälder och två barn. Noden "30", key är 30, har exempelvis en referens till förälder noden "75". Om ni vart uppmärksamma på bilden så har ni märkt att varje barn nod har ett värde som är lägre än föräldern, detta är för att det är en Max Heap på bilden. Det innebär att root noden i trädet innehåller det högsta värdet som finns sparat i strukturen och varje nods barn har lägre värde än sig själv.

Max Heap och Min Heap kallas även för PriorityQueue, då vi kan använda dem för att skapa en prioriterad kö. Om vi alltid plockar ut root elementet kommer man alltid få ut det värde som har högst eller minst värde i strukturen. Då blir det som en kö fast istället för Fisrt in First out beror det på vilket värde man har, eller prioritet som det kallas.

När man lägger till ett värde i en Heap läggs värdet sist/längst ner. Sen jämförs det med sin förälder. Är det nya värdet mindre så blir det ett barn till den föräldern. Är det nya värdet större kommer barnet ta förälderns plats och en ny jämförelse sker på nästa förälder. På så sätt kommer alltid det största värdet vara i toppen, i "roten". Man lägger alltid till nya värden sist för att hålla trädet balanserat och med så få nivåer som möjligt.

###Lägga till {#lagga-till}  

Stegen som tas för att lägga till värden är:  
1. Lägg till element i den lägsta nivån.  
2. Jämför värdet med föräldern. Är föräldern större, stanna.  
3. Annars byt plats på dem och upprepa steg 2.

Vi lägger till värdet "80":  

[FIGURE src=/image/oopython/kmom05/heap2.png]

80 är större än sin förälder, 30. De ska då byta plats:  

[FIGURE src=/image/oopython/kmom05/heap3.png]  

Samma gäller för nästa förälder. 80 är större än 75, så de ska byta plats:  

[FIGURE src=/image/oopython/kmom05/heap4.png]  

80 är mindre än 100 så nu ligger det nya värdet på rätt plats. Om vi lägger till ett nytt värde nu så hamnar det till vänster under noden "10". Det har skett en så kallad "inplace"-sortering.



###Ta bort värde {#ta-bort-varde}  

När man extraherar ett värde från heapen tar man alltid roten, i detta fallet det största då det är en max-heap.  

Stegen som tas för att ta bort ett värde är:  
1. Byt ut roten mot sista elementet på den sista nivån.  
2. Jämför den nya roten med sina barn. Är barnen mindre, stanna.  
3. Annars byt plats med det största barnet och upprepa steg 2. (Byt med minsta barnet i en min-heap)  

Vi tittar på hur det kan se ut:  

[FIGURE src=/image/oopython/kmom05/heap5.png]  

30 är mindre än båda sina barn så vi byter plats med det största barnet:  

[FIGURE src=/image/oopython/kmom05/heap6.png]  

Ett barn är mindre så vi skiftar plats:  

[FIGURE src=/image/oopython/kmom05/heap7.png]

Nu håller trädet måttet för att kallas en max-heap. Om vi skulle haft en min-heap istället hade det varit det minsta värdet i roten.



Binary Search Tree {#bst}
------------------------------
Hej


Avslutningsvis {#avslutning}
------------------------------

Något här också.

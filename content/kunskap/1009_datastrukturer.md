---
author: lew
revision:
    "2017-02-08": (A, lew) First version.
category:
    - oopython
...
Datastrukturer
===================================

[FIGURE src=/image/oopython/kmom05/datastructure_top.png?w=c5 class="right"]

Inom programmering är en 'datastruktur' en struktur för att organisera data. Valet av datastruktur är viktigt då de har olika betydelse för prestanda och presterar olika beroende på vilka algoritmer som har planerats att användas. En datastruktur är en abstrakt beskrivning till skillnad från 'datatyper'. En datatyp kan vara exempelvis _Integer_, _String_ eller _boolean_. Det har en fast betydelse medan en datastruktur beskriver något _odefinierbart_, till exempel en lista eller array.

<!--more-->

Det finns många olika datastrukturer i olika kategorier. Vi har "Linjära datastrukturer" (Lista, Stack, Kö, etc.). En annan struktur-kategori som har en stor plats inom programmering är "Träd". De är lite mer komplexa än till exempel en Stack. Vi ska gå igenom en typ av träd, en så kallad "Max Heap".  

Många datastrukturer finns redan inbyggda i programmeringsspråken (tex lista i Python) och det finns färdiga moduler och bibliotek som har strukturen implementerad och klar. Det är dock viktigt att ha en insikt i hur de fungerar "på insidan".

I artikeln kommer det tas upp tre olika datastrukturer.  
* Stack (Linjär datastruktur)  
* Kö (Linjär datastruktur)  
* Max Heap (Träd)



Förutsättning {#pre}
-------------------------------

Du kan grunderna i Python och objektorientering. Du har jobbat igenom övningen [exceptions](kunskap/exceptions).



Stack {#stack}
------------------------------

[FIGURE src=/image/oopython/kmom05/stack.jpg?w=c5 class="right"]

En **Stack** är en linjär datastruktur som påminner om, precis som det låter, en trave eller stapel. Tänk dig en stapel med tallrikar där en tallrik representerar ett objekt, variabel eller vad det nu är man lagrar. För att hantera "insättning och uttag" arbetar man från toppen. Arbetssättet kallas "LIFO" (Last In First Out). En Stack innehåller samma datatyp.

Man använder sig oftast av en särskild uppsättning metoder:  
1. .push() (Lägger till)  
2. .pop() (Tar bort)  
3. .peek() (Visar vad som ligger överst utan att ändra i stacken)  
4. .is_empty() (Returnerar True/False beroende på om stacken är tom)  
5. .size() (Returnerar antal element i stacken)

[FIGURE src=/image/oopython/kmom05/stack_explained.png caption="En Stack med specifierat antal platser."]

En implementation av en Stack kan se ut som följer:  
```python
class Stack:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return self.items == []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        try:
            return self.items.pop()
        except IndexError:
            return "Empty list."

    def peek(self):
        return self.items[len(self.items)-1]

    def size(self):
        return len(self.items)
```

Att arbeta med stacken kan gå till så här:
```python
>>> from stack import Stack
>>> myList = Stack()
>>> myList.push(3)
>>> myList.push(19)
>>> myList.push(5)
>>> myList.peek()
5
>>> myList.pop()
5
>>> myList.peek()
19
>>> myList.size()
2
>>> myList.is_empty()
False
>>> myList.pop()
19
>>> myList.pop()
3
>>> myList.pop()
'Empty list.'
>>> myList.size()
0
```



Queue {#queue}
------------------------------

[FIGURE src=/image/oopython/kmom05/queue.png?w=c5 class="right"]

En **Queue** (kö) är en linjär datastruktur som påminner om en Stack. Skillnaden är att en Kö är öppen i båda ändar. Den ena änden används för att lägga till element och den andra för att ta bort element. Arbetssättet kallas "FIFO" (First In First Out).

Metoderna som används är vanligtvis:  
1. .enqueue() (Lägger till)  
2. .dequeue() (Tar bort)  
3. .peek() (Visar vad som ligger överst utan att ändra i kön)  
4. .is_empty() (Returnerar True/False beroende på om kön är tom)  
5. .size() (Returnerar antalet element i kön)

[FIGURE src=/image/oopython/kmom05/queue_explained.png caption="En kö utan specifierat antal platser."]

En implementation av en Queue kan se ut som följer:  
```python
class Queue:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.insert(0,item)

    def dequeue(self):
        try:
            return self.items.pop()

        except IndexError:
            return "Empty list."

    def peek(self):
        return self.items[len(self.items)-1]

    def size(self):
        return len(self.items)

```

Att arbeta med en Queue:
```python
>>> from queue import Queue
>>> myList = Queue()
>>> myList.is_empty()
True
>>> myList.enqueue("Tiger")
>>> myList.enqueue("Lion")
>>> myList.enqueue("Moose")
>>> myList.is_empty()
False
>>> myList.dequeue()
'Tiger'
>>> myList.peek()
'Lion'
>>> myList.enqueue("Godzilla")
>>> myList.dequeue()
'Lion'
```


Länkad lista {#lankad_lista}
------------------------------

För både Queue och Stack har vi använt oss av Pythons inbyggda List:a för att lagra värden, så än så länge har vi bara gjort en specialversion av Pythons List. Tanken är att vi inte ska behöva List utan att vi ska bygga hela datastrukturen själva. För att lyckas med det ska vi använda oss av noder och kommer bygga en egen länkad lista. Queue och Stack är även bara en specialversion av Länkad lista.

Vi kan tänka oss en vanlig List/Array som bilden nedan. Arrayen ligger sparad i minnet som en bit och i den biten ligger värdena ordnade efter varandra. Då behöver vi inte ha koll på var varje värde ligger utan bara arrayen.

[FIGURE src=/image/oopython/kmom04/array2.png caption="Array i minnet"]

För en länkad lista med noder kan vi inte göra antagandet att värdena ligger intill varandra utan de allokeras till olika platser i minnet. Därför måste varje värde i den Länkade listan ha koll på nästa värde. Det använder vi en Node klass för.  

[FIGURE src=/image/oopython/kmom04/linked_list.png caption="Länkad lista med noder"]  

Den enklaste versionen av en Node klass innehåller bara två attribut, ett för att hålla data och ett för att hålla koll på nästa nod. Den typen av listor kallas för enkellänkade listor. Det finns även dubbellänkade listor, då är varje nod kopplad till noden före och efter.

[FIGURE src=/image/oopython/kmom05/noder.png caption="Enkel- och dubbellänkade noder"]  

En annan vanlig typ är Cirkulär länkad lista. I en Cirkulär länkad lista är sista noden länkad till den första.

[FIGURE src=/image/oopython/kmom04/circl-list.png caption="Cirkulär Enkellänkad lista"]

Sen finns det så klart också Cirkulär dubbellänkad lista och de kan vara sorted eller unsorted. En sorted lista sorterar automatiskt lista. När man lägger in ny data i listan letas hela listan igenom för att hitta rätt plats i ordningen. En unsorted lista lägger enbart till värdet, oftast sist i listan.

## Nod klassen {#nod}

Då ska vi titta på hur koden kan se ut för nod klassen. Det behövs väldigt lite kod då vi enbart behöver ett attribut för data och ett för nästa nod.

```python
class Node:
    """
    Node class
    """
    def __init__(self, data):
        """
        Initialize object with the data and set next to None.
        next will be assigned later when new data needs to be added.
        """
        self.data = data
        self.next = None
```

Vi testar använda den i python3 interpretatorn.

```python
>>>n1 = Node(1)
>>>n1
<__main__.Node object at 0x743545132>
>>>n1.data
1
```

Vi har skapat ett Node objekt och testat skriva ut det och dess data.
Nu ska vi skapa ett till objekt och koppla ihop vår `n1` med det nya.

```python
>>>n2 = Node(32)
>>>n2.data
32
>>>n1.next

>>>n1.next = n2
>>>n1.next
<__main__.Node object at 0x7453468745>
>>>n1.next.data
32
```

När vi printar `n1.next` första gången får vi ingen output för värdet är `None`. Efter vi tilldelat "n1.next" till `n2` innehåller "n1.next" vårt "n2" objekt. Då kan vi skrive `n1.next.data` för att komma åt datan, 32 i "n2" objektet.  
Testa själva att skapa en till nod, `n3`, och tilldela till `n2.next`. Skriv ut "n3's" värde via `n1.next.next.data` och `n2.next.data`.



### Traversera noder {#trav_nod}

Vi måste på något sätt traversera igenom våra node för att kunna hämta, sätta och radera data. Det gör vi lättast med en `while` loop och en temp variabel.

```python
head = Node(0) # Create Node and set as head
temp = Node(2) # Create Node and assign to temp variable
temp.next = Node(4) # Create Node and assign to temp.next
head.next = temp # Assign head.next to temp
```
Ovanför skapar vi en enkel lista som innehåller `[0, 2, 4]`. Listan skapas i följande ordning `0`, `2`, `[2, 4]` och sist sätts den ihop `[0, 2, 4]`.  
Nu ska vi traversera igenom den för att hämta ut ett värde med index.

```python
# Get value by index
if head is not None:
    current_node = head
    counter = 0
    pass
else:
    pass
    # Raise exception for index out of bound
```
Vi börjar med att kolla så "head" inte är `None`, alltså att listan är tom. Sen skapa vi variabeln `current_node` som vi kommer använda när vi traversera för att hålla noden vi är på. `counter` används för räkna vilket index vi är på. Om listan då är tom, `head == None`, vet vi att vad än index är så kommer det vara out-of-bound och ska då lyfta ett exception.  
Nu ska vi skapa en loop som går igenom listan.

```python
# Get value by index
if head is not None:
    current_node = head
    counter = 0
    while current_node.next is not None and counter < index:
        current_node = current_node.next
        counter += 1
else:
    pass
    # Raise exception for index out of bound
```

Vi har en "while" loop som kör så länge det finns en nästa nod, alltså `head.next` inte är `None`, och vår räknare är under `index`. `index` ska innehålla vilket index vi vill hämta värdet från. Om "next" inte är "None" ändrar vi `current_node` till nästa nod och ökar räknaren med ett. Med andra ord fortsätter loopen antingen tills listan är slut eller `counter == index`.

```python
# Get value by index
if head is not None:
    current_node = head
    counter = 0
    while current_node.next is not None and counter < index:
        current_node = current_node.next
        counter += 1
    if counter == index:
        print(current_node.data)
    else:
        # Raise exception for index out of bound
        raise IndexError()
else:
    # Raise exception for index out of bound
    raise IndexError()
```

Efter vår while loop behöver vi kolla om den tog slut för att index är för högt eller om vi har hittat index. Om vi är på index printar vi värdet annars lyfter vi ett index-out-of-bounds error.  
Detta är ett sätt att skriva koden för att leta igenom en lista för ett index, det finns minst 20 andra sätt att skriva den på. Försök gärna komma på andra sätt att skriva den.

Nu har vi kod för att hämta från listan och även sett hur vi kan koppla ihop flera noder. Hur gör vi för att ta bort en nod från listan?

### Ta bort nod {#del_node}

För att ta bort en nod behöver vi först traversera igenom noderna och hitta noden som ska raderas. Sen kopplar vi om noden som är före till noden efter den vi vill ta bort. Sist radera vi noden vi vill ta bort, `del temp`.

[FIGURE src=/image/oopython/kmom04/del_node.png caption="Ta bort en nod"]

### Lägg till nod {#add_node}

När vi ska lägga till en nod är det viktigt med vilken ordning vi gör saker annars kan vi tappa alla noder som ska vara efter den nya vi lägger till. I bilden nedan utgår vi från listan `[0, 2, 4]` och vi vill stoppa in en ny nod, med siffran `5` som värde, mellan `2` och `4`. Listan ska se ut `[0, 2, 5, 4]` när den är klar.

[FIGURE src=/image/oopython/kmom04/add_node.png caption="Lägg till en ny nod"]

Först letar vi upp noden som ska vara framför den nya och tilldelar den till variabeln `temp`. Tilldela `temp.next` till den nya nodens `.next`. Avsluta med att tilldela den nya noden till `temp.next`. Om vi gör det i den här ordningen behöver vi inte vara oroliga för att tappa några noder. Fundera på vad som hade hänt om vi hade skippat steg 2 och istället direkt tilldelade den nya noden till `temp.next`.



Heap {#heap}
------------------------------

Heap ingår inte direkt i kursmaterialet och återkommer inte i någon uppgift eller övning. Det är dock nyttigt att bekanta sig övergripligt med hur den fungerar. Python har en egen modul för bland annat [heap](https://docs.python.org/3.0/library/heapq.html) och [max-heap](https://pypi.python.org/pypi/heapq_max/0.21).

Heap tillhör struktur-kategorin "Träd". Tänk dig en trädliknande struktur:  

[FIGURE src=/image/oopython/kmom05/heap1.png caption="Max heap."]

Varje cirkel representeras av en nod (Node) som har koll på sina föräldrar. Noden "30" vet exempelvis att föräldern "75" är större osv. Lägger man till ett nytt värde hamnar det längst ner i det vänstra benet. Där jämförs det med sin förälder. Är det nya värdet mindre så blir det ett barn till den föräldern. Är det nya värdet större kommer barnet ta förälderns plats och en ny jämförelse sker på nästa förälder. På så sätt kommer alltid det största värdet vara i toppen, i "roten". Man fyller på med nya värden på den första lediga platsen. Man jobbar för att hålla trädet med så få nivåer som möjligt. Det hänger såklart på vilka värden man stoppar in och när.

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

Såja. Nu ligger det nya värdet på rätt plats. Lägger vi till ett nytt värde nu så hamnar det till vänster under noden "10". Det har skett en så kallad "inplace"-sortering.



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



Avslutningsvis {#avslutning}
------------------------------

Det finns som sagt många sorters datastrukturer. För en lista kan du kika på: [List of datastructures](https://en.wikipedia.org/wiki/List_of_data_structures). Här har vi tagit upp tre utav de vanligaste. Hoppas du har fått en liten insikt i hur de fungerar.

---
author: aar
category: python
revision:
  "2017-05-29": (A, aar) Första utgåvan inför kursen Python.
...
Introduktion till variabler och datatyper
==================================

I den här artikeln ska vi lära oss vad värden och variabler är i programmering. Vi ska också titta på hur man skriver ut information till terminalen och hur man kan mata in information till programmet från terminalen. När du har jobbat igenom artikeln har du gjort ett program som tar emot ett namn och en ålder från användaren, åldern används bland annat till att räkna ut födelseår. Namnet, ålder och födelseåret används i en hälsning som skrivs ut i terminalen.  
Vi kommer gå igenom hur man skriver kod i en fil och kör den koden från terminalen.

Du kan hitta koden för detta exempel på [Github](https://github.com/dbwebb-se/python/blob/master/example/first_program/) och i `example/first_program`.

<!--more-->

# Ordlista {#ordlista}
* Funktion
* Argument
* Interpretator
* Exekvera


Förkunskap {#forkunskap}
--------------------------------------

Du har gjort övningen [Kom igång med ditt första program i Python](kunskap/kom-igang-med-ditt-forsta-program-i-python)".



Introduktion {#introduktion}
--------------------------------------

När du programmerar skapar du ofta ett program som har ett specifik syfte. Du har en startpunkt och en slutpunkt. Det är viktigt att veta vad du börjar med och hur det ska fungera när du är klar. För att ta dig från punkt A till punkt B kan vi bland annat använda oss av värden och variabler. 

Vi ska börjar med att skriva ett program som skriver ut en hälsning och en ålder. Sen utvecklar vi programmet så det tar emot inmatning (input) från användare under exekveringstiden (när programmet körs). Ett namn och en ålder ska skickas in och användas hälsningen. Vi avslutar med att även räkna ut vilket år personen föddes.


Värden och typer {#varden-och-typer}
--------------------------------------

Inom programmering används värden, t.ex. heltalet 4 (Integer) eller en text "Hello world" (String). Värden är av olika typer, vilket ger dem olika egenskaper i koden.

### Heltal (Integer) {#heltal}

Vi kan använda oss av heltal, även kallat _Integer_ på engelska (förkortas med __int__), för bland annat göra [matematisk operation](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex).

Följande kod är exekverad i Python interpretatorn, skriv `python3` i din terminal. För att lämna Python interpretatorn håll in "ctrl+d" eller skriv `exit()`. Skriv koden själv, läs inte bara.

```python
>>> 4 + 4
8
>>> 0 * 8
0
>>> 5 % 3
2
>>> 3 + 4 + 4 * 2
15
>>> 3 + (4 + 4) * 2
19
```

Vid [operationer](https://sv.wikipedia.org/wiki/Operation_(matematik)) (+ , - , / ...) följer Python den matematiska konventionens prioriteringar:

1. Paranteser.
1. Upphöjning (exponentiering).
1. Multiplikation och Division.
1. Addition och subtraktion.
1. Operatorer med samma prioritering exekveras från vänster till höger.



### Decimaltal (Float) {#decimaltal}

`3.14` är ett decimaltal och heter _Float_ på engelska. Decimaltal (Float) precis som heltal (Integer) användas för att göra matematiska operationer. Det går även att blanda Floats och Integers när man  gör aritmetik.

```python
>>> 3.14 + 3
6.140000000000001
>>> 3.14 + 3.14
6.28
>>> 2.5 * 4
10.0
>>>
```



### Sträng (String) {#strang}

Textvärden heter [_sträng_](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str) på svenska och _string_ på engelska (förkortas med __str__). En String är en sekvens av karaktärer omslutna av enkla ('), dubbla (") eller trippla (' ' '/" " ") citattecken. Vi vet att `"Hello world"` är en sträng (ett textvärde) för att den är omsluten av citattecken. En sträng kan inte innehålla samma typ av citattecken som den är omsluten av, en sträng avslutas så fort ett likadant citattecken påträffas i sekvensen.  
I koden nedanför visas vårt första felmeddelande. Felmeddelanden visas när program "crashar", de slutar exekvera för att något gick fel. Vi får ett felmeddelande för att vi försöker skriva värdet `"It"s Learning"`, alltså en sträng skapad med `"` och innehåller en `"`. Kolla på felmeddelandet och se om du förstår vad felet är, jag förklarar felet i texten under koden.

```python
>>> "3.14"
'3.14'
>>> "It's Learning"
"It's Learning"
>>> 'It"s Learning'
'It"s Learning'

>>> "It"s Learning"
  File "<stdin>", line 1
    "It"s Learning"
        ^
SyntaxError: invalid syntax
```

Python interpretatorn klarar bara av att exekvera kod som följer en viss struktur. När vi skriver `"It"s Learning"` skapar vi en sträng som innehåller karaktärerna 'It'. När den andra `"` påträffas i koden avslutas strängen och då blir de efterföljande karaktärerna inte en del av strängen. Python interpretatorn klara inte av att det kommer ett `s` efter en sträng och då stoppas programmet och interpretatorn visar felet som vi ser ovanför, ett så kallat syntax fel. Syntax fel betyder att koden inte är korrekt skriven. Vi kan även se att koden är på rad 1 och en "^" som pekar på vart felet är.

Det går att lägga ihop två strängar (konkatenera) med ett "+" mellan två strängar.

```python
>>> "Hello" + "World!"
'HelloWorld!'
>>> "Hello " + "World!"
'Hello World!'
>>> "Hello" + " "  + "World!"
'Hello World!'
```




### Boolean {#boolean}

[Boolean](https://docs.python.org/3/library/stdtypes.html#boolean-values) (förkortas med __bool__) är en datatyp som endast kan var sann eller falsk. Även värden av andra typer kan vara falska eller sanna. Vi kan kolla om ett värde räknas som True eller False med funktionen _[bool()](https://docs.python.org/3/library/functions.html#bool)_. "bool()" är en inbyggd funktion i Python som tar emot ett argument (ett värde) och returnerar True eller False beroende på om värdet räknas som sant eller falskt (skicka in ett värde inom funktionens paranteser och då skickar den tillbaka True eller False). 

```python
>>> bool(0)
False
>>> bool(1)
True
>>> bool(-41)
True
>>> bool(53)
True
>>> bool("")
False
>>> bool("Hej!")
True
>>> bool(0.0)
False
>>> bool(0.1)
True
```
Integern 0, Float 0.0 och en tom String räknas som False medans alla andra Integers och Floats, inklusive negativa, och icke tomma strängar räknas som True.   



För att kolla vilken typ ett värde har kan vi använda den inbyggda funktionen `type()`. Till "type()" kan vi skicka ett värde i paranteserna (ett argument) så returnerar den vilken typ värdet har.

```python
>>> type(4)
<class 'int'>
>>> type("hej")
<class 'str'>
>>> type('hej')
<class 'str'>
>>> type("4")
<class 'str'>
>>> type(3.14)
<class 'float'>
>>> type(False)
<class 'bool'>
```



Vårt program del 1 {#program-del1}
--------------------------------------

Än så länge har vi bara skrivit kod i Python interpretatorn i terminalen, den är jätte bra för att testa små enskilda saker som vi har gjort nu. Men nu ska vi skriva ett sammanhängande program som består av flera rader och då underlättar det att skriva all [kod i en fil](https://www.youtube.com/watch?v=LokzBtJ-ssY&index=2&list=PLKtP9l5q3ce93pTlN_dnDpsTwGLCXJEpd) och exekvera filen i terminalen. Tänk på att när du skriver kod i en fil, till skillnad från i Python interpretatorn, så skrivs inte saker ut av sig själv. Vi måste använda oss av funktionen "print()" för att specifikt skriva ut något i terminalen.  

Programmet vi ska skapa har ett syfte, att skriva ut en hälsning, vilken kod behövs för att uppnå det? Vi behöver en hälsning, alltås ett värde, som ska vara en sträng om hälsningen ska innehålla bokstäver. Sen behöver vi möjligheten att skriva ut värdet i terminalen.

Starta din texteditor, troligen Atom, skapa en ny fil som heter "hello.py" och skriv följande kod:

```python
print("Hej Jack Black, du är 48 år gammal.")
```

Vi använder oss av den inbyggda funktionen `print()`. "print()" tar emot ett argument, vi skickar in en sträng, "Hej Jack Black, du är 48 år gammal.". "print()" skriver ut värdet i terminalen som startade programmet.

För att köra programmet navigera i terminalen, med hjälp av cd, ls och pwd, till mappen din fil ligger i. Starta programmet med kommandot:

```bash
python3 hello.py
```

Då börde du få följande utskrift.

```python
Hej Jack Black, du är 48 år gammal.
```

Behöver kanske gör `chmod 755 hellp.py` först.

I nästa version av progremmet ska vi göra så att användaren som startar programmet får skriva in namnet och ålder. För att kunna skriva ut vad användaren skriver in måste vi använda oss av _variabler_ för att spara värdet som skrivs in.



Variabler {#variabler}
--------------------------------------

Variabler används för att lagra värden som vi kan referera till och manipulera. Fördelen med variabler är att vi kan ge dem förklarande namn, så det lätt att veta vad dem gör när man läser koden, och vi kan återanvända och ändra värdet genom att använda variabeln.  
Vi leker lite i Python3 interpretatorn i terminalen. Tänkt på att använda förklarande variabelnamn.

```python
>>> an_integer = 23
>>> print(an_integer)
23
>>> type(an_integer)
<class 'int'>
```

[FIGURE src=/image/python/variable-memory1.png class="right" caption="an_integer refererar till värdet 23 i minnet."]

Jag börjar med att tilldela heltalet 23 till variabeln `an_integer`. Precis som med värden kan vi använda "type()" funktionern för att kolla vilken datatyp variabelns värde har och som förväntat är det ett heltal (int). Vi fortsätter med att skapa några fler variabler.

```python
>>> a_bool = True
>>> a_string = "en sträng"
>>> a_float = 3.14
```

[FIGURE src=/image/python/variable-memory2.png class="right" caption="Flera variabler refererar vill värden i minnet."]

Nu har jag skapat tre variabler till, en som innehåller en bool, en med en sträng och en som innehåller ett decimaltal. Vi kan byta de värden variablerna har.

```python
>>> a_bool = False
>>> print(a_bool)
False
>>> a_float = a_string
>>> print(a_float)
'en sträng'
```

[FIGURE src=/image/python/variable-memory3.png class="right" caption="Flera variabler refererar vill värden i minnet."]

Först ändrar jag värdet på `a_bool` till False. Sen sätter jag `a_float` till värdet av `a_string`, då får a_float en kopia av a_string's värde.

## Namngivning och Keywords {#namngivning_keywords}

När du namnger något ska det var på engelska, beskrivande och dokumentera av vad variabeln används till. Variabelnamn kan innehålla både bokstäver, siffror och vissa andra karaktärer men får inte börja på siffror. Om ditt namn ska innehålla flera ord bör du seperera dem med ett "\_", det är inte tillåtet med mellanslag (" ") i namn.

Vi kikar på några namn.

```python
>>> 23_number = 23
  File "<stdin>", line 1
    23_number = 23
            ^
SyntaxError: invalid syntax
```

Variabelnamnet, "23_number", börjar på en siffra och då får vi ett SyntaxError. Det betyder att interpretatorn inte kan läsa din kod, den är skriven på fel sätt.

```python
>>> number 23 = 23
  File "<stdin>", line 1
    number 23 = 23
            ^
SyntaxError: invalid syntax
```

Ett till SyntaxError för att namnet innehåller ett " ".

Vissa ord går inte att använda då de är så kallade "keywords", det betyder att Python har reserverat dem och de betyder speciella saker i koden. Följande keywords finns i Python3.

```python
'False',    'None',     'True',     'and',      'as',
'assert',   'break',    'class',    'continue', 'def',
'del',      'elif',     'else',     'except',   'finally',
'for',      'from',     'global',   'if',       'import',
'in',       'is',       'lambda',   'nonlocal', 'not',
'or',       'pass',     'raise',    'return',   'try',
'while',    'with',     'yield'
```

Detta betyder att vi till exempel inte kan döpa en variabel till `and` men ett variabelnamn kan fortfarande innehålle "and", t.ex. `android`.

```python
>>> android = "Mitt namn kan innehålla and"
>>> and = "Jag kan inte heta and"
  File "<stdin>", line 1
    and = "Jag kan inte heta and"
      ^
SyntaxError: invalid syntax
```

Jag får ett SyntaxError när jag försöker döpa variabeln till ett keyword.



Uttryck {#uttryck}
--------------------------------------

Ett uttryck, _Expression_ på engelska, kan vara ett värde, en operation eller en variabel. Man kan säga att det är något som resulterar i ett värde. I följande kod är varje rad ett uttryck.

```python
True
"Hej" + " då"
2 / 3
round(3.14)
```

På sista kodraden använder jag en till inbyggd funktion, `round()` tar emot ett argument, ett decimaltal, och skickar tillbaka (returnerar) värdet avrundat. "round(3.14)" resulterar i "3".



Sats {#sats}
--------------------------------------

En sats, _Statement_ på engelska, är något som gör något. Ett program består av en sekvens av minst en sats. Det kan vara svårt att veta skillnaden på ett uttryck och en sats då ett uttryck också är en sats och definitionen att ett "uttryck producerar ett värde" och "en sats gör något" inte alltid stämmer. Vi tittar på några statements.

```python
print(43)
x = "heej"
print(x)
5 + 5 / 3
```

Sista raden är både ett uttryck och en sats.

Ta en 10 min paus innan du fortsätter med nästa del. Tänk igenom vad du har lärt dig, kanske kolla igenom det lite snabbt igen.



Vårt program del 2 {#program-del2}
--------------------------------------

Vi går tillbaka till vår fil "hello.py" och fortsätter utveckla vårt program. Nästa steg är att be användaren skriva in namn och ålder och använda det i utskriften. Del 2 var att användaren ska mata in vilket namn och vilken ålder som ska användas i hälsningen. Vad behöver vi i koden? Vi behöver få input från användaren, namn och ålder, spara värdena så vi kan använda dem, bygga hälsnings strängen med värdena och skriva ut hälsningen.

Först ska vi kommentera koden vi redan har så andra utvecklare och du själv vet vad den gör.



### Kommentera {#kommentera}

Kommentarer används för att förklara vad kod och program gör så att andra utvecklare lätt vet vad saker ska göra. Du gör det även för dig själv, om det var länge sedan du jobbade med en kod och sen återvänder kan det vara svårt att komma ihåg vad all kod gör, då är det bra om du har kommenterat den.  
Karaktären "#" används för att kommentera en rad. När Pyhton interpretatorn läsern en "#" vet den att allt som kommer efter här på denna raden är en kommentar och försöker inte exekver det som kod.

Vårt program innehåller inte mycket än så länge men vi kan lägga en kommentar överst i filen som förklarar vad programmet ska göra.

```python
# Programmet skriver ut en hälsning till Jack Black

print("Hej Jack Black, du är 48 år gammal.") # Skriver ut ett string värde
```

Du kan testa köra programmet igen för att se att kommentaren inte har påverkat programmet.

```bash
python3 hello.py
Hej Jack Black, du är 48 år gammal.
```

Det finns en till typ av kommentar som kallas _Docstring_. Den brukar användas överst i filer för att förklara vad koden i filen gör eller när en kommentaren är flera rader lång. Docstring görs med trippel citattecken `"""`.

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""

print("Hej Jack Black, du är 48 år gammal.") # Skriver ut ett string värde
```



### Inmatning {#inmatning}

Funktionen "[input()](https://docs.python.org/3/library/functions.html#input)" gör att användaren kan mata in ett strängvärde till programmet.
Vi testar använda "input()" i vår fil.

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""
input()
print("Hej Jack Black, du är 48 år gammal.") # Skriver ut ett string värde
```

Koden exekveras uppifrån och ner och en rad åt gången. När vi testar programmet kommer programmet börja med att vänta på att användaren ska skriva något i terminalen och klicka "enter". Sen exekveras nästa rad som skriver ut vår hälsning. Testa programmet.

```bash
python3 hello.py 
skriver något
Hej Jack Black, du är 48 år gammal.
```

Om du testade köra koden själv märkte du att du inte får någon utskrift när du ska mata in en sträng, jag skrev "skriver något" som inmatning. I fall du vill få en utskrift när du ska skriva in kan du skicka en sträng som ett argument till "input()" funktionen som skrivs ut när användaren ska skriva in. Vi testar.

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""

input("Skriv något, klicka sen enter: ")
print("Hej Jack Black, du är 48 år gammal.") # Skriver ut ett string värde
```

Testa starta ditt program.

```bash
python3 hello.py 
Skriv något, klicka sen enter: skriver något igen
Hej Jack Black, du är 48 år gammal.
```

Jag skrev in "skriver något igen". Än så länge gör vi inget med värdet vi har skrivit in. "input()" är en funktion som returnerar värdet vi skriver in. Om vi vill spara värdet i en variabel behöver vi tilldela en variabel vad "input()" returnerar. Tänk dig att när "input()" returnerar skickas värdet till vänster. Vi ändrar koden igen och ber användaren skriva in namnet, som programmet ska hälsa till, och skriver ut namnet med "print()".

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""

name = input("Skriv ett namn, klicka sen enter: ")
print(name) # Skriver ut ett string värde
```

Nu skapar vi variabeln "name" och tilldelar den värdet av vad "input()" returnerar. Testa exekvera koden.

```bash
python3 hello.py 
Skriv ett namn, klicka sen enter: Jack Black
Jack Black
```

[FIGURE src=/image/python/variable-memory4.png class="right" caption="variabeln 'name' har värdet Jack Black."]

Nu kan vi testa konkatenera (lägga ihop två strängar) namnet med hälsningen.

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""

name = input("Skriv ett namn, klicka sen enter: ") # Ber användaren mata in ett namn
greeting = "Hej " + name + ", du är 48 år gammal." # Sätter ihop "Hej", name och ", du är 48 år gammal." till ett värde.
print(greeting) # Skriver ut ett string värde
greeting = "test" + 24 # Testar konkaternera en stäng med en integer bara för att se vad som händer.
```
Vi skapar variabeln `greeting` och tilldelar den värdet av vad som finns till höger om "=" tecknet. Vi har ett uttryck till höger som resulterar i ett nytt strängvärde som tilldelas till variabeln "greeting". Exekvera koden och se vad som händer. Vad tror du kommer hända när sista raden exekveras?

```bash
python3 hello.py 
Skriv ett namn, klicka sen enter: Jack Black
Hej Jack Black, du är 48 år gammal.
Traceback (most recent call last):
  File "hello.py", line 6, in <module>
    greeting = "test" + 24 # Testar konkaternera en stäng med en integer bara för att se vad som händer.
TypeError: Can\'t convert \'int\' object to str implicitly
```

[FIGURE src=/image/python/variable-memory5.png class="right" caption="Variablerna 'name' och 'greeting' har värden i minnet."]

Nu "crashade" programmet. Läs "Traceback" uppifrån och ner. I filen "hello.py" på rad 6 finns felet, sen har raden som ger felet skrivits ut så vi lätt kan se vilken rad det är. Sist får vi reda på vad för typ av fel vi har, vårt fel är ett `TypeError`. Interpretatorn kan inte göra om en sträng till ett heltals av sig själv. Vi får felet för att vi försöker skapa en ny sträng av en sträng och ett heltal. Utöver den raden funkar programmet som det ska. Namnet vi skrev in användes i hälsningen. Vi tar bort den sista raden igen och går vidare.

Nu kan användaren bestämma namnet, nästa steg är att bestämma åldern. Då behöver vi en till "input()". Allt "input()" returnerar är av typen sträng, så även om vi skriver in siffror i terminalen blir de inte ett heltal utan en sträng.

```python
"""
Programmet skriver ut en hälsning till Jack Black
"""

name = input("Skriv ett namn, klicka sen enter: ") # Ber användaren mata in ett namn
age = input("Skriv en ålder, klicka sen enter: ") # Ber användaren mata in en ålder
greeting = "Hej " + name + ", du är " + age + " år gammal." # Sätter ihop "Hej", name, ", du är ", age och " år gammal." till ett värde.
print(greeting) # Skriver ut ett string värde
```

Vårt program frågar nu efter ett namn följt av en ålder. Vi sparar namnet och åldern i två variabler som används för att skapa en ny sträng som sparas i variabeln "greeting". Vi avslutar med att skriva ut innehållet av "greeting" till terminalen.

```bash
python3 hello.py 
Skriv ett namn, klicka sen enter: Bo Burnham
Skriv en ålder, klicka sen enter: 27
Hej Bo Burnham, du är 27 år gammal.
```

[FIGURE src=/image/python/variable-memory6.png class="right" caption="Variablerna 'name' och 'greeting' har värden i minnet."]

Nu börjar det likna något, vi har kvar att räkna ut året då personen föddes och lägga till det i utskriften. 



Vårt program del 3 {#program-del3}
--------------------------------------

Vi räknar ut vilket år personen föddes med hjälp av åldern som användaren skriver in och ett _hårdkodat_ värde för vilket år det är nu. Ett hårdkodat värde skapas i koden, det kommer inte från inmatning. Vi behöver ett heltalsvärde för vilket år det är nu, räkna ut födelseåret och lägga in det i hälsninen.

Jag tar bort kommentarerna på gammal kod för att det ska bli luftigare i koden och lättare för dig att läsa den nya.

```python
year = 2017 # Hårdkodat värde för vilket år det är

name = input("Skriv ett namn, klicka sen enter: ")
age = input("Skriv en ålder, klicka sen enter: ")

year_born = year - age # Födelseår räknas ut. (2017 - inmatat värde)

greeting = "Hej " + name + ", du är " + age + " år gammal och föddes år " + year_born
print(greeting)
```

Läs igenom koden noggrant så du förstår vad som händer och starta sen programmet.

```bash
python3 hello.py 
Skriv ett namn, klicka sen enter: Bo Burnham
Skriv en ålder, klicka sen enter: 27
Traceback (most recent call last):
  File "hello.py", line 11, in <module>
    year_born = year - age # Födelseår räknas ut. (2017 - inmatat värde)
TypeError: unsupported operand type(s) for -: 'int' and 'str'
```

Var du beredd på felet? Jag skrev tidigare att allt "input()" returnerar är av typen sträng och vi har sett att vi inte kan blanda strängar och heltal i operationer. Därför får vi ett TypeError fel på rad 11 i "hello.py" när vi försöker göra 2017 minus "27".

### Typkonvertering {#typkonvertering}

För att kunna använda värdet, ålder, vi får från "input()" behöver vi ändra dess typ från sträng till heltal. Vi har redan gjort detta med bool värden. Då använde vi funktionen "bool()", nu ska vi använda funktionen `int()`. "int()" tar emot ett argument, ett värde, och returnerar det värdet som typen integer.

```python
year = 2017 # Hårdkodat värde för vilket år det är

name = input("Skriv ett namn, klicka sen enter: ")
age = input("Skriv en ålder, klicka sen enter: ")

year_born = year - int(age) # Födelseår räknas ut. Gör om age från string till integer med int()

greeting = "Hej " + name + ", du är " + age + " år gammal och föddes år " + year_born
print(greeting)
```

Nu räknar vi ut "year_born" med "year" (2017) minus "age" (inmatat värde). Kan du se nästa fel?

```bash
python3 hello.py                                  
Skriv ett namn, klicka sen enter: Bo Burnham
Skriv en ålder, klicka sen enter: 27
Traceback (most recent call last):
  File "hello.py", line 13, in <module>
    greeting = "Hej " + name + ", du är " + age + " år gammal och föddes år " + year_born # Sätter ihop "Hej", name, ", du är ", age och " år gammal." till ett värde.
TypeError: Can\'t convert \'int\' object to str implicitly
```

Läs felmeddelandet uppifrån och ner. Så i Filen "hello.py" på rad 13 har vi ett TypeError, kan inte konvertera från heltal till sträng av sig själv. Med andra ord behöver vi göra om "year_born" till en sträng, med funktionen `str()`, för att kunna konkatenera year_born med resten av strängarna.  
Vi kan göra konverteringen på olika ställen beroende på vad du föredrar. Nedanför visar jag olika ställen i koden vi kan göra konkateneringen.

```python
greeting = "Hej " + name + ", du är " + age + " år gammal och föddes år " + str(year_born) # version 1

year_born = str(year_born) # version 2

year_born = str(year - int(age)) # version 3
```

Nedanför förklarar jag de olika sätten. Tänk på operations prioriteringarna, paranteser räknas ut först. Jag utgår från värdena jag matade in senast jag testade programmet, Bo Burnham och 27.

**Version 1**, vi gör om "year_born" till en sträng när vi konkatenerar den med resten av strängarna.

1. "year_born" konverteras till en sträng.
1. 'Hej' läggs ihop med "Bo Burnham".
1. 'Hej Bo Burnham ' konkateneras med ", du är".
1. 'Hej Bo Burnham, du är ' konkateneras med "27".
1. 'Hej Bo Burnham, du är 27' konkateneras med ' år gammal och föddes år '.
1. 'Hej Bo Burnham, du är 27 år gammal och föddes år ' konkateneras med "1990".

**Version 2**, vi gör om "year_born" till en sträng efter uträkningen.

1. "year_born" konverteras till en sträng.
1. Strängen tilldelas till variabeln "year_born".

**Version 3**, vi gör om "year_born" till en sträng när vi gör uträkningen:

1. "age" blir ett heltal.
1. Räknar ut year - age.
1. Resultatet görs om till en sträng.
1. "year_born" tilldelas strängen.

Jag väljer att använda version 3 i min kod.

```python
year = 2017 # Hårdkodat värde för vilket år det är

name = input("Skriv ett namn, klicka sen enter: ")
age = input("Skriv en ålder, klicka sen enter: ")

year_born = str(year - int(age)) # Födelseår räknas ut. Gör om age från string till integer med int()

greeting = "Hej " + name + ", du är " + age + " år gammal och föddes år " + year_born
print(greeting)
```

Nu borde vi vara färdiga med programmet, det tar namn och ålder som input, räknar ut födelseåret och skriver ut en hälsning med namn, ålder och födelseår. Testa köra programmet och kolla så det funkar.

```bash
python3 hello.py 
Skriv ett namn, klicka sen enter: Bo Burnham
Skriv en ålder, klicka sen enter: 27
Hej Bo Burnham, du är 27 år gammal och föddes år 1990
```

[FIGURE src=/image/python/variable-memory7.png class="right" caption="Variabler refererar till värden i minnet."]



Avslutningsvis {#avslutning}
--------------------------------------

Nu har vi fixat en ikon och en splash screen. I och med att vi bara använder oss av Android kunde vi ha lagt in bilderna direkt i mapparna i `platforms/android/res/` men nu vet vi hur man gör om vi hade haft flera plattformar.

Om du har frågor eller tips så finns det en särskild tråd i forumet om [denna artikeln](t/40777).

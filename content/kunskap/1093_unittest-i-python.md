---
author: lew
revision:
    "2017-12-12": (A, lew) Updated for v2.
category:
    - oopython
...
Att skriva enhetstester
===================================

[FIGURE src=/image/oopython/kmom02/test_top.png class="right"]

Enhetstester, eller *unittester*, används för att testa så enskilda metoder eller funktioner gör det de ska. Till exempel om en metod ska returnera bool-värdet `True`, så ska den aldrig kunna returnera `False`.  

Det var det enklaste fallet av ett enhetstest, men poängen går nog fram.

Vi ska titta lite närmare på de olika delarna av pythons inbyggda testramverk *unittest*. Vi hoppar inte i den djupa delen av bassängen, utan vi håller oss vid det grundläggande delarna.
Vill du läsa mer kan du kika på [docs.python.org](https://docs.python.org/3/library/unittest.html).

<!--more-->



Förutsättning {#pre}
-------------------------------

Du kan grunderna i Python och du vet vad variabler, typer och funktioner innebär.



Varför ska man skriva enhetstester? {#varfor-ska-man-skriva-enhetstester}
------------------------------

Enhetstester skrivs som sagt av anledningen att minimera risken för "trasig" kod och för att validera funktionaliteten. I många lägen handlar det inte bara om att enbart du ska förstå koden, utan det kan finnas andra utvecklare som tar över ditt projekt eller bara ska hjälpa till. Då är det bra om det är testat ordentligt. Har man bra tester som går igenom så har man bra kod.



###Pythons testramverk {#pythons-testramverk}

Python kommer med en inbygg modul, ett ramverk kallat "unittest". Inspirationskällan till det kommer från Javans [JUnit](http://junit.org/junit4/). Vi ska framför allt titta på basklassen *TestCase* som tar hand om enskilda tester på bland annat metoder.



###Kom igång med ett enhetstest {#kom-igang-med-ett-enhetstest}

Artiklen utgår från filerna som vi hittar i [exempelmappen](https://github.com/dbwebb-se/oopython/tree/master/example/unittest). Där hittar vi klassen _Phone_ i `phone.py` och en tillhörande testfil, `test.py`. Det är testfilen som vi skriver våra enhetstester i. Testerna kör man med:

 ```python
 >>> python3 test.py
 ```

Då så. Vi tittar på grundstrukturen i `test.py`:

```python
#!/usr/bin/env python3
""" Module for unittests """

import unittest

class Testcase(unittest.TestCase):
    """ Submodule for unittests, derives from unittest.TestCase """

    # omitted code in explanation purpose

if __name__ == '__main__':
    unittest.main()
```

Vi importerar modulen och skapar en subklass av _unittest.TestCase_. Blocket med _unittest.main()_ kör igång ett interface för testskriptet och producerar en bra utskrift. Notera att vi har med docstrings nu. Docstrings som används i metoderna kommer skrivas ut när testfilen körs.

Ett enkelt test på den inbyggda funktionen *.upper()* kan se ut så här:

```python
#!/usr/bin/env python3
""" Module for unittests """


import unittest

class Testcase(unittest.TestCase):
    """ Submodule for unittests, derives from unittest.TestCase """

    def test_upper(self):
        """ Test builtin uppercase """
        self.assertEqual('programmering'.upper(), 'PROGRAMMERING')

if __name__ == '__main__':
    unittest.main()
```

Vi använder metoden _assertEqual_ för att jämföra om två värden är lika. Följande tabell är hämtad från [docs.python.org](https://docs.python.org/3/library/unittest.html) och visar överskådligt de vanligaste typerna av enhetstester.


| Method                    |        Checks that   |
|---------------------------|:---------------------|
| assertEqual(a, b)	        | a == b	           |
| assertNotEqual(a, b)	    | a != b	           |
| assertTrue(x)	            | bool(x) is True	   |
| assertFalse(x)	        | bool(x) is False	   |
| assertIs(a, b)	        | a is b               |
| assertIsNot(a, b)	        | a is not b           |
| assertIsNone(x)	        | x is None            |
| assertIsNotNone(x)	    | x is not None        |
| assertIn(a, b)	        | a in b               |
| assertNotIn(a, b)	        | a not in b           |
| assertIsInstance(a, b)	| isinstance(a, b)     |
| assertNotIsInstance(a, b)	| not isinstance(a, b) |

Om vi nu kör testet får vi utskriften:

```bash
.
----------------------------------------------------
Ran 1 test in 0.000s

OK


>>> python3 test.py -v
test_upper (__main__.Testcase)
Test builtin uppercase ... ok

----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

Med flaggan `-v` ser vi att vi får en tydligare utskrift, där testerna skrivs ut med. Det fungerar bara om man döper testmetoderna med "test_" i början. Vi ser även docstringen utskriven. Det är trevligt med fina utskrifter så vi kör vidare på det.



###Enhetstesta objekt {#enhetstesta-objekt}

Nu är det dags att titta på hur vi skriver några enhetstester för vår klass, _Phone_. Klassen ligger i filen `phone.py`.

Vi öppnar `test.py` och kikar några delar av koden. Om du undrar varför testerna är döpta med en versal (A-L) så är anledningen att testerna exekveras i bokstavsordning och man vill ha kontroll på när exekveringen ska ske. Med hjälp av _doc-strings_ får vi som sagt bättre utskrifter:

```python
#!/usr/bin/env python3
"""
Unittest file for Phone
"""

import unittest
from phone import Phone

class Testcase(unittest.TestCase):
    """Submodule for unittests, derives from unittest.TestCase"""
    # Create instances to use in the tests
    phone = Phone("Samsung", "Galaxy S8", "Android")
    phone_two = Phone("Apple", "iPhone 8", "iOS")

    # Tests if the objects are the same
    def test_A_equal_objects(self):
        """ Should return True, they are not the same """
        self.assertIsNot(self.phone, self.phone_two)

    # Tests if the objects are instances of Person
    def test_B_are_object_instance_of(self):
        """ Should return True, is is instance of Phone """
        self.assertIsInstance(self.phone, Phone)

    # Tests if owner returns correct when none is set
    def test_C_no_owner(self):
        """Should return 'No owner yet' if correct"""
        self.assertEqual(self.phone.get_owner(), "No owner yet")

    ########## Omitted test D-G ##########

    # Test if phonebook is empty
    def test_H_empty_phonebook(self):
        """Should return False if phonebook is empty"""
        self.assertFalse(self.phone.has_contacts())

    # Test if phonebook is not empty
    def test_I_not_empty_phonebook(self):
        """Should return True if phonebook has contacts"""
        self.phone.add_contact("Andreas", 12345)
        self.phone.add_contact("Emil", 67890)
        self.assertTrue(self.phone.has_contacts())

    # Test phonebook length
    def test_J_phonebook_length(self):
        """Should return the number 2"""
        self.assertEqual(self.phone.get_contacts_length(), 2)

    # Test get contact that not exists
    def test_K_faulty_contact(self):
        """Should return None"""
        self.assertIsNone(self.phone.get_contact("Kenneth"))

    # Test get contact that exists
    def test_L_get_contact(self):
        """Should return tuple with contact name and number"""
        self.assertEqual(self.phone.get_contact("Andreas"), ("Andreas", 12345))



if __name__ == '__main__':
    unittest.main()
```

Ett exempel på varför metoderna är skrivna med A-L kan vi se i testet `test_L_get_contact`. Om testerna inte styrdes med A-L hade testet inte exekverats i rätt läge. Personerna läggs till i `test_I_not_empty_phonebook`, vilken kommer efter `test_L_get_contact` (om vi tar bort versalen) och personen hade då inte funnits i testet. Detta går såklart att motverka på fler sätt, till exempel med att skapa utgångsläget i varje deltest, eller lägga till personerna överst, efter instansieringen. Välj själv väg och ha i åtanke vad det är du vill testa och vilket sätt som hade fungerat bäst.

Kör vi alla test i testfilen får vi resultatet:

```bash
>>> python3 test.py -v

test_A_equal_objects (__main__.Testcase)
Should return True, they are not the same ... ok
test_B_are_object_instance_of (__main__.Testcase)
Should return True, is is instance of Phone ... ok
test_C_no_owner (__main__.Testcase)

Should return 'No owner yet' if correct ... ok
test_D_set_owner (__main__.Testcase)
Should return 'Pelle' if correct ... ok
test_E_prop_manufacturer (__main__.Testcase)
Should return 'Samsung' if correct ... ok
test_F_prop_model (__main__.Testcase)
Should return 'S8' if correct ... ok
test_G_prop_os (__main__.Testcase)
Should return 'Android' if correct ... ok
test_H_empty_phonebook (__main__.Testcase)
Should return False if phonebook is empty ... ok
test_I_not_empty_phonebook (__main__.Testcase)
Should return True if phonebook has contacts ... ok
test_J_phonebook_length (__main__.Testcase)
Should return the number 2 ... ok
test_K_faulty_contact (__main__.Testcase)
Should return None ... ok
test_L_get_contact (__main__.Testcase)
Should return tuple with contact name and number ... ok

----------------------------------------------------------------------
Ran 12 tests in 0.001s

OK
```

Om ett test inte går igenom visas en tydlig utskrift på vad och var felet gäller. Vi rensar filen och lägger in ett test som genererar ett fel:

```python
#!/usr/bin/env python3
"""
Unittest file for Phone
"""

import unittest
from phone import Phone

class Testcase(unittest.TestCase):
    """Submodule for unittests, derives from unittest.TestCase"""

    phone = Phone("Samsung", "Galaxy S8", "Android")

    # Tests if the objects are the same
    def test_error(self):
        """ Should return True, they are not the same """
        self.assertEqual(self.phone.get_model(), "iPhone X")



if __name__ == '__main__':
    unittest.main()
```

Nu kan vi läsa av felmeddelandet när vi kör filen:

```bash
>>> python3 test.py -v

test_error (__main__.Testcase)
Should return True, they are not the same ... FAIL

======================================================================
FAIL: test_error (__main__.Testcase)

Should return True, they are not the same
----------------------------------------------------------------------
Traceback (most recent call last):
  File "test.py", line 16, in test_error
    self.assertEqual(self.phone.get_model(), "iPhone X")
AssertionError: 'Galaxy S8' != 'iPhone X'
- Galaxy S8
+ iPhone X


----------------------------------------------------------------------
Ran 1 test in 0.001s

FAILED (failures=1)
```



Avslutningsvis {#avslutning}
------------------------------

Det här var lite om enhetstester och hur man kan gå tillväga för att testa sin kod. De flesta testerna är relativt självförklarande och kommer inte gås in djupare på. Läs gärna mer om enhetstester:  

* [docs.python.org](https://docs.python.org/3.5/library/unittest.html)  

* [docs.python-guide.org](http://docs.python-guide.org/en/latest/writing/tests/)

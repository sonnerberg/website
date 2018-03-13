---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Inkapsling
==================================

Vi ser hur begreppet inkapsling kan begränsa användandet av objektet och ge möjlighet att uppdatera klassens implementation, utan att störa main-programmet.

Spara koden du skriver i denna övningen i `index_person2.php`.



Inkapsling av medlemsvariabler {#private}
----------------------------------

Ta en kopia av `src/Person1.php` och spara som `src/Person2.php`.

Uppdatera så att klassens medlemsvariabler är `private` istället för `public`. Metoden kan fortsätta vara publik.

```php
class Person2
{
    private $name;
    private $age;

    public function details() {
        return "My name is {$this->name} and I am {$this->age} years old.";
    }
}
```

Ta nu och kopiera `index_person1.php` till `index_person2.php` och uppdatera så att klassen `Person2`används.

Kör programmet, vad händer? Kan du gissa?

[FIGURE src=image/snapvt18/oophp-person2.png?w=w3 caption="Medlemsvariablerna är nu privata och kan inte nås från main-programmet utifrån klassen."]

Vi kommer nu inte åt de privata delarna i objektet. I klassen har vi sagt vilka delar som är `private`.

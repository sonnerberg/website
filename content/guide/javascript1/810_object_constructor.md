---
...
Constructor
==================================

En "konstruktor" är enbart en funktion som hjälper oss att initiera flera objekt från samma bas. Vi tar föregående kod och gör om det till en konstruktor-funktion.

```javascript
function MyObj(size, background) {
    this.size = size;
    this.background = background;
    this.draw = function() {
        var element = document.createElement("div");
        element.style.margin = "5px";
        element.style.height = this.size.h + "px";
        element.style.width = this.size.w + "px";
        element.style.backgroundColor = this.background;
        document.getElementsByClassName("content")[0].appendChild(element);
    }
}

var obj1 = new MyObj({h: 25, w: 54}, "green");
var obj2 = new MyObj({h: 100, w: 250}, "red");
var obj3 = new MyObj({h: 65, w: 147}, "yellow");

var allObjects = [obj1, obj2, obj3];

for (var i = 0; i < allObjects.length; i++) {
    allObjects[i].draw();
}
```

När vi har en konstruktor använder vi nyckelordet `new` samt en stor bokstav i objektets namn.



# Resultat {#resultat}

Om vi nu tittar på resultatet kan vi se att det är likadant som tidigare.

[FIGURE src=/image/javascript/guide/obj-construct.png?w=w3 caption="Former skapade med konstruktor."]

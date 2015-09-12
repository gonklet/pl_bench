#PL Test Cases:

## Arithmatic:

### Basic Arithmetic
 Addition, Subtraction, Multiplication, Division, Exponents, and Modulo.
 
```javascript
var r;
r = 1+1; // 2
console.log(r);
r = 3-2; // 1
console.log(r);
r = 3*2;
console.log(r); // 6
r = 6 2;
console.log(r); // 3
r = Math.pow(6,2);
console.log(r); // 36
r = 6%2;
console.log(r);

```
https://repl.it/BE2

### Bit-Wise Arithmetic
* AND, OR, NOT, XOR, NOR, LSHIFT, RSHIFT
* Bit-Wise Definitions
* Bit-Fields

```c
#include "stdio.h"

int main(void) {
    // Disable stdout buffering
    setvbuf(stdout, NULL, _IONBF, 0);

    unsigned int r= 0xFF; // bit-wise definition
    printf("%d\n", r); // 255
    
    r = r >> 1; // right-shift by 1
    printf("%d\n", r); // 127

    r = r << 1; // left-shift by 1
    printf("%d\n", r); // 254
    
    r = r & 0x0F; // bit-wise AND
    printf("%d\n", r); // 14
    
    r = r | 0x01; // bit-wise OR
    printf("%d\n", r); // 15
    
    r = r & 0x01; // bit-wise XOR
    printf("%d\n", r); // 1

    r = ~0x00; // bit-wise NOT
    printf("%d\n" , r); // -1

    r = ~(r | 0x00); // bit-wise NOR
    printf("%d\n" , r); // 0
    
    return 0;
}
```
https://repl.it/BE4o

### Casting Arithmetic
```c
#include "stdio.h"

int main(void) {
    // Disable stdout buffering
    setvbuf(stdout, NULL, _IONBF, 0);

    int a = 13;
    int b = 15;
    
    printf("%d\n", a/b); // 0
    printf("%f\n", a/b); // 0.000000
    printf("%f\n", (double)(a/b)); // 0.000000
    
    printf("%f\n", (double)a/b); // 0.866667
    printf("%f\n", a/(double)b); // 0.866667

    double c = 7;
    printf("%f\n", a/c); // 1.857143
    
    printf("%f\n", a/(c + b)); // 0.590909
    
    return 0;
}
```
https://repl.it/BE4w

## Object Oriented Programming

### Classes
```c++
#include <iostream>
#include <math.h>
using namespace std;

class Jeep {
private:
    int gas_tank;
public:
    Jeep(int gas) : gas_tank(gas) {
    }
    
    int totalTravelDistance() {
        return 10 * gas_tank;
    }
    
};

int main() {
    Jeep jeep = Jeep(10);
    int distance = jeep.totalTravelDistance();
    cout << "This Jeep can travel for " << distance << " miles." << endl;
}


```
https://repl.it/BE8R/1

### Inheritance
```c++
#include <iostream>
#include <math.h>
using namespace std;

class Jeep {
protected:
    int gas_tank;
public:
    Jeep(int gas) : gas_tank(gas) {
    }
    
    int totalTravelDistance() {
        return 10 * gas_tank;
    }
    
};

class JeepCherokee : Jeep {
public:
    JeepCherokee(int gas) : Jeep(gas) {}

    int totalTravelDistance() {
        return 10 * 1.3 * gas_tank;
    }
    
};

int main() {
    JeepCherokee cherokee = JeepCherokee(10);
    int distance = cherokee.totalTravelDistance();
    cout << "This Jeep can travel for " << distance << " miles." << endl;
}

```
https://repl.it/BFpB

### Multiple Inheritance
```c++
#include <iostream>
#include <math.h>
using namespace std;

class Jeep {
protected:
    int gas_tank;
public:
    Jeep(int gas) : gas_tank(gas) {
    }
    
    int totalTravelDistance() {
        return 10 * gas_tank;
    }
    
};

class TurboEngine {
protected:
    int gas_tank;
    int nitro_tank;
public: 
    TurboEngine(int gas, int nitro) : gas_tank(gas), nitro_tank(nitro)  {
    }
    
    int totalTravelDistance() {
        return (10 * gas_tank) + (15 * nitro_tank);
    }
};

class TurboJeepCherokee : public Jeep, public TurboEngine {
public: 
    TurboJeepCherokee(int gas, int nitro) : Jeep(gas) , TurboEngine(gas, nitro) {
    }
};

int main() {
    TurboJeepCherokee turbo_cherokee = TurboJeepCherokee(10, 3);
    int distance = turbo_cherokee.TurboEngine::totalTravelDistance();
    cout << "This Jeep can travel for " << distance << " miles." << endl;
}
```
https://repl.it/BFrU

### PolyMorphism

```c++
#include <iostream>
#include <string>
#include <math.h>
using namespace std;

class Person {
protected:
    string name;
public: 
    Person(string name) : name(name) {
    }

    string greetings() = 0;

    // string greetings() {
    //     return "Hello, my name is " + name + ".";
    // }
};

class Teacher : public Person {
public:
    Teacher(string name) : Person(name) {
    }

    string greetings() {
        return "Hello, my name is " + name + ".\n" + "I am a teacher.";
    }
};

class Artist : public Person {
public:
    Artist(string name) : Person(name) {
    }

    string greetings() {
        return "Hello, my name is " + name + ".\n" + "I am an artist.";
    }
};

int main() {
    Person* people[3];
    
    people[0] = new Teacher("Jeff");
    people[1] = new Teacher("Tom");
    people[2] = new Artist("Yorik");    
    
    Teacher * tim = new Teacher("Tim");
    cout << tim->greetings() << endl;
    
    for (int i = 0; i < 3; i++) {
        cout << people[i]->greetings() << endl;
    }
    
}
```

### Virtual Methods and Abstract Classes
```c++
#include <iostream>
#include <math.h>
using namespace std;

class Polygon {
public:
    virtual double area() = 0;
};

class Triangle : public Polygon {
protected:
    double base, height;
    
    Triangle() : base(0), height(0) {
    }
public: 
    
    Triangle(double base, double height) : base(base), height(height) {
    }
    
    double area() {
        return 0.5 * base * height;
    }
};

class EquilateralTriangle : public Triangle {
private:
    double side;
public: 
    EquilateralTriangle(double side) : side(side) {
    }
    
    double area() {
        return ( pow(3, 0.5) / 4 ) * side;
    }
}; 

int main() {
    
    Triangle t = Triangle(2,2);
    EquilateralTriangle et = EquilateralTriangle(2);
    cout << t.area() << endl;
    cout << et.area() << endl;
}
```

### Interfaces
```java
interface Greetable {
    public String greetings();
}

class AnnouncementSpeaker{
    private String companyName;
    
    public AnnouncementSpeaker(String companyName) {
        this.companyName = companyName;
        
    }
    
    public void announce() {
        // Some Code...
    }
    
    public String greetings() {
        return "Welcome to " + companyName;
    }    
    
}

class RoboWaiter {
    public String greetings() {
        return "Nice to meet you, I am RoboWaiter." + System.lineSeparator() + "What would you like to orders?";
    }
}

class Main {
  public static void main(String[] args) {
    AnnouncementSpeaker announcementSpeaker = new AnnouncementSpeaker("PL_TEST");
    System.out.println(announcementSpeaker.greetings());
    
    RoboWaiter roboWaiter = new RoboWaiter();
    System.out.println(roboWaiter.greetings());
  }
}
```

### Friends
```c++
interface Greetable {
    public String greetings();
}

class AnnouncementSpeaker{
    private String companyName;
    
    public AnnouncementSpeaker(String companyName) {
        this.companyName = companyName;
        
    }
    
    public void announce() {
        // Some Code...
    }
    
    public String greetings() {
        return "Welcome to " + companyName;
    }    
    
}

class RoboWaiter {
    public String greetings() {
        return "Nice to meet you, I am RoboWaiter." + System.lineSeparator() + "What would you like to orders?";
    }
}

class Main {
  public static void main(String[] args) {
    AnnouncementSpeaker announcementSpeaker = new AnnouncementSpeaker("PL_TEST");
    System.out.println(announcementSpeaker.greetings());
    
    RoboWaiter roboWaiter = new RoboWaiter();
    System.out.println(roboWaiter.greetings());
  }
}
```

## Functional Programming

### Recurssion
```javascript
/*
* Assumes that the sequence starts with index 0.
*/
function fibonacci(index) {
    
    if (index <= 1) return index;
    
    return fibonacci(index - 1) + fibonacci(index - 2);
}

fibonacci(8);

```





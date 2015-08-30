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

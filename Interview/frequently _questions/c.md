- What is difference between Structure and Union ?

> With a union, you're only supposed to use one of the elements, because they're all stored at the same spot. This makes it useful when you want to store something that could be one of several types. 
    
> A struct, on the other hand, has a separate memory location for each of its elements and they all can be used at once.

```
union foo {
  int a;   // can't use both a and b at once
  char b;
} foo;

struct bar {
  int a;   // can use both a and b simultaneously
  char b;
} bar;

union foo x;
x.a = 3; // OK
x.b = 'c'; // NO! this affects the value of x.a!

struct bar y;
y.a = 3; // OK
y.b = 'c'; // OK

```

- What is bit field in C ? What is the benefit of using it ?
> The number of bits in a bit field sets the limit to the range of values it can hold

```
 #include <stdio.h>
 
 struct S {
  // three-bit unsigned field,
  // allowed values are 0...7
  unsigned int b : 3;
 };
 
 int main()
 {
     struct S s = {6};
     ++s.b; // store the value 7 in the bit field
     printf("%d\n", s.b);
     ++s.b; // the value 8 does not fit in this bit field
     printf("%d\n", s.b);// formally implementation-defined, typically 0
 }

```

- What is structure padding ? How to avoid it ?
    > Architecture of a computer processor  read 1 word (4 byte in 32 bit processor) from memory at a time. To make use of this advantage of processor, data are always aligned as 4 bytes package which leads to insert empty addresses between other member’s address.

    [Structure Member Alignment, Padding and Data Packing](https://www.geeksforgeeks.org/structure-member-alignment-padding-and-data-packing/)

    [C – Structure Padding](https://fresh2refresh.com/c-programming/c-structure-padding/)

    [The Lost Art of Structure Packing](http://www.catb.org/esr/structure-packing/)
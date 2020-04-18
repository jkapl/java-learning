# Types
## Primitive Types
- boolean
- byte
  - 1 byte
  - range -128 to +127
  - all numbers are signed
- short
- int
  - 4 bytes
  - range approx. - to + 2 billion
- long
  - huge numbers
- float
  - only 4 bytes to represent number, not as accurate as double
- char
- double
  - double preferred to float for more precision
### Math
- convert double to int
```java
int i = int(3.0);
```

## Reference Types
- Object
  - Supertype for all objects is java.lang.Object
### String
  - Immutable
  - Standard class is java.lang.String
  - The method below will reveal the location in the heap of an object
```java
System.identityHashCode();
```
  - Java strings are immutable (like JavaScript)
  - When concatenation happens, StringBuilder is used to append the strings, toString() is called, a new object is created with the copied contents of the two concatenated strings, and the new object points to a new memory location
  - StringBuilder is mutable, can append to it and then call toString() method
  - String.equals(), String.equalsIgnoreCase(). Lots of cool methods
  - Use an array of char for storage
### Arrays
  - arrays are objects and are immutable
```java
// array literal syntax
int[] intArr = {1, 2, 3};
char[] ac = {'d','o','g'};
String s = new String(ac);
// for each loop in java
for (String s : ac) {
  System.out.println(s)
}
// array decaration style - use new to allocate space in the heap, type for container and number of elements
int[] values = new int[5];
```
# Objects
- Java doesn't really have functions, only methods, strongly OO
## Static methods (class methods)
- Don't need an instance of an object to call
- e.g. `Math.sin(1.0);`
- Java standard library provides thousands
### Method syntax
*return type first, then name of method, then parameters and type expected for each*
- can indicate method returns no data with void keyword
```java
int add(int x, int y) {
    return x + y;
}

String numOfX(int i) {
    return i > 10 ? "XXX" : "X";
}

void printPos(double d) {
    if (d > 0.0) {
        System.out.println("D:" + d);
    }
}
``` 
# Classes
## Constructors
- Name must match name of class
- No return type 
```java
class Pet {
    String name;
    String getName() {
        return name;
    }
    void feed() {
        System.out.println("I'm feeding " + name);
    }
    Pet(String me) {
        name = me;
    }
}
```
# Memory
- Classes point to a space on the heap
- They are references to that memory location
- Method calls (functions) create stack frames that create either local variables in that stack or point to objects on the heap
Areas of memory at runtime
- Per method local variables
- Global shared heap shared between methods/call frames and threads
- Per class read only constant pool
- Per method temporary evaluation stack as there are no registers in the JVM

# Compilation & Execution
- Call javac and Main.java becomes Main.class binary fine
- Everything in java must live in a class
- make classes public
- make methods public or private
- always make fields private
```java
public class Main {
  public static void main (String[] args) {
    System.out.println(System.currentTimeMillis());
    for (String s : args) {
      System.out.println(s);
    }
  }
};
```
- static: don't need an instance of the class main to call this method. Can just call with Main.main()
- Call java Main without the class extension to run the program
## Class loading
- Allows alteration of files before loaded
- Start with .java file on disk, compile to .class file - intermediate representation
- Class files then loaded by class loader, passed to interpreter for execution, then may be further modified by JIT compiler into high performance machine code
- Linking phase
- Verification phase: spends time up front to verify code but gives back speed at runtime 
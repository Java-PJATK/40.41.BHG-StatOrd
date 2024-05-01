# BHG-StatOrd
40 BHG-StatOrd/Stats.java 73 41 BHG-StatOrd/Main.java 74

Cont. from [39.AFL-FunRecur](https://github.com/Java-PJATK/39.AFL-FunRecur)  

## 8.6 Initializing blocks  

Inside the definition of a class, we can put static and non-static initialization blocks.   

They have the form of a block of code enclosed in curly braces; in case of static initializer block we add keyword static if front of it.  

The block must be put outside of any functions!  

The body of the non-static initializer block will be executed in the process of creating any object after the object itself has been created and after its members have
been initialized with default values but before entering a constructor.  

Therefore, we can put into the initializer a code which should be executed at the beginning of any of the overloaded constructors.  

Static initializer block is executed only once: when a class is loaded by the JVM (after creating enum constants, if the class happens to be an enum.) If a class contains also static fields, initialization of static fields comes first, then initializer blocks are executed in the order they appear in the definition. In a static block we can initialize fields whose proper initialization requires some code to be executed.  

The order of initialization can be seen from the output of the following program:  

with main in class Main:

## Listing 41 BHG-StatOrd/Main.java  

```java
public class Stats {
    private static int sino;
    private static int siyes = 2;
    private static final int fin;

    {          // nonstatic initialization block
        show("nonstatic init");
        sino = 1;
    }

    static {   // static initialization block
        show("   static init");
        fin = 3;
    }

    public Stats() {
        show("   constructor");
    }

    private static void show(String mes) {
        System.out.println(mes + ":" +
                " sino=" + sino +
                " siyes=" + siyes +
                " fin=" + fin);
    }
}
```


```java
public class Main {
    public static void main(String[] args) {
        Stats e = new Stats();
    }
}
```

which outputs

```
static init: sino=0 siyes=2 fin=0
nonstatic init: sino=0 siyes=2 fin=3
constructor: sino=1 siyes=2 fin=3
```

Next: [Listing 42 BHF-StatBlocks](https://github.com/Java-PJATK/42.BHF-StatBlocks)  


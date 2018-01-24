# Generics in Java

---


# Lecture Objectives
- To understand the objective of generic programming
- To be able to implement generic classes and methods
- To understand the relationship between generic types and inhericance
- Bounded and Unbounded type parameters
  - Upper Bound Wildcards
  - Lower Bound Wildcards

# Up to now
- For example:
  - We often use the class Object to represent "any class". But this might cause type safety problems
- Consider the following example, where we are trying to model a "Glass" that holds liquid

# Glass.java
```java
public class Glass {
  public Juice liquid;
}
```

In this case a Glass can only hold juice - no other liquid. Suppose you want a glass to hold milk or water?
```java
public class Glass {
  public Object liquid;
}
```

# GlassDemo.java
```java
public class Demo {
  public static void main(String[] args) {
    Glass g = new Glass();
    Juice juice = new Juice();
    g.liquid = juice;
    Juice j = (Juice)g.liquid; // casting is required! Otherwise ClassCastException //
  }
}
```

# GlassG.java using Generics
```java
public class GlassG<T> {
  public T liquid;
}
```

Glass can hold any type T

```java
public class GlassGDemo {
  public static void main(String[] args) {
    GlassG<Juice> g = new GlassG<Juice>();
    Juice juice = new Juice();
    g.liquid = juice;

    // retrieve //
    Juice j = g.liquid; // no need for casting! //

    GlassG<Water> gw = new GlassG<Water>();
    Water water = new Water();
    gw.liquid = water;
  }
}
```

# Box
```java
public class Box<E> {
  E data;

  public Box(E data) {
    this.data = data;
  }

  public E getData() {
    return this.data;
  }
}


class BoxDemo{
  public static void main(String [] args){
    Box<Integer> intBox = new Box<Integer>(42);
    int x = intBox.getData(); // No need to for casting
    System.out.println(x);

    Box<String> strBox = new Box<String>("Hello");
    String st = strBox.getData(); //No need to for casting
    System.out.println(st);
  }
}
```

# Generics
- Java, starting with version 5.0, has a feature called:
  - **parametric polymorphism**,
  - **parametric classes**, or
  - **generics**

- The **"<E>"** after the class name is a parametrisation of the class definition using the symbol **"E"**
- That is, **E** refers to a **particular type** and that anywhere **E** appears in the class definition, the **particular class type** referred to by **E** should be used

- Notice for instance, that the constructor for Box takes an input of the *specific* **type E**, not any type (ie. subclass of Object)
- Likewise, the **getData()** method **returns** exactly the type being held, not the superclass Object











#

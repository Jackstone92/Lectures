# Introduction to Java

---

# Java Programming Language
## What is Java?
- A simple, object-oriented programming platform for developing portable, hardware-independent applications and libraries
- Java was designed with modern computing in mind and thus contains facilities for networking, graphics and security

## The Java programming Language
- Java is a programming language and computing platform first released by Sun Microsystems in 1995
- There are lots of applications and websites that will not work unless you have Java installed, and more are created every day
- Java is fast, secure and reliable. From laptops to data-centres, games consoles to scientific supercomputers, cell phones to the Internet, Java is everywhere!
- Java programs are built from classes that have methods consisting of statements that perform tasks

## Hello World example
```java
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

## Java execution environment
- Java was designed to be platform independent
  - "Write once, run anywhere"
- Java programs are compiled into binary class files that contain machine instructions called bytecode
- The bytecode is executed by a Java virtual machine (JVM)
- A **Java virtual machine (JVM)** is an abstract computing **machine** that enables a computer to run a **Java** program

## Compiling and running a Java program
- A Java class is described in a text file that contains its source code
- the name of the file corresponds to the name of the class
  - Eg. HelloWorld.java
- Compiling and running a java program using a terminal:
```
javac HelloWorld.java (compile)
java HelloWorld (run)
```

# Primitive Types
In addition to class types, Java has eight primitive types:

| boolean | true or false |
| --- | --- |
| char | 16-bit Unicode character |
| byte | 8-bit signed integer |
| short | 16-bit signed integer |
| int | 32-bit signed integer |
| long | 64-bit signed integer |
| float | 32-bit IEEE 754-1985 floating point |
| double | 64-bit IEEE 754-1985 floating point |

# Comments in Java
```java
/*
  This is my first program written in Java!!!
*/

public class HelloWorld {
  // the main method
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

# Differences between C++ and Java
- Java does not have goto statement
- Java has no pointers
- Java has built-in memory management (Garbage Collector)

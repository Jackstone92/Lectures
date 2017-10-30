# Defining and Calling Methods in Java

---

# Why write methods?
Methods are commonly used to break a problem down into small manageable pieces. This is called **divide and conquer**
- They simplify programs. If a specific task is performed in several places, a method can be written once to perform that task, and then can be executed anytime it is needed. This is known as **code reuse**

# What does a class have?
- Members of a class:
  - **Attributes** (instance variables, data)
    - For each instance of the class (object). values of attributes can vary, *hence instance variables*
  - **Methods**
Eg.
```java
class Rectangle {
  float width, length; // attributes
  float perimeter(float x, float y) {} // method
  float area(float x, float y) {} // method
}
```

# Two parts of method declaration
Method header:
```java
public static void displayMessage()
```
Method body:
```java
{
  System.out.println("Hello World!");
}
```

## Parts of a method header
Method modifiers:
- `public` - method is publicly available outside the class
- `static` - method belongs to a class, not a specific object
```java
public static
```

Return type:
- Either return *data type* from a value-returning method or `void` (don't return anything)
```java
void
```

Method name:
- Name that is descriptive of what the method does
```java
displayMessage
```

Parentheses
- Contain nothing or a list of one or more variable declarations if the method is capable of receiving arguments
```java
()
```

# Calling a method
- A method executes when it is called
- The `main` method is **automatically called when a program starts**, but other methods are executed by **method call statements**
```java
displayMessage();
```
- Notice that the method modifiers and the *void* return type are not written in the method call statement. Those are only written in the method header

## Passing arguments to a method
- Values that are sent into a method are called arguments
```java
System.out.println("Hello");
number = Integer.parseInt(str);
```
- The data type of an argument in a method call must correspond to the **variable declaration in the parentheses of the method declaration**. The **parameter** is the variable that holds the value being passed into a method

## Main method
- The main method can be in the same class or in a separate class

## Naming methods
- Use a verb to name method
  - Actions
  - getBalance, deposit, changeAddress
- Use camelCase

## Local variables
- Declared within a method

## Blocks
- **Block** and **compound** statement
  - A set of Java statements enclosed in braces {}
- A variable declared within a block
  - is local to the block
  - when the block ends, the variable "disappears"

# Math-class methods
- Class **java.lang.Math**
  - provides common mathematical calculations

Eg. to calculate the square root of 900.0:
```java
Math.sqrt(900.0);
```
- Method *sqrt* belongs to class *Math*

Eg. random-number generators
```java
(int)(Math.random() * 6);
```
- produces integers from 0-5

# Recursive functions
- A recursive method is a method that calls itself
- In computer science, some problems are more easily solved by using recursive functions
  - eg. traversing through a tree of search results
```java
public static int mystery(int n) {
  if(n == 0) {
    return 0;
  } else {
    return n + mystery(n-1);
  }
}
```

# Introduction to Object-Oriented Programming

---

# What is an object?
- Any entity can be an object
- Eg. car, chair, football, dog

## Example: Car object
Attributes (what do we know about a car?):
- Make
- Model
- Year
- Colour
- etc.

Methods or operations (what can a car do?):
- Start
- Stop
- Apply Breaks
- Change Gear
- etc.

## Example: Bank account
Attributes:
- Account number
- Account holder name
- Balance
- Address
- etc.

Methods or operations:
- Deposit
- Withdraw
- Change address
- Change phone number
- etc.

# What is a class?
- A class is a **blueprint** of a particular classification of **objects**
- An object belongs to a class of objects
- An object is an instance of a class
- For example:
  - myBicycle, yourBicycle are are **instances** of a class Bicycle.
  - myCar, yourCar are **instances** of a class Car.
  - myDog, yourCat are **instances** of a class Animals

# General format of a class
```Java
class Class_Name {
  Instance Var Declaration 1
  Instance Var Declaration 2
  ...
  Instance Var Declaration Last

  Method Def 1
  Method Def 2
  ...
  Method Def Last

  Main method
}

```

Test Class (Main Method) can be separated:

```Java
class Class_Name {
  Instance Var Declaration 1
  Instance Var Declaration 2
  ...
  Instance Var Declaration Last

  Method Def 1
  Method Def 2
  ...
  Method Def Last
}

class Class_Name_Demo {
  Main method
}

```

# Structure of a class definition

```Java
class name {
  declarations // attributes and symbolic constants //

  constructor definitions // how to create and initialise objects //

  method definitions // how to manipulate the state of objects //
}

```

# What is a Constructor?
- Constructor is a special method that gets **invoked
“automatically”** at the time of **object creation**.
- Normally used for **initialising objects with default values** unless different values are supplied.
- Constructor has the **same name** as the **class name**.
- Constructor **cannot** return **values**.
- A class can have **more than one constructor** as long as they have **different signature** (i.e., different input arguments syntax).

# Static Variables in Java
- Static -> class variable
- Non-static -> instance variable
- Memory for static variable is allocated only at the time when the class is loaded in the program
- Preceded by 'static' keyword
- Static variables can be accessed with class reference

# Non-Static Variables in Java
- Memory for non-static variables are allocated at the time of object creation from a class
- Not preceded by any static keyword
- Non-static variables can be accessed with object reference

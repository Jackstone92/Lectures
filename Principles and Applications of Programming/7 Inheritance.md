# Inheritance

---

# What is inheritance?
- Another fundamental object-oriented technique
- Used to organise and create reusable classes
- Allows a software developer to derive a new class from an existing one
- The existing class is called the **parent class**, or **super class**, or **base class**
- The derived class is called the **child class*, or **subclass**
- The child **inherits characteristics** of the parent - **methods and data** defined for the parent class
- To tailor a derived class, the programmer can add new **variables or methods** and can even **modify** the inherited ones
- By using existing software components to create new ones, we capitalise on all the effort that went into the design, implementation and testing of the existing software

# Various forms of inheritance
- Single inheritance
- Hierarchical inheritance
- Multi-level inheritance
- Multiple inheritance (NOT SUPPORTED BY JAVA!)

# Defining a subclass
Syntax:

```Java
class subclassName extends superclassName {
  // variable declarations;
  // method declarations;
}

```

- Extend keyword signifies that properties of the super class are **extended** to the subclass
- Subclass **will not** inherit **private members** of super class

The subclass can:
- Add **new** functionality
- Use **inherited** functionalities
- Override **inherited** functionalities

# What really happens?
- When an object is created using **new**, the system must **allocate enough memory** to hold all its **instance variables**.
  - This includes any inherited instance variables

# Inheritance Hierarchy
- Each Java class has one (and only one) superclass
  - C++ allows for multiple inheritance
- Inheritance creates a class hierarchy
  - Classes higher in the hierarchy are more general and more abstract
  - Classes lower in the hierarchy are more specific and concrete
- There is no limit to the number of subclasses a class can have
- There is no limit to the depth of the class tree

## The class called Object
- At the very top of the inheritance tree is a class called Object
- All Java classes inherit from Object
  - All objects have a common ancestor
- The Object class is defined in the java.lang package

# Access Control

| Access Modifiers / Access Location | Public | Protected | Default | Private |
| --- | --- | --- | --- | --- |
| Same Class | Yes | Yes | Yes | Yes |
| Subclasses in same package | Yes | Yes | Yes | No |
| Other classes in same package | Yes | Yes | Yes | No |
| Subclasses in other packages | Yes | Yes | No | No |
| Non-subclasses in other packages | Yes | No | No | No |

# Inheritance Basics
1. Whenever a **subclass** object is created, the **super class constructor is called first**
2. If super class constructor does not have any constructor of its own OR has an un-parametrised constructor then it is automatically called by Java Run Time by using call **super()**
3. If a super class has a **parameterised constructor** then it is the **responsibility** of the subclass constructor to call the super class constructor by call **super(<parameters required by super class>)**
4. Call to super class constructor **must be the first statement** in subclass constructor

# Multiple Inheritance
- Java supports single inheritance, meaning that a derived class can have only one parent class
- Multiple inheritance allows a class to be derived from **two or more classes**, inheriting the members of all parents
- **Collisions**, such as the same variable name in two parents, have to be resolved
- Java **does not support multiple inheritance**
- In most cases, the use of **interfaces** gives us aspects of multiple inheritance without the overhead

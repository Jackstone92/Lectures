# Data Structure Collections

---

# What are data structures?
- Hold a collection of data in various formats
- We can think of them as lists which look at data in different ways
- Each different type has its own advantages and disadvantages
- We need to select the right data structure for any particular situation

# Arrays
- The size of an array is fixed
- Once an array is declared, its size cannot be changed
- If you want to change the size of an array:
  - You have to copy the data to an array of the correct size
  - Delete the old array

# Java Collections Framework
DIAGRAM

# Collections
Collection: An object that stores data inside it
- The objects stored are called **elements**
- Some collections maintain an ordering, some do not
- Some allow duplications, some do not
- An array is like a very crude "collection"
- Most collections are built with particular kinds of data or operations on that data in mind

Typical operations:
- Add element
- Remove element
- Clear all elements
- Contain or find element
- get size

Examples of collections:
- List
- Bag
- Stack
- Queue
- Set
- Map
- Graph


# Java's *Collection* interface

| Method Name | Description
| ----- | ------ |
| add(value) | adds the given value to the collection |
| addAll(collection) | adds all elements from given collection to this one |
| clear() | removes all elements |
| contains(value) | returns true if the element is in the collection |
| containsAll(collection) | returns true if this collection contains all elements from the other |
| isEmpty() | returns true if the collection does not contain any elements |
| removeAll(collection) | removes all values contained in the given collection from this collection |
| retainAll(collection) | removes all values not contained in the given collection from this collection |
| size() | returns the number of elements in the list |
| toArray() | returns an array containing the elements of this collection |

## Collection interface continued
- `public boolean isEmpty()``
  - Returns true if this list contains no elements
- `public Iterator<E> iterator()`
  - Returns a special object for examining the elements of the list in order
- `public boolean remove(Object o)`
  - Removes the first occurrence in this list of the specific element
- `public int size()`
  - Returns the number of elements in this list
- `public Object[] toArray()`
  - Returns an array containing all of the elements from this list


# Lists
A **List** is the most common type (interface)
  - ArrayList
  - LinkedList
(Both implement List)

## What is a list?
- An ordered sequence of elements, each accessibly by a 0-based index
  - One of the most basic collections

## Java's List Interface
- Java also has an interface `List<E>` to represent a list of objects.
  - It adds the following methods to those in `Collection<E>:` (a partial list)

- `public void add(int index, E element)`
  - Inserts the specific element at the specified position in this list
- `public E get(int index)`
  - Returns the element at the specified position in this list
- `public int indexOf(Object o)`
  - Returns the index in this list of the first occurrence of the specified element, or **-1** if the list does not contain it
- `public int lastIndexOf(Object o)`
  - Returns the index in this list of the last occurrence of the specified element, or **-1** if the list does not contain it
- `public E remove(int index)`
  - Removes the object at the specified position in this list
- `public Object set(int index, E element)`
  - Replaces the element at the specified position in this list with the specified element
- Notice that the methods added to `Collection<E>` by `List<E>` all deal with indices
  - A list has indices while a general collection may not


# ArrayList
- **ArrayList** class *implements* **List** interface

- Declare an **ArrayList**
  - `List list<String> = new ArrayList<>();`
  - `ArrayList list<String> = new ArrayList<>();`
  - `List list<integer> = new ArrayList<>();`
  - `ArrayList list<integer> = new ArrayList<>();`

## Example
```java
import java.util.*;

class Lists {
  public static void main(String [] arg) {
    List<String> words = new ArrayList<>();
    //ArrayList<String> words = new ArrayList<>(); words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.println(words); // prints array
    System.out.println(words.size()); // prints size of arrayList
    System.out.println(words.indexOf("hello")); // prints index of 1st occurrence of hello
    System.out.println(words.lastIndexOf("hello")); // prints last index of hello
    System.out.println(words.get(0)) //prints element at the index 0
    words.remove(0); // remove the element in index 0
    words.remove("hello"); // remove fist occurrences of hello
    words.set(0,"Bye"); // sets the element at the index 0 to "Bye"
  }
}
```

## ArrayList limitations
- An `add` or `remove` operation on an **ArrayList** that is not at the end of the list will require elements to be shifted
  - This can be slow for a large list

### The underlying issue
- The elements of an **ArrayList** are too tightly attached
- Hence, it's not easy to re-arrange them

**Solution:**
- Can we break the element storage apart into a more dynamic and flexible structure?
  - eg. Singly Linked Lists

# Linked Lists
## Singly Linked Lists
- A **linked list** is a series of connected **nodes**
- Each node contains at least:
  - A piece of **data** (any type)
  - A pointer to the **next node** in the list
- **Head**: pointer to the first node
- The last node points to **NULL**

## Doubly Linked Lists
- Keeps a reference to the **first and/or last node**
- In Java, this is represented by the class `LinkedList`

## Adding elements to the list
1. Make a new node to hold the new element
2. Connect the new node to the other nodes in the list
3. Change the front of the list to point to the new node

## Linked List Performance
- To **add**, **remove**, **get** a value at a given index:
  - Must advance through the list to the node just before the one with the proper index
  - Example: To add a new value to the list, the list creates a new node, walks along its existing node links to the proper index, and attaches it to the nodes that should **preceed** and **follow** it
  - This is very fast when adding to the front or back of the list (because the list contains references to these places), but slow elsewhere

## Linked List Usage Examples
- A **LinkedList** can be used much like an **ArrayList**

```java
LinkedList<String> words = new LinkedList<String>();
// or
List<String> words = new LinkedList<String>();
```

### AddToList
```java
import java.util.*;

class AddToList {
  public static void main(String[] args) {
    // List<String> words = new ArrayList<>();
    // ArrayList<String> words = new ArrayList<>();
    // LinkedList<String> words = new LinkedList<String>();
    List<String> words = new LinkedList<String>();

    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");

    System.out.println(words); // prints list

    words.add(0, "first"); // the string "first" to index 0
    words.add(1, "pap"); // the string "pap" to index 1
    System.out.println(words); // prints list

    words.set(0, "Bye"); // sets the element at index 0 to "Bye"
    System.out.println(words); // prints list
  }
}

/*
Prints:
[hello, goodbye, this, that, hello]
[first, pap, hello, goodbye, this, that, hello]
[Bye, pap, hello, goodbye, this, that, hello]
*/
```

### GetElementOfList
```java
import java.util.*;

class GetElementOfList{
  public static void main(String[] args) {
    List<String> words = new LinkedList<String>();
    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.println(words); // prints List
    System.out.println(words.indexOf("hello")); // prints index of 1st occu of hello
    System.out.println(words.lastIndexOf("hello")); // prints last index of hello
    System.out.println(words.get(0)); // prints element at the index 0
    System.out.println(words); // prints List
  }
}

/*
Prints:
[hello, goodbye, this, that, hello]
0
4
hello
[hello, goodby, this, that, hello]
*/
```

### RemoveFromList
```java
import java.util.*;

class RemoveFromList {
  public static void main(String[] args) {
    List<String> words = new LinkedList<String>();

    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.println(words);

    words.remove(1); // removes the element at index 1
    System.out.println(words);

    words.remove("hello"); // removes first occurrence of "hello"
    System.out.println(words);
  }
}

/*
Prints:
[hello, goodbye, this, that, hello]
[hello, this, that, hello]
[this, that, hello]
*/
```

### ListsManipulation
```java
import java.util.*;

class ListsManipulation{
  public static void main(String [] arg) {
    List<String> words = new LinkedList<String>();

    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.println(words); // prints list
    System.out.println(words.size()); // prints size of list
    System.out.println(words.indexOf("hello")); // prints index of 1st occurrence of hello
    System.out.println(words.lastIndexOf("hello")); // prints last index of hello
    System.out.println(words.get(0)); // prints element at the index 0
    words.remove(0); // remove the element in index 0
    words.remove("hello"); // remove fist occurrences of hello
    words.set(0,"Bye"); // sets the element at the index 0 to "Bye"
  }
}
```

### ListsManipulation2
```java
import java.util.*;

class ListManipulation1{
  public static void main(String [] arg) {
    List<String> list1 = new LinkedList<String>();

    list1.add("hello");
    list1.add("goodbye");
    list1.add("this");
    list1.add("Bye");
    System.out.println(list1.contains(“hello”)); // prints true
    System.out.println(list1.isEmpty()); // prints false

    LinkedList <String> list2 = new LinkedList<String>();
    list2.add("this");
    list2.add("hello");

    System.out.println(list1.containsAll(list2)); // prints false

    list1.removeAll(list2); // remove all the element in list2 from list1
    System.out.println(list1);
    list2.add("this");
    list2.add("Bye");

    list1.retainAll(list2); //remove from list1 any elements which is not in list2
    System.out.println(list1);
  }
}
```

## List of Methods

| Modifier and Type | Method | Description
| --- | --- | --- |
| boolean | add(E e) | Ensures that this collection contains the specified element (optional operation) |
| boolean | addAll(Collection<? extends E> c) | Adds all of the elements in the specified collection to this collection (optional operation) |
| void | clear() | Removes all of the elements from this collection (optional operation) |
| boolean | contains(Object o) | Returns true if this collection contains the specified element |
| boolean | containsAll(Collection<?> c) | Returns true if this collection contains all of the elements in the specified collection |
| boolean | equals(Object o) | Compares the specified object with this collection for equality |
| int | hashCode() | Returns the hash code value for this collection |
| boolean | isEmpty() | Returns true if this collection contains no elements |
| Iterator<E> | iterator() | Returns an iterator over the elements in this collection |
| boolean | remove(Object o) | Removes a single instance of the specified element from this collection, if it is present (optional operation) |
| boolean | removeAll(Collection<?> c) | Removes all of this collection's elements that are also contained in the specific collection (optional operation) |
| boolean | retainAll(Collection<?> c) | Retains only the elements in this collection that are contained in the specified collection (optional operation) |
| int | size() | Returns the number of elements in this collection |
| Object[] | toArray() | Returns an array containing all of the elements in this collection |
| <T> T[] | toArray(T[] a) | Returns an array containing all of the elements in this collection; the runtime type of the returned array is that of the specified array |

---

# Iteration through elements of a list

```java
import java.util.*;
class ListItetrator {
  public static void main(String [] arg) {
    //List<String> words = new ArrayList<>();
    //ArrayList<String> words = new ArrayList<>();
    //LinkedList <String> words = new LinkedList<String>();
    List <String> words = new LinkedList<String>();
    words.add("hello");
    words.add("goodbye");
    words.add("this");

    for (String e : words) {
      System.out.println(e);
    }

    for (int i = 0; i < words.size(); i++) {
      System.out.println(words.get(i));
    }

    int j = 0;
    while (j < words.size()) {
      System.out.println(words.get(j));
      j++;
    }
  }
}
```

## Iterators
- An iterator is an object that is used with a collection to provide sequential access to the collection elements
  - This access allows examination and possible modification of the elements
- An iterator imposes an ordering on the elements of a collection even if the collection itself does not impose any order on the elements it contains
  - If the collection does impose an ordering on its elements, then the iterator will use the same ordering


## The `Iterator<T>` interface
- Java provides an `Iterator<T>` interface in the `java.util` package of the Java API
  - Any object of any class that satisfies the `Iterator<T>` interface is an `Iterator<T>`

- An `Iterator<T>` does not stand on its own
  - It must be associated with some collection object using the method `iterator()`

- if `c` is an instance of a collection class (eg. `LinkedList<String> c`)
  - The following defines an iterator for `c`:
    - `Iterator iteratorForC = c.iterator();`


## Iterator methods:
- `public boolean hasNext();`
  - Returns true if there are more elements in the iteration
- `public T next();`
  - Returns the next element in the iteration
- `public void remove();`
  - Removes the last element returned by the iterator (optional operation)


```java
import java.util.*;

class ListIterator {
  public static void main(String[] args) {
    // List<String> words = new ArrayList<>();
    // ArrayList<String> words = new ArrayList<>();
    // LinkedList<String> words = new LinkedList<String>();
    List<String> words = new LinkedList<String>();

    words.add("hello");
    words.add("goodbye");
    words.add("this");

    Iterator<String> it = words.iterator(); // ITERATOR //
    while(it.hasNext()) {
      System.out.println(it.next());
    }
  }
}
```

## Iteration usage idiom
- The standard idiom of using an iterator:
```java
Iterator<E> it = <collection>.iterator();
while(it.hasNext()) {
  // do something with it.next()
}
```

- The following code efficiently removes all Strings with an even number of characters from a linked list:
```java
// removes all strings of even length from the list
public static void removeEvenLength(LinkedList<String> list) {
  Iterator<String> it = list.iterator();
  while(it.hasNext()) {
    String element = it.next();
    if(element.length() % 2 === 0) {
      it.remove();
    }
  }
}
```

---

# List abstract data type (ADT)
- **Abstract data type (ADT)**: a general specification for a type of data structure
  - Specifies what data the data structure can hold
  - Specifies what operations can be performed on that data
  - Does **NOT** specify exactly how the data structure holds the data internally, nor how it implements each operation

- Example ADT: **List**
  - List ADT specifies that a list collection will store elements in order with integer indices (allowing duplicates and null values)
  - List ADT specifies that a list collection supports add, remove, get(index), set(index), size, isEmpty, ...
  - ArrayList and LinkedList both implement the data/operations specified by the List ADT

## ADT usage example
- The following method can accept either an **ArrayList** or a **LinkedList** as its parameter:
```java
// returns the longest string in the given list

public static String longest(List<String> list) {
  Iterator<String> i = list.iterator();
  String result = i.next();
  while(i.hasNext()) {
    String next = i.next();
    if(next.length() > result.length()) {
      result = next;
    }
  }
  return result;
}
```

# Other **Collections** static methods
- The following static methods in the **Collections** class operate on either type of list
- Eg. `Collections.replaceAll(list, "hello", "goodbye");`

| Method Name | Description |
| --- | --- |
| binarySearch(list, value) | Searches a sorted list for a value and returns its index |
| copy(dest, source) | Copies all elements from one list to another |
| fill(list, value) | Replaces all values in the list with the given value |
| max(list) | Returns the largest value in the list |
| min(list) | Returns the smallest value in the list |
| replaceAll(list, oldValue, newValue) | Replaces all occurrences of oldValue with newValue |
| reverse(list) | Reverses the order of elements in the list |
| rotate(list, distance) | Shifts every element's index by the given distance |
| sort(list) | Places the list's elements into natural sorting order |
| swap(list, index1, index2) | Switches element values at the given two indexes |

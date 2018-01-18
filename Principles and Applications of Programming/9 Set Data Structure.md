# Set Data Structure

---

# `Set` interface
  - `HashSet` implements `Set`
  - `TreeSet` implements `Set`


# Application: words in a book
- Write an application that reads the text of a book and then lets the user type words and tells whether those words are contained in the book or not
  - How would we implement this with a List?
  - Would this be a good or bad implementation?

- Notice that the code to solve this problem doesn't use much of the list functionality (only add and search)
  - Does the ordering of the elements in the List affect the algorithm? Could we use this information to our advantage?

# A new ADT: Set
- **Set**: an unordered collection with no duplicates
  - The main purpose of a set is to search it, to test objects for membership in the set (`contains`)
  - Java has an interface named `Set<E>` to represent this kind of collection
    - **Set** is an interface; you **can not** say `new Set();`

  - There are two **Set** implementations in Java:
    - **TreeSet** and **HashSet**
      - Java's set implementations have been optimised so that it is very fast to search for elements in them

# Searching a Set vs Lists
- Sets are implemented using **hash tables**
- Whenever you add an object to a set, the position within the memory of the set object is determined using the hash of the object to be added
- When testing for membership, all that needs to be done is basically to look if the object is at the position determined by its hash, so the speed of this operation does not depend on the size of the set
- For Lists, in contrast, the whole list needs to be searched, which will become slower as the list grows

# Java Set interface
- Interface **Set** has the methods of the **Collection** interface
- **TreeSet** and **HashSet** classes implement the Set interface
  - `Set<Integer> set = new TreeSet<Integer>();`
  - `Set<Integer> set = new HashSet<Integer>();`
- Notice: These list methods are **missing** from Set:
  - get(index)
  - add(index, value)
  - remove(index)
- To access each element of a set, use its **iterator** method instead

## List of methods for Set

| Method | Return type |
| --- | --- |
| size() | int |
| isEmpty() | boolean |
| contains(Object e) | boolean |
| add(Object o) | boolean |
| remove(Object o) | boolean |
| iterator(); | Iterator |
| containsAll(Collection c) | boolean |
| addAll(Collection c) | boolean |
| removeAll(Collection c) | boolean |
| retainAll(Collection c) | boolean |
| clear() | void |
| toArray() | Object[] |
| toArray(Object a[]) | Object[] |


# Iterators for sets
- A set has a method `Iterator iterator()` to create an iterator over the set
- The iterator has the usual methods:
  - `boolean hasNext()`
  - `Object next()`
  - `void remove()`
- Since sets have iterators, you can also use Java enhanced **for** loop
- `remove()` allows you to remove elements as you iterate over the set
- if you change the set in any other way during iteration, the iterator will throw a **ConcurrentModificationException**

## Iterating through a Set

```java
import java.util.*;

public class SetExample {
  public static void main(String[] args) {
    String[] words = {"When", "all", "is", "said", "and", "done", "more", "has", "been", "said", "than", "done"};

    Set<String> mySet = new HashSet<String>();

    for(int i = 0; i < words.length; i++) {
      mySet.add(words[i]);
    }

    for(Iterator iter = mySet.iterator(); iter.hasNext();) {
      String word = (String) iter.next();
      System.out.print(word + " ");
    }
    System.out.println();
  }
}
```




```java
import java.util.*;

public class SetExample2 {
  public static void main(String[] args) {
    String[] words = {"When", "all", "is", "said", "and", "done", "more", "has", "been", "said", "than", "done"};

    Set mySet = new HashSet();

    for(string i : words) {
      mySet.add(words[i])
    }

    for(String word : mySet) {
      System.out.print(word + " ");
    }
    System.out.println();
  }
}

/*
Prints:
and has more When done all than said is been
*/
```

# Set implementations
- Set is an interface; you **can't** say `new Set();`
- There are **four implementations**:
  - **HashSet** is best for most purposes
  - **TreeSet** guarantees that an iterator will return elements in sorted order
  - **LinkedHashSet** guarantees that an iterator will return elements in the order they were inserted
  - **EnumSet**

## HashSet
```java
import java.util.*;

class Sets {
  public static void main(String [] arg) {
    Set<String> words = new HashSet<String>();
    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.print(words);
  }
}

/*
Prints:
[that, goodbye, this, hello]
*/
```

## TreeSet
```java
import java.util.*;

class Sets{
  public static void main(String [] arg) {
    Set<String> words = new TreeSet<String>();
    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.print(words);
  }
}

/*
Prints:
[goodbye, hello, that, this]
*/
```

## LinkedHashSet
```java
import java.util.*;

class Sets{
  public static void main(String [] arg) {
    HashSet<String> words = new LinkedHashSet<String>();
    words.add("hello");
    words.add("goodbye");
    words.add("this");
    words.add("that");
    words.add("hello");
    System.out.print(words);
  }
}

/*
Prints:
[hello, goodbye, this, that]
*/
```

# Set Operations
- Sometimes it is useful to compare sets:
  - **subset** S1 is a *subset* of S2: if S2 contains every element from S1
    - `containsAll` tests for a subset relationship

- It can be useful to combine sets in the following ways:
  - **union**: S1 *union* S2 contains all elements that are in S1 or S2
    - `addAll` performs set union

  - **intersection**: S1 *intersect* S2 contains only the elements that are in *both* S1 and S2
    - `retainAll` performs set intersection

  - **difference**: S1 *difference* S2 contains the elements that are in S1 but *not* in S2
    - `removeAll` performs set difference

## Examples
- Testing if s2 is a *subset* of s1
  - `s1.containsAll(s2);`
- Setting s1 to the *union* of s1 and s2
  - `s1.addAll(s2);`
- Setting s1 to the *intersection* of s1 and s2
  - `s1.retainAll(s2);`
- Setting s1 to the set *difference* of s1 and s2
  - `s1.removeAll(s2);`

```java
import java.util.*;

public class SetManipulation {
  public static void main(String[] args) {
    Set set1 = new HashSet<>();
    Set set2 = new HashSet<>();
    for(int i=1;i<6;i++) set1.add(i); // populates set1 with 1 to 5
    for(int i=3;i<10;i++) set2.add(i); // populates set2 with 3 to 9
    System.out.println(set1);
    System.out.println(set2);
    System.out.println(set1.size());// prints the size of the set1
    System.out.println(set1.isEmpty());// prints true if set1 is empty
    System.out.println(set1.contains(0));// print true is 0 is in set1
    System.out.println(set1.remove(1));// remove 1 from set1
    System.out.println(set1);
    System.out.println(set1.containsAll(set2)); //print true is set2 subset of set1
    System.out.println(set1.retainAll(set2)); // keep in set1 all element in set2
    System.out.println(set1);
    System.out.println(set2);
    System.out.println(set2.removeAll(set1)); // remove from set2 all element in set1
    System.out.println(set1);
    System.out.println(set2);
    System.out.println(set2);
    System.out.println(set2.hashCode());// prints the hashcode value for set2: sum hashcode of all elem
    set2.clear(); // clears all elements of the set
    System.out.println(set2);

    Iterator iterator = set1.iterator();// iterator for set11
    while(iterator.hasNext()) {
      System.out.println(iterator.next());
    }  
  }
}
```


# The **SortedSet** Interface
- A SortedSet is just like a Set, except that an Iterator will go through it in ascending order
- SortedSet is implemented by TreeSet

# Membership testing in TreeSets
- In a TreeSet, elements are kept in order
- That means Java must have some means of comparing elements to decide which is "larger" and which is "smaller"
- Java does this by using either:
  - The `int compareTo(Object)` method of the **Comparable** interface
  - or
  - The `int compare(Object, Object)` method of the **Comparable** interface


# Why use Iterators?
- Traversing through the elements of a collection is very common in programming, and iterators provide a **uniform** way of doing so
- Advantage?
  - Using an iterator, we **don't need to know how the collection is implemented!**

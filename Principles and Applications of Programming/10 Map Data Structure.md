# Map Data Structure

---


# A variation: book word count
- Previously, we discussed an application that reads in the text of a book and then lets the user type words, and tells whether those words are contained in book
- What if we wanted to change this program to not only tell us whether the word exists in the book, but also *how many* times it occurs?

# Mapping between sets
- Sometimes we want to create a mapping between elements of one set and another set
  - Example: Map words to their count in the book
    - "the" -> 325
    - "whale" -> 14
  - Example: Map people to their phone numbers
    - "Mohammed Farah" -> "692-4540"
    - "Jenny" -> "867-5309"
- Can we do this using lists?
- **A map associates each key with a value**


# Map: new ADT
- Maps are represented in Java by the `Map<K, V>` interface
  - Two implementations:
    - `HashMap`
    - `TreeMap`

- **Map**: is an unordered collection that associates a collection of element **values** with a set of **keys** so that elements can be found very quickly
  - Each **key** can appear at **most once** (no duplicate keys)
  - A **key** maps to at most one **value**
  - The main operations:
    - `put(key, value)`
      - Maps a key to a value
    - `get(key)`
      - Returns the value that the key is mapped to


# Map operations(methods)
- Maps don't implement the **Collection** interface, but they do have the following public methods:

| Method Name | Description |
| --- | --- |
| clear() | Removes all keys and values from the map |
| containsKey(key) | Returns true if the given key exists in the map |
| get(key) | Returns the value associated with the given key (null if not found) |
| isEmpty() | Returns true if the map has no keys or values |
| keySet() | Returns a collection of all keys in the map |
| put(key, value) | Associates the given key with the given value |
| putAll(map) | Adds all key/value mappings from given map |
| remove(key) | Removes the given key and its associated value |
| size() | Returns the number of key/value pairs in the map |
| values() | Returns a collection of all values in the map |


# Declaring Map
```java
import java.util.*;

class Maps {
  public static void main(String[] args) {
    Map<String, Double> salaryMap = new HashMap<String, Double>();
    salaryMap.put("Stuart", 20000.00);
    salaryMap.put("Mary", 15500.00);
    salaryMap.put("Jenny", 86753.09);
    System.out.print(salaryMap);
  }
}

/*
Prints:
{Jenny=86753.09, Mary=15500.0, Stuart=20000.0}
*/
```

# `keySet()` and `values()`
```java
import java.util.*;

class Maps {
  public static void main(String[] args) {
    Map<String, Double> salaryMap = new HashMap<String, Double>();
    salaryMap.put("Stuart", 20000.00);
    salaryMap.put("Mary", 15500.00);
    salaryMap.put("Jenny", 86753.09);
    System.out.print(salaryMap);
    System.out.println(salaryMap.keySet());
    System.out.println(salaryMap.values());
  }
}

/*
Prints:
{Jenny=86753.09, Mary=15500.0, Stuart=20000.0}
[Jenny, Marty, Stuart]
[86753.09, 15500.0, 20000.0]
*/
```

# `containsKey()`
```java
import java.util.*;

class Maps {
  public static void main(String[] args) {
    Map<String, Double> salaryMap = new HashMap<String, Double>();
    salaryMap.put("Stuart", 20000.00);
    salaryMap.put("Mary", 15500.00);
    salaryMap.put("Jenny", 86753.09);
    System.out.print(salaryMap);

    // search the map for a name
    if(salaryMap.containsKey("Jenny")) {
      double salary = salaryMap.get("Jenny");
      System.out.println("Jenny's salary is £" + salary);
    } else {
      System.out.println("I don't have a record for Jenny");
    }
  }
}

/*
Prints:
{Jenny=86753.09, Mary=15500.0, Stuart=20000.0}
Jenny's salary is £86753.09
*/
```

# TreeMap vs HashMap
- Remember that Map is an interface
  - You **can't** say `Map m = new Map();`
- Java has two classes that implement the Map interface:
  - **TreeMap**
    - elements are stored in their natural Comparable order
    - slightly slower
    - can only be used on elements with an ordering
  - **HashMap**
    - elements are stored in an unpredictable order
    - faster to add, search, remove


# Iterators and Maps
- **Map has no iterator** method; you can't get an Iterator directly
- You must first call either:
  - `keySet()`
    - returns a **Set** of all the keys in this Map
  - `values()`
    - returns a **Collection** of all the values in this Map
- Then call `iterator()` on the key set or value collection
  - Examples:
    - `Iterator<String> keyItr = grades.keySet().iterator();`
    - `Iterator<String> elementItr = grades.values().iterator();`
  - You can also use the enhanced for loop over these collections:
```java
for(int ssn : ssnMap.values()) {
  System.out.println("Social security #: " + ssn);
}
```

# Map Example
```java
import java.util.*;

public class MapExample1 {
  public static void main(String[] args){
    Map<String, Integer> m = new HashMap<String,Integer>();
    m.put("Newton", 1643); //DoB
    m.put("Darwin", 1809);  //DoB
    System.out.println(m);

    Set<String> keys = m.keySet();
    Iterator<String> itr = keys.iterator();
    while (itr.hasNext()) {
        String key = itr.next();
        System.out.println(key + " => " + m.get(key));
    }
  }
}

/*
Prints:
{ Darwin=1809, Newton=1642}
Darwin => 1809
Newton => 1643
*/
```

# Map Practice Problems
## Reverse a map
```java
import java.util.*;

class MapRev {
  public static void main(String[] args) {
    Map<String, String> byName = new HashMap<String, String>();
    byName.put("Darwin", "748-2797");
    byName.put("Newton", "748-9901");

    System.out.println(byName);
    Map<String, String> byPhone = new HashMap<String, String>();
    Iterator<String> keyItr = byName.keySet().iterator();
    while(keyItr.hasNext()) {
      String key= keyItr.next();
      byPhone.put(byName.get(key), key);
    }
    System.out.println(byPhone);
  }
}
```

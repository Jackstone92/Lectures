# Collections

---

# Motivation
> We have seen a number of data structures for storing data by now. Is there
a unifying concept behind storing data items?

# Definition
Collection:
> a grouping of some variable number of data items. aka:
“container” (C++)

Linear Collection:
> a collection with an underlying linear order

| Collection | Linear? |
| --- | --- |
| Linked List | Yes |
| Dynamic Array | Yes |
| Binary Tree | ? |
| Set | No |
| Multiset | No |
| Stack | Yes |
| Queue | Yes |
| Priority Queue | Yes |
| Dequeue | Yes |

- Binary tree: No way of accessing elements in a set order - multiple ways

# Operations
## Generic Collection
Size:
- how many elements does the collection contain?
Insert[o]:
- add o to the collection
Find[o]:
- is the object o in the collection?
Remove[o]:
- return a collection with all instances of o removed
Count[o]:
- how many times is o stored in the collection?
Sum:
- what is the sum of the objects in the collection?
(Maximum and Second Maximum are also operations)  
Iterate[f]:
- visit all items of the collection, calling f (function) on each item
## Linear Collection
Position[o]:
- what index is o at, if any?
Get[i]:
- get the object at index i

# Reading
- Explore Drozdek[Java] section 1.5, 3.7, 4.1.1

# Vectors

---

# Motivation
- Useful abstraction of memory
- Basic building block

# Definition
> A vector is a finite fixed-size sequential collection of data

**Finite**
- a vector has a non-negative integer length

**Fixed-size**
- the length of the vector is immutable

**Sequential**
- a vector has a defined and static storage order of its elements

#Operations
**Length**
- return the number of elements in the vector
**Select[k]**
- return the kth element of the vector
**store![o,k]**
- set the kth element of the vector to o

In pseudocode:
```
length: LENGTH(v)
select[k]: v[k]
store![o,k]: v[k] ← o
```

# Non-vector Operations
- delete!
- insert!
- resize!

# Implementation

*	Sentinel (C Strings)

	| 0 |1 |2 |3 |4| $ |
	|---|---|---|---|---|---|

	*	**Iterates through string until the sentinel($)** to get the length

* 	length-data (everything else)

	|L| 0 |1 |2 |3 |4|
	|---|---|---|---|---|---|

	*	Read the **length slot(L)** to get the length.

---

# Complexity analysis
How much work do operations take?

## select, store!
1. offset calculation: base address + k x element size
2. pointer read (select) or write (store!)

## length
Depends on implementation strategy:  
**Sentinel**
1. initialise count to 0, position to 0
2. iterate position through string, incrementing count until the sentinel ($)
3. return count

**Length-data**
1. read the length slot

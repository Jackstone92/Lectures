# Hash Tables

---

# Motivation
- Non-linear collection, representation of sets (if we don't care which order it is in)
- A different way to implement a collection, with different performance
implications

# Definition
> A hash table is a data structure that can represent a set, or more generally
a map of **keys to values (an associative array)**, by computing a numeric
value for each key using a **hash function** and then using that numeric
value to compute an index into an array to look up the value.

- Number is computed by hash function (has to be the same), then use that number to look up value in table

# Set Operations
Insert[o]:
- insert the object o into the set
Find[o]:
- is the object o in the set?
Delete[o]:
- delete the object o from the set

# Sets of small integers
- Represent sets of non-negative integers smaller than N using an array of
size N . e.g. for domain [0,5]:
  - if a number is in the set, represent it as 1, else 0
  - eg. {0, 1} of [0, 5] => {1, 1, 0, 0, 0, 0}
- The set {0, 3, 5}
  - Represented as: [1, 0, 0, 1, 0, 1]

```
insert[o] S[o] ← true
find[o] return S[o]
delete[o] S[o] ← false
```

# Sets of unbounded integers
- Cannot apply same representation due to overflow
  - 2<sup>32</sup> integers requires 2<sup>29</sup> bytes of RAM (512 MB)

If the expected size of the sets is small (even if the range of possible values is large):
1. choose a reasonable size for the array, say twice expected size
2. reduce the integer to within the range of array indices using a
function f(n)
3. store the (unreduced) integer in the array slot

Then:

```
insert[o] S[f(o)] ← o
find[o] return S[f(o)] = o
delete[o] S[f(o)] ← NIL
```

# Example
- Range [0, 2<sup>10<?sup>]
- Set size: 5

- => Choose array size of (say) 11 and compute index as f(n) = n mod 11

- Used as a lookup

# Complexity Analysis
- Provided that the reducing function f(n) is Θ(1),
Insert:
- Θ(1) reductionand Θ(1) memory operations
> ⇒ Θ(1)

Find:
- Θ(1) reduction and Θ(1) memory operations
> ⇒ Θ(1)

Delete:
- Θ(1) reduction and Θ(1) memory operations
> ⇒ Θ(1)

# Sets of arbitrary things
Compute an integer (a *hash code*) for the things using a *hash function*
- equal things **must** have equal hash codes
- unequal things should be unlikely to share hash codes
computing an integer for the things:
 - Java public int hashcode()
 - C++ operator() functor second template argument to container
 equal things must have equal integer codes:
- Java public boolean equals(Object o)
- C++ operator() functor third template argument to container

# Pairs

# Motivation
- Can (in principle) build all record types out of Pairs
- Basic building block

# Definition
> A pair is a 2-tuple of data

**tuple**
- an ordered collection

**2-**
- with exactly two elements

# Operations
**Left**
- return the left element of the pair
**Right**
- return the right element of the pair
**Set-left![o]**
- set the left element of the pair to o
**Set-right![o]**
- set the right element of the pair to o

In pseudocode:
```
left: LEFT(p)
right: RIGHT(p)
set-left![o]: LEFT(p) ← o
set-right![o]: RIGHT(p) ← o

Constructor:
new Pair(l, r)
```

# Implementation
| 3 | 4 |
|---|---|

# Complexity analysis
**left, set-left!, right, set-right!**
1. pointer read (left, right) or write (set-left!, set-right!)


**Constructor**
1. fixed-size (two-word) allocation
2. two pointer writes

# Higher-cardinality tuples
**(a, b, c)**
- ((a, b), c)

**(a, b, c, d)**
- (((a, b), c), d)

**(a, b, ..., z)**
- ((a, b)... z)

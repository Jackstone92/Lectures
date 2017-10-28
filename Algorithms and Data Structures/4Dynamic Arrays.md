# Dynamic Arrays

---

# Motivation
- Constant-time access of (fixed) arrays
- Extensibility of linked lists
- Java: `ArrayList`, C++ `std::vector`

# Definition
> A dynamic array is a finite sequential collection of data (removal of "fixed-size" from the definition of vector)

# Operations
**Length**
- return the current size of the dynamic array
**Select[k]**
- return the kth element of the dynamic array
**Store![o,k]**
- set the kth element of the array to o
**Push![o]**
- increase the length of the dynamic array by 1, and set the endmost element to o
**Pop!**
- return the endmost element, decreasing the size of the dynamic array by 1

# Implementation
| Ptr | L'|
|   ---   | --- |

- **Ptr (Pointer)** points to L  
- **L'** Stores the number of elements  

---

# Push!
From:  

| Ptr | 4 |
| --- |---|

| 5 | 0 | 1 | 2 | 3 |   |
|---|---|---|---|---|---|

To:  

| Ptr | 5 |
| --- |---|

| 5 | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|

Pseudocode:
```
Require: A :: dynamic array
  function push!(A,k)
    if length(left(A)) = right(A) then
      extend(A)
    end if
    A[right(A)] ← k
    right(A) ← right(A) + 1
  end function
```

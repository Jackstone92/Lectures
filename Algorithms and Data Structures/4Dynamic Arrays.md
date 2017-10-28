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

# Extend
From:

| Ptr | L' |
| --- |--- |

| 5 | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|

To:

| 9 | 0 | 1 | 2 | 3 | 4 |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|

Pseudocode:
```
Require: A :: dynamic array
  function extend(A)
    newL ← newLength(right(A))
    new ← new Vector(newL)
    for 0 ≤ i < length(A) do
      new[i] ← left(A)[i]
    end for
    left(A) ← new
  end function
```

# Complexity analysis
**length, select, store!**
- each is a pointer read (to get the storage array) and a Θ(1) array operation  
  - **⇒ Θ(1)**

**push!**
- usual case:
  - increment length
  - store value in storage array
    - **⇒ Θ(1)**
- when extending storage array:
  - as above plus...
  - ... copy existing contents to new array
    - **⇒ Θ(N)**

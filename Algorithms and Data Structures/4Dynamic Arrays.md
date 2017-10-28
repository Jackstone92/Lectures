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
Pointer points to L  
L' Stores the number of elements  

| Pointer | L'|
|   ---   | --- |

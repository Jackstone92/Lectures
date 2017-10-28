# Linked Lists

---

# Motivation
- Simple application of pairs
- Building block for more complex data structures
  - Stacks
  - Queues
- Useful for considering issues in algorithm design:
  - Complexity and scaling
  - Iteration and recursion

# Definition
> A linked list is a sequential collection of data

# Operations
### **First**
- return the first element of the list  

### **Rest**
- return the list with the first element removed  

### **Cons[o]**
- return a new list whose first is o and whose rest is the list  

### **Set-first![o]**
- set the first of the list to o  

### **Set-rest![l]**
- set the rest of the list to l  

### **Null?**
- return true if the list is the empty list  

# Special value
**NIL** - the immutable empty list


# Implementation

| 3 | Ptr |
|---| --- |

&darr;

| 4 | Ptr |
|---| --- |

&darr;

| 25 | Ptr |
|---| --- |

&darr;

| -6 | NIL |
|--- | --- |

- **Ptr (Pointer)** points to L  
- **NIL** the immutable empty list  

# Complexity analysis
### first, rest, set-first!, set-rest!
1. pointer read (first, rest) or write (set-first!, set-rest!)
> ⇒ Θ(1)

### cons
1. fixed-size (two-word) allocation
2. two pointer writes
> ⇒ Θ(1)

### null?
1. single comparison
> ⇒ Θ(1)

### construct a linked list
... with N elements
1. construct N nodes
2. set-first! N times
3. set-rest! N-1 times
> Θ(N)

### or
Let the time for constructing a linked list with k elements be T<sub>k</sub>
1. construct a list of length N-1: T<sub>N-1</sub>
2. construct a node: Θ(1)
> ⇒ 𝑇𝑁 = 𝑇𝑁 −1 + Θ(1)
> Θ(N)


# Linear linked list algorithms
```
if base case is true
	What is the answer for the empty list?
else
	Compute the answer for the rest of the list.
	Modify that answer based on the current node.
```

# Example (length)
```
function LENGTH(l)
	if NULL?(l)
		return 0
	else
		r <- LENGTH(REST(l))
		return r + 1
	end if
end function
```

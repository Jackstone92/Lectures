# Stacks

---

# Motivation
- Last-in First-out collection
- useful for modelling (computational) state:
  - function calls / activation records
  - function-local temporary storage area

# Definition
> A stack is an extensible linear collection of data whose top element (only) is accessible

# Operations
**Push![o]**
- add o to the top of the stack  

**Top**
- return the top element of the stack  

**Pop!**
- remove and return the top element of the stack  

**Empty?**
- return true if the stack has no elements


# Implementation

| Ptr (to pointer below) |
| --- |

&darr;

| Ptr (to "foo") |
| --- |

&darr;

| Ptr (to "bar") |
| --- |

&darr;

| Ptr (to "baz") |
| --- |


# Complexity analysis
### Top
- Two pointer reads **⇒ Θ(1)**

### Pop!
- Three pointer reads, one pointer write **⇒ Θ(1)**

### Push!
- One pair allocation, one pointer write **⇒ Θ(1)**

### Empty?
- One pointer read, one equality comparison **⇒ Θ(1)**


# Dynamic arrays, revisited
Can use a dynamic array directly as a stack
- **push![o], pop!** directly supported
- **top** select[length-1]
- **empty?** length = 0

Compare with linked list implementation:
- Space complexity:
  - **linked list** - 2 words per item (+1 word overhead)
  - **dynamic array** - 1 word per item (+2+k words overhead)
    - dynamic array up to twice as space efficient
- Time complexity
  - **linked list** - operations Θ(1) in all cases
  - **dynamic array** - operations Θ(1) amortised (over time)

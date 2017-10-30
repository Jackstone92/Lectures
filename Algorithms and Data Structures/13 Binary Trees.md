# Binary Trees

---

# Motivation
- Simplest form of tree data structure
- Algorithms straightforward to understand
  - and (reasonably) simple to analyse
- Generalise to practical applications
  - eg. B-Trees for disk storage

# Definition
> A binary tree is an ordered collection of data

# Operations
**Left**  
- return the right-child of the tree  

**Right**
- return the left-child of the tree  

**Key**
- return the data stored at this node of a tree  

**Parent**
- return the parent of the node (and associated setters)  

## Collection Operations
**Search[o]**  
- return *true* if o is in the collection  

**Max**
- return the maximum element (with respect to some ordering) for the collection  


# Complexity analysis
## left, right, key, parent
Single pointer reads (or writes for setters)
> ⇒ Θ(1)


# Traversal
**Vector**
- start at index zero, and visit elements in order of index until you reach the end  

**Dynamic array**
- as vector  

**Linked list**
- start at the head of the list and visit the *first* of each successive *rest*  

**Binary tree**
- multiple possibilities!


# Depth-first traversal
## Pre-order
```
function pre-order(T)
  if ¬null?(T) then
    visit(T)
    pre-order(left(T))
    pre-order(right(T))
    end if
end function
```

## Post-order
```
function post-order(T)
  if ¬null?(T) then
    post-order(left(T))
    post-order(right(T))
    visit(T)
  end if
end function
```

## In order
```
function in-order(T)
  if ¬null?(T) then
    in-order(left(T))
    visit(T)
    in-order(right(T))
  end if
end function
```

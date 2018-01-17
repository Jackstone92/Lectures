# Binary Trees (recap)

---


# Motivation
- simplest for of tree data structure
- algorithms straightforward to understand
  - and (reasonably) simple to analyse
- generalise to practical applications
  - eg. B-Trees for disk storage

# Definition
> A binary tree is an ordered collection of data

# Operations
**left**
- return the left-child of the tree

**right**
- return the right-child of the tree

**key**
- return the data stored at this node of a tree

**parent**
- return the parent of the node

(and the associated setters)

# Collection Operations
**search[o]**
- return *true* if o is in the collection

**max**
- return the maximum element (with respect to some ordering) of the collection

# Complexity analysis
**left**, **right**, **key**, **parent**
- single pointer reads (or writes for setters)
> ⇒ Θ(1)


# Traversal
**vector**
- start at index zero, and visit elements in order of index until you reach the end

**dynamic array**
- as vector

**linked list**
- start at the head of the list, and visit the *first* of each successive *rest*

**binary tree**
- multiple possibilities!


# Depth-first traversal
## Pre-order
- start at parent node (top)
- traverse down left to bottom node
- zigzag up and down from left to right, visiting next node from left to right

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
- start at bottom left-most node
- work from left to right, zigzagging up and down
- end at parent node (top)

```
function post-order(T)
  if ¬null?(T) then
    post-order(left(T))
    post-order(right(T))
    visit(T)
  end if
end function
```

## In-order
- start at bottom left-most node
- zigzag up and down working from left to right
- end at rightmost bottom node

```
function in-order(T)
  if ¬null?(T) then
    in-order(left(T))
    visit(T)
    in-order(right(T))
  end if
end function
```

# Breadth-first traversal
- start at parent node (top)
- go down to left child and work way from left to right
- then go down a level down the left side and repeat for as many levels
- end at rightmost bottom node

```
function enqueue-if!(Q,T)
  if ¬null?(T) then
    enqueue!(Q,T)
  end if
end function

function breadth-first(T)
  Q ← new Queue()
  enqueue-if!(Q,T)
  while ¬empty?(Q) do
    t ← dequeue!(Q)
    visit(t)
    enqueue-if!(Q,left(t))
    enqueue-if!(Q,right(t))
  end while
end function
```

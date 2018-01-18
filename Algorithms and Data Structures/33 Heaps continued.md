# Heaps and Implicit Heaps

---

# Insert

```
Require: heap :: Heap
  function insert!(heap,object)
    s ← next(heap)
    p ← parent(s)
    while p ≠ NIL ∧ p.key < object do
      s.key ← p.key
      s ← p; p ← parent(p)
    end while
    s.key ← object
  end function
```

# Constructing a heap incrementally
```
function make-heap(S)
  H ← new Heap()
  for 0 ≤ i < length(S) do
    insert!(H,S[i])
  end for
  return H
end function
```

# Complexity analysis
To build a heap with N elements, incrementally:
  - each incremental addition takes Ω(ℎ) time (ℎ is the current height of the tree)
  - in the worst case, there are 𝑁/2 nodes with height log(𝑁)

> ⇒ Ω(𝑁 log(𝑁)), and in fact Θ(𝑁 log(𝑁)))


---


# Implicit Heaps

# Implicit representation
Implicit representations, previously:
  - dope vector (multidimensional array)
  - sorted sequence (binary search tree)
  - partially-sorted sequence (insertion sort)

# Implicit Heap
- an array
- a heap size (must be ≤ array length)
> [stores array, stores heap size]

# Parents and children
For zero-based arrays:

```
function left(i)
  return 2×i+1
end function

function right(i)
  return 2×i+2
end function

function parent(i)
  return ⌊(𝑖−1)/2⌋
end function
```

(One-based arrays have simpler calculations, but generalise less well)


# Heapify (also called siftDown)
Given a root with two (max-)heaps as children, make the root be a valid max heap:

```
function max-heapify(a,i)
  l ← left(i)
  r ← right(i)
  largest ← i
  if l < a.heapsize ∧ a[l] > a[largest] then
    largest ← l
  end if
  if r < a.heapsize ∧ a[r] > a[largest] then
    largest ← r
  end if
  if largest ≠ i then
    swap(a[i],a[largest])
    max-heapify(a,largest)
  end if
end function
```

# Complexity analysis
## Time Complexity
- 𝑇(𝑁) ≤ 𝑇(2𝑁/3) + Θ(1)

> ⇒ Θ(log(𝑁)) or Θ(ℎ)


# Constructing a heap in one go
Half of the nodes are already heaps!

```
function build-max-heap(a)
  a.heapsize ← a.length
  for ⌊a.length/2⌋ < j ≤ 0 do
    max-heapify(a,j)
  end for
end function
```

# Complexity analysis
## First analysis
- N/2 calls to max-heapify
- each takes time 𝑂(log(𝑁))

> ⇒ 𝑂(𝑁 log(𝑁))

## Improved bound
- most calls to max-heapify are near the leaves
- height of most trees is small

- 𝑇(ℎ) ≤ 𝑂 (1 ×𝑁/2 + 2 × 𝑁/2<sup>2</sup> + 3 × 𝑁/2<sup>3</sup> + ... + ℎ × 𝑁/2<sup>ℎ</sup>)

> ⇒ 𝑂(𝑁)



# Operations
## Insert
```
function insert!(heap,k)
  heap[heap.heapsize] ← k
  i ← heap.heapsize
  heap.heapsize ← heap.heapsize + 1
  while i > 0 ∧ heap[parent(i)] < heap[i] do
    swap(heap[i],heap[parent(i)])
    i ← parent(i)
  end while
end function
```

## Extract-Max!
```
function extract-max!(heap)
  max ← heap[0]
  heap[0] ← heap[heap.heapsize-1]
  heap.heapsize ← heap.heapsize - 1
  max-heapify(heap,0)
  return max
end function
```

# Complexity analysis
## insert!
- at most ℎ calls to swap

> ⇒ Θ(log(𝑁))

## extract-max!
- same as max-heapify

> ⇒ Θ(log(𝑁))




# Heapsort

```
function heapsort(array)
  build-max-heap(array)
  while array.heapsize > 0 do
    i ← array.heapsize
    array[i] ← extract-max!(array)
  end while
  return array
end function
```


# Complexity analysis
- N calls to extract-max!
- each call takes 𝑂(log𝑁)

> ⇒ 𝑂(𝑁 log 𝑁)


- worst case, the first N/2 calls to extract-max! each do  ⌈log 𝑁⌉ work

> ⇒ Θ(𝑁 log 𝑁)


# Priority Queues
A priority queue tracks items along with priorities, and provides access to the highest-priority item.  

**maximum**
- return the highest-priority item

**extract-max!**
- remove and return the highest-priority item  

**insert![o]**
- insert an item into the priority queue  

(exactly the same as the heap operations)

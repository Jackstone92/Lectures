# Heaps

---

# Motivation
- interesting non-trivial data structure
- asymptotically efficient support for many operations:
  - comparison sort
  - priority queues
- component of efficient algorithms for:
  - graph traversal
  - selection of k<sup>th</sup> largest element

# Operations
**maximum**
- return the maximum element

**extract-max!**
- remove and return the maximum element

**insert![o]**
- insert the object o into the heap

**size**
- how many elements are currently stored?

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

# Complexity analysis
**insert!**
- new element goes at the bottom of the tree
- in principle could be moved up ℎ times, with constant work each time
> ⇒ Θ(ℎ) = Θ(log(𝑁))


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
- to build a heap with N elements incrementally:
  - each incremental addition takes Ω(ℎ) time (ℎ is the *current* height of the tree)
  - in the worst case, there are N/2 nodes with a height log(N)
> ⇒ Ω(𝑁 log(𝑁)), and in fact Θ(𝑁 log(𝑁)))

# Other operations
**maximum**
- trivial

**extract-max!**
- see next term

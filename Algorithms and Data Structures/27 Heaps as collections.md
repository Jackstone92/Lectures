# Heaps as Collections

---


# Heap Property
- Let x be a node in a max-heap. If y is a (generalised) parent of x, then y.key ≥ x.key

# Motivation
- An unordered collection for ordered keys which supports efficient construction **and** efficient determination of the maximum key

# Definition
> A heap is a tree data structure which both satisfies the heap **contents** property, and also satisfies the (nearly-)complete **shape** property

# Collection operations
## Find

```
Require: heap :: max Heap
  function find(heap,object)
    if null?(heap) then
      return false
    end if
    if heap.key = object then
      return true
    else if heap.key < object then
      return false
    else
      return find(heap.left,object) ∨ find(heap.right,object)
    end if
  end function
```

## Max

```
Require: heap :: non-empty max Heap
  function max(heap)
    return heap.key
  end function
```

# Complexity analysis
## Find
- must in principle go down both branches (e.g. to find object smaller than minimum element)
> ⇒ Θ(𝑁)

## Max
- read key or root node
> ⇒ Θ(1)

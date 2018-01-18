# Binary Search

---

# Motivation
- Simple, efficient search algorithm
- one or two interesting practical lessons

# Definition
> Given a suitable data structure, binary search is a search algorithm for an item within that structure that can exclude half of the search space with a single comparison.

# Binary search on trees
```
function binary-search(tree,k)
  if tree = NIL then
    return false
  else if tree.key = k then
    return true
  else if k < tree.key then
    return binary-search(tree.left,k)
  else
    return binary-search(tree.right,k)
  end if
end function
```

# Binary search on sorted arrays
```
function binary-search(A,lo,hi,k)
  mid ← ⌊(lo+hi−1)/2⌋
  if lo = hi then
    return false
  else if A[mid] = k then
    return true
  else if k < A[mid] then
    return binary-search(A,lo,mid,k)
  else
    return binary-search(A,mid+1,hi,k)
  end if
end function
```

# Complexity analysis
## Recurrence relationship
> 𝑇(𝑁) = 𝑇 (𝑁/2) + 1

## Recursion tree
> 𝑇(𝑁) -> 𝑇(𝑁/2) -> 𝑇(𝑁/4) etc.
> log<sub>2</sub>N

## Master theorem
> 𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑛)

  - a = 1; b = 2; 𝑓 (𝑛) ∈ Θ(1) = Θ(𝑛<sup>0</sup>) so c = 0
  - log<sub>𝑏</sub>𝑎 = 0 = c so **case 2**
> ⇒ Θ(log 𝑁)

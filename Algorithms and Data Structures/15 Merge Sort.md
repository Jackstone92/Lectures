# Merge Sort

---

# Motivation
Merge sort: A straightforward, efficient sorting algorithm, with some additional useful properties:
- stability
- genericity (linked lists and vectors)

# Definition
> To sort a sequence using merge sort: sort two half-length subsequences, then combine the results

# Merge(vector)
```
Require: a,b :: Vector
  function merge(a,b)
    al ← length(a); bl ← length(b); cl ← al + bl
    c ← new Vector(cl)
    ai ← bi ← ci ← 0
    while ci < cl do
      if ai = al then
        c[ci] ← b[bi]; bi ← bi + 1
      else if bi = bl ∨ a[ai] ≤ b[bi] then
        c[ci] ← a[ai]; ai ← ai + 1
      else
        c[ci] ← b[bi]; bi ← bi + 1
      end if
      ci ← ci + 1
    end while
    return c
  end function
```

# Merge(linked list)
```
Require: a,b :: Linked List
  function merge(a,b)
    if null?(a) then
      return b
    else if null?(b) then
      return a
    else if first(a) ≤ first(b) then
      return cons(first(a), merge(rest(a), b))
    else
      return cons(first(b), merge(a, rest(b)))
    end if
  end function
```

# Mergesort
```
function mergesort(s)
  sl ← length(s)
  if sl ≤ 1 then
    return s
  else
    mid ← ⌊sl/2⌋
    left ← mergesort(s[0...mid))
    right ← mergesort(s[mid...sl))
    return merge(left,right)
  end if
end function
```

# Complexity Analysis
## Time complexity: merge
- Each iteration:
  - Two compares
  - Two memory read/writes
  - One addition
- Exactly **length(a) + length(b)** iterations
> ⇒ Θ(𝑁𝐴 + 𝑁𝐵)

## Time complexity: mergesort
> 𝑇(𝑁) = 2 × 𝑇 (𝑁/2) + Θ(𝑁)
⇒ ...?

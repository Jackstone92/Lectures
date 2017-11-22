# Cycle Detection

---

# Motivation
- Did your SLList code suffer from baffling infinite loops at any point?
  -

# Definition
> Cycle detection algorithms detect whether there are loops in a graph,
graph, or repeated values in a function with same domain and range, and
where and how long those loops are.

# Linkedlist implementation
Eg. What if
```
set-rest!(rest(rest(rest(list))), rest(list))
```

- Becomes infinite loop: 3, 4, 25, -6, 3, 4, 25, -6..... etc

# Naïve circularity detection
Algorithm: at each step, check all previous steps for repeat

## Helper function
```
function is-in?(sequence,node,end)
  j←0
  x ← sequence
  while j < end do
    if x = node then
      return true
    end if
    x ← rest(x)
    j←j+1
  end while
  return false
end function
```

## Main function
```
Require: sequence :: list
  node ← rest(sequence)
  end ← 0
  while node ≠ NIL do
    end ← end + 1
    if is-in?(sequence,node,end) then
      return true
    end if
    node ← rest(node)
  end while
  return false
```

## Complexity Analysis
Space:
- No extra space required
> ⇒ Θ(1)

Time:
- T k = T k−1 + Θ(k)
  - If there is no cycle, the algorithm traverses the entire list, checking an increasing amount of the entire list each time
> ⇒ Θ(N 2 )

- If there is a cycle, the algorithm stops at the first repeated node after once round the cycle
> ⇒ Θ((j + l) 2 )


# Less naïve circularity detection
Algorithm: at each step, check all previous steps for repeat
- Trade-off: Space for time

## Hash-table Memory
```
Require: sequence :: list
  table ← new Hashtable
  node ← sequence
  while node ≠ NIL do
    if node ∈ table then
      return true
    end if
    table[node] ← true
  end while
return false
```

## Complexity Analysis
Space:
- Hash table with N entries required
> ⇒ Θ(N ) extra space

Time:
- T k = T k−1 + Θ(1)
- If there is no cycle, the algorithm traverses the entire list, doing a constant-time lookup each time
> ⇒ Θ(N )

- If there is a cycle, the algorithm stops at the first repeated node
> ⇒ Θ(j + l)

- (assumes hash-table lookup is Θ(1))

# Hare and Tortoise algorithm
- Also known as Floyd’s cycle-finding algorithm
## Key insight
- for circularity of length l beginning at position j
  - L[k + nl] = L[k]
- for all k > j, n ≥ 0.

## Or in words...
If two nodes at different positions in the list are identical, the difference in
positions is an integer multiple of the circularity length.

## Converse
If there is a circularity and two iterators are each within it, incrementing
the difference between two list iterators by 1 will always lead to the two
iterators arriving at the same list node.

## Algorithm
```
Require: sequence :: list
  tortoise ← rest(sequence)
  hare ← rest(tortoise)
  while hare ≠ NIL do
    if hare = tortoise then
      return true
    end if
    tortoise ← rest(tortoise)
    hare ← rest(rest(hare))
  end while
return false
```

## Complexity Analysis
Space:
- No extra space needed
> ⇒ Θ(1)

Time:
- If there is no cycle, the hare traverses the list; in that time, the tortoise traverses half the list:
> ⇒ Θ(N )

- If there is a cycle, the hare and tortoise meet no more than l steps after the tortoise is in the cycle
> ⇒ Θ(j + l)

## Additional information from algorithm
### Position of first repeat:
1. reset tortoise to the head of the list
2. move hare and tortoise one step at a time (same speed)
3. count steps until hare and tortoise are equal

### Length of circularity
1. hold tortoise still
2. move hare one step at a time
3. count steps until hare and tortoise are equal again

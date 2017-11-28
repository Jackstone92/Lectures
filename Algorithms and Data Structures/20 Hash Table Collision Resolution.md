# Hash Table collision resolution

# Motivation
- We need (in general) the ability to insert an object whose reduced hash code is the same as that of an object already in the hash table.

# Definition
> A collision resolution strategy says what to do if a collision is found.
Routines for **insert**, **find** and **delete** must all agree on the collision
resolution strategy.


# Separate Chaining
aka: “Open hashing”, “Closed addressing”: each hash-table slot contains a *list* of values.  
- closed addressing because you always use the address you're given
- more open where you're storing

## Closed addressing
- The location in the hash table is always the place implied by the hash code
## Open hashing
- The object isn’t directly stored in the hash table

## find
- get index from hash function, and find objects on the contents of the hash table button

```
function find(o,h)
  i ← hash(o,h)
  return find(o,h.table[i])
end function
```

```
function insert(o,h)
i ← hash(o,h)
h.table[i] ← cons(o,h.table[i])
end function
```

```
function delete(o,h)
i ← hash(o,h)
return delete(o,h.table[i])
end function
```

careful! set tombstone not empty to avoid errors


# Open Addressing
aka: “Closed hashing”: if there’s a collision, probe for a empty slot somewhere else
## open addressing
- find a different location in the hash table than that implied by the hash code
## closed hashing
- always directly store in the hash table


## find

```
function find(o,h)
  i ← hash(o,h); k ← 0
  repeat
    j ← probe(i,k,h); k ← k + 1
    if h.table[j] = o then
      return true
    end if
  until empty?(h.table[j])
  return false
end function
```

## insert

```
function insert(o,h)
  i ← hash(o,h); k ← 0
  repeat
    j ← probe(i,k,h); k ← k + 1
  until free?(h.table[j])
  h.table[j] ← o
end function
```


## Linear Probing
If there’s a collision, probe by looking at the next slot.

```
function probe(i,k,h)
return (i + k) mod size(h.table)
end function
```

- good locality of reference
- simple to implement  

but

- similar hash codes lead to secondary collisions

## Why free?, not empty?, in insert?

Delete
```
function delete(o,h)
  i ← hash(o,h); k ← 0
  repeat
    j ← probe(i,k,h); k ← k + 1
  until h.table[j] = o
  h.table[j] ← † // set tombstone
end function
```

Free
```
function free?(value)
  return empty?(value) ∨ value = † // set tombstone
end function
```

## Quadratic probing
If there’s a collision, probe by looking at slots square numbers away.

```
function probe(i,k,h)
return (i - (-1) k × k2) mod size(h.table)
end function
```

- reduced primary clustering
- preserves some locality of reference
- size(h.table) must be a prime number


## Complexity of hash-table Operations
no collisions:
> Θ(1)

everything collides:
> Θ(N)

- usual case: somewhere in between
Improve the usual case:
- decrease probe length

### Robin Hood linear probing
While inserting:
- if you find a value that is less far from its natural space
- steal that space and insert the value you’ve displaced instead
- Make sure that maximum probe length is not too long


## Extending and Re-Hashing
Too many collisions?
1. make a bigger table
2. re-insert all the current contents
  - different reduction will mean different, fewer collisions
  - expensive

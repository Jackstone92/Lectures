# Analysis of Vector Operations

---

# Motivation
- Understand consequence of data structure design decisions
- Simple example of random-access model and big-O notation

# Implementation
Here we are thinking as the data structure **implementor**, not the data structure **user**
- Look "behind the curtain" of the data structure
- Implementing operations, so we can't **use** them!

Primitives:
- mref(n) ⇒ ℤ
- alloc(n) ⇒ ℤ (and allocates memory)
- arithmetic

# Constructor
### Length-data

| n | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|

```
function vNew(n)      // 2
  v ← alloc(n+1)      // 1
  mref(v) ← n         // 1
  return v
end function
```
> ⇒ Θ(1)

### Sentinel

| 0 | 1 | 2 | 3 | 4 | $ |
|---|---|---|---|---|---|

```
function vNew(n)      // 2
  v ← alloc(n+1)      // 1
  mref(v+n) ← $       // 1
  return v
end function
```
> ⇒ Θ(1)

# Dereference
### Length-data

| n | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|

```
function [](v,i)
  return mref(v+i+1)      // 3
end function
```
> ⇒ Θ(1)

### Sentinel

| 0 | 1 | 2 | 3 | 4 | $ |
|---|---|---|---|---|---|

```
function [](v,i)
  return mref(v+i)       // 2
end function
```
> ⇒ Θ(1)

# Length
### Length-data

| n | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|

```
function length(v)
  return mref(v)
end function
```
> ⇒ Θ(1)

### Sentinel

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|

```
function length(v)
  l ← 0                       // 1
  while mref(v+1) ≠ $ do      // 3n+3
    l ← l + 1                 // 2n+2
  end while
  return l
end function
```
> ⇒ Θ(𝑛)

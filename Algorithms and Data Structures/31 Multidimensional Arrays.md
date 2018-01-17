# Multidimensional Arrays

---

# Motivation
- Sometimes the data that you want to store is naturally expressed as a table with more than one dimension.

# Definition
> A multidimensional array is an array that is subscipted using more than one index  
NB: the “multidimensional” in multidimensional arrays refers to the subscripting, **not** the data that is stored:  
**linear array of 3-component colours** Vector  
**linear array of 3-dimensional vectors** Vector  
**2d array of grayscale values** Multidimensional array  
**3d array of temperature values** Multidimensional array  

# Operations
**size**
- return the number of elements in the multidimensional array

**select[k,m,...,n]**
- return the element at position k in the first dimension, me in the second,..., and n in the last dimension

**store![o,k,m,...,n]**
- set the element at position k in the first dimension, m in the second,..., and n in the last dimension to o.

# Implementation: Iliffe vector
- Array of references to lower-dimensional arrays
> An array of Arrays

# Implementation: Dope vector
- One-dimensional array with extra metadata (the "dope" on the array)
> eg. arr[0] stores length, arr[1] and arr[2] store dimensions (eg. 2x4), then following items can be indexed using calculation

# Implementation: example
- Storing a 2x4 matrix:
  - 1,2,3,8
  - 2,3,5,7

## Iliffe vector
- Row-major ordering
[2]  
[[4,1,2,3,8]]  
[[4,2,3,5,7]]  
- 2 and 4s are the length of the arrays

## Dope vector
- Row-major ordering
  - [11, 2, 4, 1, 2, 4, 8, 2, 3, 5, 7]
- Column-major ordering
  - [11, 2, 2, 4, 1, 2, 2, 3, 4, 5, 8, 7]

# Size
## Iliffe vector
```
Require: A :: two-dimensional (Illife) array
  function size(A)
    return length(A) × length(A[0])
  end function
```

## Dope vector
```
Require: A :: multidimensional (dope) array
  function size(A)
    D ← A[0]
    result ← 1
    for 0 ≤ d < D do
      result ← result × A[1+d]
    end for
    return result
  end function
```

# Select
## Iliffe vector
```
Require: A :: multidimensional (Iliffe) array
Require: ks :: list of indices
  function select(A,ks)
    if length(ks) = 1 then
      return A[first(ks)]
    else
      return select(A[first(ks)],rest(ks))
    end if
  end function
```

## Dope vector
```
Require: A :: multidimensional row-major (dope) array
Require: ks :: tuple of indices
  function select(A,ks)
    D ← A[0]
    index ← 0
    for 0 ≤ d < D do
      index ← index × A[1+d] + ks[d]
    end for
    return A[1+D+index]
  end function
```

# Complexity analysis
## Time
- Operations take time proportional to the number of dimensions D, but independent of the size of each dimension.
- For given D, all operations (size, select, store!) take time in **Θ(1)**

## Space
### Iliffe vector
- space overhead proportional to the size of each dimension (worst case, space overhead in **Θ(𝑁)**)

### Dope vector
- space overhead proportional to the number of dimensions (for a given dimension, space overhead in **Θ(1)**)

Multidimensional array (with dope vector) is an example of an **implicit data structure**

# Implicit Data Structures

---

# Motivation
- Pointers in data structures can be wasteful of space and cause inefficiencies on modern architectures. Encoding relationships (e.g. parent, left-child) between elements using storage location can help.
- Pointers/references can also be hard to work with. We’re not going to solve *that* problem here.

# Definition
> An **implicit data structure** is one where the space overhead for encoding the relationship between data contained in the structure is constant, regardless of the number of elements contained in the data structure  
𝑆(𝑁) ∈ Θ(1)

# Example: Linked List
- Space overhead is linear
> 𝑆(𝑁) ∈ Θ(𝑁)

- Implement as a pair of static array and counter (A, c):
  - **first**
    - return A[c]

  - **rest**
    - return (A, c+1)

  - **set-first![o]**
    - A[c] ← o

  - **set-rest![l]**
    - ?

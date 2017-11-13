# Binary Search Trees

---

# Binary Search Tree Property
Let x be a node in a binary search tree. If y is a node in the left subtree of x, then y.node < x.node. If z is a node in the right subtree of x, then z.node ≥ x.node

# Search in Binary Tree
```
Require: tree :: binary tree
  function search(tree, object)
    if null?(tree) then
      return false
    end if
    if tree.key = object then
      return true
    end if
    return search(tree.left, object) ∨ search(tree.right, object)
  end function
```

# Find in Binary Tree
```
Require: tree :: binary search tree
  function find(tree,object)
    if null?(tree) then
      return false
    end if
    if tree.key = object then
      return true
    else if tree.key > object then
      return find(tree.left,object)
    else
      return find(tree.right,object)
    end if
  end function
```

# Complexity Analysis
## Find
- 𝑇(𝑁) = 𝑇(𝑘) + 𝑇(𝑁 − 𝑘 − 1) + Θ(1)
> ⇒ Θ(𝑁)

- Work in terms of the height ℎ of the tree
  - Key to find could in principle be on the lowest level of the tree
> ⇒ Θ(ℎ)

- For a **complete binary search tree**, ℎ is ⌈log(𝑁)⌉
  - 𝑇(𝑁) = 𝑇(𝑁/2) + Θ(1)

## Max
- (as with find: traverse all nodes)
- Descend right subtrees as far as possible
> ⇒ Θ(ℎ)

  - For a **complete binary search tree**, ℎ is s ⌈log(𝑁)⌉
> ⇒ Θ(log(𝑁))

## Constructor
> ⇒ Θ(𝑁 log(𝑁))

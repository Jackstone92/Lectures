# The Master Theorem

---

# Motivation
- (Asymptotically) solves recurrence relationships
- Including:
  - Straightforward ones (from first year)
  - Harder ones (from this course)
- You need to:
  - **Know** the result
  - Be able to **apply** the result
- (You don't need to know the proof)

# Examples
## Binary Search
> 𝑇(𝑁) = 𝑇(𝑁/2) + 𝑂(1)

## Binary Tree Traversal
> 𝑇(𝑁) = 2𝑇(𝑁/2) + 𝑂(1)

## Merge Sort
> 𝑇(𝑁) = 2𝑇(𝑁/2) + 𝑂(𝑁)

## Recursion Trees
> 𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑁)
⇒ 𝑇(𝑁)

# Theorem Statement
> 𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑁)

## Three Cases:
1. 𝑓(𝑁) ∈ 𝑂(𝑁<sup>𝑐</sup>) where 𝑐 < log<sub>𝑏</sub>𝑎
2. 𝑓(𝑁) ∈ Θ(𝑁<sup>𝑐</sup>log<sup>𝑘</sup>𝑁) where 𝑐 = log<sub>𝑏</sub>𝑎
3. 𝑓(𝑁) ∈ Ω(𝑁<sup>𝑐</sup>) where 𝑐 > log<sub>𝑏</sub>𝑎


### Theorem Statement Case 1:
𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑁)  
- 𝑓(𝑁) ∈ 𝑂(𝑁<sup>𝑐</sup>) where 𝑐 < log<sub>𝑏</sub>𝑎

#### Result:
> 𝑇(𝑁) ∈ Θ(𝑁<sup>log<sub>𝑏</sub>𝑎</sup>)

#### Example (binary tree traversal)
𝑇(𝑁) = 2𝑇(𝑁/2) + 1
- 𝑎 = 2, 𝑏 = 2, log<sub>𝑏</sub>𝑎 = 1; 𝑓(𝑁) = 1 ∈ 𝑂(𝑁<sup>0</sup>)
So
> 𝑇(𝑁) ∈ Θ(𝑁<sup>1</sup>) = Θ(𝑁)

### Theorem Statement Case 2:
𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑁)
- 𝑓(𝑁) ∈ Θ(𝑁<sup>𝑐</sup>log<sup>𝑘</sup>𝑁) where 𝑐 = log<sub>𝑏</sub>𝑎

#### Result:
> 𝑇(𝑁) ∈ Θ(𝑁<sup>log<sub>𝑏</sub>𝑎</sup>log<sup>𝑘+1</sup>𝑁)

#### Example (binary search)
𝑇(𝑁) = 𝑇(𝑁/2) + 1
- 𝑎 = 1, 𝑏 = 2, log<sub>𝑏</sub>𝑎 = 0; 𝑓(𝑁) = 1 ∈ Θ(𝑁<sup>0</sup>)
So
> 𝑇(𝑁) ∈ Θ(𝑁<sup>0</sup>log<sup>1</sup>𝑁) = Θ(log𝑁)

#### Example (merge sort)
𝑇(𝑁) = 2𝑇(𝑁/2) + 𝑁
- 𝑎 = 2, 𝑏 = 2, log<sub>𝑏</sub>𝑎 = 1; 𝑓(𝑁) = 𝑁 ∈ Θ(𝑁<sup>1</sup>)
So
> 𝑇(𝑁) ∈ Θ(𝑁<sup>1</sup>log<sup>1</sup>𝑁) = Θ(𝑁log𝑁)

### Theorem Statement Case 3:
𝑇(𝑁) = 𝑎𝑇(𝑁/𝑏) + 𝑓(𝑁)
- 𝑓(𝑁) ∈ Ω(𝑁<sup>𝑐</sup>) where 𝑐 > log<sub>𝑏</sub>𝑎

#### Result:
> 𝑇(𝑁) ∈ Θ(𝑓(𝑁))

#### Example (quickselect)
𝑇(𝑁) = 𝑇(𝑁/2) + 𝑁
- 𝑎 = 1, 𝑏 = 2, log<sub>𝑏</sub>𝑎 = 0; 𝑓(𝑁) = 𝑁 ∈ 𝑂(𝑁<sup>1</sup>)
So
> 𝑇(𝑁) ∈ Θ(𝑓(𝑁)) = Θ(𝑁)

# Proof
- See CLRS for details:
  - Polynomially smaller/bigger
  - Handling floor ⌊𝑥⌋ and ceiling ⌈𝑥⌉
  - Regularity condition for case 3

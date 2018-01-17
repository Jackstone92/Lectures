# Knuth-Morris-Pratt Matching

---


# Motivation
- Deterministically Θ(𝑚 + 𝑛) string matching

# Definition
> Knuth-Morris–Pratt matching uses information about the pattern P to
avoid redundant work when doing string matching.

# Example
Consider match(abcde, text)
- all characters in P different
- mismatch in index position 𝑘
  - matches in all previous positions [0,𝑘)
  - can safely advance next start position to 𝑘

# Prefix table
Also called "prefix function" or "failure function"
- encode for each index 𝑘 the length of the longest **prefix** of the pattern P which is a **suffix** of the subsequence of the pattern P[0..𝑘]

# Knuth-Morris-Pratt Algorithm
```
function KMPmatch(T,P)
  n ← length(T); m ← length(P)
  π ← computePrefix(P)
  q ← 0
  for 0 ≤ i < n do
    while q > 0 ∧ P[q] ≠ T[i] do
      q ← π[q-1]
    end while
    if P[q] = T[i] then
      q ← q + 1
    end if
    if q = m then
      return i - m + 1
    end if
  end for
  return false
end function
```

## Knuth-Morris-Pratt Algorithm: compute prefix
```
function computePrefix(P)
  m ← length(P)
  π ← new Array(m); π[0] ← 0
  k ← 0
  for 1 ≤ q < m do
    while k > 0 ∧ P[k] ≠ P[q] do
      k ← π[k-1]
    end while
    if P[k] = P[q] then
      k ← k + 1
    end if
    π[q] ← k
  end for
  return π
end function
```





























#

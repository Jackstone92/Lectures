# String Matching

---

# Motivation
generalisation of search operation (sequences, not just single
elements)
- applications include text editors, classifiers, information retrieval systems
- extensions used in
- spelling checkers
- DNA sequence matching
- protein structure representations


# Definition
> String matching returns the smallest index at which the pattern, P, is found
exactly in the text, T, or false if the pattern is not present in the text at all.  
**C++ std::string::find()**  
**Java java.lang.String.indexOf()**  

# String Matching Algorithm

```
function match(T,P)
  m ← length(P)
  for 0 ≤ s ≤ length(T) - m do
    if T[s...s+m] = P[0...m] then
      return s
    end if
  end for
  return false
end function
```

# Naïve Algorithm

```
function match(T,P)
  m ← length(P)
  for 0 ≤ s ≤ length(T) - m do
    found ← true
    for 0 ≤ j < m do
      if T[s+j] ≠ P[j] then
        found ← false; break
      end if
    end for
    if found then
      return s
    end if
  end for
  return false
end function
```

# Complexity Analysis
## space
- no particular requirements for additional storage
> ⇒ Θ(1)

## time
- outer loop happens n − m + 1 times (worst case)
- inner loop m times (worst case)
> ⇒ Θ((n + 1)m − m<sup>2</sup> ) ∼ Θ(nm)

For particular sizes of pattern:
- **small** m ∼ c ⇒ Θ(n)
- **large** m ∼ n ⇒ Θ(n)
- **intermediate** m ∼ n/2 ⇒ Θ(n 2 )

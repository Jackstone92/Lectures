# Rabin-Karp String matching

---


# Motivation
- naïve string matching takes time in Θ(𝑚𝑛)
- lots of wasted work

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

# Less work in the inner loop
- avoid Θ(𝑚) comparisons where possible
- constant-time test:
  - hash value comparison

# Rabin-Karp Algorithm

```
function RKmatch(T,P)
  m ← length(P); hm ← hash(P)
  for 0 ≤ s ≤ length(T) - m do
    if hash(T[s...s+m]) = hm then
      found ← true
      for 0 ≤ j < m do
        if T[s+j] ≠ P[j] then
          found ← false; break
        end if
      end for
      if found then
        return s
      end if
    end if
  end for
  return false
end function
```

# Hash function
Normally:
- hash(T[s...s+m]) takes time in Θ(𝑚)
- no saved work in general

# Rolling hash
Clever choice of hash function makes a difference!
> rolling-hash(h,T[s-1],T[s+m])

Examples of suitable hash functions:
- modular add: ∑<sub>𝑖</sub> 𝑥<sub>𝑖</sub> mod 𝑘
- exclusive or: ⊕<sub>𝑖</sub>𝑥<sub>𝑖</sub>
- modular polynomial: ∑<sub>𝑖</sub> 𝑥<sub>𝑖</sub>𝑝<sup>𝑖</sup> mod 𝑘

# Modular add
> ∑<sub>𝑖</sub> 𝑥<sub>𝑖</sub> mod k

- 21-bit characters: k might be 2<sup>24</sup> or 2<sup>32</sup>
  - (resist temptation to use 8-bit characters and k or 2<sup>8</sup>)

```
function rolling-hash(prev,remove,add)
  return (prev - remove + add) mod k
end function
```

- extremely limited bit mixing
- high chance of hash collisions in typical texts
  - eg. hash(ab) = hash(ba)

# Exclusive or
> ⊕<sub>𝑖</sub>𝑥<sub>𝑖</sub>

- no parameters
  - (still need to resist temptation to use 8-bit characters)

```
function rolling-hash(prev,remove,add)
  return prev ⊕ remove ⊕ add
end function
```

- no bit mixing at all
- high chance of hash collisions in typical texts
  - eg. hash(oboe) = hash(bell)

# Modular polynomial
> ∑<sub>𝑖</sub> 𝑥<sub>𝑖</sub>𝑝<sup>𝑖</sup> mod 𝑘

- typically choose a small(ish) prime 𝑝
- use machine word (eg. 2<sup>32</sup>) for 𝑘

```
function rolling-hash(prev,remove,add)
  return ((prev − remove × 𝑝𝑚−1) × 𝑝 + add) mod 𝑘
end function
```

- good mixing (eg. for prime 𝑝 = 101, character bits 0-7 affect hash bits 0-13)
- **hash collisions in typical texts rarer**


# Complexity analysis
## Space
- No need for extra space that scales with any parameter
> ⇒ Θ(1)

## Time
- For good rolling hash:
  - new hash computation from old hash in Θ(1) time
  - hash collisions rare (still need to do at least two o Θ(m) hash computations)
> ⇒ Θ(𝑛) + Θ(𝑚) (average case)

- even for the best hash function...
  - ...suitably adversarial input will collide a lot
> ⇒ Θ(𝑛𝑚) (worst case)

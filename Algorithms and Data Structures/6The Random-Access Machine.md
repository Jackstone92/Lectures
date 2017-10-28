# The Random-Access Machine

---

# Motivation
- Model for real computers
- Simple enough to reason about

# Definition
A random-access machine is a computer with
- an unbounded amount of memory
  - addressable by integers
  - each memory access takes a constant time step
- a program made up of simple instructions
  - executed one-at-a-time
  - each simple instruction takes a constant time step
- program combinations using functions, loops, conditionals
  - the combination itself takes a constant time step
  - the result of combination takes longer

# Time and space
### Running time
The number of constant time steps taken
- memory access
- simple instructions executed
- combinations executed

### Space used
The number of memory locations used
- in addition to the space used by the input: "additional space used"

# Example
```
function Exercise1(v)
  a ← 0; b ← 0                                // 2  O(2)
  for 0 ≤ i < length(v) do                    // n = Length(v)  O(n)
    if v[i] > b then                          // n  O(n)
      if v[i] > a then                        // up to n  O(n)
        b ← a                                 // up to n  O(n)
        a ← v[i]                              // up to n  O(n)
      else
        b ← v[i]                              // up to n  O(n)
      end if
    end if
  end for
  return b
end function
```

# The point of all this
In software design and implementation, we often want to:
- minimise the time the program takes to run
- minimise the resources (eg. memory, disk space) the program consumes

The Random-Access Machine model
- simple enough to compute answers, at least approximately
- realistic enough to be a guide to real computers

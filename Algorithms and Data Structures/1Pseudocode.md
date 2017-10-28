# Introduction to Pseudocode

---

## Definition:
Pseudocode is an informal, high-level description of the operation of a computer program or other algorithm

## Implications:
* use simplest way to describe things
  * even if that is in English
* not executable by a computer
  * walk-through by humans
  * reasonable

---

# General

## Variable assignment
Variable assignment is indicated by the `←` symbol:  
eg.
```
x ← 1
```

Variables in pseudocode do not need to be declared

### Vertical space
Statements separated by vertical space happen in sequence:
```
x ← 1
y ← x
x ← 2
```

### Semicolons
Alternatively, semicolons separate statements in a sequence:
```
x ← 1; y ← x; x ← 2
```

---

# Conditionals
## Conditional operators
Use mathematical notation (not code notation) in pseudocode:
- =, <, >
- ≤, ≥ (not <=, =>, >=)
- ∨, ∧, ¬

# Equality operators
### Use `=` as equality operator (**not** assignment operator)
Instead of `==`, pseudocode uses `=` to compare two variables.
eg.
```
return 1 = 3
// false

return 1 = 1
// true
```

## `if`
Use **if then** to decide whether to do a sequence or not.  
End the sequence with **end if**
```
x ← 0
if x > -6 then
  x ← x + 1
end if
```

## `else`
Use **else** to delimit a sequence to execute if the conditional is **not** true
```
x ← 0
if x > 17 then
  x ← x + 1
else
  x ← x - 1
end if
```

## `else if`
Define chains of conditionals using **else if**. At most one of the sequences is executed.
```
x ← 0
if x > 3 then
  x ← 5
else if x > -3 then
  x ← 7
else if x > -8 then
  x ← 9
else
  x ← 11
endif
```

# Loops
## `for`
To loop with a variable bound to a series of numbers, use **for** with a description of the series:
```
x ← 0
for 0 ≤ i < 100 do
  x ← x + 1
end for
```

The order might matter: start with the **left-hand** bound and move towards the right-hand one.

```
x ← 0
for 0 ≤ i < 100 do
  x ← i
end for

x ← 0
for 100 > i ≥ 0 do
  x ← i
end for
```

### `continue`
Use **continue** to proceed directly to the next iteration of the innermost loop:
```
x ← 0
for 0 ≤ i < 10 do
  x ← x + 1
  if x > 3 then
    continue
  end if
  x ← x + i
end for
```

### `break`
Use **break** to finish the innermost loop:
```
x ← 0
for 0 ≤ i < 10 do
  x ← x + 1
  if x > 3 then
    break
  end if
  x ← x + i
end for
```

### Nested Loops
With nested loops, for each iteration of an outer loop, do the whole inner loop:
```
x ← 0
for 0 ≤ i < 3 do
  for 0 ≤ j < 4 do
    x ← x + 1
  end for
end for
```

## `forall`
Iterate over members of a collection using forall:
```
x ← 0
  for all p ∈ prime numbers below 10 do
  x ← x + 1
end for
```

### Ordering
There may be a natural order to the iteration (eg. when iterating over a linear collection), but usually there won't be. Don't rely on a particular order!

## `while`
Use **while** to express a loop which tests a condition at the *start* of a sequence, and if that condition is *true*, does another iteration of the loop:
```
x ← 0
y ← 3
while y > 0 do
  x ← x + 1
  y ← y − 1
end while
```

## `repeat`
Use **repeat until** to express a loop which tests a condition at the *end* of a sequence, and if that condition is *false*, does another iteration of the loop:
```
x ← 0
y ← 3
repeat
  x ← x + 1
  y ← y − 1
until y < 0
```

## `loop`
Use **loop** to express an unconditional loop.  
You will need to use **break** to terminate the loop!
```
x ← 11342
loop
  if x = 1 then
    break
  else if x is even then
    x ← x ÷ 2
  else
    x ← 3 × x + 1
  end if
end loop
```

---

# Functions
Define functions using **function**, and return a value using **return**
```
function fact(n)
  if n = 0 then
    return 1
  else
    return n × fact(n−1)
  end if
end function
```

## Function calls
Functions have zero or more arguments and return one result. Call them using their name, with arguments in brackets
```
n ← 5
x ← fact(n)
```

## Pre- and post- conditions
Make it clear to the reader what conditions a function requires to operate correctly, and what it does if those conditions are mathematical
```
Require: n ∈ ℕ₀
Ensure: Compute and return n!
  function fact(n)
    if n = 0 then
      return 1
    else
      return n × fact(n−1)
    end if
  end function
```

### Pre-conditions
Things are required to be `true` **before** a function or a method is abled to be called.

### Post-conditions
Things are must be `true` **after** a function or a method is complete.

### Invariants
Things are always `true` before running a method or a function, and stay `true` after a method is complete

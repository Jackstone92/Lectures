# Introduction to Pseudocode

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

## if
Use **if then** to decide whether to do a sequence or not.  
End the sequence with **end if**
```
x ← 0
if x > -6 then
  x ← x + 1
end if
```

## else
Use **else** to delimit a sequence to execute if the conditional is **not** true
```
x ← 0
if x > 17 then
  x ← x + 1
else
  x ← x - 1
end if
```

## else if
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
## For
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

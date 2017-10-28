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
Variable assignment is indicated by the `<-` symbol:  
eg.
```
x <- 1
```

Variables in pseudocode do not need to be declared

### Vertical space
Statements separated by vertical space happen in sequence:
```
x <- 1
y <- x
x <- 2
```

### Semicolons
Alternatively, semicolons separate statements in a sequence:
```
x <- 1; y <- x; x <- 2
```

---

# Conditionals
## Conditional operators
Use mathematical notation (not code notation) in pseudocode:
- =, <, >
- ≤, ≥ (not <=, =>, >=)
- ∨, ∧, ¬

## if
Use **if then** to decide whether to do a sequence or not.  
End the sequence with **end if**
```
x <- 0
if x > -6 then
  x <- x + 1
end if
```

## else
Use **else** to delimit a sequence to execute if the conditional is **not** true
```
x <- 0
if x> 17 then
  x <- x + 1
else
  x <- x - 1
end if
```

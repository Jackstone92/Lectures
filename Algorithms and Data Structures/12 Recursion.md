# Recursion

---

# Motivation
### A way to describe solutions of problems that makes them
- easy to prove correct
- easy to compute how they scale

# Definition
> The definition of a problem or solution in terms of (variant forms of) itself

# Ingredients
- **Base case**: non-recursive condition (possibly more than one)
- **Recursive steps**: rules reducing the problem towards the base case
> Recursion = base case + recursive steps

# Examples
## Factorial
```
n! = n × (n-1)! and 0! = 1
```

## Fibonacci numbers
```
F(n) = F(n-1) + F(n-2) and F(0) = 0, F(1) = 1
```

## Tower of Hanoi
```
FUNCTION MoveTower(disk, source, dest, spare):
IF disk == 0, THEN:
  move disk from source to dest
ELSE:
  MoveTower(disk - 1, source, spare, dest)   // Step 1 above
  move disk from source to dest              // Step 2 above
  MoveTower(disk - 1, spare, dest, source)   // Step 3 above
END IF
```

# Examples: list algorithms
## **Search**  
Is the object o present in the list l?
- **Base case**: is the object o present in the list NIL?
- **Recursive step**: is the object o equal to the first element of the list? If not, is it in the rest of the list?

## **Selection**
Return the maximum of the objects in the list l  
- **Base case**: what is the maximum element of the empty list?
- **Alternative base case**: what is the maximum element of a list with one element?
- **Recursive step**: how does the first element compare with the maximum of the rest of the list?

## **Selection**
Return the k<sup>th</sub> biggest of the objects in the list l
- **Base case**: what is the k<sup>th</sup> biggest element of a list with k elements?
- **Recursive step**: how does the first element compare with the k<sup>th</sup> biggest element of the rest of the list?
- **Base case, second try**: what are the k<sup>th</sup> biggest elements of a list with k elements?
- **Recursive step, second try**: how does the first element compare with the k<sup>th</sup> biggest elements of the rest of the list?

# Control Flow and Iterations

---

# Flow Control
- Unless specified otherwise, the order of statement execution through a method is linear (one statement after another in sequence)
- Some statements allow us to
  - decide whether or not to execute a particular statement
  - execute a statement over and over, repetitively
- These decisions are based on *boolean expressions* (or *conditions*)
- The order of statement execution is called the *flow of control*

# Conditional statements
- Let us choose which statement will be executed next
- Therefore they are sometimes called *selection statements*
- Conditional statements give us the power to make basic decisions
- The Java conditional statements are:
  - *if statement*
  - *if-else statement*
  - *switch statement*

## if statement
```java
if(condition) {
  statement;
}
```
If the *condition* is true, the *statement* is executed. If it is false, the *statement* is skipped

## if-else statement
```java
if(condition) {
  statement1;
} else {
  statement2;
}
```
If the *condition* is true, *statement1* is executed. If the *condition* is false, *statement2* is executed. One or the other will be executed, but not both

## switch statement
- Provides another way to decide which statement to execute next
- Evaluates an expression, then attempts to match the result to one of several possible *cases*
- Each case contains a value and list of statements
- Often a *break statement* is used as the last statement in each case's statement list
  - causes control to transfer to the end of the *switch* statement
  - otherwise, the flow of control will continue to the next case
- Can have an optional *default case*
  - if present, control will transfer to it if no other case values match
  - if no default case and no other value matches, control falls through the to the statement after the switch
- The expression of a *switch* statement must result in an *integral type* (int or char)
  - cannot be a *boolean* value, a floating point value (float or double) or another integer type
  - can now result in a string type which uses .equals() to compare strings

```java
switch(option) {
  case 'A':
    statement1;
    break;
  case 'B':
    statement2;
    break;
  case 'C':
    statement3;
    break;
  default:
    baseCase;
    break;
}
```

---

# Repetition statements
- Allow us to execute a statement multiple times
- Referred to as *loops*
- Controlled by boolean expressions
- Java has three kinds of repetition statements:
  - *while loop*
  - *do-while loop*
  - *for loop*

# The while statement
```java
while(condition) {
  statement;
}
```
- If the *condition* is true, the *statement* is executed
- Then the condition is evaluated again, and if it is still true, the statement is executed again
- The statement is executed repeatedly until the condition becomes false
- The body of a *while* loop will execute **zero or more times**

## Infinite Loops
An example of an infinite loop:
```java
int i=0;
while(i<=0) {
  System.out.println(i);
  i = i-1;
}
```
- This loop will continue executing forever!

# The do-while statement
```java
do {
  statement;
} while(condition);
```
- The *statement* is executed once initially, and then the *condition* is evaluated
- The statement is executed repeatedly until the condition becomes false
- The body of a *do-while* loop will execute **one or more times**

# The for statement
```java
for (initialisation; condition; increment) {
  statement;
}
```
- The *initialisation* is executed once before the loop begins
- The *statement* is executed until the *condition* becomes false
- The *increment* is executed at the end of each iteration

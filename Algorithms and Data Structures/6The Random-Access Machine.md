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

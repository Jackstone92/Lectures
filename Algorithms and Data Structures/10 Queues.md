# Queues

---

# Motivation
- First-in first-out collection
- Useful for mediating access to resources
  - wait your turn
  - (but see priority-queues)

# Definition
> A queue is an extensible collection of data where removal of data
happens at the head of the queue (maintaining the order of
remaining elements), and addition of data happens at the tail of the
queue (again maintaining order of other elements)

# Operations
**Head**
- return the element at the head of the queue  

**Dequeue!**
- return and remove the element at the head of the queue  

**Enqueue![o]**
- add o to the tail of the queue  

**Empty?**
- return true if the queue has no elements  

# Implementation

| Ptr (to below) |
|      ---       |

&darr;

| Ptr to ("foo", 17) | Ptr (to below) |
| --- | --- |

&darr;

| Ptr to ("bar", -3.4) | Ptr (to below) |
| --- | --- |

&darr;

| Ptr to ("baz", 55) | Ptr (to below) |
| --- | --- |


# Complexity analysis
### head, dequeue!, empty?
- Exactly the same as stack operations top, pop!, empty?
> ⇒ Θ(1)

### enqueue!
- Add to the **end** of the underlying list: N pointer reads
> ⇒ Θ(N)

# Better Implementation
![](http://slideplayer.com/slide/5381188/17/images/21/Priority+Queue+Implementation.jpg)

# Updated complexity analysis
### head, dequeue!, empty?
- As before, exactly the same as stack operations top, pop!, empty?
> ⇒ Θ(1)

### enqueue!
- One pair allocation, two pointer writes
> ⇒ Θ(1)

## Linked List

### Common Techniqu: Runner (second pointer)

```
The runner technique means that you iterate through the linked list with two pointers simultaneously, with one ahead of the other. 

The "fast" node might be ahead by a fixed amount, or it might be hopping multiple nodes for each one node that the "slow" node iterates through. 

For example, suppose you had a linked list:
    a1 ->a2 -> ••• ->an ->b1 ->b2 -> ••• ->bn and you wanted to rearrange it into:
    a1 ->b1 ->a2 ->b2 -> ••• ->an ->bn. 

Using 2 pointer: one pointer pl (the fast pointer) move every two elements for every one move that p2
makes. 

When p1 hits the end of the linked list, p2 will be at the midpoint. Then, move pl back to the front
and begin "weaving"the elements. On each iteration, p2 selects an element and inserts it after pl. 
```
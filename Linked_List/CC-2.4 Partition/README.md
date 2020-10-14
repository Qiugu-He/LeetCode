## #2.4 Partition: 

Write code to partition a linked list around a value x, such that all nodes less than x come before all nodes greater than or equal to x. If x is contained within the list the values of x only need to be after the elements less than x (see below). The partition element x can appear anywhere in the "right partition"; it does not need to appear between the left and right partitions. 

```
E.g: 
Input: 3 -> 5 -> 8 -> 5 -> 10 -> 2 -> 1 [partition= 5] 
Output: 3 -> 1 -> 2 -> 10 -> 5 -> 5 -> 8

```

## Solution:
```Java
/*
1. Create two different linked lists: one for elements less than x, and one for elements greater than or equal to x. 

2. Iterate through the linked list, inserting elements into before list or after list. Once reach the end of the linked list and have completed this splitting, merge the two lists. 
*/

class Solution { 
    public LinkedListNode partition(LinkedListNode node, int x) { 
        LinkedlistNode beforeStart = null; 
        LinkedListNode beforeEnd = null; 
        LinkedListNode afterStart = null; 
        LinkedListNode afterEnd = null; 

        /* Partition list*/
        while (node!= null) {
            LinkedListNode next= node.next;
            node.next = null;
            
            /* Insert node into end of before list*/
            if (node.data< x) {
                if (beforeStart == null) {
                    beforeStart = node;
                    beforeEnd = beforeStart;
                } else {
                    beforeEnd.next = node;
                    beforeEnd = node;
                }
            } else {
            /* Insert node into end of after list*/
            if (afterStart == null) {
                afterStart = node;
                afterEnd = afterStart;
            } else {
                afterEnd.next = node;
                afterEnd = node;
            }
        }
        node = next;
    }

    if (beforeStart == null) {
        return afterStart;
    }

    /* Merge before list and after list */
    beforeEnd.next = afterStart;
    
    return beforeStart;
}
```
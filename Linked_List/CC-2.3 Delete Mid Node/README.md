## #2.3 Delete Middle Node: Implement an algorithm to delete a node in the middle (i.e., any node but the first and last node, not necessarily the exact middle) of a singly linked list, given only access to that node. 

## Solution:
```Java
/*
Simply copy the data from the next node over to the current node, and then to delete the
next node. 
*/

class Solution { 
    public boolean deleteMid (LinkedListNode midNode) {
        if(midNode == null || midNode.next == null){
            return false;
        } 

        LinkdedListNode next = midNode.next;
        midNode.data = next.data;
        midNode.next = next.next;

        return true;
    }
}

```
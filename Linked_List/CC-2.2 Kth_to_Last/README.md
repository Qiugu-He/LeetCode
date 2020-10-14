## #2.2 Return Kth to Last: Implement an algorithm to find the kth to last element of a singly linked list.

## Solution : 2 pointer 
```Java
/*
Use two pointers: pl and p2. 

 - Putting p2 at the beginning and moving p1 k nodes into the list.

 - Move them at the same pace: 
    - p1 will hit the end of the linked list after k steps
    - At this point, p2 will be k nodes into the list, or k nodes from the end.
*/
class Solution { 
    public void nthTolast (LinkedListNode head, int k) { 
        LinkedlistNode p1 = head;
        LinkedlistNode p2 = head;

        //move p1 -> k nodes in list
        for (int i =0; i< k; i++){
            if(p1 == null){
                return null;
            }

            p1=p1.next;
        }

        //move p1, p2 same pace, when p1 hits end, p2 will be at right element
        while(p1 != null){
            p1=p1.next;
            p2=p2.next;
        }

        return p2;
    }
}

```
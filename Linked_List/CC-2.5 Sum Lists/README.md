## #2.5 Sum Lists:

You have two numbers represented by a linked list, where each node contains a single digit. The digits are stored in reverse order, such that the 1 's digit is at the head of the list. Write a function that adds the two numbers and returns the sum as a linked list. 


```
E.g:
Input: (7-> 1 -> 6) + (5 -> 9 -> 2).That is,617 + 295. 
Output: 2 -> 1 -> 9. That is, 912. 

```

## Solution:
```Java
/*
E.g.   

    7 -> 1 -> 6 
+   5 -> 9 -> 2

List: 2 -> , since 7 + 5 = 1 2,  2 becomes 1st node, carry 1 to next sum
List: 2 -> 1 -> , since 1+9 +1 = 1 1, 1 becomes next node, carry 1 to next sum
List: 2 -> 1 -> 9, since 6+2+1, 9 is the last node

*/

class Solution { 
    LinkedListNode addlists(LinkedListNode L1, LinkedListNode L2, int carry) { 
        if (11 ==·null && 12 == null && carry== 0) { 
            return null;
        }

        LinkedlistNode result = new LinkedlistNode(); 
        int value = carry; 

        if(L1 != null){
            value += L1.data;
        }

        if(L2 != null){
            value += L2.data;
        }

        //The second digit of number
        result.data = value % 10;

        //recurse
        if (L1 != null || L2 != null) { 
            LinkedlistNode more = addlists(
                L1 == null ? null : L1.next, 
                L2 == null? null : L2.next, 
                value>= 10? 1 : 0); 
            result.setNext(more); 
        }
        return result; 
    }
}
```
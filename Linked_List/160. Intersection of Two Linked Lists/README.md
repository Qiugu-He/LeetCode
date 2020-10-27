## 160. Intersection of Two Linked Lists

Write a program to find the node at which the intersection of two singly linked lists begins.

For example, the following two linked lists:
```
      a1 -> a2
                \
                  c1 -> c2 -> c3
b1 -> b2 -> b3  /

Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Reference of the node with value = 8
Input Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
```

```Java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null)
            return null;
        
        //get Length of A
        ListNode cur = headA;
        int lenA = 0;
        while(cur!= null){
            lenA ++;
            cur = cur.next;
        }
        
        //get length of B
        cur = headB;
        int lenB = 0;
        while(cur!= null){
            lenB++;
            cur = cur.next;
        }
        
        ListNode curA = headA;
        ListNode curB = headB;
        
        //get the intersection point( Move smllest list's pointer)
        if(lenA > lenB){
            for(int i =0; i< lenA-lenB; i++){
                curA = curA.next;
            }
        }
        if(lenA < lenB){
            for(int i =0; i< lenB-lenA; i++){
                curB = curB.next;
            }
        }
        
        //find the intersection point
        while(curA != null){
            if(curA == curB)
                return curA;
            curA = curA.next;
            curB = curB.next;
        }
        
        return null;
        
        
    }
}
```


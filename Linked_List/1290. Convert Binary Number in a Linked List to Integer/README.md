## 1290. Convert Binary Number in a Linked List to Integer
Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

 

Example 1:


Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
Example 2:

Input: head = [0]
Output: 0
Example 3:

Input: head = [1]
Output: 1

```Java
class Solution {
    public int getDecimalValue(ListNode head) {
        if(head == null)
            return 0;
        
        String res = "";
        String temp = null;
        ListNode tmpNode = head;
    
        while(tmpNode != null){
            temp = Integer.toString(tmpNode.val);
            res += temp;
            tmpNode = tmpNode.next;
        }
        
        return Integer.parseInt(res, 2);
    }
}
```
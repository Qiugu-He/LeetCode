## 21. Merge Two Sorted Lists
Merge two sorted linked lists and return it as a new sorted list. The new list should be made by splicing together the nodes of the first two lists.

Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]

```Java
/*
   - The key to solve the problem is defining a fake head. 
   - Then compare the first elements from each list. 
   - Add the smaller one to the merged list.
   - Finally, when one of them is empty, simply append it to the merged list, since it is already sorted.

*/
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head = new ListNode();
        ListNode dumme = head;
        
        ListNode p1 = l1;
        ListNode p2 = l2;
        
        while(p1 != null && p2 != null){
            if(p1.val > p2.val){
                dumme.next = p2;
                p2 = p2.next;
            }
            else{
                dumme.next = p1;
                p1 = p1.next;
            }
            
            dumme = dumme.next;
        }
        
        if(p1 != null)
          dumme.next = p1;
        
        if(p2 != null)
            dumme.next = p2;
        
        return head.next;
    }
}
```
## Merge a linked list into another linked list at alternate positions
Given two linked lists, insert nodes of second list into first list at alternate positions of first list

```
E.g:
L1: 5->7->17->13->11
L2: 12->10->2->4->6

Output: 
L1: 5->12->7->10->17->2->13->4->11->6
L2: null

L1: 1->2->3 
L2: 4->5->6->7->8

Output: 
L1: 1->4->2->5->3->6 
L2: 7->8

```


```Java
    void merge(LinkedList q) 
    { 
        Node p_curr = head, q_curr = q.head; 
        Node p_next, q_next; 
  
        // While there are available positions in p; 
        while (p_curr != null && q_curr != null) { 
  
            // Save next pointers 
            p_next = p_curr.next; 
            q_next = q_curr.next; 
  
            // make q_curr as next of p_curr 
            q_curr.next = p_next; // change next pointer of q_curr 
            p_curr.next = q_curr; // change next pointer of p_curr 
  
            // update current pointers for next iteration 
            p_curr = p_next; 
            q_curr = q_next; 
        } 
        q.head = q_curr; 
    } 
```
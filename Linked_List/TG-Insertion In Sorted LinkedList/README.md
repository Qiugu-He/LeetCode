## Given a sorted linked list and a value to insert, write a function to insert the value in a sorted way.
```
E.g:
Input: 2 - 5 - 7 - 10 - 15, 9

Output: 2 - 5 - 7 - 9 - 10 - 15
```

```Java
 void sortedInsert(Node n) 
    { 
        Node curr; 
  
        /* Special case for head node */
        if (head == null || head.data  >= n.data) { 
            n.next = head; 
            head = n; 
        }
        else 
        { 
            curr = head; 
            while (curr.next != null && curr.next.data < n.data) {
                curr = curr.next; 
            }
  
            n.next = curr.next; 
            curr.next = n; 
        } 
    } 
```
## Given a Singly Linked List, write a function to delete a given node.

```Java
    void deleteNode(Node head, Node n) { 
        
        //Case 1:  When node to be deleted is head node 
        if (head == n) { 
            if (node.next == null) { 
                System.out.println("There is only one node. Deletion not allowed "); 
                return; 
            } 
            head.data = head.next.data; 
            head.next = head.next.next; 
  
            return; 
        } 
  
        // Case 2: Not first node, follow the normal deletion process 
        // 1. find the previous node 
        Node prev = head; 
        while (prev.next != null && prev.next != n) { 
            prev = prev.next; 
        } 
        // 2. Check if node really exists in Linked List 
        if (prev.next == null) { 
            System.out.println("Given node is not present in Linked List"); 
            return; 
        } 
        // 3. Remove node from Linked List 
        prev.next = prev.next.next; 

        return; 
    } 
```
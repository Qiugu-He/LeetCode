## #2.1. Remove Dups: Write code to remove duplicates from an unsorted linked list. 

## Solution 1: Using a Hashtable to track dups
```Java

/*
Iterate through the linked list, adding each element to a hash table. When
we discover a duplicate element, we remove the element and continue iterating
*/
class Solution { 
    public void deleteDups(LinkedListNode n) { 
        HashSet<Integer> set = new HashSet<Integer>(); 

        LinkedListNode previous = null; 
        while (n != null) {
            if (set.contains(n.data)) { 
                previous.next = n.next; 
            } else { 
                set.add(n.data); 
                previous = n; 
            }
            n = n.next;
        }
    }
}

```

## Solution 2: No buffer allowed
```Java

/*
Iterate with two pointers: current which iterates through the linked list, 
and runner which checks all subsequent nodes for duplicates. 
*/
class Solution { 
    public void deleteDups(LinkedListNode head) { 
        LinkedListNode current = head; 
        while (current != null) { 
            /* Remove all future nodes that have the same value */ 
            LinkedListNode runner = current;
            while (runner.next != null) { 
                if (runner.next.data == current.data) { 
                    runner.next = runner.next.next; 
                }else{
                    runner = runner.next; 
                }
            }
            current current.next; 
        }
    }
}

```





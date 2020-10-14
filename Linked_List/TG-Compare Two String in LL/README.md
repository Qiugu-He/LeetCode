Given two strings, represented as linked lists. Write a function compare() that works similar to strcmp().
    - It returns 0 if both strings are same
    - 1 if first linked list is lexicographically greater
    - -1 if the second string is lexicographically greater.

```
E.g.:
Input: list1 = g->e->e->k->s->a
       list2 = g->e->e->k->s->b
Output: -1

Input: list1 = g->e->e->k->s->a
       list2 = g->e->e->k->s
Output: 1

Input: list1 = g->e->e->k->s
       list2 = g->e->e->k->s
Output: 0
```

```java
class LinkedList{
    Node head;
    Node a, b;

    class Node{
        char data;
        Node next;

        Node(char c){
            data = c;
            next = null;
        }
    }

    int compare(Node node1, Node node2){
        if(node1 == null && node2 == null){
            return 1;
        }

        while(node1 != null && node2 != null && node1.data == node2.data){
            node1 = node1.next;
            node2 = node2.next;
        }

        // if the list are different in size 
        if (node1 != null && node2 != null) { 
            return (node1.data > node2.data ? 1 : -1); 
        } 
  
        // if either of the list has reached end 
        if (node1 != null && node2 == null) { 
            return 1; 
        } 
        if (node1 == null && node2 != null) { 
            return -1; 
        } 


        return 0; 
    }
}
```
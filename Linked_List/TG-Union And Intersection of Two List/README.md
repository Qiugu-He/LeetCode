## Union and Intersection of two Linked Lists
Given two Linked Lists, create union and intersection lists that contain union and intersection of the elements present in the given lists. Order of elements in output lists doesn’t matter.

```
E.g: 
Input:
   List1: 10->15->4->20
   lsit2:  8->4->2->10

Output:
   Intersection List: 4->10
   Union List: 2->8->20->4->15->10
```

### Solution 1: List traversal
```Java

/*
    Intersection : Traverse list1 and look for its every element in list2, if the element is present in list2, then add the element to result.

    Union: 
        - Traverse list1 and add all of its elements to the result.
        - Traverse list2. If an element of list2 is already present in result then do not insert it to result, otherwise insert.

*/

List x = new List();

void getIntersection(Node head1, Node head2) 
{ 
    Node result = null; 
    Node t1 = head1; 

    while (t1 != null) { 
        if (isPresent(head2, t1.data)) 
            x.push(t1.data); 
        t1 = t1.next; 
    } 
} 


void getUnion(Node head1, Node head2) 
{   

    Node t1 = head1, t2 = head2; 

    while (t1 != null) { 
        x.push(t1.data); 
        t1 = t1.next; 
    } 

    while (t2 != null) { 
        if (!isPresent(head, t2.data)) 
            x.push(t2.data); 
        t2 = t2.next; 
    } 
} 

```


### Solution 2: Merge Sort 

    1. Sort the both Linked List using merge sort.
    2. Linearly scan both sorted lists to get the union and intersection.


### Solution 3: HashTable
```Java

/*
    Intersection : 
        - Initialize the result list as NULL and create an empty hash table. 
        - Traverse list1. For each element being visited in list1, insert the element in the hash table.
        - Traverse list2, for each element being visited in list2, look the element in the hash table. If the element is present, then insert the element to the result list. If the element is not present, then ignore it.

    Union: 
        - Initialize the result list as NULL and create an empty hash table. 
        - Traverse both lists one by one, for each element being visited, look the element in the hash table.
        - If the element is not present, then insert the element to the result list. If the element is present, then ignore it.

*/

LinkedList getIntersection(Node head1, Node head2) 
    { 
        HashSet<Integer> hset = new HashSet<>(); 
        Node n1 = head1; 
        Node n2 = head2; 
        LinkedList result = new LinkedList(); 
  
        // loop stores all the elements of list1 in hset 
        while (n1 != null) { 
            if (hset.contains(n1.data)) { 
                hset.add(n1.data); 
            } 
            else { 
                hset.add(n1.data); 
            } 
            n1 = n1.next; 
        } 
  
        // For every element of list2 present in hset 
        // loop inserts the element into the result 
        while (n2 != null) { 
            if (hset.contains(n2.data)) { 
                result.push(n2.data); 
            } 
            n2 = n2.next; 
        } 
        return result; 
    } 


LinkedList getUnion(Node head1, Node head2) 
    { 
        // HashMap that will store the 
        // elements of the lists with their counts 
        HashMap<Integer, Integer> hmap = new HashMap<>(); 
        Node n1 = head1; 
        Node n2 = head2; 
        LinkedList result = new LinkedList(); 
  
        // loop inserts the elements and the count of 
        // that element of list1 into the hmap 
        while (n1 != null) { 
            if (hmap.containsKey(n1.data)) { 
                int val = hmap.get(n1.data); 
                hmap.put(n1.data, val + 1); 
            } 
            else { 
                hmap.put(n1.data, 1); 
            } 
            n1 = n1.next; 
        } 
  
        // loop further adds the elements of list2 with 
        // their counts into the hmap 
        while (n2 != null) { 
            if (hmap.containsKey(n2.data)) { 
                int val = hmap.get(n2.data); 
                hmap.put(n2.data, val + 1); 
            } 
            else { 
                hmap.put(n2.data, 1); 
            } 
            n2 = n2.next; 
        } 
  
        // Eventually add all the elements 
        // into the result that are present in the hmap 
        for (int a : hmap.keySet()) { 
            result.append(a); 
        } 
        return result; 
    } 
```
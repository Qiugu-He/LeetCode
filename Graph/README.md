# Graph:


## Breadth-First Search (BFS):
                1
             /     \
           2         3
          /  \
         4    5

Start at root, then explores all nodes at the present depth, then move to next depth level.
<br>Output: 1 2 3 4 5

## Depth First Search:
Starts at the root, explores as far as possible along each branch before backtracking.
1. Inorder (Left, Root, Right): 4 2 5 1 3
2. Preorder (Root, Left, Right): 1 2 4 5 3
3. Postorder (Left, Right, Root) : 4 5 2 3 1

```java
/* Binary Tree - Post order traversal */
void printPostorder(Node node) 
    { 
        if (node == null) 
            return; 
        // first recur on left subtree 
        printPostorder(node.left); 
        // then recur on right subtree 
        printPostorder(node.right); 
        // now deal with the node 
        System.out.print(node.key + " "); 
    } 

/* binary tree - inorder*/
    void printInorder(Node node) 
    { 
        if (node == null) 
            return; 
 
        /* first recur on left child */
        printInorder(node.left);   
        /* then print the data of node */
        System.out.print(node.key + " ");   
        /* now recur on right child */
        printInorder(node.right); 
    } 
/* binary tree - preorder*/
    void printPreorder(Node node) 
    { 
        if (node == null) 
            return;   

        /* first print data of node */
        System.out.print(node.key + " ");   
        /* then recur on left sutree */
        printPreorder(node.left);  
        /* now recur on right subtree */
        printPreorder(node.right); 
    } 
```


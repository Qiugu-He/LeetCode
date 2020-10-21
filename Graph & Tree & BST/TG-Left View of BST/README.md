## Print Left View of a Binary Tree

Given a Binary Tree, print left view of it. Left view of a Binary Tree is set of nodes visible when tree is visited from left side.

```
Input : 
                 1
               /   \
              2     3
             / \     \
            4   5     6             
Output : 1 2 4

Input :
        1
      /   \
    2       3
      \   
        4  
          \
            5
             \
               6
Output :1 2 4 5 6
```

```Java
 // recursive function to print left view 
void leftViewUtil(Node node, int level) 
{ 
    // Base Case 
    if (node == null) 
        return; 

    // If this is the first node of its level 
    if (max_level < level) { 
        System.out.print(" " + node.data); 
        max_level = level; 
    } 

    // Recur for left and right subtrees 
    leftViewUtil(node.left, level + 1); 
    leftViewUtil(node.right, level + 1); 
} 
```
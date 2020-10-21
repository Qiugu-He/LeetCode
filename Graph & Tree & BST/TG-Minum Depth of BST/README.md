## Find Minimum Depth of a Binary Tree

Given a binary tree, find its minimum depth. The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

```
E.g.
                1
               / \
            2       3
           / \
        4       5

The minimum height of below Binary Tree is 2.
```

```Java
/*

O(n) appraoch:

Traverse the given Binary Tree. For every node: 
    - Check if it is a leaf node. 
    - If yes, then return 1. 
    - If not leaf node then if the left subtree is NULL, 
    - then recur for the right subtree. And if the right subtree is NULL, then recur for the left subtree. 
    - If both left and right subtrees are not NULL, then take the minimum of two heights.
*/

int minimumDepth(Node root) 
{ 
    if (root == null) 
        return 0; 

    // Base case : Leaf Node. This accounts for height = 1. 
    if (root.left == null && root.right == null) 
        return 1; 

    // If left subtree is NULL, recur for right subtree 
    if (root.left == null) 
        return minimumDepth(root.right) + 1; 

    // If right subtree is NULL, recur for left subtree 
    if (root.right == null) 
        return minimumDepth(root.left) + 1; 

    return Math.min(minimumDepth(root.left), 
                    minimumDepth(root.right)) + 1; 
} 
```
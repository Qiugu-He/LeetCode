## Check whether a binary tree is a full binary tree or not

A full binary tree is defined as a binary tree in which all nodes have either zero or two child nodes. Conversely, there is no node in a full binary tree, which has one child node.

```
To check whether a binary tree is a full binary tree we need to test the following cases:-

1) If a binary tree node is NULL then it is a full binary tree.
2) If a binary tree node does have empty left and right sub-trees, then it is a full binary tree by definition.
3) If a binary tree node has left and right sub-trees, then it is a part of a full binary tree by definition. In this case          recursively check if the left and right sub-trees are also binary trees themselves.
4) In all other combinations of right and left sub-trees, the binary tree is not a full binary tree.
```

```Java
class BinaryTree  
{ 
    Node root; 
       
    /* this function checks if a binary tree is full or not */
    boolean isFullTree(Node node) 
    { 
        // if empty tree 
        if(node == null) 
            return true; 
           
        // if leaf node 
        if(node.left == null && node.right == null ) 
            return true; 
           
        // if both left and right subtrees are not null 
        // and they are full 
        if((node.left!=null) && (node.right!=null)) 
            return (isFullTree(node.left) && isFullTree(node.right)); 
           
        // if none work 
        return false; 
    } 
}
```
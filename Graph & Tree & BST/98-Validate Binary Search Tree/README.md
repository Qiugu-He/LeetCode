## 98. Validate Binary Search Tree

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

```
    2
   / \
  1   3

Input: [2,1,3]
Output: true


    5
   / \
  1   4
     / \
    3   6

Input: [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```

```Java
    public class Solution {
        public boolean isValidBST(TreeNode root) {
            //helper
            return isValid(root, null, null);
        }

        public boolean isValid(TreeNode root, Integer lower_Limit, Integer uper_Limit) {

            /*
                     5
                    / \
                   1   4
                        / \
                        3   6
            
            */
            if(root == null) 
                return true;
            if(lower_Limit != null && root.val <= lower_Limit) 
                return false;
            if(uper_Limit != null && root.val >= uper_Limit) 
                return false;

            return isValid(root.left, lower_Limit, root.val) && isValid(root.right, root.val, uper_Limit);
        }
}

```
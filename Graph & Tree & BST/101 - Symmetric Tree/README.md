## 101. Symmetric Tree

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

```
For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

    1
   / \
  2   2
 / \ / \
3  4 4  3


But the following [1,2,2,null,3,null,3] is not:

    1
   / \
  2   2
   \   \
    3    3
```

```Java
/*  
            R
        
        L       R

---------------------->>>>>>>>>>>>>>>>>>>>>>>>>>>>

            r       mirror          r
        
        L       R               R        L

    
    Iterative:
        - Using queue, each two consecutive node should equal, and mirror subtrees should equal

        - First, queue contains: root and root
        - Then algorithms works with some key differences.
        - Each time the two nodes are extracted and their value are compared
        - Then the right & left child are inserted in the queue.
        - Algorithm stops when either the queue is empty, or we detect that the tree is not symmetric 
*/

class Solution {
    public boolean isSymmetric(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        
        q.add(root);
        q.add(root);
        
        while(!q.isEmpty()){
            TreeNode n1 = q.poll();
            TreeNode n2 = q.poll();
            
            if(n1 == null && n2 == null) return true;
            if(n1 == null || n2 == null) return false;
            
            if(n1.val != n2.val) return false;
            
            q.add(n1.left);
            q.add(n2.right);
            
            q.add(n1.right);
            q.add(n2.left);
        }
        
        return true;
    }
}

/*
    Recursive


*/
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return helper(root, root);
    }

    public boolean helper(TreeNode n1, TreeNode n2){
        if(n1 == null && n2 == null) return true;
        if(n1 == null || n2 == null) return false;

        return (n1.val == n2.val) && helper(n1.right, n2.left) && helper(n1.left, n2.right);
    }
}


```
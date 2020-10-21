## Maximum Path Sum in a Binary Tree
Given a binary tree, find the maximum path sum. The path may start and end at any node in the tree.

```
E.g.

Input: Root of below tree
       1
      / \
     2   3
Output: 6

See below diagram for another example.
1+2+3

```

```Java
class BST{

    //..


    int findMaxUtil(Node node, Res res) {
        // Base Case 
        if (node == null) 
            return 0; 
        
        // l and r store maximum path sum going through left and 
        // right child of root respectively 
        int l = findMaxUtil(node.left, res); 
        int r = findMaxUtil(node.right, res); 


        // Max path for parent call of root. This path must 
        // include at-most one child of root 
        int max_single = Math.max( Math.max(l, r) + node.data,  node.data); 

        // Max Top represents the sum when the Node under 
        // consideration is the root of the maxsum path and no 
        // ancestors of root are there in max sum path 
        int max_top = Math.max(max_single, l + r + node.data); 

        // Store the Maximum Result. 
        res.val = Math.max(res.val, max_top);

        return max_single; 
    }
  
    // Returns maximum path sum in tree with given root 
    int findMaxSum(Node node) { 
  
        // Initialize result 
        // int res2 = Integer.MIN_VALUE; 
        Res res = new Res(); 
        res.val = Integer.MIN_VALUE; 
  
        // Compute and return result 
        findMaxUtil(node, res); 
        return res.val; 
    } 

    int findMaxSum() { 
        return findMaxSum(root); 
    } 
}
```


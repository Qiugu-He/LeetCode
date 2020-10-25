## 108. Convert Sorted Array to Binary Search Tree



```Java
/*
    Solution: Similary to the Binary search

     - Find the mid index;
     - creat the node as parent node
     - assing the left child of this node by recursivly passing the left part of array
     - assign the right child of this node by recursivly passing the right part of array
     - return the node as root;
*/
public TreeNode sortedArrayToBST(int[] num) {
    if(num.length == 0)
        return null;

    TreeNode root = helper(num, 0, num.length -1);

    return root;
}

public TreeNode helper(int[] num, int low, int high) {

    if(low > high) return null;

    int mid = low + (low+high)/2;

    TreeNode node = new TreeNode(num[mid]);
    node.left = helper(num, low, mid-1);
    node.right = helper(num, mid+1, high);

    return node;
    
}
```
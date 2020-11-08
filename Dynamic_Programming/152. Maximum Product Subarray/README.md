## 152. Maximum Product Subarray

Given an integer array nums, find the contiguous subarray within an array (containing at least one number) which has the largest product.

```
Example 1:

Input: [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
Example 2:

Input: [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```

```Java
class Solution {
    public int maxProduct(int[] nums) {
        int maxSoFar = nums[0], minSoFar = nums[0];
        int res = nums[0];
        
        for(int i =1; i< nums.length; i++){
            maxSoFar *= nums[i];
            minSoFar *= nums[i];
            
            if(nums[i] < 0){
                int temp = maxSoFar;
                maxSoFar = minSoFar;
                minSoFar = temp;
            }
            
            maxSoFar = Math.max(maxSoFar, nums[i]);
            minSoFar = Math.max(minSoFar, nums[i]);
            
            res = Math.max(res,maxSoFar);
        }
        
        return res;
    }
}
```
## #53. Maximum Subarray
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.
```
    Input: [-2,1,-3,4,-1,2,1,-5,4],
    Output: 6
    Explanation: [4,-1,2,1] has the largest sum = 6.
```

## 0(n) Solution
```Java
/* 
Pseudo
    result, curSum = 0
    Loop through the array
        1. curSum: max{ curSum + array[i], array[i] }
            
       2.  result = max{ result, curSum }
    return result
    
For example: 
    A = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

    i        ->     0   1   2   3   4   5   6   7   8 
    array[i] ->     -2  1   -3  4   -1  2   1   -5  4
    curSum   ->  0  -2  1   -2  4   3   5   6   1   5 
    result   ->  0  0   1   1   4   4   5   6   6   6   

This alrightm is kind like string aligin algs.

*/
public class Solution {
    public int maxSubArray(int[] nums) {
        int res = Integer.MIN_VALUE, curSum = 0;
        for(int num: nums){
            curSum = Math.max(curSum + num, num);
            res = Math.max(res, curSum);
        }
        
        return res;
    }
}
/*
Time complextiy : O(n)
*/
```





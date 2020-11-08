## 268. Missing Number

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

Follow up: Could you implement a solution using only O(1) extra space complexity and O(n) runtime complexity?

 

Example 1:

Input: nums = [3,0,1]
Output: 2
Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.
Example 2:

Input: nums = [0,1]
Output: 2
Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.

```Java
class Solution {
    public int missingNumber(int[] nums) {
        Arrays.sort(nums);
        
        //ensure n is at the last index
        if(nums[nums.length-1] != nums.length)
            return nums.length;
        else if(nums[0] != 0)//ensure 0 is at the fist index
            return 0;
            
        
        //find missing numbers
        for(int i = 1; i< nums.length; i++){
            if(nums[i-1] + 1 != nums[i])
                return nums[i-1] + 1;
                
        }
        
        return -1;
    }
}
```
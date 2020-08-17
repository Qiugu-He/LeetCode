## #26. Remove Duplicates from Sorted Array
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
```
    Example:
    Given nums = [1,1,2],

    Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
```

## Solution: Two Pointer
```Java
/* Pseudo
    using two pointers
    i -> slow runner
    j -> fast runner
    
    when looping: 
        if count nums[i] == nums[j], found duplicate, increment j to skip duplicate
        if count nums[j] != nums[i], increment slow runner, place its value with nums[j]
*/

class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums.length == 0) return 0;

        int i =0;
        for(int j = 1; j< nums.length; j++){
            if(nums[j] != nums[i]){
                i++; // increase slow runner
                nums[i] = nums[j]; // 
            }
        }
        return i+1;
    }
}

/*
Time complextiy : O(n)
Space complexity : O(1)
*/
```





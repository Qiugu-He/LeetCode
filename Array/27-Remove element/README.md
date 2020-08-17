## #26. Remove Element
Given an array nums and a value val, remove all instances of that value in-place and return the new length.
```
    Example:
    Given nums = [3,2,2,3], val = 3,

    Your function should return length = 2, with the first two elements of nums being 2.

    It doesn't matter what you leave beyond the returned length.
```

## Solution: Two Pointer
```Java
/* Pseudo
    using two pointers
    i -> slow runner
    j -> fast runner
    
    i start at 0
    when looping: 
        if count nums[i] == val found value, increment j to remove it
        if count nums[j] != val
            replace nums[i] with nums[j]
            i++
*/
class Solution {
    public int removeElement(int[] nums, int val) {
        int i =0;
        for(int j =0; j< nums.length; j++){
            if(nums[j] != val){
                nums[i] = nums[j];
                i++;
            }
        }
        
        return i;
    }
}
/*
Time complextiy : O(n)
Space complexity : O(1)
*/
```





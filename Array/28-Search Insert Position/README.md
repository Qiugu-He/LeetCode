## #35. Search Insert Position
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
```
    Example:
    Input: [1,3,5,6], 5
    Output: 2

    Example: 
    Input: [1,3,5,6], 2
    Output: 1
```

## Solution: Binary Search
```Java
/* Pseudo
    Regular Binary Search to goes to the proper position for the target

    If the target not found, we got satrt & end pointer, compare them pointer with target to find the insert position
        - if nums[start] >= target
            return start
        - else if nums[end] < targer
            return end+1
        -else 
            return end
*/
class Solution {
    public int searchInsert(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1; // the last index
        
        //Binary search
        while (start + 1 < end){
            int mid = start + (end - start )/2;
            if(nums[mid] == target){
                return mid;
            }
            //goes right half
            else if(nums[mid] < target){
                start = mid;
            }
            //goes left half
            else{
                end = mid;
            }
        }
        
        //find the insertion position
        if(nums[end] < target){
            return end + 1;
        }else if(nums[start] >= target){
            return start;
        }else{
            return end;
        }
    }
}
/*
Time complextiy : O(log n)
*/
```





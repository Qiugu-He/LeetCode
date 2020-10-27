Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example:
```
Input: [3,2,3]
Output: 3

Input: [2,2,1,1,1,2,2]
Output: 2

```
Solution - O(n)
```Java
    /*
        The stragegy is using two pointers to scan the array from both side
    */
    class Solution {
        int majorityCount = nums.length/2;

                for (int num : nums) {
                    int count = 0;
                    for (int elem : nums) {
                        if (elem == num) {
                            count += 1;
                        }
                    }

                    if (count > majorityCount) {
                        return num;
                    }

                }

        return -1;    
    }
```
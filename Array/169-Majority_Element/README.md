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
        public int[] twoSum(int[] numbers, int target) {
            if(numbers == null || numbers.length == 0)
                return ull;
            int i =0;
            int j = numbers.length -1;

            while(i < j){
                int check = numbers[i]+numbers[j];

                if(check < target){
                    i++;
                }else if(check > target){
                    j--;
                }else{
                    return new int[]{i+1, j+1};
                }
            }
        }
    }
```
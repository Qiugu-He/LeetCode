## 136. Single Number

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

```
Input: nums = [2,2,1]
Output: 1

Input: nums = [4,1,2,1,2]
Output: 4

Input: nums = [1]
Output: 1
```
```Java
class Solution {
    public int singleNumber(int[] nums) {

        /*
            Map<Key, Frequence>
        */
        HashMap<Integer, Integer> table = new HashMap<>();
        
        for(int i: nums){
            table.put( i, table.getOrDefault(i, 0)+1);
        }
        
        for(int i: nums){
            if(table.get(i) == 1){
                return i;
            }
        }
        
        return 0;
    }
}
```
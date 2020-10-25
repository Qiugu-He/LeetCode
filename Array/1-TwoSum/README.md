## #1 - Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.
```
    Example:
    Given nums = [2, 7, 11, 15], target = 9,

    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].
```

## Solution 1: Brute Force
```Java
/*
Simply using a nested loop to loop through the array and find the indices

Time complexity : O(n^2) 
Space Complexity: O(1)
*/
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i = 0; i< nums.length; i++){
            for(int j=i+1 ; j< nums.length; i++){
                if(nums[j] == target - nums[i]){
                    return new int[] {i ,j};
                }
            }
        }
        
    throw new IllegalArgumentException("No two sum solution");
    }
}
```

## Solution 2: two pass Hash Table
```Java
/*
    Build a Hash table to check if the complement exists in the array

    Time complexity : O(n) 
    Space Complexity: O(n)
*/
class Solution {
    public int[] twoSum(int[] nums, int target) {

        //Map <Key, Value>
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int i =0; i< nums.length; i++){
            map.put(nums[i], i);
        }
        
        for(int i =0; i< nums.length; i++){
            //check complement
            int complement = target - nums[i];
            if(map.containsKey(complement) && map.get(complement) != i ){
                return new int [] {i, map.get(complement)};
            }
        }
        
         throw new IllegalArgumentException("No two sum solution");
    }
}

```
```
Data Structure: HashMap 
Map<key, value> map = new HashMap<>();
map.put(k,v)   //add value 
map.get(k)      //get value by a given key
map.containsKey(k) // check if a given key exists in HashMap
map.containsValue(v) // check if a given value exists in HashMap
```





## #1.1. Is Unique: Implement an algorithm to determine if a string has all unique characters. What if you cannot use additional data structures? 


## Solution 1: 
```Java

/*
Using an array of boolean values, where the flag at index i indicates whether character i in the alphabet is contained in the string. Immediately return false if the string length exceeds the number of unique characters in the 128 alphabet

*/
class Solution { 
    Public boolean isUniqueChars(String str){
        if(str.length () > 128)
            return false;
        
        boolean []char_set = new boolean[128];

        for(int i =0; i < str.length(); i++){
            int val = str.charAt(i);

            if(char_set[val]){
                return false;
            }

            char_set[val] = true;
        }

        return true;
    }
}

```





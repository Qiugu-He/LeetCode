## 28. Implement strStr()
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

```
Example 1:

Input: haystack = "hello", needle = "ll"
Output: 2
Example 2:

Input: haystack = "aaaaa", needle = "bba"
Output: -1
Example 3:

Input: haystack = "", needle = ""
Output: 0
```

```Java
/*
    Brute Force Approach:

    - Loop through the first string
        - using a temp value store curr index
    - Loop through the second string
        - if found the first letter
        - continue check the remainding of str1 and str2
        - return i when finishd
    
    return -1 

*/
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle == null || haystack == null)
            return 0;
        
        if(needle.length() == 0)
            return 0;
    
        
        for(int i =0; i< haystack.length(); i++)
        {   
            if( i + needle.length() > haystack.length())
                return -1;
            
            int curr = i;
            for(int j = 0; j< needle.length(); j++)
            {
                if(haystack.charAt(curr) == needle.charAt(j))
                {
                    if(j == needle.length()-1)
                         return i;
                    curr++;
                }else
                {
                    break;
                }
            }//innter for
        }//outter for   
        
        return -1;
   }
}
```
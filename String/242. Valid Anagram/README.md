### 242. Valid Anagram

Given two strings s and t , write a function to determine if t is an anagram of s.

Example 1:

Input: s = "anagram", t = "nagaram"
Output: true
Example 2:

Input: s = "rat", t = "car"
Output: false


```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length())
            return false;
        
        int []letters = new int[128];
        char[]s_array = s.toCharArray();
        
        for(char c: s_array){
            letters[c]++;
        }
        
        for(int i =0; i< t.length(); i++){
            int c = (int)t.charAt(i);
            letters[c] --;
            if(letters[c] < 0)
                return false;
        }
        return true;
        
    }
}

```